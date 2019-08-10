---
layout: post
title:      "Refactor, Repeat: Lessons From My First Project"
date:       2019-08-10 01:37:36 +0000
permalink:  refactor_repeat_lessons_from_my_first_project
---


I did it. I started with a blank screen and *actually* created something that *actually* works! Full disclosure: this didn't happen without a few moments where I considered throwing my laptop across the room.

For my first coding project ever, I created a CLI Gem that scrapes data from timeanddate.com and lets users quickly get information on what is going on in the sky above their city - right from their terminal. After inputting a zipcode, the CitySkies gem generates a URL within timeanddate.com, scrapes data on the current weather, moon phases, and planet visibility in that zip code.

As I drafted my project on paper, it seemed simple. When I actually began: not so much. There were more than a few frustrating moments, but I came out on the other side of this project with several well-learned lessons. 

## Lesson 1: Sometimes setting up is the hardest part.
Just setting up my file tree was a process. Luckily, using the bundler gem made it much easier than it might have otherwise been. Requiring files and setting up my configuration was one of the hardest parts for me, and I had to rewatch our recorded study group on the topic several times. 

**My tip:** Check out public repos - in this case, especially gems - on GitHub to get an idea of how your file tree should be structured.

## Lesson 2: You should reach out if you get stuck. Really. 
Being a stubborn person, I often want to figure things out for myself. However, there's no reason to go it alone in coding. Reaching out to your cohort, your technical coach, and even Googling like crazy will not only get you unstuck, but might save your mental sanity. Whatever your question or problem is, you're probably not the first person to have had it.

## Lesson 3: You're never done refactoring.
By Thursday, I had code that provided the functionality I wanted and considered myself more or less done coding. I set up a meeting with my technical coach (thanks Morgan!) and got some suggestions on how the code could be cleaner. I sat down on Friday morning thinking I would spend an hour refactoring and be done with it.

Once I started refactoring, it was like falling down a rabbit hole. With every improvement I made to my code, I found another aspect to change. I spent nearly four hours on this part, and in the end I came away with a similar but much better interface and *much* DRY-er code. 

All in all, I would consider my first project week a success. I am more than ready to take a day off and let my brain vegetate with some Netflix, then get back to the grind on Monday!

Check out my video below to see a demonstration of my gem, and a brief explanation of how the code behind it works:

<iframe width="560" height="315" src="https://www.youtube.com/embed/kUpeMKj3S_Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






