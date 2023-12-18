---
layout: confession
title: "How I lost 90% of my project's data"
permalink: /confessions/:title/
date: 2022-09-08
category: Blog
author: Callum Mole
about: Research Data Scientist at The Alan Turing Institute
link: https://www.turing.ac.uk/people/research-engineering/callum-mole
uid: callum
---
### What's the background?

When I was working as a PhD student and a researcher I always spent a lot of time designing an experiment and then enjoyed getting to run it, publish it and do talks about it. There was always a fear that a bug in the code could bring everything crashing down and one time it did. 

### What happened?

I was working on a big psychology project and was writing the code for handling the experimental results. The experiment consisted of lots of trials for multiple conditions. Each trial was supposed to have one file containing the results for each condition.

When it came to analysing the results I realised that I had made the cardinal sin of saving over the data. I had forgotten to include the trial number in the file name, I only had the results of one trial and had been overwriting the results each time a new trial was conducted. I'd lost about 90% of the data from the experiment. It wasn't something I could keep quiet and was very embarrased to own up to it, but I didn't have a choice. Everyone invovled was initially quite annoyed, but later found it funny and it turned into a long running joke.

### What did I learn?

* That I should write tests (even though I still often don't)
