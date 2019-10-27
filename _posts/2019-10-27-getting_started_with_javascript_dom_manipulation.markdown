---
layout: post
title:      "Getting Started With JavaScript DOM Manipulation"
date:       2019-10-27 15:47:20 +0000
permalink:  getting_started_with_javascript_dom_manipulation
---


For the past two weeks, I have been working through the JavaScript curriculum. It has been a humbling experience to say the least. After gaining so much confidence with Ruby and being able to fly through writing code, JavaScript has brought me down a few notches as I've returned to constant google searches for basic syntax and language features.

Despite the frustrations, getting aquainted with JavaScript has also been an exciting time in my coding journey. I finally feel like an (almost) real web developer. Learning just a bit of JavaScript has greatly increased what I'm able to accomplish with code - and I can't wait to go back to previous projects and jazz them up. 

The best feat I've been able to accomplish with JavaScript is DOM manipulation. And the good news is, the basics aren't too hard, and you can get augment your projects with just a small amount of code!

## First things first: What is the D.O.M.?
DOM stands for "document object model." Programmers think of it as a "tree" of nested HTML nodes representing what the user sees on a web page. You can see the DOM by opening up the developer tools in your browser - if you are using chrome, you can do this by clicking View > Developer > Developer Tools.

## Using JavaScript to Manipulate the DOM in Real Time
In your Dev Tools, you can add or change almost anything about the HTML you see representing the web page you are currently viewing. These changes won't be saved, but it can be fun to play around and see how changes in HTML markup affect the page in real-time.

You can use your code manipulate this markup for real.

### Step 1: Load your script(s) in your HTML file.
You need to let your HTML file know that your JavaScript file exists. At the bottom of your file, import your script like this:

 ```<script src="myscripts.js"></script>
 ```
 
 Note: the src attribute should be set to your JavaScript filename.
 
 Place these at the end of your HTML file as scripts can take longer to load, and you don't want your user to have to wait for them before they can see any content.
 
 ### Step 2: Add Basic DOM Manipulation Functions with EventListeners
 A lot can be done with one simple JavaScript feature: Event Listeners.
 
 Event listeners can be added to any element (like a button, for example). When a user is viewing a page, this button will always be "listening" to see if the user interacts with it.
 
First, let's identify our buttons using querySelector. This will search our DOM for anything matching our query (in this case, 'button' elements):
```
const buttons = document.querySelector('button')
```
We could have also searched by a class name, or an ID.

Now that our script knows what we mean by "buttons", let's add event listeners to all those buttons. We'll do this by writing a function called 'addClickListenersToButtons.'

```
function addClickListenersToButtons() {
  buttons.forEach(button => {
	  button.addEventListener('click', turnGreen(event))
		}
	}
	```
	This function will go to every button and tell it "hey, if someone clicks on you, run the turnGreen() function."
	
	But how will we automatically call this function to make sure our buttons all have this listener? We can call it automatically by having our document as a whole "listen" for its own loading event, and automatically fire this function. Let's add this code:
	
	```
	document.addEventListener('DOMContentLoaded, addClickListenersToButtons());
	```
	
	Now, when the DOM is loaded it will automatically go to our addClickListenersToButtons function and add all of our event listeners.
	
	Finally, let's complete the process by defining the turnGreen function that is called when someone clicks one of our buttons:
	
	```
	function turnGreen(event) {
	  event.target.style.color = "green";
	}
	```
	This code takes in the "event" (in this case, a click), and alters that element with some in-line CSS to turn the element green. 
	
	You can imagine the possiblities with DOM manipulation. In addition to changing element colors, we can also tell our DOM to generate new elements when our buttons are clicked:
	
	First, modify the event listener to also fire the generatePTag function:
	```
	function addClickListenersToButtons() {
	  buttons.forEach(button => {
		  button.addEventListener('click', turnGreen(event))
			button.addEventListener('click', generatePTag())
		}
	}
	```
	
	Then, define the generatePTag function. This will use JavaScript's createElement function.
	
	```
	function generatePTag() {
	  const pTag = document.createElement('p')
		p.innerText = "A button was clicked!"
		document.main.appendChild(pTag)
	}
	```
	This function generates a p tag, and sets its inner text to "A button was clicked!". We could have generated any type of HTML element we wanted. You can even use JavaScript to set the element's className for styling purposes, or set an ID to refer to it later.
	
	## In conclusion
	This blog post only scratches the surface of what JavaScript is capable of in terms of manipulating the DOM and making your web application more dynamic. I can't wait to learn more!
 
 


