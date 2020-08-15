---
layout: post
title:      "React does not always need Redux"
date:       2020-08-15 00:53:31 +0000
permalink:  react_does_not_always_need_redux
---


I just completed my final project for the Software Engineering Bootcamp. I wanted to create my dream workout app, one that simply logs workouts and then shows me helpful charts and graphs about my progress. 

As this is my dream app, I have a passionate vision for what it is supposed to be. I wanted to use this project as a rough draft or a test run of my ideal app. I know from my previous projects that the perfect app does not get developed in two weeks, notwithstanding an actual miracle. 

This project served that role very well. This is my first project with React and I needed to really familiarize myself with the design patterns to help me visualize how I want to make my app work. One major concept that this project really helped solidify in my mind is that React does not alway need Redux. There are plenty of times when state can be managed sucessfully and potentially more efficiently and simply by using state saved locally to the component rather that using state stored in the Redux store. 

In the beginning of my project I thought it would be useful to useful to store the most recent 5 logged workouts to the Redux store. Later I realized this was only used in one component and it wasn't useful anywhere else. As I continued to build my app I found that each component was using data that wasn't useful beyond a parent or sibling component. I was able to asynchronously request data using React's ComponentDidMount function and save it to the state of a container component and send that data down as a prop to several different child components.

In the end I acutally removed all of the Redux funtionality from my app because it really didn't serve any useful purpose. Admittiedly, this app is a few major steps from my dream app and I may end up bringing Redux back in before my dream app is made real. As I see it, those major steps would include, make this a mobile app, add user accounts, and user authentication.
