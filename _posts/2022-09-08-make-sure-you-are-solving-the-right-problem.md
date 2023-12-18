---
layout: confession
title: "Make sure you are solving the right problem"
permalink: /confessions/:title/
date: 2022-09-08
category: Blog
author: Sadie Bartholomew
about: Computational scientist working for the National Centre for Atmospheric Science
link: https://sadielbartholomew.github.io/
uid: sadie
---
### What's the background?

I was working on an open source Python library hosted on Github in a team of about 5 people. This used a standard workflow with an issue tracker, new branches being made for each issue and pull requests with code reviews being used to put code back on the main branch.

### What happened?

I was investigating a bug and went through various debugging techniques trying to fix it. I thought I had identified the problem and changed some logic which partially fixed the bug. But I couldn't find a solution to fully fix it and started to get frustrated. In the process I noticed another bug, fixed that and submitted a pull request. The second bug
appeared to be trivial and I described it in the pull request. A colleague picked up the pull request for review and tried to reproduce the bug, but wasn't able to. It turned out that the bug was caused by my initial fix for the first bug and my colleague couldn't reproduce it as they didn't have the code for that bug fix.

### What did I learn?

* Getting frustrated can lead to illogical thinking, it is a sign that it is time to stop and come back to the problem later.
* Software developers like to solve problems, but make sure you are solving the right problem!
* Context switching contributed to this problem, be sure to re-centre yourself on a new problem after a context switch.
* Keeping notes on what you were doing can help with context switching.
* Code review really can stop bugs getting into production code.