---
layout: post
title:  "My First Ruby Gem"
date:   2017-03-17 06:19:47 +0000
---


When I began this project I hated scraping with a passion. In fact I really dragged my feet starting the project, I just didn't want to face it. The truth, of course, was that I just wasn't good at scraping a website and it hadn't captured me the way other coding topics had.

Fast forward a week and I'm not sure what I was worrying about. Once I applied myself to really understanding scraping it wasn't quite so scary and before long it was getting pretty easy. Then I hit a snag, I wanted to create a gem for the best whisky bars in the world (because I loooove whisky) but I just couldn't work out how to scrape the website. Fortunately it occurred to me to put out the full page and look for the data I was wanting. It just wasn't there!! The div that contained the information was there but it wasn't open and nothing inside it was showing! 

Quick email to my supervisor, Corinna, and back came the reply - add some sleep time to give the website time to open everything as it was based on javascript. I added in sleep from 1 second to 10 seconds to 20 seconds to 40 seconds (any self-respecting user had left at this point) and nothing changed the situation. I began googling, thinking surely someone has come across this issue before. While I was googling I came across an article about respecting the terms of use of a website. I had never noticed that websites had terms of use and of course was now thinking that if I wanted my app to be a gem and be published it couldn't infringe on someones copyright (fair enough too). I went back to my website and sure enough "no scraping" was in the terms of use (as well as heaps of other ways they didn't want their information used). I never got to the bottom of why I couldn't access the data, it was time to move on.

Back to nutting out what my app was going to be. I explored a few ideas but each time I couldn't use the site. I thought of a book app..best crime books of the year but none of the obvious sites allowed their information to be used. Then I read the Learn project outline again and the word 'public' finally hit me in the face. Of course, public information is mostly....duh! public!

My first idea was something for aged care as I know that in Australia it is very hard to get information on entitlements and assistance for the elderly. After exploring the idea I can see why people have problems, the Aged Care website is full of vague information and in the main you need to make a phone call for more information. The website wasn't going to meet the project requirements.

Another love of mine is travel and seeing natural wonders. Thinking on this took me to public travel sites and then to the website on which my project is based, the NSW National Parks website. The coding and scraping for this was mainly straight forward with the only real issue I came across accessing the information on the region a park was found in. Originally, I found the information on each park page but with 239 parks the scrape and collate was taking near to two minutes...way too long. I managed to find a work-around from a page that listed the regions and then gave a list of the parks the region held. Next snag, the text for the park name returned from each region was sitting in the middle of the page and not to the left and my comparison to the parks in my @@all array was failing...no matches found. More googling and another instance of something slapping me in the face, now where had I seen '.strip' before, duh! My issue had been leading and trailing white space! 

With the coding, commenting and Readme completed it was time to look at how to create a Ruby Gem. This was surprisingly easy using the Learn info, RubyGem guides and a great blog by Matt Huggins at  https://quickleft.com/blog/. First thing to do is to create your gem bundle with `bundle gem 'your_gem_name'`. This gives you a rakefile and 'your file name'.gemspec which you will use to build your gem.

The .gemspec file lists the name of your gem, the version of your gem, the author, the author's email address, the homepage of the gem (usually either a git page or a RubyGems page), a description and summary of the gem, details on files and details on development dependencies (bundler, rake, nokogiri, rspec, etc).

Once I had all the files completed and my version information entered it was time to build the gem. This again was easy, simply enter `gem build 'your_gem_name.gemspec`and done:

Successfully built RubyGem
Name: nswparks
Version: 1.0.0
File: nswparks-1.0.0.gem

Publishing the gem at RubyGems.org was a simple matter of creating an account with RubyGems at their website: https://rubygems.org/ and then returning to my terminal and entering `gem push nswparks-1.0.0.gem` and done:

Pushing gem to RubyGems.org...
Successfully registered gem: nswparks (1.0.0)
 
78 commits later, hours of coding, lots of head scratching and I had done it! My first Ruby Gem published!

![](https://scontent.fbne1-1.fna.fbcdn.net/v/t1.0-9/17264120_1198772976907269_6788419453713729961_n.jpg?oh=593c9d3d89d91f197a7dd0b9f971469e&oe=596019BD)
![](http://i.imgur.com/US0B0J3.png)




