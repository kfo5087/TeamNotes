---
title: Team Notes 
description: This is a post about the final project. 
date: 2022-03-20
tags:
  - another tag
layout: layouts/post.njk
---
Project: [word-guess-game] Make a letters that make up a word game 

## Brief Description of Project

Creating a word-guess-game web component that follows a set of rules established by the multiple clones that exist (some allow infinite guessing, some a limited amount, some let you pick a new word, etc) but this must have a well defined set of rules that I agree to.
Make a microservice on vercel that picks a word at random for the user to play


## Microservice Requirements

READ web service must serve up a word of the day
READ get a new random word
POST API end point that checks the current user guess and returns which squares are correct
Storing # of attempts (on any guess, store)
Storing # of winners (on correct solution, store)
Parameter that returns a word of the size in question
READ get success vs attempts data for the word in question

## Web Component Requirements

Needs to support right / wrong visualization via CSS, using SimpleColors API `@lrnwebcomponents/simple-colors` as the Base Class in order to handle color contrast
Needs to celebrate when the user wins the game
Needs to lock out attempts if they fail to get the right answer by the last round
Button to load a new word but only after winning or losing
A container component + a "guess" component so at least 2 if not more components
User input needs to allow for guessing while revealing the letters that are correct along the way
Don't require typing correct letters over again
When game is over, show how many got it right

## Solution Brainstorm

* Diagram of the relationship between front end and back end:
![relationship](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dnxiqtu7wwu6olvlxezs.jpg)

* Starting to draw the front end, pointing out how different aspects of it are handled visually
![front](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6eugevbsf8ogx3t19p6x.png)

* What does the API look like?
 The API can return which user guesses are correct/incorrect (POST API)
    Potential solution: cloud based storage API? 

* What data does the front end have that the back end needs?
 Input data (words the user guesses)

* What information does the back end need to bring to the front end?
Correct user guesses
User guesses that are correct, not placed correctly
User guesses that are incorrect
