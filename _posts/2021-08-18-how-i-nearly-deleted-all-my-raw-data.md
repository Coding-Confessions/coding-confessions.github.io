---
layout: confession
title: "How I nearly deleted all my raw data"
permalink: /confessions/:title/
date: 2021-08-18
category: Blog
author: Anonymous
about:
link:
uid: anon2
---
### Background
We keep all our raw data (which was very expensive to generate) on a big server, Server 1, which, when you need to use it requires copying it across to another server, Server 2. Server 2 is only supposed to be for data analysis and we are encouraged to delete any data files that we are no longer working on.

### What Happened
I accidentally used mv (move) rather than cp (copy) in command line to move the data from Server 1 to Server 2. When I was done with it I was about to delete it all, luckily I realised my mistake last minute and scp'd the data back to Server 1.

### What did you learn?
I confessed to my near miss and asked for the data permissions to be changed so that no one else would repeat my mistake. The permissions have yet to be changed but I share my scp code any chance I get so that others on the team don't have to work out how to move/copy data themselves.
