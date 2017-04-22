---
layout: post
title:  "Back Yourself & Leave That Endless Loop"
date:   2017-04-22 02:10:16 +0000
---


Far too often I have wasted time coding late at night. I'd have an error that made no sense and I'd go chasing the red herring. Round and round I'd go changing code that I was sure was right only to get another strange message, another red herring. Of course, in the morning, fresh and rested I would find the problem in no time!

The thing I have learnt from this is to back myself. I do know how to code and if it isn't a syntax issue and I am sure my code is right then the error message isn't necessarily pointing to the problem, I need to think outside the box and often, I just need to go to bed or take a break.

A recent example was the Sinatra Playlister lab. I was creating the form for a new song that included an artist, that may or may not exist, and adding genres to the song. I knew my song and artist creation was spot on and felt sure my redirect was right for the post, the only thing I wasn't sure about was the genre addition, but for some reason I put that out of my mind. The messages were that the Name field was missing, not the case, or that my redirect was wrong, not the case. I spent a small amount of time chasing the red herring and then called it a night. 

Excellent idea as in the morning I looked closely at my genres addition and realised that I had not set the form up correctly at all:
<% @genre.each do |genre| %>
		<input type="checkbox" name="genres" id="<%= genre.name %>" value="<%= genre.name %>"><%= genre.name %></input>
	<% end %>
	
What was sent to the controller from the form as a genres 'string' and in the controller I was doing:
	params[:genres].each do |new_genre|
			@song.genres << Genre.find_by(name: new_genre)
		end	
		
So, I was trying to use a string like an array which of course was not working, such a small error but a huge impact.
Fresh eyes and mind in the morning spotted the issue:
	<% @genre.each do |genre| %>
		<input type="checkbox" name="genres[]" id="<%= genre.name %>" value="<%= genre.name %>"><%= genre.name %></input>
	<% end %>
	
Of course, I needed 'genres[]' not just 'genres', I was forgetting that the name field in the input area not only sets the name of the params variable but it also sets the format of the params variable. I could have spent hours chasing this error and not finding it because the error messages were not pointing directly to it.

So, remember to trust yourself as a coder and know when to call a session quits, it is always better to take a break and come back with fresh eyes.
