---
title: Sunday Check 4
description: This is check in 4
date: 2022-04-10
tags: second tag
layout: layouts/post.njk
---

The following is an update on our progress for our ~~Wordle~~ Non-descript 5 letter word guessing game. Links to repos that contain code are provided in this document and are posted at the bottom so they're easier to find.

 API Post for Week 4

##Open API Specification Document

In order to have a dictionary of words to pull from for the Wordle game, we need to connect to an API that provides us with 5-letter dictionary words. 

We will be using the [Random Words API](https://random-word-api.herokuapp.com/all) to first give us a repository of all dictionary words. From here, we will specify that we want to pull only 5-letter words for our game. In the past we have been able to do this by specifying it in the URL (like an example project we have done with NASA Images API), but we are still working through figuring out this aspect of the API. 

As we start to build our API spec documentation in our repository, we will be adding fields to the JSON file to specify details about this API that we are using. As of right now, we are building out the information field and paths field. 

### Info Field
The information field in the specifications document requires fields for the title of the API and the version. Other fields such as license, contract, and terms of service are optional but valuable fields to identify.

### Paths Field
The paths field defines the relative paths to the API endpoint. These paths are appended to the end of the URL to help build out the entire, expanded URL. 

Our start of the document can be found in the [GitHub repository](https://github.com/abbeylyle4/Final-Project-Word-Game/tree/main) called "openapi.json".

You can find more info about the spec doc fields [here](https://swagger.io/specification/#:~:text=The%20OpenAPI%20Specification%20(OAS)%20defines,or%20through%20network%20traffic%20inspection.)

## Front end Week 4

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
.keyButton {
 font-size: 1rem;
 font-weight: 700;
 padding: 0.5rem;
 margin: 0 2px;
 cursor: pointer;
 text-transform: uppercase;
}
 
**Script.js**
 
/*
 Get words from backend or wherever
 import { wordArr} from "./words.js";
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
 
 
function addLetter (pressedKey) {
   if (nextLetter === 5) { //Already filled
       return
   }
   pressedKey = pressedKey.toLowerCase()
 
   let row = document.getElementsByClassName("wordRow")[6 - guessesRemaining]
   let box = row.children[newLetterIndex]
   box.textContent = pressedKey
   box.classList.add("usedBox")
   currentGuess.push(pressedKey)
   newLetterIndex += 1
}
 
function removeLetter () {
   let row = document.getElementsByClassName("letter-row")[6 - guessesRemaining]
   let box = row.children[nextLetter - 1]
   box.textContent = ""
   box.classList.remove("usedBox")
   currentGuess.pop()
   newLetterIndex -= 1
}
 
 
 
 
document.addEventListener("keyup", (e) => {
 
   if (guessesRemaining === 0) {
       return
   }
 
   let pressedKey = String(e.key)
   if (pressedKey === "Backspace" && newLetterIndex !== 0) {
       removeLetter()
       return
   }
 
   /* need to hook up with backend
    if (pressedKey === "Enter") {
       checkGuess()
       return
    }
   */
 
   let allowedInput= pressedKey.match(/[a-z]/gi)
   if (!allowedInput|| allowedInput.length > 1) { //stops numbers and shift/cntrl from being inputted
       return
   } else {
       addLetter(pressedKey)
   }
})
 
initBoard();
 
## Backend Week 4
- [woordle.js](https://github.com/TaylorMorini/Final-Project-Word-Game/blob/main/src/woordle.js)
- [wordGenerate.js](https://github.com/TaylorMorini/Final-Project-Word-Game/blob/main/api/wordGenerate.js)
- Issues solved this week:
   * figured out the issue with our API
       (shoutout to the other wordle group)
   * got 5 letter words to be produced  

https://github.com/TaylorMorini/Final-Project-Word-Game/blob/main/src/woordle.js
https://github.com/TaylorMorini/Final-Project-Word-Game/blob/main/api/wordGenerate.js
https://github.com/Nick-Telles/Final-Project-Word-Game
https://github.com/abbeylyle4/Final-Project-Word-Game/tree/main
https://github.com/GigiFitiany/Final-Project-Word-Game
