---
layout: post
title:      "Authentication in React Redux "
date:       2020-09-28 18:25:32 +0000
permalink:  authentication_in_react_redux
---


Authentication - the process or action of verifying the identity of a user or process.

Authorization - giving permission or authority.

I am a recent Flatiron Graduate from the Software Engineering Bootcamp. For my final project I created an app to track weight lifting progress. A user logs sets (exercise type, weight, and number of reps), then they can view their recently logged sets feed or they can view overall statistics for each different workout type. 

When I submitted my final project my authentication system was very simple and not secure. To log in, a user would enter their email address. When the form was submitted a Redux action was triggered sending a fetch request to the Rails API with the assistance of Redux Thunk. If that email address exists in the database then the API would return that user’s information. When the promise resolved the user id would be saved in the Redux store, the user would be “logged in” and redirected to their dashboard.

One of the very next things that I want to learn next is the authentication and authorization pattern in React Redux and how can I implement OAuth or something that will allow users to login securely via Facebook or other similar third-party applications. 

In the Redux FAQ section (https://redux.js.org/faq/miscellaneous) this question is answered. The pattern is basically what I have already implemented! The specifics of how users are authenticated is up to your application, but the general pattern is to have actions for LOGIN_SUCCESS and LOGIN_FAILURE. Use Redux Thunk to fire a network request with the user’s login information then respond appropriately to that response. 

Great! I’m halfway to my goal of allowing users to login via Facebook. However, this second part has been a bit of a challenge for me. What are my options for authenticating users? How can I make sure they are who they say they are?

One option would be to handle authentication on my own by making users create a password. That would work, but at this point in our technological evolution, nobody wants to type anything or remember passwords. 

Ideally, I would like to use OAuth because I have experience using this framework. In the past I used OAuth for a Rails web application so my first question was, 

**“Will OAuth work with a React Application with a Rails API?”**

A quick stop by OAuth’s documentation page quickly answers the question, yes OAuth will work with a single page application. 

One option is to handle authentication completely in the front-end. (https://aaronparecki.com/oauth-2-simplified/#single-page-apps) This option needs to be implemented differently than a server based web app like a Rails app because with a Browser-Based app like React, the secret cannot be kept confidential. 

Could this work with my application? Yes. The action triggered by a user submission would trigger the authentication request. Then, based on the resolution of the authentication request, I would either send another request to the Rails API to fetch user information, or redirect and display an error message. 

Another option is to handle the authentication in the back-end server (https://tools.ietf.org/html/draft-parecki-oauth-browser-based-apps-02 section 6.2)

To avoid the risks inherent in handling OAuth access tokens from a
purely browser-based application, implementations may wish to move
the authorization code exchange and handling of access and refresh
tokens into a backend component.

This was my original intention however, when I thought back to my Rails experience with OAuth I remembered redirecting users to a specific OAuth url, then the users are redirected back to my application. My confusion was that with my single page app, how am I going to redirect users? I want the user to stay on the same page while this happens in the background.

The source of my confusion was that I forgot that we can send GET and POST http requests in the background without redirecting the user.  I have yet to implement this in my application so we may see a follow up blog post in the near future. With that in mind, this in my tentative implementation plan: 

1.	A user clicks the “Login via Facebook” button.
2.	An action is triggered sending a request to the Rails API.
3.	In the Rails API send a GET request to OAuth’s Authorization server.
4.	 The user will be prompted to allow my app to access their information. They will allow access.
5.	OAuth’s authorization server will send a request back to my application with an authorization code.
6.	My app will send that authorization code back in exchange for an access token.
7.	The user is authenticated, I can send a request to my Rails API for their user information and redirect the user to their dashboard. 

Keep a lookout for a follow up blog post that will document my successes and failures. 

