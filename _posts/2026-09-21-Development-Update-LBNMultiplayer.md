---
title: "Development Update: Lucky Brain Noodle Multiplayer Update"
excerpt_separator: "<!--more-->"
tagline: "This is a custom tagline content which overrides the default page excerpt."
header:
  overlay_image: /assets/images/Games/LuckyBrainNoodle/LuckyBrainNoodles.jpg
  caption: "Lucky Brain Noodle Concept Art"
categories:
  - UE5
  - Development Update
  - LBN
  - Games
tags:
  - readability
  - standard
  - Development Update
  - UE5
  - Games
  - Multiplayer
  - Steam
---




Hey Everyone!

It's been quite a while since my last update for my super secret project I hinted about a couple months ago. This isn't because a lack of trying but just time. As some of you may know I'm actually graduating college soon! While this is an exciting time for most people for me it's an extremely stressful one. This leads to having to not work on the game for a bit longer then I personally would have liked. Boring personal stuff aside however, I'm happy to announce the title of my top secret project! 

<!--more-->

It's called: 
# Lucky Brain Noodle! 
<sub>Don't tell anyone just yet though... </sub>

<!--more-->

*"Lucky Brain what now?"* 

Some of you could be asking. To which I say if you want information about it though your gonna have to wait a *little* bit longer as we are still finalizing some of the final things for the big beta release where we are gonna have a whole big party with it. 

*"Well why the big development blog announcement then?"*

While we did want to talk a bit about the development and the **HUGE** milestone we just hit, which is Steam integrated Multiplayer functionality! Before that though I wanted to take a second and talk about some of the under the hood development of the game which could help other developers in the future as LBN did have it's fair share of trials that it went through. In the future I'll most likely talk more about LBN development in future blogs, as it really was a big part of what I did in my off time at college. For this blog specifically we are going to be talking about Multiplayer Functionality in UE5 and common pitfalls. It's going to cover not only the mistakes I made but hopefully serve as a cautionary tale for things to look out for if you plan to make a game multiplayer. 

First thing first. If you want a game to be multiplayer have this in mind when you start the game. While I was lucky enough to have known since the beginning if the game was co-op, I seen multiple people where they decided it randomly half way through development of their game try to include multiplayer inside their plans. This should be something that you decide as soon as you start your project as it will heavily effect the way you make your games logic going forward especially in Unreal Engine especially with blueprints. Unreal Engine blueprints are extremely helpful during the development of the game. It could rapidly speed up the prototyping efforts which is wonderful when your in that stage of development or want to test something without having too much commitment. While it does fall short in some area's like math and compile time Where I'd argue it falls short the hardest is the networking section. While you completely can make a multiplayer game using Unreal Engine's blueprint network features you will learn extremely quickly it's quite limiting especially when it comes to trying to add multiplayer to systems you developed in blueprint. A large part of this is due to the simplicity of blueprints. For an example if you wanted to make a small emote that plays for all players you will need at minimum: A ServerRPC, A MultiRPC, A function to call both RPCs, Branches checking Authority, Replicated Variables, and references to other actors. 
