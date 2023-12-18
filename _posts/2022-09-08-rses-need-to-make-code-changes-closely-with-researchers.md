---
layout: confession
title: "RSEs need to make code changes closely with researchers"
permalink: /confessions/:title/
date: 2022-09-08
category: Blog
author: Dan Katz
about: Chief Scientist at the National Center for Supercomputing Applications
link: https://danielskatz.org/
uid: dan
---
### What's the background?

I was working at JPL in NASA with a distributed team of scientsts from across the country. Their project had a series of performance milestones that they had to meet in order to get paid.

### What happened?

I started looking at their code and found some inefficiencies and spent two or three weeks optimising these. But they didn't make much difference to the overall execution time and it turned out there were parts of the code that didn't get used very much. I learned to target my optimisations and moved to some other parts of the code. Compilers in this era weren't very good at making automatic optimisations and I had to resort to some major restructuring and manual loop unrolling. This made the code harder to read, but it did measurably improve its speed. This allowed them to meet their targets for the milestone and they got paid. When it came to the next milestone they asked me to help with some other parts of the code and I realised my earlier changes weren't there. They said that my changes had turned it from their code into my code and they didn't understand the code anymore and didn't feel they could own it.

### What did I learn?

* Target your performance optimisations to things which run often.
* RSEs need to make code changes closely with researchers and ensure they still feel that they own the code.