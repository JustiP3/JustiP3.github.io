---
layout: post
title:      "CLI Ruby Gem - Your Favorite Artist"
date:       2019-12-03 20:41:17 +0000
permalink:  cli_ruby_gem_-_your_favorite_artist
---


Project # 1 complete. Nice.

My CLI Ruby Gem is called "Your Favorite Artist". It works with the last.fm API to gather information about your favorite artist and display results based on your input.

I think this is the first time in my programming career where I've created a project that interfaces with an external source, and it feels very satisfying to see my program work. 

I have worked on projects that interface with external data at work (I am a PLC controls technician in the material handling warehouse industry). I don't count that though, because it's not my project and I don't have a complete understanding of how it works. 

In that application the PLC (Programmable Logic Controller) is responsible for contorlling the hardware - when do conveyors start and stop, when to allow packages to merge, and when to divert packages on a sorter. What the PLC is not responsible for is the relationships between barcodes and orders, logical lane names, and divert assignments - we rely on a software server to tell us that information. So there is an interface, we send and receive message instructions via some sort of connection - generally ethernet. 

It's not my responsibility usually to set up that communication so I don't know much about it. This was my first time really getting into an API which was the main source of struggle for this whole project. I felt that in this point of the course I had a strong understanding of object oriented ruby and that was not difficult to manage.

In addition to never working with an API, I had never worked with the HTTParty ruby gem. With a little bit of help I was able to see how to parse a response from the last.fm API using HTTParty, then I was in the clear. Creating an artist class to store all of that information was an obvious next step, and was explicitly listed in the project requirements so I started building an artist class to hold all of my data.

Later, I found that to display album information it would make sense to additionally have an Album class. Again, this felt like a natural next step after all of our work in object oriented ruby. 

At the conclusion of this project I feel like I'm walking away with 
API skills +10
HTTParty skills +10
Object-Oriented Ruby +3 

I am very excited to start database work because that is also something totally new for me. 
Let's get this bread 
