---
layout: confession
title: "Documentation and other stories"
permalink: /confessions/:title/
date: 2021-09-17
category: Blog
author: Yo Yehudi
about: Executive Director of Open Life Science, a non-profit mentoring and training company
link: https://yo-yehudi.com/
uid: yo
---
## Confession 1

I'm going to talk about the time when I joined the University of Cambridge.
At this point, I'd been working in my research group for about three weeks.
I was a front-end developer, which meant that I worked on the stuff that people interacted with and that they clicked on the screen.
For some reason, our web servers were managed by the front-end developers.
I don't know why it was the case, but it just was.
Now, my colleague, the other front-end developer, had gone on holiday and someone said "Hey Yo, we have some problems with these sites, could you reboot the server?"
So, sure enough, I log on to this server and I spend a little time hunting down the docs.
We were using dokku, something like an open-source version of heroku, which is an online web host effectively that allows you to run certain applications.
We were running dokku on our own server.
I thought that I'd looked up the docs and done everything really well, so I rebooted it.
I should mention at this point that we had about five or six sites running on this, including our API documentation that tens of developers from a large community and around the world used.
And, perhaps more importantly, our PI's website was hosted on this server.

I rebooted the website three weeks into the job; it did not come back up.
And one of the most mortifying things to do is go to a senior colleague and say "Yeah, I've just broken everything, including our boss's website".
It was so hard to do!
Obviously, they were gonna figure it out at some point, so I had to go and tell someone, but there's definitely a feeling of "Swallow your pride, hope you keep your job next week and tell someone what's going on".
Thankfully, the senior colleague in question was really good, they approached the sysadmin and asked about backups and whether they could help us.
And after lots of "documentation spelunking" (that's really the only way I can describe it), just looking through unclear, mysterious documentation that doesn't quite work with your scenario, I did manage to get these sites back up.

### My lesson from this is:
Document your stuff really well and don't assume people's knowledge.
If someone goes away and everything breaks, then that is not documented well enough.
So I don't feel too bad about it for myself, but it is one of my favourite stories just to introduce newbies and interns if I have someone like a Google summer of code student working with me, first thing I would tell them early on is, you know, if something goes wrong, it's okay to tell me, and then I share this story, because it's really useful to know that even destroying everything, it's okay - we will figure it out as long as it's an honest mistake.

## Confession 2

The next one is about git which, for those of you who haven't used it, is a good version control system.
Git keeps everything indelibly on the public record.
That means that if you accidentally put stuff in there that you didn't want to, it may still be in the public record even when you remove it -- it may just be a little bit harder to find.

Now, I kept on getting messages from our sysadmin saying "Yo, you're over space, you have a TB over space".
And it's like "No, I know I've never downloaded a TB of data, I've never generated a TB of data, there is no way".
So I just kept on ignoring these silly messages.
And then one day, the sys admin literally came down and looked at me like "Yo, why are you still over quota?"
So I actually went and I looked, and I ran some commands, and sure enough, there it was!
That TB of folder space that was taken up.
So how is this happening?
After some digging, I found out that someone had checked in a bunch of data into a git repository I'd cloned and then removed it.
This meant that I couldn't see the data in the repository, because old stuff is still on the record but it's not obviously visible.
So I had a TB worth of "removed" invisible data just hiding there, clogging up everyone's space for ages, which was really embarrassing.

## Confession 3

And I have a bonus one, also about git and things that are indelibly in the public record.
When you are making commit messages (where you explain what's going on and why you've made a commit -- a "save" as it were in the version control), check that you don't have typos.
I tried to write a commit message about having added a module organism called "yeast" into the database.
But, the "d" key is very close to the "s" key and the last thing that you ever want to be adding into your git repo indelibly is something about ass yeast.
[A tweet about this story](https://twitter.com/yoyehudi/status/840161418779471872?s=20)
