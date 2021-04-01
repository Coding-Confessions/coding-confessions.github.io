---
layout: page
title:  "The typo that nearly broke my first paper"
date:   2021-02-09 09:59:55 +0000
category: Blog
author: Eirini
---

### What's the background?

This happened in the second year of my PhD, when I submitted my first ever paper for publication. My background is in experimental psychology and most of my coding was about cleaning data and running inferential statistics in R.

### What happened?

I got back the reviews for this very fist paper and saw that one comment was about something weird in my stats. A strict method of assessing statistical significance was finding a lower *p* value than a more lenient method of assessing statistical significance.

What happened? A typo. But not one of the typos that throws an error. No this was a mode insidious typo, the kind that breaks your analysis and you don't notice. So, for people who use the lme4 package in R, I used "*" instead of ":" to specify interactions between my predictors. When comparing my full regression model to models with these interactions removed, instead of removing only the effect of interaction, I removed the effect of the interaction **and** the individual predictors. This made my interactions seem they had massive effects when, in fact, they really didn't.

This realisation easily led to the more terrifying Sunday afternoon of my PhD, when I reran all my analyses not knowing if I was reporting a real effect in my first submitted paper. In my panic, I didn't even stop to think that this only affected the effects I reported about interactions - effects I didn't actually care about.

### What did I learn?

1. Peer review actually works!
2. Don't work on Sundays.
3. Panic is not helpful - if you find yourself panicking, try to take a step back and take some deep breaths.
4. When doing a new kind of analysis, get someone to check your code!
5. It's okay to make mistakes. I almost convinced myself that a *real* scientist would never make a mistake like this but when I finally found the courage to talk about this to my peers, no one thought it was strange. And that was truly liberating.
