---
title: Endpoints
description: This is a list of potential endpoints
date: 2022-03-22
tags:
  - Backend Brainstorm 
layout: layouts/post.njk
---
Project: [word-guess-game] Make a letters that make up a word game 

## Potential API Sources Needed (functionally)
- Random word generator (somehow needs to be 5 letters)
- Position indicator (will show if the letter is in correct position)
    - Messages? (probably just need to hold information from this (do not need own connection))
- Storage? 
    - How to store the wins/losses of user? does this need to persist across days/weeks? 
- Countdown (until next word is available)
    ![wordle](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/aflsgpu7nmnw6ytvv3qi.png)
- Sharing : copies results to clipboard 
    ![wordle results](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h7eon4rwta6b61gu72jq.png)
- Word not in database
    - Spellcheck API? 
## Open Source Endpoints/Potential Solutions
- https://github.com/mcnaveen/Random-Words-API (random word generator)
- https://api.cognitive.microsoft.com/bing/v7.0/spellcheck/[?text][&amp;mode][&amp;preContextText][&amp;postContextText][&amp;mkt] (spell check )

