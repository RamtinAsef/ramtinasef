+++
title = 'Unit Testing: Is Coverage Metrics Bad'
date = 2024-02-22T20:34:20+01:00
draft = true
+++

I started reading 'Unit Testing' by Vladimir Khorikov and as I go through it, I would like to pick some of the topics he goes through and write them down. I believe this helps me understand the subject better.

![](/images/unit-testing-by-vladimir-khorikov.png)

In the first chapter, he discusses the importance of _coverage metrics_. Most of us have seem them and experienced a project where a specific code coverage was _required_.

During my studies we had a course about testing code, where we also went by different coverage metrics. In one of our assignments, I remember there was a requirement for a quite high code coverage percentage, and I think we all experienced - even on such a small project as the ones we do during studies - that coverage metric requirements can be a pain to work with.

I think I can also speak for everyone when I say that we all experiences having our focus the wrong place - naimly on the coverage metric and not on the _quality_ of the tests themselves. That's one of many of the points Vladimir has regarding the risks of using coverage metrics in his book.

So, what is coverage metrics?

Coverage metrics refer to the measurement of how much of the source code is exercised by automated tests or as Vladimir states:

> A coverage metric shows how much source code a test suite executes, from none to 100%

There are different types of coverage metrics, but some of the well-known ones are:

+ Line coverage (_or "code coverage" as Vladimir calls it_)
+ Branch coverage
+ Function coverage

I won't dive into the different types but rather what to be aware of.

I like the phrase Vladimir uses and try to always have it in the back of my head when seeing coverage metrics:

> coverage metrics are a good negative indicator, but a bad positive one

You can easily have 100% code coverage without even _really_ testing anything - just use a lot of assertion-free testing as the example mentioned in his book. And even though the intentions with the use of code coverage metrics are good, a required high percentage code coverage metric can conflict with deadlines, costs, etc, resulting in people trying to do a workaround just to reach the metric.

Instead of focusing on the metrics, focus on the quality, what matters and costs.

> The cost component is determined by the amount of time spent on various activities:
> + Refactoring the test when you refactor the underlying code
> + Running the test on each code change
> + Dealing with false alarms raised by test
> + Spending time reading the test you're trying to understand how the underlying code behaves