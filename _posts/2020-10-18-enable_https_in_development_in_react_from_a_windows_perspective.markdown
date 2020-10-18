---
layout: post
title:      "Enable HTTPS in Development in React from a Windows Perspective"
date:       2020-10-18 20:23:56 +0000
permalink:  enable_https_in_development_in_react_from_a_windows_perspective
---



In my last blog post I made a plan to implement user authentication via facebook. That goal has not yet been achieved. Instead I have encountered an obstacle that has engulfed enough of my time to warrant it’s own blog post. 

Why do I need to enable HTTPS? 

I am using Facebook’s guide “Facebook Login for the Web with the JavaScript SDK” (https://developers.facebook.com/docs/facebook-login/web). Facebook requires HTTPS to be enabled on all applications that want to authenticate users via Facebook. 

How do I enable HTTPS in development in my ReactJS application?

Note: I am using WSL (windows subsystem for linux) so these commands are for linux. When I browse, I am browsing using Google Chrome for Windows.

One way is from the command line. Simply type “HTTPS=true npm start”

[Imgur](https://i.imgur.com/WHTQx3q.png)

Alternatively, you can create a .env file in the root directory of your React app and add HTTPS=true.

[Imgur](https://i.imgur.com/tMPgyuK.png)

Both of these options achieve the same results. 

When you navigate to your application you will encounter a warning: NET::ERR_CERT_AUTHORITY_INVALID

[Imgur](https://i.imgur.com/R06rYd1.png)

When you click on the certificate you Google Chrome will tell you what this means. This certificate is not trusted. We also see what we need to do next, install this certificate in the Trusted Root Certification Authorities store. 

[Imgur](https://i.imgur.com/P9IiKuN.png)

You might be wondering,
Why do I need to do this now and why don’t I need to do this every time I visit a secure website?
What is a Certificate Authority?

In cryptography, a certificate authority or certification authority (CA) is an entity that issues digital certificates. A CA acts as a trusted third party—trusted both by the subject (owner) of the certificate and by the party relying upon the certificate. (wikipedia)

Live websites rely on third party Certificate Authorities to assign digital certificates that are known to be trusted so we don’t usually run into this warning while browsing live websites.

We see this on our React App because React Creates a self-signed certificate that is not trusted.

Let’s add this certificate to the Trusted Root Certification Authorities store. I followed this guide:
https://help.ivanti.com/ap/help/en_US/fd/4.4/Content/FileDirector/Admin/3_Clients/Install_Root_Certificate_on_Windows.htm

And there you have it! Don’t forget to close your browser and restart your Dev server.

[Imgur](https://i.imgur.com/2mih4np.png)


And now for my next challenge: Implement user authentication via Facebook. Stay tuned!

