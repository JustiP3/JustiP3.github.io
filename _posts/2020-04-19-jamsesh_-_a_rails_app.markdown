---
layout: post
title:      "Jamsesh - A rails app"
date:       2020-04-19 22:22:49 +0000
permalink:  jamsesh_-_a_rails_app
---


The idea behind this project was vague, and as a result the process felt messy. The initial idea was, "A web application to connect musicians both serious and casual. Maybe that means someting like tinder for musicians. Maybe users can post recordings and post constructive critisism. Maybe users can also review and talk about professionally recorded recently released music. 

Somehow, after navigating through endless possibilites I ended with a reasonably consice web application. This process involved cutting out many tangential ideas in order to create something that makes sense and also meets the project requirements. 

One of my next greatest challenges after deciding what Jamsesh is was navigating the very abstract form helper methods like "button_to" and "collection_select". 
If I'm being honest I still don't have a perfectly solid understanding of these helpers. What I know is that these helpers abstract complex html into a single line. In order to make this complex html work, we need to pass in a number of arguments. What those arguments are and what those words mean is the source of my confusion (object, method, collection, value_method, text_method, options = {}, html_options = {}).

I know object is the object of the form - @user in the example below
<%= fields_for @user do |u| %> 
The method I believe needs to be a method of the object. What this method does and how it's used I am not sure.
The collection is the collection that we want to select from.
The value method is what will be sent in the params hash and is what we want to work with in the controller.
The text method is the method called on each element of the collection and what will be displayed in the view/template dropdown menu.
options and html_options are outside of my knowledge completely at this point, all I know is that you can pass a block with some code. 

The way I was able to make this work was to copy some example from the doumentation, change the arguments to what I thought matched my application then use error driven development to make it work. Usually this is a pretty quick process for me but with both collection_select and button_to I spent a lot more time than I am proud to admit troubleshooting these methods. 

Despite my frustration, or maybe because of my frustration, I am proud of the result of this project. Also, I am not too worried about my vague understanding of these form helpers, with time and repetition everything difficult becomes easy like second nature. 

