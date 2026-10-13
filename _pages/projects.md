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
    excerpt: "Lucky Brain Noodle is a Multiplayer CO-OP beat em up Currently being Made!"
    url: "https://www.linkedin.com/feed/update/urn:li:activity:7492551071832309761/"
    btn_label: "Check Progress"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/SurvivalGameConcept/Survival Game Background.png
    title: "Survival Game Concept"
    excerpt: "This is a medium-high level Prototype of a Unreal Engine v5 Game, done mainly in C++. In this prototype it's a proof of concept of the basic mechanics of a survival game. It includes: Eating, Harvesting trees, Mining Rocks, Other creatures, Health, Stamina, Hunger, Inventory system, & A building system with even more to discover. The level uses Unreal Engine v5 landscaping tools to create a simple level that could be added upon if wanted too."
    url: "https://justin-bytes-code.itch.io/survival-game-concept"
    btn_label: "Play Now!"
    btn_class: "btn--primary"

  - image_path: assets/images/Games/FirstPersonGamePrototype/First Person Game Prototype.png
    title: "First Person Game Prototype"
    excerpt: "First Person Game Prototype is a Medium-High level Prototype in Unreal Engine v5 showcasing gameplay mechanics that could be implemented in a larger first-person shooter. Built from scratch using C++ and Blueprints in Unreal Engine, the project demonstrates a collection of modular, bite-sized features designed to extend the default First Person template."
    url: "https://justin-bytes-code.itch.io/first-person-game-prototype-example"
    btn_label: "Play Now!"
    btn_class: "btn--primary"
    
projects_row:
  - image_path: assets/images/Projects/OpenGLHouse/OpenGLHouse.jpg
    title: "OpenGL House"
    excerpt: "This was a medium-to-high level assignment completed in C++ to recreate an entire house in OpenGL, featuring accurate texturing and custom lighting. It also includes a camera with custom Controls!"
    url: "https://github.com/Justin-Bytes-Code/Open-GL-House"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

website_row:
  - image_path: assets/images/Projects/Websites/ChineseFoodWebsite/Chinese Food Website.jpg
    title: "Chinese Food Website"
    excerpt: "This is a medium-level HTML project where I was challenged to create a website for an established Chinese restaurant."
    url: "https://github.com/Justin-Bytes-Code/Chinese-Food-Website"
    btn_label: "Check Source Code!"
    btn_class: "btn--primary"

ai_row:
  - image_path: assets/images/Projects/AI/PirateAI.png
    title: "Pirate Artificial Intelligence"
    excerpt: "A Python project exploring reinforcement learning and Deep Q-Learning to train an AI agent."
    url: "https://github.com/Justin-Bytes-Code/Pirate_Artifical_Intelligence"
    btn_label: "View Source Code"
    btn_class: "btn--primary"
---

# Games
{% include feature_row id="game_row" %}

# AI 
{% include feature_row id="ai_row" %}

# Websites
{% include feature_row id="website_row" %}

# Applications 

# Projects
{% include feature_row id="projects_row" %}

