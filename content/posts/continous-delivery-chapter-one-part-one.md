+++
title = 'Continous Delivery: Chapter One, part one'
date = 2024-10-13T18:45:33+02:00
draft = false
+++

I've started reading Continous Delivery by Jez Humble and David Farley (aka Dave Farley). And a way for me to better remember the things I dive into is to write them down. This forces me to have at least a minimum understanding of what I've done, or else I won’t be able to write it down properly.

![](/images/continous-delivery-book.png)

But why *that* book? The "why" is always important. In this case a good colleague of mine had recommended the book. The colleague has a *very* high level of technical skills and when someone highly skilled within a specific domain recommends something within that domain then I honestly tend to listen more. It's also a domain that I work with and where I have a lot to learn, so it's a 100% win.

I won't dive into who Dave Farley or Jez Humble are for now, but for now, I'll stick purely to Chapter 1 of the book.

*There is so many things to talk about just from Chapter 1, so i've decided to split it up into several parts.

Here I'll go through

+ The main focus of this chapter
+ The 3 release anti-patterns mentioned

### Chapter 1

The authors really try to lay the foundation for the book by explaining the importance of Continous Delivery (CD) in modern software development.

> This book describes an effective pattern for getting software from development to release

They emphasize that this process, for many, is tense, stressful since it has a lot of risks associated with it - *making release a scary time*.

I personally don't yet have a huge experience in the tech industry, but I've already witnesses situations, where we were just that - stressed, tense and worried about the risks following a release.

But I've also been on the other side. I'm actually there right now, in a situation where we don't fear deployments to Production or *Prod* as we call it. And why is that? I'll dig into that later, but I can already tell that it's definitely by *trying* to follow many of the steps that is mentioned in this chapter.

So what do the authors cover in this chapter?

They expain some of the common release antipatterns - and I admit ***I've done them all***.

### Antipattern: Deploying Software Manually

Who hasn't tried that? And in a *professional* setup? I have. Many times. I've tried following a long tutorial/guide on how to do a deployment, following specific steps, then after the deployment of Service A, another manual process had to be done for Service B - asap!

I’ve seen situations where very few people knew how to deploy—even in a big organization, where only one person could deploy. And that person did so manually from their own laptop...

And again, let me remind you that I don't have a long track record as a developer.

As we know with so many other things, manual processes have a risk of error.

In the book some signs of this antipattern are mentioned:

+ The production of extensive, detailed documentation that describes the
steps to be taken and the ways in which the steps may go wrong

+ Reliance on manual testing to confirm that the application is running
correctly

> There should be two tasks for a human being to perform to deploy software into a development, test, or production environment: to pick the version and environment and to press the “deploy” button

### Antipattern: Deploying to a Production-like Environment Only After Development Is Complete

The authors describe a situation where the first time software is deployed to a production-like environment (like staging) is after most of the development work is finished. 

This can be problematic (and I’ve truly witnessed the difference since joining my current team), as teams may realize too late that their assumptions about the production environment are incorrect, leading to deployment failures and a rush to patch critical issues.

> This pattern leads to avoidable errors, missed steps, and stressful, last-minute fixes.

The authors recommend **integrating testing** (TDD works wonders here), deployment, and release activities into the development process. By continuously testing in environments similar to production, teams can catch issues early. Everyone involved—developers, testers, and operations—should work together from the start, so by the time a release happens, deployment is routine and low-risk.

### Antipattern: Manual Configuration Management of Production Environments

The last anti-pattern mentioned in this chapter discusses manual configuration management of production environments. Just mentioning *manual* should raise some flags. I'm fully aware that sometimes that is just how it is within the organisation, but let's try to not focus on the excuses, but instead focus on the best practices and how to get there.

Regarding it being for Production Environments, I’d even stretch it to say that the same goes for non-production environments.

Some of the signs of this antipattern include:

+ You cannot step back to an earlier configuration of your system, which
may include operating system, application server, web server, RDBMS, or
other infrastructural settings.

+ Configuration of the system is carried out by modifying the configuration
directly on production systems.

> All aspects of each of your testing, staging, and production environments, specifically the configuration of any third-party elements of your system, should be applied from version control through an automated process.

### Why state the obvious?

Reading through the book, I sometimes catch myself nodding, especially as I recognize many of the guidelines and standard practices in my current work. I also catch myself thinking that I wish I had known more about this sooner so that I could have avoided some of the bad practices I adopted in the past.

Of course, back then, we sometimes knew we were committing an antipattern, but we either lacked the technical skills or the solutions to fix it, or no one stood their ground to prioritize resolving the antipatterns—instead, we kept focusing on delivering tasks and features...

Now that I’m a bit more "mature" in this industry and have gained more experience, I’ll definitely—even though I’m no technical guru—require or set some minimum standards.

That's it for part one of Chapter 1. After only reading this chapter, I’m pretty hyped about what comes next. I'll continue reading and, in the meantime, upload the rest of my notes for Chapter 1.