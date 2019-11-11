---
layout: post
title:      "My first Javascript App"
date:       2019-11-11 02:32:04 +0000
permalink:  my_first_javascript_app
---


The Javascript and Rails project was a whole different beast from the projects of previous modules. Not only did it force me to put a heavy focus on the front end for the first time, but the requirement that the application consist of just one page (with no refreshes)  added an extra challenge.

For this demanding project, I built a simple workout tracking application. Because I'm not terribly creative, it is simply called *Work*.

## Focus on Object Orientation
Setting out in constructing this application, I knew I wanted all of my functions to be encapsulted into classes. I had 5 in total: *Exercise*, *Workout*, and *Liftset* (which corresponded to my three models in the Rails backend) plus an *App* class, which handles most of the HTML rendering and manipulation, and the *API* class, which handles fetch calls of every variety to the back end.

The app launches with an eventListener set to 'DOMContentLoaded' that instantiates a new instance of *App* and fetches and renders all workouts from the API.

```
const app = new App;

document.addEventListener('DOMContentLoaded', () => {
  api.getWorkouts();
});
```

## Coding CRUD Actions
*Work* is at its core a CRUD application, as it lets users create, view, edit, and delete workouts, exercises, and personal records. The most challenging of these to code was the "update workout" functionality. 

The first step was to create a button that would act as a trigger to render an edit form. In a straight Rails app, this would have been the 'get /workouts/:id/edit' route. However, being a single page application, I needed to simply create an HTML form and append it to the <div> that the user is currently viewing, like so:
```
static renderEditWorkoutButton(workoutObject) {
        let button = document.createElement('button');
        button.innerText = 'Edit Workout'
        button.addEventListener('click', function(){
          App.renderEditForm(workoutObject.id);
        })
        document.getElementById(workoutObject.id).appendChild(button);
      }
			
			static renderEditForm(workout_id){
      let form = document.createElement('form');
      form.id = 'edit-workout-form';
      document.getElementById(workout_id).appendChild(form);

      let titleInput = document.createElement('input');
      titleInput.setAttribute("type", "text");
      titleInput.setAttribute("name", "title");
      titleInput.setAttribute("value", "Workout Title");
      form.appendChild(titleInput);

      let dateInput = document.createElement('input');
      dateInput.setAttribute("type", "text");
      dateInput.setAttribute("name", "date");
      dateInput.setAttribute("value", "Workout Date");
      form.appendChild(dateInput);

      let focusInput = document.createElement('input');
      focusInput.setAttribute("type", "text");
      focusInput.setAttribute("name", "focus");
      focusInput.setAttribute("value", "Workout Focus");
      form.appendChild(focusInput);

      let workoutIdField = document.createElement('input');
      workoutIdField.setAttribute("type", "hidden");
      workoutIdField.setAttribute("value", workout_id);
      form.appendChild(workoutIdField);

      let submit = document.createElement('input');
      submit.setAttribute("type", "submit");
      form.appendChild(submit);

      form.addEventListener('submit', function(event){
        event.preventDefault();
        api.updateWorkout(workout_id);
      })
    }

```

The renderEditWorkoutButton creates a button that listens for a click, and generates an HTML form via the renderEditForm function. In turn,  the newly created form listens for a submit event. If it receives one, it fires the updateWorkout button and sends a patch fetch request to the API:

```
 updateWorkout(id) {
      let form = document.getElementById('edit-workout-form');
      
      fetch(`${BASE_URL}workouts/${id}`, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
          "Accept": "application/json"
        },
        body: JSON.stringify({
          "title": form.querySelector('input[name="title"]').value,
          "date": form.querySelector('input[name="date"]').value,
          "focus": form.querySelector('input[name="focus"]').value
        })
      })
      .then(response => response.json())
      .then(function(object){
         let w = new Workout(object)
         workoutContainer.removeChild(document.getElementById(object.id))
         workoutContainer.innerHtml += w.render(object);
      })
      .catch(function(error){
        alert("An error occurred. Please try again.")
        console.log(error.message);
      })
    }
```
This patch fetch request is received by the workouts#update controller action in the backend, while the front end is updated by removing the <div> containing the workout information and replacing it with a re-rendered version of the new data.

Coding this and the other CRUD actions was a big challenge, but also a big learning experience for me as a coder.

Overall, do I love JavaScript? Not yet, but I think once I learn a little more, we can be friends!
