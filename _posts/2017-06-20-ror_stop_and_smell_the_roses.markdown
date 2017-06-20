---
layout: post
title:  "ROR stop and smell the roses!"
date:   2017-06-20 23:07:28 +0000
---


What an amazing journey into the world of magic that is Rails! 

My biggest take away from this journey is to 'stop and smell the roses'. Learning Rails is fast paced and it is easy to stay on the fast track but you may find when you reach your destination that your knowledge bag is lighter than it should be. 

I raced through the topics admiring the magic, using the magic in the labs and then moving on to the next amazing topic. When I left each topic I felt I had a solid grasp of the content. It wasn't until I got to the final projects that I realised just how many topics I had covered and how few of them I could still say I fully understood and remembered. I had a vague memory of some and for some a 'feeling' I had covered them but some of the key knowledge was hazy at best.

When it came time to complete the major project I had to go back and relearn a number of topics. What I discovered was the first time around I had learnt the 'how' of the topic but I didn't necessarily understand the 'why'. Without the 'why' I couldn't fully comprehend when I needed to use methodologies nor could I get them to work by just copying the code in the lessons.

One example was nested attributes, especially nested attributes without the magic of 'accepts_nested_attributes_for'. I quickly coded in a method in my model but when I tested it I did not have a working method. My first attempt wasn't too bad:

def movements_attributes=(movements_hashes)
 		movements_hashes.each do |i, movement_attributes|
				move = Movement.find_or_create_by(name: movement_attributes[:name])
				move.movement_type = movement_attributes[:movement_type]
				move.save
				self.movements << move
 		end	
end

I was handling the hash ok, I had the find_or_create_by happening but there was this funny attempt at forcing the relationship with 'move.movement_type'. My second attempt just got worse, I lost the hash concept somewhere in the wrestling with the method and doubled up on the build and lost the 'all' in the find_or_create_by:

def movements_attributes=(movements_attributes)
 	movements_attributes.values.each do |movement_attribute|
			move = Movement.find_or_create_by(name: movement_attribute[:name], movement_type: 
										 movement_attribute[:movement_type])
					self.movements << move
					movements_attributes.each do |movement_attribute|
							self.movements.build(movements_attributes)
					end	
  	  end
end			

...obviously I did not understand what I was trying to achieve and the lack of knowledge made the debugging process near impossible. Back I went to study this topic in depth. My final attempt was simple, succinct and most importantly worked:

def movements_attributes=(movements)
		movements.each do |i, movement|
				movement = Movement.all.find_or_create_by(movement)
				self.movements << movement
		end	
end

When magic is involved it is far too easy to code by rote without fully grasping what you are doing. Moving forward I will think harder about each topic I tackle and I won't move on until I understand the how and the why as well as being able to use the methodology on my own. 


