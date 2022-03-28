---
title: Sunday Check-in 2
description: This is a post for the second check in. 
date: 2022-03-27
tags:
  - another tag
layout: layouts/post.njk
---
## Sunday Requirements

-  Your checkin site should be updated with a heading for week 2
  -   Week 2 should have any updates of what you worked on, where you are in the project, visuals created, etc. It should end with questions and next steps
  -  Your repo that you are working in should start to have some code. Front end people should start working on front end assets. Backend people should start working on some endpoints. API people should be making user-flow diagrams that indicate what users of the solution do, how the front end works with this input, what the backend returns, how the front end then uses this to inform the user.
   - You should have at least 2 of these user flows attempted. In the end you'll need every process loop documented of the user + frontend + backend and how they play together
  -  Any data structures you need for backend and frontend should at least start being documented / generated. This will change over time potentially but you need some aggreed upon early work to get started at least. This would look like (hypothetically, this is not THE answer here this was like 2 min of thinking about it on my part): getNewWord.js

## Potential API Sources Needed (functionally)
- Random word generator (somehow needs to be 5 letters)
- Position indicator (will show if the letter is in correct position)
    - Messages? (probably just need to hold information from this (do not need own connection))
- Storage? 
    - How to store the wins/losses of user? does this need to persist across days/weeks? 
    - jsonbin.io
- Countdown (until next word is available)
    ![wordle](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/aflsgpu7nmnw6ytvv3qi.png)
- Sharing : copies results to clipboard 
    ![wordle results](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h7eon4rwta6b61gu72jq.png)

    maybe use: [sharing](https://patternflyelements.org/components/clipboard/)

- Word not in database
    - Spellcheck API? ?
## Open Source Endpoints/Potential Solutions
- https://github.com/mcnaveen/Random-Words-API (random word generator)
- https://api.cognitive.microsoft.com/bing/v7.0/spellcheck/[?text][&amp;mode][&amp;preContextText][&amp;postContextText][&amp;mkt] (spell check )
- https://www.mongodb.com/developer/how-to/wordle-bash-data-api/
- https://rapidapi.com/twinword/api/word-dictionary/?utm_source=ANIA-KUBOW&utm_medium=DevRel&utm_campaign=DevRel 
(word dictionary)
- https://rapidapi.com/sheharyar566/api/random-words5/?utm_source=ANIA-KUBOW&utm_medium=DevRel&utm_campaign=DevRel
(random words)

## Project Requirements
- Because of freeness, jsonbin.io is hooked up in the example repo

## Potential Backend Data Structures
- wordGenerate.js :
  - Required to: 
    - Connect to api (either dictionary or the random generator one)
    - Get word of day (Is there some sort of timer to connect to?)
    - Spell check api connection? (checks spelling, may be used to see letter position?)
- wordCheck.js
  - This may not be necessary (wordGenerate could possibly cover the requirements)
  - Required to:
      - only run when the user enters a letter that is in the correct answer
      - Connect to the spell check api
      - Read the user input, return whichever letters are correct
          - this is position based, going to need to know where letters are specifically
          

  
     