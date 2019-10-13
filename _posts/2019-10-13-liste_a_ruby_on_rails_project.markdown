---
layout: post
title:      "Liste: A Ruby on Rails Project"
date:       2019-10-13 20:27:51 +0000
permalink:  liste_a_ruby_on_rails_project
---


Liste is a task and to-do-list managing app built with Rails that lets team managers and members organize tasks by projects and who is responsible for each piece. 

Building this web application from the ground up was the most difficult yet satisfying coding endeavor I have taken on this far. Luckily, using Rails and its conventions let me get the basic functionality up and running quickly by handling the association of routes and views.

Liste is set up using an MVC pattern.

## Models
Liste has five models: the User, List, Task, Assignment, and Note classes. The bulk of the application's functionality comes from the many-to-many relationship between users and tasks, which are joined via the Assignment join table. The diagram below shows the schema for the models:


![]https://imgur.com/a/W78TXz5


## Controllers and Views
One of the biggest challenges of designing the application was deciding which controller actions should link to which views. It was important to me to use RESTful routing, but I also did not want to bloat my application with unnecessary routes since I have a high number of models. I had a few cases where RESTful CRUD actions logically made sense as nested routes, but seemed superfluous in their un-nested form.

For example: /lists/:id/tasks/new seems like a good route to have.

However, from a UX perspective, the following URL seems unneccessary: 

/tasks/new.

In the end, I decided to keep my application lean and user-friendly, so the list_tasks_path handles the bulk of user interactions.

## The Visual
Going into this project, I knew styling and CSS was something I wanted to dive much deep into than I had in my Sinatra project. I imported bootstrap to get my views up and running quickly, then followed tutorials to help me make a layout of nested divs that give the illusion of a single column of organized content. Trying to wrap my head around building grids in HTML and CSS was a challange and I still have quite a way to go, but I'm proud of my application's styling when I think about what an insecurity this aspect was in my previous projects.

I am excited to move on to Javascript and get more projects into my portfolio!





