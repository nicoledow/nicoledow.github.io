---
layout: post
title:      "Coverless: A React and Rails Project"
date:       2019-12-30 01:41:57 +0000
permalink:  coverless_a_react_and_rails_project
---


I used to be adamant that front-end development was not what I wanted to focus on. Learning React has changed all that - I've seen the light and now realize that front-end development is more than just writing HTML and CSS. The React module has shown me how fun building dynamic components can be, and how it helps bring a page to life. I have only just begun to dip my toes into the front end, but I am happy to discuss my first React project: "Coverless", an app for people who can't help themselves from judging a book by its cover.

## What is Coverless?
Coverless is a web application that uses a React/Redux front end and a Ruby on Rails back end. 

On load, data is fetched from the New York TImes books A.P.I. Users are able to choose any one of the NYT bestselling book lists to browse. The browsing interface mimics tinder, and users can swipe through books on the list and see the title, author, and summary blurb but NO cover. Books that users "like" are added to the "My Books" list, accessible in the top navigation bar. The hope is that users will choose a book based on whether it actually interests them, rather than be enticed or repelled by the cover.

You can see Coverless in action here:

<iframe width="560" height="315" src="https://www.youtube.com/embed/FBih6UNfqJg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## How it works: The Front
The front end was generated with the create-react-app command. It includes just one HTML file ("index.html"), containing a div tag with the id "root" on which the entire App component is rendered.

On load, an App component is rendered on the D.O.M. The App component contains a Navbar component as well as a react-router switch that specifies which component should be rendered based on the four available paths. Each of these switch statements renders a container component.

The container components are the BooksContainer, MyBooksContainer, ListsContainer, and ReadBooksContainer. I decided to have all connections to the Redux store (via the mapStateToProps and mapDispatchToProps functions) configured in my container components for simplicity and predictability. Any data from the store or callback functions needed by child components are passed down from the container.

I used a Redux store, created in index.js, to hold data on books fetched from both the N.Y.T. A.P.I. and LikedBook objects fetched from the Rails back end. All interactions with the store are managed in a single reducer function called handleBooks.

## How it works: The Back
The Rails back end was fairly simple for this first version of Coverless. Although a User model with authentication as well as a Review model are forthcoming, in this version the only model needed was "LikedBook." 

The LikedBook table keeps track of only books that the user has "hearted." In an earlier iteration of Coverless, I had saved all books with a boolean column called "liked" that defaulted to "false," but it seemed unneccessary to be saving data for rejected books. 

When a user clicks "like" on the client side, a post request is sent to /likedbooks and routed to the "create" action in the controller. There, a LikedBook object is instantiated with all data included from the N.Y.T. A.P.I. and a "read" attribute is set with a value of "false." A similar process (but with a "patch" request) is triggered when a user clicks the delete or finish buttons.

Although the PostgreSQL database automatically adds an ID column to each entry, the isbn attribute is saved and typically used to find and reference liked books. This avoids confusion as the N.Y.T. A.P.I. also gives an "id" attribute to each book.

## Next Steps
I am eager to learn more about React and to take this project further. The immediate next step is to configure sessions and user authentication. Further down the line, I hope to study React Native and create a mobile version of Coverless.


