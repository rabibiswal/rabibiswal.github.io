---
layout: post
title: Unit Testing - Best Practices
tags: unit-testing best-practices
---

We all know importance and benefits of unit testing. However, many fail to use this tool to their benefits due to different reasons :

- Failing to realize the importance
- Project pressure, lack of time
- Unit Testing is often seen as a task-after-code

> In any case, there is one single important thing, that makes creating unit tests difficult – No Dependency Injection


I’m not talking about using any DI framework, DI means simply DI. If Unit A has a dependency on Unit B, are you injecting the dependency or hard-wired (new operator or static methods) the dependency? If you are using DI, welcome to the world of Unit Testing.

<!--more-->

###### ARE THERE ANY BEST PRACTICES FOR UNIT TESTING?

If you have a plural sight login, you can watch this video –
<a href="https://app.pluralsight.com/library/courses/mocking-with-moq" target="_blank">Mocking with Moq</a>. I personally liked this video very much and few of the below points are borrowed from there.

Characteristics of good unit tests.

- **Atomic**
One unit test should always meant to test one small unit. It shouldn’t attempt to test multiple units.

- **Deterministic**
Unit test result should be either pass/fail. It should not be inconclusive.

- **Repeatable**
Given same source code and same unit test, you should be able to run unit test repeatedly expecting same test result.

- **Order Independent/Isolated**
One unit test must not depended on another. Each and individual test should be able to run in isolation.

- **Fast**
Ideally, one unit test should complete the run in less than a second. If it’s taking more than that, you might be doing something fundamentally wrong.

- **Easy To Setup**
Ideally, unit tests should be able to run in almost any environment without needing any infrastructure setup. If you have any third party dependencies, make sure to mock them so that unit tests don’t need them during the run.

###### THUMB RULES?

-  use DI properly
-  use a mocking framework
