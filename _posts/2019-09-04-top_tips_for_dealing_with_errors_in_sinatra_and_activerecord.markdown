---
layout: post
title:      "Top Tips for Dealing With Errors in Sinatra and ActiveRecord"
date:       2019-09-04 21:44:23 +0000
permalink:  top_tips_for_dealing_with_errors_in_sinatra_and_activerecord
---


Most of the time, Sinatra and ActiveRecord feel like magic. Relatively few lines of code perform some sort of sorcery behind the scenes and create web applications capable of taking in and storing data. It might make you feel like this:
<iframe src="https://giphy.com/embed/12071fYBO811v2" width="480" height="276" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/movie-film-90s-12071fYBO811v2">via GIPHY</a></p>

However, sometimes this sorcery gets a little tricky to manage, and you may end up feeling something like this:
<iframe src="https://giphy.com/embed/7EVdUObyP1Mn6" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/show-hocus-pocus-director-7EVdUObyP1Mn6">via GIPHY</a></p>

Here are my top tips for figuring out *what* is causing your errors, and the common silly mistakes that I've spent hours wasting my time on, so you don't have to:

## 1. *Always* check that the routes match in your controller and form.
When you get the dreaded "Sinatra doesn't know this ditty" page in your browser, don't fret -- this is usually one of the easier errors to solve! If you just submitted a form and get this message, look at what route Sinatra is telling you it's trying to go to (this is what is written into your form *action* and *method*). Does this exactly match the route written in your controller? I can't tell you how many times I have called a route '/message' in my form and '/message*s*' in my controller.

## 2. If Sinatra still doesn't know this ditty...you probably forgot to mount your controller.
You can write all of the beautiful code you want in your controller, but if it isn't mounted, it's not doing you any good. Try to get in the habit of automatically mounting every controller you use in config.ru as soon as you create the file!
```
# config.ru :
use TweetsController
use UsersController
run ApplicationController
```

## 3. Use Pry effectively. It will become your best friend.
The first thing I do with any code I write is to make sure I have the Pry gem added to my Gemfile. There are a few ways this guy comes in handy:
* Add a rake task to quickly start a pry session with just a few keystrokes. If at any point in time you are confused about how your code works, you can drop into a pry session and play around with mock objects and not worry about messing up your real data. This is especially helpful to do right after you set up your ActiveRecord associations to make sure you have all the correct functionality that you intended.

* While running your server via the shotgun gem, put a binding.pry in the route you're trying to hit. I like to place it at the beginning, before the rest of my code runs (or often before I've even written any code in the route!) to check my params and make sure I have the correct data. This can either help me debug code I've already written, or guide me in writing new code so I can get it right the first time.

 
```
post '/tweets' do
  binding.pry
	@tweet = Tweet.create(params["content"])
end
```

* Let *not* hitting a binding.pry be a hint that your routes aren't working the way you think they are. If you put a binding.pry in and expect to hit it but you don't, that's your clue that things aren't behaving the way you intended! Put on your thinking cap and start figuring out why.

My most important tip, though, is to remember that your program isn't going to do anything you didn't tell it to. Even though it may sometimes feel like your program has a mind of your own, it doesn't. 
