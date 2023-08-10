---
layout: confession
title: "Database for financial transactions"
permalink: /confessions/:title/
date: 2021-10-18
category: Blog
author: Anonymous
about:
link:
uid: anon1
---
**What happened?**

An early task at a new job was to move a subset of rows from one database table to a new table, deleting the original rows. This involved writing a migration script, running it on a test database, then getting it signed off to be run in production. On the test database, this went perfectly, so it was signed off. On production however, it went... less than perfectly - the entire system stopped processing transactions. What had happened was that the condition used to select rows did not use an index, and so the table was locked while the delete was carried out. The production table was orders of magnitude larger than the test database, so this meant it needed to be locked for a very long time. Thankfully, the problem was caught before too long (although long enough to cause problems) and the operation cancelled. Later we found a safer (although more complex) approach to solve the problem.

**How can others prevent repeating it?**

Testing is always important, but it's just as important to know (and record) the differences between your test environment/assumptions and your production environment.

However, the most important thing I learned from the incident was not specifically coding-related - the thing I learned was that it was okay to make mistakes. I might have written the code, but not one person blamed me - other people also signed the change off, and there were other places in the process where changes could have prevented the issue.

