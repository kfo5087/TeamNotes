---
title: Sunday Check 3
description: This is check in 3
date: 2022-04-03
tags: second tag
layout: layouts/post.njk
---
Other aspects of our posts such as the Workflow diagrams can be found in the archive sectiuon of our webpage.

## Frontend Week 3 Work
**indexx.html**
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta http-equiv="X-UA-Compatible" content="IE=edge">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Wordle</title>
</head>
<body>
   <h1> Wordle </h1>
  
   <div id="layout">
 
   </div>
 
    //Keyboard layout
    //Setting the possible inputs for the game
    <div id="keyboard">
       <div class="rowKeys">
           <button class="keyButton">q</button>
           <button class="keyButton">w</button>
           <button class="keyButton">e</button>
           <button class="keyButton">r</button>
           <button class="keyButton">t</button>
           <button class="keyButton">y</button>
           <button class="keyButton">u</button>
           <button class="keyButton">i</button>
           <button class="keyButton">o</button>
           <button class="keyButton">p</button>
       </div>
       <div class="rowKeys">
           <button class="keyButton">a</button>
           <button class="keyButton">s</button>
           <button class="keyButton">d</button>
           <button class="keyButton">f</button>
           <button class="keyButton">g</button>
           <button class="keyButton">h</button>
           <button class="keyButton">j</button>
           <button class="keyButton">k</button>
           <button class="keyButton">l</button>
       </div>
       <div class="rowKeys">
           <button class="keyButton">Del</button>
           <button class="keyButton">z</button>
           <button class="keyButton">x</button>
           <button class="keyButton">c</button>
           <button class="keyButton">v</button>
           <button class="keyButton">b</button>
           <button class="keyButton">n</button>
           <button class="keyButton">m</button>
           <button class="keyButton">Enter</button>
       </div>
   </div>
 
 
</body>
</html>
 
**script.js**
 
/*
 Get words from backend or wherever
 import { wordArr} from "./wordGenerate.js" These words will come from the API fetch;
*/
 
let guessesRemaining = 6;
let currentGuess = [];
 
//This is the random word the user is trying to guess
//let AnswerWord = wordArr[Math.floor(Math.random() * WORDS.length)]
 
 
 
//Creating the actual game layout
 
 
function initLayout(){
 let layout = document.getElementById("layout");
  //Row for each guess
 for (let i = 0; i < NUMBER_OF_GUESSES; i++) {
         let row = document.createElement("div")
         row.className = "wordRow"
      
 //5 boxes for each guess
       for (let j = 0; j < 5; j++) {
           let box = document.createElement("div")
           box.className = "letterBox"
           row.appendChild(box)
       }
 
       layout.appendChild(row)
   }
}
 
initBoard();
// the front end layout display of our wordle game, 
**style.css**
#layout{
   display: flex;
   align-items: center;
   flex-direction: column;
}
 
.letterBox{
 
   font-size: 2.5rem;
   font-weight: 700;
   text-transform: uppercase;
   height: 3rem;
   width: 3rem;
   display: flex;
   justify-content: center;
   align-items: center;
   border: 2px solid gray;
   border-radius: 3px;
}
 
.usedBox {
 border: 2px solid black;
}
 
.wordRow {
 display: flex;
}
 
 
 
## Backend Week 3 Work
 
**Rough Draft of WordGenerate.js**
 
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m4jgp7nbcviucklutlss.png)
 
**Hashing out WordGenerate.js**
```
import fetch from 'node-fetch';
import {key} from './word.js';
export {wordGenerate};
 
function wordGenerate()   //creating a new function that renders the word each day
{
fetch('https://random-words5.p.rapidapi.com/getRandom?wordLength=5', {
"method": "GET",   		//fetching the 5 letter word from the random words API specifying that the length = 5
"headers": {
  "x-rapidapi-key": key, 	
  "X-RapidAPI-Host": "random-words5.p.rapidapi.com"
}
 
}) 
.then(response =>response.json())   //creating the promise that the api will be fetched and return with a response
.then(response => {
   console.log(response);
   console.log(response.content);
})
.catch(err => {
   console.error(err);
});
}
```
**Word.js**
- This is where the API key is
```
var config = { API_KEY : '0d0dad91cdmshd70ac9ca4bc57cbp14e277jsn50f8a6d27b53' };
 
let key = config.API_KEY;
 
export {key};
```
 
- Problem with API key ? -> "api key is invalid"
  - entry issue?
 
**What the API end points are**
- Currently: using a random word generator API
- How it is used: this is used to get random words. one of the parameters is to set the word to  letters; this way there are never words that are less than/more than 5 letters long