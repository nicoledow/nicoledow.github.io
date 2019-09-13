---
layout: post
title:      "Planifier - My Sinatra Application"
date:       2019-09-13 19:38:13 +0000
permalink:  planifier_-_my_sinatra_application
---


After about 8 weeks of eating, sleeping, and breathing code, I have my first fully-functional web application. For my Sinatra project, I created *Planifier*, a social lesson-plan sharing website for teachers to share, view, and save lessons with their colleagues. 

I feel good about my project. Is it perfect? No. Did I create something way beyond what I could've ever done three weeks ago? Absolutely yes.

This project was by far the most complex thing I have ever built with code. I included all parts of the stack: a database, a controller that manages classes and data through ActiveRecord, and a visual interface made with HTML, CSS, and ERB. I followed the Model-View-Controller (M.V.C.) conventions to keep my project organized.

A breakdown of the pieces of my project:

## Models
The bulk of my app is carried by three classes: Teachers, Courses, and Lessons. The main associations that allow Planifier to function are teachers have_many courses, courses have many lessons, and teachers have many lessons through courses.

Later in the process, I wanted to add the ability for teachers to save lessons from other colleagues to refer back to later on. I did this by creating the SavedLessons class, whose table acts as a join table, with each record containing the id of the saving teacher and the lesson's id.


## Views
My ERB files, or views, are organized by the three classes. Some classes had additional needs, but in general each class had an index page (which listed all entries of that class), a show page that shows an instance of the class, and a new/edit page.


## Controllers 
The controllers are the workhorse of the application. I used four in total, one for each class, plus an Application Controller that dealt with high-level actions such as registering users. 

Controllers are responsible for moving the user around the various resources that Planifier has to offer. The most important aspect in designing the routes held in my controllers was following the principals of RESTful routing - I tried to ensure that all routes were logical, predictable, and directly tied to the type of resource requested and the requested CRUD action.

## Taking pride in my project and overcoming insecurity:
One of the hardest parts of the project, without a doubt, was visual styling and utilizing CSS. Despite feeling so proud of all my hard work on the back end of my project, I can't help but feel terribly insecure about how it looks visually. When my friends ask to see my project, I get nervous because they'll only see my (lack of) basic CSS skills. Unfortunately, the front end doesn't do the back end justice.

Even if it isn't the prettiest, I remind myself that I worked so hard on this project and that even if it looks simple on the service, there is so much hard work going on behind the scenes with user data. I have a plan to build my CSS skills on the side to prepare for the next project. I want to feel proud when I show my friends and family what I've built!
