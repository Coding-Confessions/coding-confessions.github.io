---
layout: confession
title: "How it took five years to realise I wasn't closing my database connections"
permalink: /confessions/:title/
date: 2021-09-17
category: Blog
author: Jannetta Steyn
about: Senior Research Software Engineer at Newcastle University
link: https://rse.ncldata.dev/team/jannetta-steyn
uid: jannetta
---
My name is Jannetta Steyn and I am a Senior Research Software Engineer at Newcastle University. I worked in industry for many years before returning to university to do a PhD. After the PhD I worked as a Bioinformatician and then a couple of years as a Senior Research Associate before joining the Newcastle University's Research Software Engineering Team in 2019.

My code confession is about something that happened to me many, many years ago - pre-Internet days actually. But, I think this is my favourite boo-boo because although it happened so long ago I still remember the panic and what I learnt is still very applicable to today.
I worked at a company where we developed software for the financial markets. It was a rather weird and complicated infrastructure. We were using UCSD Pascal running on the on an operating called the p-system (most people have probably never heard of this) and this was running on top of MSDOS (the old Microsoft Disk Operating System which was used on PCs) and then we ran Novell's Btrieve database in MSDOS.

Now I only take partial responsibility for my mistake and the reason for this is: My boss, at the time, wrote all the libraries that we needed to get access to the architecture's underlying features. So there were some Assembler functions and loads of Pascal libraries that would have the p-system communicate with MSDOS and Btrieve. Obviously my boss didn't document any of these things so you discovered things in one of two ways, you either asked him about it or you opened the source code of the libraries and extracted all the headers which would give you an idea of the functions and procedures that were available to call. I remember asking him how to open a connection to the Btrieve database and he told me what function to use.

At that time I had to write a system for the Reserve Bank of South Africa to manage their Treasury and Landbank Bills which they issued every Friday. Companies would tender for a certain values worth of these Bills. Their tenders and the preferred denominations would be entered into the system and then, when the tender process closed, the system would automatically do the allocations, verify or recalculate the dominations, and print out the bills. Entering the bills were done manually but there were usually no more than 20 or 25 bills. So this must have worked for about two or three years. I actually left the company for a couple of years after that but shortly after I returned, one Friday, I get a call that the system is bombing out. I was a wreck. How can something that has been running for four or five years suddenly start breaking? Where do I start looking. So I took the data for the last few weeks and started entering it like they would at the bank. Everything worked, except for that specific Friday's data. After a while I noticed that the only difference was that for the first time there were more than 25 entries - there were 27 but the program would bomb out on 26. I stared at the code under great pressure. I had to get the code working before something like 2pm because that was when they were suppose issue the bills to those who won the tenders. I was desperate. I called my boss over. He looked at the code and started giggling and then started walking away. "Aw come on!", I said, "What is it? What's wrong?"

The problem was: After entering the tenders there was a loop in the code that would read the tenders from the database one after another. Inside the loop I would open the database, read the record and then do whatever needed doing to it. What that meant, to the way things worked in those days, was that every time I opened the database it would open the database file. However, DOS was, by default, configured with 25 file handles - meaning it could open a maximum of 25 files and then you would get an error. I never closed the file before exiting the loop because my boss never told me that there was a closing function and I never though about it so I never asked. All I needed to do was one of two things, either close the file before exiting the loop, or the better and more efficient way was to move the opening of the database to before the loop, then read all the records in the loop and then close the database when I exited the loop.

So the lessons learnt:

1.  Tell your boss to document his code! Or perhaps more general - everyone should document their code :-)
2.  If you open or allocate something make sure to close or free it. If closing is not obvious - investigate whether there is a need for it. Nowadays files and database connections are often closed automatically by compilers and IDEs will give you a warning. But, I check it anyway, it has been engraved in my brain.
3.  Make sure the stuff you put in a loop needs to be in the loop - it might not need to be repeated and would be more efficient outside a loop.
4.  Test with more than what you are given - just generate dummy records or loads of duplcates if your system would allow it.