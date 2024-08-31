+++
title = 'Deleting Code'
date = 2024-08-18T18:45:33+02:00
draft = false
+++

I recently saw [a YouTube video](https://www.youtube.com/watch?v=y376JcBl1t8&list=PLeWAY-mDr91ho-PVkNT5PL53bc2c0AuwU&index=60 "Youtube reference") of Steven Hazels talk from the Nerd Nite Austin #160 where he talked about deleting code and shared strategies on how to approach it effectively.

In his 18-minute talk he drops a few tactics on how to get it done.

I'll simplify it by dividing it into 3 topics.

1. Letting Go of Commented Code
If any commented code exists in the code, if often times is better to remove it.
Shold we have an urge to want to view the commented code at a later point, Steven suggests that we instead use the Git history to find the commented code. Also if we have the code because we think we will refactor or implement af better version of it in the future, then he suggests to instead delete it and implement the feature / method / whatever whenever that time comes since the expected design and output most likely have changed at that point.

2. DRY (Don't repeat yourself)
A concept stating that instead of having the same or nearly same code written multiple places in the code, you wanna abstract it out, e.g. move it to a function and instead call it from multiple places. It’s essential to consider whether abstraction actually simplifies your code or adds unnecessary complexity.

3. Simplify code
Where I work right now, we use Test Driven Development (TDD), where we write a failing test, implement the code so the test passes and _then_ we refactor (often times simplify the code) - the last part oftentimes also results in deletion of unnecessary lines.

Steven emphasises that simplification and deletion should be done while modifying code for other purposes, making it easier to integrate with ongoing development work.

After the talk he runs a Q&A, where one asks "Do you think the long code is necessary for short code?" where Steven answers that when something is created from scratch it is natural to create a mess. I've read somewhere else that you deliver the best code for that particular time, but experience and more knowledge, new features, etc introduces reasons for changing / refactoring the code.

Trying too hard to keep up with best practices from the beginning can result in 'premature prooning'. 

> Also Steven states that even though he enjoys deleting code, there is no need to urge deleting code that already works perfectly if that holds the team back from developing on other features.