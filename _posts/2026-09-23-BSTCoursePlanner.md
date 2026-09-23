---
title: "Code Review: BSTCoursePlanner"
excerpt_separator: "<!--more-->"
categories:
  - Code Review
  - C++
  - Algorithm
tags:
  - Data Structure
  - Algotithm
  - readability
  - Code Review
  - standard
  - SNHU
---

Hey Everyone!

For my final capstone at SNHU, I was tasked with revisiting some of my older projects and polishing them with the skills I have developed throughout my degree. One of the areas recommended for improvement was algorithms, which led me to go back through my GitHub and look at some of the projects I had not touched in a couple of years.

While looking through my older work, I came across one of my final projects from my Algorithms and Data Structures course: **BSTCoursePlanner**. At first glance, it is a relatively simple console application, but it was one of the first larger projects where I had to implement and work with a more involved algorithm. At the time, building and understanding a Binary Search Tree was a significant challenge for me. Revisiting this project several years later gave me an opportunity to look at the code from a completely different perspective. Instead of simply making the application work, I could now identify areas where the original implementation could be improved and apply what I have learned since building it.

The best part about this project is this is when I started coding semi-competently! I started making a lot of basic mistakes and errors so this code review will be a lot smaller then my previous code review that could be found [Here](https://justin-bytescode.github.io/Portfolio/code%20review/ue5/games/Code-Review-Survival-Game-Concept/) 

As hinted by the name of this project, this project is to demonstrate my ability to use an algorithm that would work best inside this file structure. I wouldn't exactly call it a "Complex" project in the same scope as my other projects but this assignments only purpose to demonstrate my knowledge in a realistic world scenario of being given data and figuring out what to do with it along with figuring out ways to assist the client. 

For this assignment the client wanted to search up courses in the CSV file then select courses to see what prerequisites students might have to take. This instantly made me start to think specifically about the requirement "Searching". Searching is a keyword when deciding an algorithm to use to handle a data set. Notably they also didn't say anything about deleting or inserting from the search tree as they were importing it from a file. This heavily narrowed it down to a few common data structures that allow for fast searching. A couple of these were Hashmaps, Binary Search Trees, and Sorted Arrays. I then went 1 by 1 thinking about the requirements again of how they want to search and then do another check to see more information on the course they found. A HashMap was another possible option because course codes could be used as keys to retrieve course information. However, I wanted the data structure to maintain an ordered relationship between course codes while also supporting future insertion and deletion operations. This instantly chopped out HashMap. This also removed a sorted Array (A sorted array would be great for a dataset that doesn't change often or is constantly loaded. For this assignment a requirement is that they load it in from a CSV which means the contents might be shifted or changed often). This left me with a Binary Search Tree. 

A Binary search tree(BST) would be a great choice for this sort of dataset as it maximizes the searching power of trying to find an item while also allowing for flexibility if in the future they wanted to add deletion or insertion operations into the program. While a BST could be a bit slower with deletion or insertion it still would allow for that type of expansion unlock some other algorithms. So to summarize... 

# How To Pick Your Data Structure

- Figure out the requirements of the client first
- Look for primary operations along with keywords like Searching, Deleting, Inserting, Changing Files, Changing Data, and Speed
- Once you found those keywords Start to look at data structures that are great at that specific thing while still allowing for potential expansion.
- Check the dataset if provided a sample. This might change your opinion of available data sets 
- Eliminate the options that doesn't fit the requirements wlel
- Choose the structure whose tradeoffs best fit the project

# The Code

As stated previously the code is a lot better then my [Previous Code Review](https://justin-bytescode.github.io/Portfolio/code%20review/ue5/games/Code-Review-Survival-Game-Concept/). But much like everything in life there is always room for improvement which is why code reviews are important. The first issue I noticed when checking the code inside a IDE was: 
```
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <algorithm>
#include <cctype>
```
While this doesn't look like anything on here in my IDE *``#include <algorithm>``* was greyed out giving a warning sign. Which means this include isn't used at all inside the file. While this is small it could turn into a bigger issue when your including lots of libraries and your trying to reduce all dependencies this specific file could need. Including random files could get extremely annoying in the future if the problem gets bad later which is why it's important to fix it now. 

Going a little further down in the code you'll see this line in ``Main()``
```
CourseTree* myCourseTree = new CourseTree();
```
This is one of the first thing that executes in main when the program runs. Which dynamically allocates memory. That's fine in practice and completely acceptable but there is one thing missing inside the main function too, a ``delete`` or a deconstructor. This means if the ``main()`` finishes the pointer will disappear but the memory allocated by ``new CourseTree()`` wasn't released. While this is a smaller program and can definitely be fine if this leak stays it's still a huge issue that will need to be fixed if you want to build programs that are scaleable. This issue could also be worse if you factor in how I was creating nodes. 
```
root = new Node(course);
current->left = new Node(course);
current->right = new Node(course);
```
I am creating nodes the proper way and unlike before where I completely forgot a ``delete`` I remembered this time. The issue is, it doesn't do this unless the program is deleting that specific node. Meaning if you close the program the memory could still be allocated. 

Now onto a silly mistake I realized only during this coding review
```
        switch (menuChoice) {

        case 1: {
            std::cout << "Enter CSV file name "
                << "(HINT: with .csv extension): ";

            std::cin >> currentFile;

            loadCourses(currentFile, myCourseTree);

            dataLoaded = true;

            break;
        }
```
This is the menu selection specifically for ``1. Load Courses from File``. This has a funny logical issue where no matter what you attempt to load into the program it will always change ``dataLoaded`` to true! This is a small simple mistake that could entirely be fixed by just adding 1 small check after selecting that option. For an example something like: 
```
if (!file.is_open()) {
    std::cout << "Error: Could Not Open File "
        << csvFile << std::endl;
    return;
}
```
This would allow for the other menu options not to run after you failed to load a file into the program. Also preventing any bugging that could occur due to it always being true.


The project can be found [Here](https://github.com/Justin-Bytes-Code/BSTCoursePlanner) on my GitHub. 
