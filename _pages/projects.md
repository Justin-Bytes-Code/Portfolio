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
# excerpt: "Bacon ipsum dolor sit amet salami ham hock ham, hamburger corned beef short ribs kielbasa biltong t-bone drumstick tri-tip tail sirloin pork chop."

game_row:
  - image_path: assets/images/Games/LuckyBrainNoodle/LuckyBrainNoodles.jpg
    title: "Lucky Brain Noodle"
    excerpt: "Lucky Brain Noodle is a co-op beat 'em up developed in Unreal Engine 5 using C++ and Blueprints. The project features custom gameplay systems and Steam-integrated multiplayer, with ongoing development focused on networking and combat."
    url: "https://www.linkedin.com/feed/update/urn:li:activity:7492551071832309761/"
    btn_label: "Check Progress"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/SurvivalGameConcept/Survival Game Background.png
    title: "Survival Game Concept"
    excerpt: "Survival Game Concept is an Unreal Engine 5 prototype developed primarily in C++ that explores the core mechanics of a survival game. Features include resource gathering, inventory management, player needs, creature interactions, and a building system."
    url: "https://justin-bytes-code.itch.io/survival-game-concept"
    btn_label: "Play Now!"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/FirstPersonGamePrototype/First Person Game Prototype.png
    title: "First Person Game Prototype"
    excerpt: "First Person Game Prototype is an Unreal Engine 5 project built with C++ and Blueprints to explore mechanics for a first-person shooter. Features include projectile effects, terrain deformation, portal-based teleportation, and procedural terrain generation."
    url: "https://justin-bytes-code.itch.io/first-person-game-prototype-example"
    btn_label: "Play Now!"
    btn_class: "btn--primary"

software_row:
  - image_path: assets/images/Projects/Apps/TrackerPet/TrackerPetSnip.png
    title: "Tracker Pet"
    excerpt: "Tracker Pet is an Android application developed in Java that helps users manage animal profiles and track important information. It uses an SQLite database for offline data storage and supports registering, editing, and deleting animal records."
    url: "https://github.com/Justin-Bytes-Code/Tracker_Pet"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"
  - image_path: assets/images/Projects/BSTCoursePlanner/BSTCoursePlanner.png
    title: "Tracker Pet"
    excerpt: "BST Course Planner is a C++ terminal application that helps students and faculty explore course information and prerequisites. It uses a binary search tree to organize course data loaded from a file."
    url: "https://github.com/Justin-Bytes-Code/BSTCoursePlanner"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

graphicandsystem_row:
  - image_path: assets/images/Projects/OpenGLHouse/OpenGLHouse.jpg
    title: "OpenGL House"
    excerpt: "OpenGL House is a 3D graphics project developed in C++ that recreates a house using OpenGL. It demonstrates 3D transformations, texture mapping, shader-based lighting, and interactive camera controls."
    url: "https://github.com/Justin-Bytes-Code/Open-GL-House"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"
  - image_path: assets/images/Projects/OpenGLBreakout/Breakout.png
    title: "OpenGL Breakout"
    excerpt: "OpenGL Breakout is a C++ remake of the classic Breakout arcade game using OpenGL. The project explores 2D rendering, basic physics, and collision detection to recreate the core gameplay experience."
    url: "https://github.com/Justin-Bytes-Code/OpenGL-Breakout"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

ai_row:
  - image_path: assets/images/Projects/AI/PirateAI.png
    title: "Pirate Artificial Intelligence"
    excerpt: "Pirate Artificial Intelligence is a Python project exploring reinforcement learning and Deep Q-Learning. It focuses on training an AI agent to learn actions through interaction with its environment."
    url: "https://github.com/Justin-Bytes-Code/Pirate_Artifical_Intelligence"
    btn_label: "View Source Code"
    btn_class: "btn--primary"

webdevelopment_row:
  - image_path: assets/images/Projects/Websites/ChineseFoodWebsite/Chinese Food Website.jpg
    title: "Chinese Food Website"
    excerpt: "Chinese Food Website is an basic HTML-based web project designed for a Chinese restaurant. It demonstrates foundational web development skills through the creation of a restaurant-focused website."
    url: "https://github.com/Justin-Bytes-Code/Chinese-Food-Website"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"
    
  - image_path: assets/images/Projects/Websites/TravlrWebsite/Travlr.png
    title: "Travlr Website"
    excerpt: "Travlr is a full-stack travel web application developed using the MEAN stack, including MongoDB, Express.js, Angular, and Node.js. It combines a customer-facing website for browsing travel packages with an Angular administrative interface for managing trip data, supported by REST APIs, database operations, and JWT-based authentication."
    url: "https://github.com/Justin-Bytes-Code/Travlr"
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

