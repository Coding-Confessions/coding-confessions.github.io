---
layout: confession
title: "Trust your intuition!"
permalink: /confessions/:title/
date: 2021-11-09
category: Blog
author: Anonymous
about:
link:
uid: anon3
---
## Background

I was trying to set up a new simulation with a pre-existing fluid flow model. I wanted to simplify the situation I was modelling while I debugged it but it wasn't easy to change the parameters so I hard coded one of them, the rotation rate, to be zero while I got on with the debugging (you can probably see where this is going, unfortunately I couldn't at the time...)

## What happened?

Well I fixed the problems with setting up the simulation but whatever I did I could not get anything that looked like rotating flow. I kept tweaking things and plotting the fields and muttering to myself "it's almost like the flow just isn't even rotating". Honestly, it was over a week before I remembered that I had hard coded the rotation rate to be zero. I was furious with myself for forgetting what I had done, but more than that I was furious with myself for not trusting my intuition that the modelled flow was not actually rotating!

## What was learned?

One thing I learnt is that it should be easy for users to set up new parameters for a model without having to dig into the depths of the code. I also like to have the simulation print out a log of what it thinks it is doing for me to check that everything is set up how I think it should be. But mostly I've learnt that when I start muttering "it's almost like..." then that it is a very good clue for where I need to start with my debugging!