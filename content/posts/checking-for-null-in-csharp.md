+++
title = 'Checking for null in C#'
date = 2024-08-31T18:45:33+02:00
draft = false
+++

Nick Chapsas has [a YouTube video](https://www.youtube.com/watch?v=1oeMTz7LwrU "Nick Chapsas null check") where he talks us through the 'right way' of checking for null in C#.

In his video he discusses the complexities of performing null checks in C# and how the language's evolution has introduced overlapping and sometimes conflicting methods for handling null references.

Nick explains that while C# is a robust language, its age and the addition of new features without altering existing behaviors have created a confusing landscape for null checking.

### Traditional Null Checks

Traditionally (until C# 6), null checks in C# were done using `user == null` and the opposite using `user != null` 

The issue with the equal / not equal operators is that it can be overloaded.

### The *is* operator

Starting from C# 6 the *is*-operator was introduced, allowing for null checks like this this: `user is null`

> This approach checks the reference directly and cannot be overloaded, making it a more reliable way to check for null.

(I am no expert, but as I write this post I honestly can't come up with a scenario where one would want to override the *==* operator...)

### The *not* operator

From C# 9 the *not*-operator was introduced, which allows us to check if something *is not* null  like this: `user is not null`

This *new* syntax aligns more closely with how I presume developers typically read `user == null` as `user is null` anyway and thus I think the *new* approach is 

However, Nick emphasizes that this newer approach doesn't apply to Unity developers, who checks if something exists rather than checking for an actual null reference. This distinction adds to the complexity and potential confusion.

Bonustip from his own comment on the video:

> And for those wondering, both null-coalescing operators (??= and ??) and the ?. operator will be compiled to the "is null" version if the compiler detects that the operator is overloaded