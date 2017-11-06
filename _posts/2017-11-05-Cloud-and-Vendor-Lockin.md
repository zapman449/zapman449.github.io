---
layout: post
title: Clouds and Vendor Lock-in
subtitle: Threading the cliffs of politics
bigimg: /img/Trafoulas_canyon.jpg
tags: [it, devops]
---
# Clouds and Vendor Lock-in

An oft repeated refrain is "We should be cloud agnostic" or "We should support multiple cloud vendors".

We apparently still fighting the last war (with apologies to Terry Goodkind).

## The Previous War

In the "last war" we learned how bad of an idea it was to choose vendors with de facto monopoly power.  Microsoft
typified this challenge.  You paid for the OS. You paid for the developer tools, you paid for the office suite, and
you paid for the Exchange Servers, and you paid in time, frustration and moral for the terrible tools you paid 
vast sums of money for<sup>1</sup>.

The problem here was frequently described as 'vendor lock-in'.  But in actuality, it was two distinct, but related
problems: 
1. Poor vendor selection
2. Lack of available vendors

The companies choosing to get into bed with Microsoft could see what was happening to their neighboring companies.
They could clearly see the high fees being racked up, and the costs going out the door.  Yet they chose Microsoft
regardless.  Partially this was due to everyone else doing this.  However...

Microsoft was also eating all of it's competitors.  Lotus 1-2-3 was famous.  Ami Pro was fantastic.  Word Perfect SILL
lives on, on life support from the legal community.  But they were all victims of Embrace and Extend.  And at best,
they are shadows of their former selves.

### Cloud Lock-in

The other reason people ask for "cloud agnosticism" is the example of Nirvanix, who imploded in 2013. Between the
announcement, and the shutdown, Nirvanix did not have sufficient bandwidth for customers to exfiltrate all their data.  It was mathematically impossible.

That was obviously bad.  However this too is more an example of bad vendor selection than vendor lock-in.  

Nirvanix offered prices which were wildly lower than AWS.  Or Google.  Or Rackspace, or anyone else that I recall.
These prices were described in the press as "Too good to be true".  And they were... which lead to bankruptcy.

For the rest of this post, I'll assume that you've done vendor-selection properly and chosen a top 5 cloud vendor,
or have solid reasons for not doing so.

## Today's problems with "Cloud Agnosticism"

There are two real problems with aspiring to the "Cloud Agnostic" model for cloud vendors:
1. The Benefits of delayed complexity
2. Operational Costs are unaccounted

### The Benefits of Delayed Complexity

With the cloud hosted services, you have the benefit of just using someone else's service for massive amounts of
your infrastructure.  It buys you a ton of runway to figure out where your real complexity pain-points are.

Credit to an old boss who told me "Understand what is Necessary Complexity, and Accidental Complexity".  Necessary
Complexity is the "secret sauce" of your company.  Accidental Complexity is the stuff around getting your speciality
to customers.  And the stuff around that, and so on.

Probable Examples of Accidental Complexity: 
1. MS Exchange on premise
2. LDAP Clustering
3. External DNS Servers
4. Home grown monitoring tools
5. Elastic Search clusters

The list goes on.  The huge benefit of the cloud is you can use your cloud vendors version of these things for a long
time before they become Necessary Complexity. 

And when you outgrow them, you can replace only the piece which is causing you pain, and grow the needed expertise to
run it well.

### Operational costs

Bringing a team (or several) up to speed on a cloud vendor is a huge undertaking; it's going to take months for 
your people to become proficient.  Trying to bring a team up to speed on two of them at the same time is asking 
for the task to take too long or be done poorly or most likely, both.  The cost gets even higher when you need to
troubleshoot something which turns out to be a misunderstanding of how compute works in the cloud (try explaining
VPC networking to someone in less than an hour.)

And the worst, vastly under-appreciated pain of multi-cloud is you can't leverage the best features of the vendors.

You loose:
1. Managed Database - RDS, CloudSQL, etc. - You don't have to build, harden, manage, build in fail-over, etc to your
   data tier.  Your efforts to build this for your company have almost all failed.  And you can't afford the talent
   to do it for yourself.
2. Managed Queueing - SQS, Cloud Pub/Sub, etc - Managing a Kafka or RMQ cluster is almost as hard as building a
   quality database tier.  It's offered as a service.
3. Managed alerting, notifications, logging, The list goes on for pages.  And best of all, you don't have to build
   and harden them.  You just have to configure them.  The operational cost just dropped by at least 2/3rds.

You'll have to build your own... for each of these you need... in at least two different cloud vendors compute
environments.

## Wrapping Up 

Ultimately, vendor lock-in is a fact of life.  You choose good vendors, and the problem is small.  When those
vendors misbehave, you migrate.  No one seriously proposed building and running an Oracle and an Informix DB
simultaneously.  When Oracle behaved too badly, you migrated to Informix, or MSSQL, or whatever.  

Treat cloud vendors the same way.  But when you choose one, go all in, and you'll have a better experience, with less
pain for your teams and better outcomes on your projects.

<sup>1</sup> In Microsoft's defense, their tools have vastly improved since the early 2000s, and they have responded
to these problems admirably.  However Microsoft longer wields monopoly power either, so it is innovate or die...
