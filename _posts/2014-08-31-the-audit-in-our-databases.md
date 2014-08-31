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

But before I moved on to other forms, I inspected the previous method more closely.

Let's assume we have the following three tables:

#### Students

* ID (PK)
* Name
* Address
* PhoneNumber

#### Courses

* ID (PK)
* Name
* Code
* StartingDate

#### Subscriptions

* ID (PK)
* StudentID (FK : Students(ID))
* CourseID (FK : Courses(ID))
* Score

Using the method mentioned above, we will add to each table of these the 6 columns that perform the auditing.

A number of characteristics become apparent to us:

1. You only keep the latest version.
2. No rollbacks.

But the thing that really bugged me was that I have to repeat those 6 columns over and over again. You may think that here in these three tables, it is not that big an issue; but when I first saw it, it was in 40 different tables, not counting joins.

The first idea that came to my mind was to create a table for the common columns, and point the other tables to it.

It was something like this.

#### Auditable

* ID (PK)
* CreatedBy
* CreationDate
* ModifiedBy
* ModificationDate
* DeletedBy
* DeletionDate

#### Students

* ID (PK, FK : Auditable(ID))
* Name
* Address
* PhoneNumber

#### Courses

* ID (PK, FK : Auditable(ID))
* Name
* Code
* StartingDate

#### Subscriptions

* ID (PK, FK : Auditable(ID))
* StudentID (FK : Students(ID))
* CourseID (FK : Courses(ID))
* Score

