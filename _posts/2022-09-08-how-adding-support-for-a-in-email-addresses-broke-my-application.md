---
layout: confession
title: "How adding support for a + in email addresses broke my application"
permalink: /confessions/:title/
date: 2022-10-17
category: Blog
author: Mark Woodbridge
about: Software developer at the UK Dementia Research Institute at Imperial College London
link: https://markwoodbridge.com/
uid: mark
---

### What's the background?

I’m a long-time research software engineer, mainly working on backend services and infrastructure. This story is about an instance where I was maintaining a web application that included functionality to search for users by email address. It was reported that this feature wasn't working for addresses containing a "+" symbol (e.g. `a+b@gmail.com`). I was no Angular expert (and not a full-time frontend developer) but already had a hypothesis about the issue so decided to take a look.

It turned out that we had introduced such email addresses ourselves for internal users.

### What went wrong?

_Mistake #1 was doing this without collectively considering any potential implications._

The consequence was that the server was receiving search requests for `a b@gmail.com` because, as the W3C URI spec says:

> Within the query string, the plus sign is reserved as shorthand notation for a space. Therefore, real plus signs must be encoded.

So the obvious fix was to the encode any search parameters. On invesigation it turned out that no parameters were being encoded in the reassuringly named client-side `search()` function. I changed it and added an automated test.

_Mistake #2 was assuming this change would be without consequences i.e. I didn't check downstream code._

The fix seemed to work fine - existing searches worked, as did the previously broken ones. So I opened a PR including a description of the diagnosis and the cure, as well as manual test script, and assigned it to a reviewer. They were an experienced developer but no more familiar than me with Angular, and hadn't previously worked with the relevant part of the code. However, they agreed with the approach, followed the test script, and approved the MR.

_Mistake #3 was that they perhaps weren't sufficiently skeptical about the wider implications of the change, including why unencoded parameters hadn't previously been an issue._

The change was deployed to development and pass to designer for review. They were happy to see an unusually comprehensive test script, so followed it and further approved the PR.

_Mistake #4 was that they were so directed by the test script that they didn't do any further testing._

The change was pushed to staging, and again manually tested and signed-off.

_Mistake #5 was that although staging contains very different (i.e. more realistic) data than development, a full regression test wasn't performed as would normally be the case, because the fix appeared so targeted and there was pressure to ship the change._

In the meantime another developer noticed that pagination was broken on the development system.

_Mistake #6 was my assumption that this was a recurrence of a (rare) race condition under separate investigation._

Eventually another member of the team noticed breakage in a seemingly unconnected part of the app i.e. assignment of users to groups. The ultimate cause of this was the search method, despite its name, was not only used for search but also for retrieval of resources by ID(s). But in this case the comma separated list of IDs was encoded before calling the function. Pagination had also silently broken because it relied on a continuation token being passed to the search function, which had also already been encoded.

_Mistake #7 was not having comprehensive E2E tests for these features._

### So we learnt some lessons:

- Actively discourage deference to other developers who are more experienced or more familiar with the code in questions - this does not make anyone infallible. It's good to regard all changes with skepticism!
- Don't assume that code changes only have local effects
- Automate tests wherever possible, but if you rely on manual testing then ensure that it is done with discipline

### And we made some changes:

- Perform acceptance tests in staging, and do regression testing without exception
- Improve E2E test coverage
- Consider how typing can be used to distinguish between raw and encoded inputs

All in all this was an educational (if sobering) experience. The issue and fix were fairly mundane, but as an experienced developer it was surprising (to me) how many classic traps I fell into, and how many improvements could be made as a result of a thinking thoroughly about the root causes. This is a very real example of how mistakes are an opportunity to learn!


