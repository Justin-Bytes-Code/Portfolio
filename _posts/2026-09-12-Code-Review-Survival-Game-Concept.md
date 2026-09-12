---
title: "Code Review: Survival-Game-Concept"
excerpt_separator: "<!--more-->"
categories:
  - Code Review
  - UE5
tags:
  - Post Formats
  - readability
  - Code Review
  - standard
  - SNHU
  - UE5
---

Hey Everyone!

For my final Capstone at SNHU I was tasked with looking at some of the older games I have made in the development of my time at this SNHU as someone who is now about to graduate. The first thing I thought of was *"Oh this is going to be embarrassing!"*, which I was completely right! After looking at my older code for a while I realized I made so many mistakes back in the day that were extremely silly to make. As it was required by class to spend a week polishing the game (while not completely rewriting it) to make it a bit nicer for a portfolio; I wanted to make a semi post mortem/code review just for fun. I also wanted a chance to talk about thing I have learned from then along with how I would approach the same situation much differently if given a chance to do a complete rewrite instead of polish. 

This project was made using mainly C++ but also does have a small aspect of blueprints for the UI elements. While I could talk about the blueprints for this code review I would only like to talk about the C++ as that's where the bulk of the code is and what this project is suppose to be demonstrating. 

The project can be found [Here](https://github.com/Justin-Bytes-Code/Survival-Game-Concept) on my Github. 

<!--more-->

---

First I'd like to say the biggest issue with this entire project I really wish I was allowed to change for my polishing. Is where the code actually is. A major part of the code is located inside the: `PlayerChar.cpp` & `PlayerChar.h`. 
This is an issue for **multiple** reasons such as refactoring, tweaking, testing, and expandability along with even more. With a smaller game project, such as this one, it could be alright but a good programmer should always plan for expandability rather then expecting it will never be expanded upon or looked on again by another programmer.The larger issue is that several different gameplay systems are being handled directly inside `PlayerChar.cpp.` While player-specific logic belongs in the player class, systems such as resource management and building could be separated into their own components or classes as the project grows. You should try to the best of your ability to make every system modular to the best ability you can. While this can be seen as a time waste by some other people I'd argue the opposite, if you ever need the code later you will be thanking yourself in the past for having the forethought for making it a lot easier on yourself to scan through your code. This also is in general a great habit to develop like all of OOP principals, as it stops a lot of redundant code from having to be written along with heavily speeds up your development time. 

<!--more-->

---

Breaking down the code I'd like to talk about this at the start of `PlayerChar.cpp`

```
  BuildingArray.SetNum(3);
	ResourcesArray.SetNum(3);
	ResourcesNameArray.Add(TEXT("Wood"));
	ResourcesNameArray.Add(TEXT("Stone"));
	ResourcesNameArray.Add(TEXT("Berry"));
```

While this code is functional and does work as intended it could be written in a cleaner nicer way while still allowing for expandability. I'd change the initialization and data structure to make the resource system dynamically scalable. I manually initialized the array to a size of 3, which creates unnecessary rigidity. It also introduces the *"Magic Number"* issue as let's say later down the line we want to add 100s of resources. We would have to memorize the size was 100 then remember to add to that number if we ever decided to add more or less which could cause issues in the future. 

<!--more-->

---

Another section of my code I heavily did improve upon even if I wasn't allowed to "completely rewrite the code" is 
```
void APlayerChar::SetHealth(float amount)
{
	if (Health + amount < 100)
	{
		Health = Health + amount;
	}
}

void APlayerChar::SetHunger(float amount)
{
	if (Hunger + amount < 100)
	{
		Hunger = Hunger += amount;
	}
	else {
		Hunger = 100;
	}
}

void APlayerChar::SetStamina(float amount)
{
	if (Stamina + amount < 100)
	{
		Stamina = Stamina + amount;
	}
}

void APlayerChar::DecreaseStats()
{
	if (Hunger > 0)
	{
		SetHunger(-1.0f);
	}
	
	SetStamina(10.0f);

	if (Hunger <= 0)
	{
		SetHealth(-3.0f);
	}
}
```

The first thing you might notice is *"there isn't a singular comment!"*. Which is a good thing to notice but the bigger issue the naming convention + logic. For an example naming a function ``void APlayerChar::SetHealth(float amount)`` might make you think it's to set a player health function but it's actually a additive healing function intended to heal the player. I would rename it something like ``GainHealth`` instead then add a smaller comment explaining what it does. This is also true for a function named ``void APlayerChar::DecreaseStats()`` it only decreases 2 stat which a better way to write this might be ``void APlayerChar::PassiveHungerDrain()``

There is also the issue with the logic. The logic in almost all of these isn't set up in a scalable/Modular way. Firstly they all include the *"Magic Number"* issue I spoke about before where there is no context for most of these variables which could lead other programmers confused. They also could lead to hard coded numbers which could cause issues in the future. For an example a game designer says *"Hey Justin, let's make the player health around 150 instead of 100"*. You'd have to manually go in and change a lot of variables as now ``if (Health + amount < 100)`` doesn't work anymore. There is also edge case logic that is a even larger issue in this code. For this example we are going to use this snippet. 

```
void APlayerChar::SetHealth(float amount)
{
	if (Health + amount < 100)
	{
		Health = Health + amount;
	}
}

```
Let's say Your health is at 80 and you eat a berry which heals you for 30. It would be 80 + 30 which means your *new* health value is 110 and 110 < 100 isn't true. This means you would need the **EXACT** amount of healing to regain HP to max again. This could be easily fixed by fixing this line of code or adding another snippet for *KISS* simplicity like:
```
else if (Health + amount >= MaxHealth)
{
  Health = MaxHealth;
}
```
This could easily fix the code while not introducing complex logic to the problem that might make it a bit harder to read. 


<!--more-->

---

Now for the big one which is the ``FindObject()`` function where **MOST** of the game logic is stored and has deep nesting issues along with no comments. 

```
void APlayerChar::FindObject()
{
	FHitResult HitResult;
	FVector StartLocation = PlayerCamComp->GetComponentLocation();
	FVector Direction = PlayerCamComp->GetForwardVector() * 800.0f;
	FVector EndLocation = StartLocation + Direction;

	FCollisionQueryParams QuaryParams;
	QuaryParams.AddIgnoredActor(this);
	QuaryParams.bTraceComplex = true;
	QuaryParams.bReturnFaceIndex = true;

	if (!isBuilding)
	{
		if (GetWorld()->LineTraceSingleByChannel(HitResult, StartLocation, EndLocation, ECC_Visibility, QuaryParams))
		{
			AResource_M* HitResource = Cast<AResource_M>(HitResult.GetActor());

			if (Stamina > 5.0f)
			{
				if (HitResource)
				{
					FString hitName = HitResource->resourceName;
					int resourceValue = HitResource->resourceAmount;

					HitResource->totalResource = HitResource->totalResource - resourceValue;

					if (HitResource->totalResource > resourceValue)
					{
						GiveResource(resourceValue, hitName);

						matsCollected = matsCollected + resourceValue;

						objWidget->UpdatematOBJ(matsCollected);

						check(GEngine != nullptr);
						GEngine->AddOnScreenDebugMessage(-1, 5.0f, FColor::Red, TEXT("Resource Collected"));

						UGameplayStatics::SpawnDecalAtLocation(GetWorld(), hitDecal, FVector(10.0f, 10.0f, 10.0f), HitResult.Location, FRotator(-90, 0, 0), 2.0f);

						SetStamina(-5.0f);

					}
					else
					{
						HitResource->Destroy();
						check(GEngine != nullptr);
						GEngine->AddOnScreenDebugMessage(-1, 5.0f, FColor::Red, TEXT("Resource Depleted"));

					}
				}
			}
		}

	}

	else
	{
		isBuilding = false;
		objectsBuilt = objectsBuilt + 1.0f;

		objWidget->UpdatebuildObj(objectsBuilt);
	}


}
```

This is probably the most egregious example on the list. ``FindObject()`` is doing way to much for the start as it's responsible for:

* Performs a line trace
* Determines what was hit
* Checks stamina
* Collects resources
* Updates resource totals
* Updates the objective UI
* Displays debug messages
* Spawns a decal
* Changes stamina
* Handles building
* Updates the building objective

That's way to much for 1 function to be handling and could be broken down in multiple smaller functiones. Which it could look something like this:

* ``TraceForObject()``
  * Handles line traces for objects
* ``HandleResource()``
  * Handles resource gathering
* ``CollectResource()``
  * Handles the math values of resource gathering
* ``UpdateObjective()``
  * Handles Objectives

A simple change like this would make the function much easier to read and most likely even prevent issues arising in the future of being unable to find bugs. 

There is also the issue of the naming convention like before ``FindObject()`` isn't a descriptive name. It could be renamed to ``InteractWithObject()`` instead with a smaller comment explaining the functionality.

Magic numbers is also the biggest issue inside this function. So many numbers are purely magic numbers which is going to make almost anyone confused if you try to code with it or tinker with it in the future. Even though I made the code 2 years ago I still struggled to understand what was even going on until I read it slowly / played the game a bit to understand it. Like stated before this is a huge issue going forward as if any value changes; for instance the ``SetStamina(-5.0f);`` which is a stamina drain. You'd have to find every variable of a 5 to change it. 

There is also the issue of logic problems much like the other issues I did found here: 

```
HitResource->totalResource = HitResource->totalResource - resourceValue;

if (HitResource->totalResource > resourceValue)
{
    GiveResource(resourceValue, hitName);
    ...
}
else
{
    HitResource->Destroy();
}
```

While the code does work I am subtracting the resource value before checking whether there is enough resources that remain. This could cause an issue in the future where the player destroys a resource without having received the final amount. This is horrible for the player experience as it's going to seem like the game is either broken or your input didn't register correctly.  

<!--more-->

Most of the code here has been redone and is currently available on my Github located [Here](https://github.com/Justin-Bytes-Code/Survival-Game-Concept)
