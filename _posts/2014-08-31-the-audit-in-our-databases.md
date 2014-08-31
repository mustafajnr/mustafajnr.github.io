---
layout: post
title: The Audit In Our Databases
published: true
---

>There is nothing worse than starting your software development career, and think that things wouldn't be different than what you already did in your education; only to find the exact opposite. This is one example.

And so I started my career. After five years, in which I tried very hard to benefit the most from, in developing my software development skills, and thought that I have went [where no man has gone before](http://en.wikipedia.org/wiki/Where_no_man_has_gone_before), with my Super Ultimate Maximally-Dynamic Relational Database Design For Generic Objects (SUMDRDDFGO, pronounced sumderdedefgo) - I will talk about it later.. one day.. hopefully -, I thought I achieved supremacy in that field.

How deeply was I mistaken.

The first wave of hits happened when I was training in [the Information Technology Institute (ITI)](http://www.iti.gov.eg/), where I found out that what I have known and practiced during these five years so far does not even come close to 1% of what I should know to start.

But, of course, nothing beats the first practical opportunity to code.

## First Contact

The first thing I noticed when I saw my technical lead's design was some strange fields that he attached to each table.

* Created By
* Creation Date
* Modified By
* Modification Date
* Deleted By
* Deletion Date

I asked him about these strange columns, and he told me that they're for keeping record of who does what.

The concept intrigued me. I went home and started looking for similar ways to do it.

Ok, I'm lying. I did ask the question.

_What is the best way to implement auditing in your database?_

Little did I know that there were already several types of auditing, each is suitable for specific needs:

