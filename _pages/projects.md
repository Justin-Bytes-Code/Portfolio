---
title: "All Projects"
layout: splash
permalink: /projects/
author_profile: true

header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: assets/images/Games/LuckyBrainNoodle/LBN1.jpg
  # actions:
  #  - label: "Download"
  #    url: "#test-link"
 excerpt: "These are all the projects I've been apart of!"

game_row:
  - image_path: assets/images/Games/LuckyBrainNoodle/LuckyBrainNoodles.jpg
    title: "Lucky Brain Noodle"
    excerpt: "Lucky Brain Noodle is my most recent game project currently still in development using C++ and Unreal Engine 5, the game is a multiplayer Co-op beat them up that works through the steam API, made with custom combat mechanics and almost every asset is hand made by me and my girlfriend."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/c++/games/ue5/multiplayer/coop/steam%20integrated/ai/Learn-More-LuckyBrainNoodle/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/SurvivalGameConcept/Survival Game Background.png
    title: "Survival Game Concept"
    excerpt: "Survival Game Concept is a Unreal Engine 5 prototype I developed primarily in C++ that shows the core mechanics of a survival game. It's designed to be simple to understand along with to implement in any project. Features include resource gathering, animal placeholders, a stamina system, and a free form building system."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/c++/games/Learn-More-SurvivalGameConcept/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/FirstPersonGamePrototype/First Person Game Prototype.png
    title: "First Person Game Prototype"
    excerpt: "First Person Game Prototype is a Unreal Engine 5 project I made with C++ and Blueprints to make a simple mechanics that could be added to any first person shooter. Some of these features are projectile effects, terrain deformation, portal-based teleportation, and procedural terrain generation. It's built so other users can see the code and add it to their game."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/c++/games/Learn-More-FirstPersonGamePrototype/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"

software_row:
  - image_path: assets/images/Projects/Apps/TrackerPet/TrackerPetSnip.png
    title: "Tracker Pet"
    excerpt: "Tracker Pet is an Android application I developed for animal breeders in Java that helps users manage animals and track important information. The idea mainly came from my father as he is a snake breeder and there is no good apps to track animals at a large scale. Tracker Pet uses an SQLite database for offline data storage and supports registering, editing, and deleting animal records."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/java/application/app/android/sql/databases/xml/Learn-More-TrackerPet/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"
  - image_path: assets/images/Projects/BSTCoursePlanner/BSTCoursePlanner.png
    title: "BST Course Planner"
    excerpt: "Binary search tree (BST) Course Planner is a C++ terminal based application that helps students and faculty look at course information and prerequisites from a CSV. It does this by using a Binary Search Tree algorithm to go through a loaded file."
    url: "https://github.com/Justin-Bytes-Code/BSTCoursePlanner"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

graphicandsystem_row:
  - image_path: assets/images/Projects/OpenGLHouse/OpenGLHouse.jpg
    title: "OpenGL House"
    excerpt: "OpenGL House is a C++ project where I built a 3D house from a reference image using OpenGL. I worked on creating the 3D objects, adding textures and lighting, and setting up a camera that lets you move around and view the house from different angles. The camera also has setting for viewing."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/c++/opengl/graphical%20programming/Learn-More-OpenGLHouse/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"
  - image_path: assets/images/Projects/OpenGLBreakout/Breakout.png
    title: "OpenGL Breakout"
    excerpt: "OpenGL Breakout is a C++ remake of the old breakout game using OpenGL. Breakout was a great way to showcase what I learned in 2D rendering, basic physics, and collision detection to recreate the core gameplay of Breakout."
    url: "https://github.com/Justin-Bytes-Code/OpenGL-Breakout"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

ai_row:
  - image_path: assets/images/Projects/AI/PirateAI.png
    title: "Pirate Artificial Intelligence"
    excerpt: "Pirate AI is a Python project where I used Deep Q-Learning to train an agent to play a game. The agent learns through trial and error, improving its decisions as it interacts with the game environment until it can play optimally, winning in as few turns as possible."
    url: "https://github.com/Justin-Bytes-Code/Pirate_Artifical_Intelligence"
    btn_label: "View Source Code"
    btn_class: "btn--primary"

webdevelopment_row:
  - image_path: assets/images/Projects/Websites/ChineseFoodWebsite/Chinese Food Website.jpg
    title: "Chinese Food Website"
    excerpt: "Chinese Food Website is an basic HTML based web project designed for a fictional Chinese restaurant."
    url: "https://github.com/Justin-Bytes-Code/Chinese-Food-Website"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"
    
  - image_path: assets/images/Projects/Websites/TravlrWebsite/Travlr.png
    title: "Travlr Website"
    excerpt: "Travlr is a full-stack travel web application developed using the MEAN stack (MongoDB, Express.js, Angular, and Node.js). It uses a customer facing website for browsing travel packages. An Angular administrative interface for managing trip data. And, it also supports REST APIs, database operations, and JWT based authentication."
    url: "https://justin-bytes-code.github.io/Portfolio/learn%20more/javascript/html/css/json/full%20stack/web%20development/angular/mongodb/Learn-More-Travlr/"
    btn_label: "Learn More!"
    btn_class: "btn--primary"

  - image_path: assets/images/Projects/Websites/Portfolio/ThisWebsite.png
    title: "My Personal Portfolio Website"
    excerpt: "This Website was built with Jekyll and the Minimal Mistakes theme! This website is hosted using GitHub pages for static websites. If you'd like to check the source code for the website I will link it below."
    url: "https://github.com/Justin-Bytes-Code/Portfolio/tree/master"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"
---

# Games & Gameplay Programming
{% include feature_row id="game_row" %}

# Software Applications 
{% include feature_row id="software_row" %}

# Graphics & Systems Programming
{% include feature_row id="graphicandsystem_row" %}

# AI & Machine Learning
{% include feature_row id="ai_row" %}

# Web Development
{% include feature_row id="webdevelopment_row" %}

# Projects
{% include feature_row id="projects_row" %}

