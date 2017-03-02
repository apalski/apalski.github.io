---
layout: post
title:  "Artificial Intelligence"
date:   2017-03-02 04:19:35 +0000
---

This blog post was due 6 days ago but I've been completely wrapped up in working on my latest project. I've been working on the Tic Tac Toe with AI and it is a big project once you start on the AI side of things. Random trivia for you, we call Tic Tac Toe Noughts and Crosses in Australia.

At the start of the project I'm thinking AI, how the hell do I tackle that, but in the end it was just like any coding problem, one step at a time. I googled "unbeatable Tic Tac Toe games" and the like and thought about what was required. 

I started with coding the logic to detect when either the current player or their opponent had two out of the three positions to win a game. You have eight possible winning combinations in a game of Tic Tac Toe to consider and I had to sit and ponder for a while to get my head around how I would do this. I ended up with a  module that gathered the currently held positions for both players. Then I had a module that did an each check for the positions they held that were part of a winning combination and put them in a hash so that I could maintain which of the eight combinations they matched.  Then I gathered only those results that had two matches into a separate hash with another each loop. Then I got rid of results where the third required position was not a valid move with an if statement. Where there was more than one move I did a sample pick to leave only one move to return to the game. 

Phew! You guessed it, when I got to look at Avi's solution later, what took me 30+ lines of code Avi did in about 4 lines! I could have beat myself up over this but I didn't, what I did was look back at my earlier Tic Tac Toe code from pre-bootcamp and see how much my logic and coding has improved. Plus, and this is a big plus, I understood Avi's solution when only weeks ago I would have gone Huh!

The coding for taking or blocking the winning position reduced games won from 89% for just random positions to 59%.  I also added in AI to check for the best positions to take and moves to make when the opponent held good positions which reduced winning games further to 52%. The object of the AI was to have two computer players (no human interference) and have neither of them able to win a game, ie. 100% drawn games. I wasn't able to get this result but I was able to reduce the number of wins in a game from 89% down to 52% through 3,000 games with my AI logic, I was pretty happy with this as I really felt my brain stretching working on this project.

We all learn in our own way and at out own pace. The penny drops and all of a sudden you can see exactly how something works but only because you've put in the ground work and stuck with it. I am learning every day and can feel my logic process becoming tighter and clearer and now I know that I can do this, I just have to be patient and put the work in and bit by bit I will become the coder that I want to be.
