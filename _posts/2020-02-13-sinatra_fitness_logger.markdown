---
layout: post
title:      "Sinatra Fitness Logger"
date:       2020-02-14 03:31:36 +0000
permalink:  sinatra_fitness_logger
---


This whole activerecord and sinatra section has been a real struggle. Not because the content is particularly difficult but because my personal life has been overwhelmingly full and it has been a struggle to put in the time to really learn. Thankfully this project served to solidify my understanding of the major concepts like RESTful routes and the structure of a MVC project. 
Interestingly, I found it a lot easier to create my own basic project from scratch (using the corneal gem) than completing the fwitter lab. Fwitter was very similar my project but between version incompatibility issues causing migration issues, and a weak understanding of RESTful routes/the MVC project structure, Fwitter was a nightmare. 

My dream for a perfect fitness logger application is much greater than what I created. I realize now that complex many to many relationships can really compliate a project quickly. I wanted to support weight lifting logging but due to my current time constraints I decided against the idea of having mulitple sets associated with a workout that are in turn associated with a user. I believe this would be a User has many Sets through Workouts type relationship. I reserve this expansion for a future time.

The project I actually created is a simpler User has many Workouts type relationship. The workout therefore is only a cardio type entry with a cardio type, distance and/or duration with a calcluated pace and title. I am proud of what I created and I think it works well. With my ongoing time limitations, I'm happy I decided against the many to many relationship for now. This was enough to really solidify my understanding of core concepts and was challenging enough as it is.
