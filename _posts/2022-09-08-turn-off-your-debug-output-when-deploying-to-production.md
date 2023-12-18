---
layout: confession
title: "Turn off your debug output when deploying to production"
permalink: /confessions/:title/
date: 2022-09-08
category: Blog
author: Anika Cawthorn 
about: Senior Research Software Developer at University College London
link: https://www.ucl.ac.uk/advanced-research-computing/people/anika-cawthorn
uid: anika
---
### What's the background?

I was developing web applications in the era before cloud servers. I would develop code and hand it over to another team
who would do a little testing before deploying it to the live system. 

### What happened?

I had developed some new code. During this process I wrote a few of my own tests, but also added some debug print statements.
These print statements saved their output into a logfile. I got the application to a point where I was pretty sure 
everything was working and I handed it over to be deployed. 

A few weeks later I got a call a few weeks later saying that the app has crashed the server. My initial reaction was 
denial, it couldn't possibly be my app which was causing this. But I had forgotten to turn off the debugging print statements
and my app had created a large logfile, run the server out of disk space and caused it to crash. 

### What did I learn?

* Turn off your debugging print statements before going into production.
* Get somebody else to stress test your code before deploying it.
* If you receive code from somebody else to deploy, stress test it first.