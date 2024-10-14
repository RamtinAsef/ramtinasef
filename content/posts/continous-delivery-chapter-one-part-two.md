+++
title = 'Continous Delivery: Chapter One, part two'
date = 2024-10-14T18:45:33+02:00
draft = false
+++

This is part two of Chapter 1 from the book Continous Delivery by David Farley and Jez Humble.

![](/images/continous-delivery-book.png)

In the previous post I went through the anti-patterns described in Chapter 1.

Here I'll briefly go through some of the other take aways from the same chapter.

So anti patterns have been mentioned, but how do we actually achieve the goal of delivering useful, working software asap to the users?

The authors emphasizes that there needs to be a focus on quality, but also speed.

In order to achieve this, frequent, automated releases are vital.

Automation makes processes repeatable and reliable, avoiding manual errors and enabling consistent, error-free deployments. **By releasing often, changes are smaller, making issues easier to identify and roll back.**

Automation also provides prompt feedback, helping teams address and act on issues immediately, fostering a culture of continuous improvement.

>It is essential that everybody in the organization is involved in this process. Allowing feedback to happen only within silos and not across them is a recipe for disaster: It leads to local optimization at the expense of general optimization—and, ultimately, finger-pointing.

Tools like continuous integration automate code builds and testing, ensuring each change is verified. Automated testing stages, including unit, functional, and nonfunctional tests, assess performance and stability, reducing risk. 

Teams should collaborate across roles—developers, testers, operations—to ensure feedback is received and improvements made.

Lastly, managing configuration through **version control** and **automating deployment** can prevent errors, reduce stress, and create a reliable release process. Manual configuration is prone to human errors, but ..

>.. with version control, every configuration change is tracked, reducing the chance of unnoticed mistakes.

Automating deployments allows for faster, frequent, and safer releases, enabling easier rollback in case of issues. Continuous integration and automated testing ensure that every code change is a potential release, maintaining a constant, production-ready state. Finally, focusing on early defect detection and emphasizing "done" as fully deployed keeps quality and delivery on target.

>It is worth emphasizing that the first release of an application is just the first stage in its life. All applications evolve, and more releases will follow. It is important that your delivery process also evolves with it.

That's it for Chapter 1. So far, so good. Again, reading a book for me gives me some insights, but writing down some of the key take aways forces me to communicate, what I've read and as a minimum to mentally go through what I've read - often times it also requires me to grab the book and re-read some of the parts.