---
layout: post
title:  "Tracking my Travels with Sinatra"
date:   2017-05-01 04:08:06 +0000
---


Project number 2 is in the bag and overall it was a quicker project than the CLI Data Gem Project. I think it helped that I knew all parts of the topic well before starting.

The project required a working Sinatra application with multiple models, at least one has_many relationship,  user accounts and validation of user input to ensure no bad data. Pretty much boiler-plate Sinatra MVC so the fleshing out of the project was reasonably quick. 

My Sinatra application is Travel Tracker, https://github.com/apalski/travel_tracker, and allows a registered and logged-in user to keep a list of all the countries and cities they have visited in the world. When you select the cities index page you see a list of cities which are each listed under their alphabeticised country heading alphabetically. You can also list just the countries you have visited alphabetically when you select the country index page.

This time I approached the project a little differently, I set out my goals in a notes.md file and then wrote some tests to meet my goals for the models, the application_controller and for /cities in city_controller. I ended up with 11 rspec tests and then coded to pass the tests. This was a great exercise and the way I would ultimately like to code as a developer. As a student though, time (and money) is limited and I didn't write anymore tests but continued on with the project.

I started with the easy stuff first and set up my models and bare-bone controllers first. Then I fleshed out the city and country controllers and views. Then I headed for the more difficult stuff and set up my user controller and views. This is the point at which I started looking at validations. I had already decided to use RackFlash3 and felt I had a reasonable handle on its use but after setting up my first catch and validate I didn't get a message! I prevented the bad data I just wasn't telling the user what the problem was. A little head-scratching later of course it was all down to how I was setting up RackFlash3. I had put 'gem rack-flash3' in my gemfile. I'd done `bundle install`. I'd required it in my environment.rb file. I placed `use Rack::Flash` and `enable :sessions` in my city_controller just like in the lessons and no flash messages! I then took a closer look at my application_controller and realised I had already placed `enable :sessions` there, so I removed that line from my city_controller and voila messages were showing!

With all the coding done the next step was running through the app multiple times with `shotgun`. And I mean multiple times, checking everything that a user might do or try within the application. Checking all my routes, attempting to put in bad data, leaving out input field entries and trying to access pages without being registered or logged-in. Once I was sure that I had idiot-proofed everything, validated all entries and blocked unauthorised access to pages it was onto presentation.

My memory of CSS was a bit sketchy so I went back through CSS in learn and refreshed and relearned. I wrote my style.css file and linked it in layout.erb and then headed to `shotgun`. Nothing. Nada. Diddly-squat! I played and played with the link path in layout.erb to no avail. I then googled CSS and erb trying to see where I was going wrong and got nowhere. I then coded the CSS inline into layout.erb and suddenly I was seeing styling coming through! Exciting, until I realised that my background pic was nowhere to be seen. Back to google and trying out different ways to write the same thing with no success, the usual red-herring stuff! 

Eventually in my reading something began to tug at my memory, was I putting the image in the right place? Yep, despite trying to place it in all sorts of folders and proximities to layout.erb the correct place had to be root/public/images/'picture'. Ok then, maybe it was the way I was declaring it? In the rails related google responses they seemed to only declare part of the file path as though some of the path was known to Sinatra.
I began to fiddle with my path link in layout.erb and then suddenly I had a background picture! Sinatra with Ruby and without Rails **expects** to find the images folder in `root/public`, you don't need to declare it in the file path. So my file path went from `../../public/images/'picture'` to `/images/'picture'`. Simple huh? 

This revelation sent me back to my CSS placement. I decided to recreate my style.css file and remove the inline CSS from layout.erb and alter the file path in the link. Sure enough, with a file path of `/stylesheets/style.css` all of a sudden I had all my styling working with external CSS styling. To say I was excited is an understatement! Again, Sinatra **expected** to find the style.css file there!!!










