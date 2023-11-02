# Lab 10 - Testing in the Real World

This recitation is an introduction to test doubles.

## Deliverables
- [ ] Use a fake to test `logIn`
- [ ] Use stubs to test `getRecommendation`
- [ ] Use mocks to test `sendPromoEmail`

## Introduction

In testing, it may sometimes be necessary to use objects or procedures that look and behave like their release-intended counterparts but are actually simplified versions that reduce the complexity and facilitate testing. Objects or procedures meant for production can be too slow, unavailable, expensive, opaque, or non-deterministic. Instead, test doubles are often used. There are multiple types of test doubles, but the most well-known/popular are Fakes, Stubs, and Mocks.

### Fakes

Fakes are fully functional classes with a simplified implementation. Usually, they take some shortcuts and are a simplified version of the real object. We use fakes to avoid interacting directly with objects that are too costly to access during testing, like databases. So, instead of querying our actual database, we use a fully functional in-memory database to simulate the same operations.

<!-- ![Fakes](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*snrzYwepyaPu3uC9.png) -->

### Stubs

A stub is an artificial class that returns pre-configured data. We use it to answer calls during tests. Stubs are used when we can't or don’t want to involve objects that would answer with real data or would have undesirable side effects. For example, instead of querying our real database, we may use a stub with predefined data to simulate only the functionality we need.

<!-- ![Stubs](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*KdpZaEVy6GNnrUpB.png) -->

### Mocks

A mock is an instrumented variant of a real class with fine-grained control. We use mocks when we don’t want to invoke expensive production code or when there is no easy way to verify that an intended action was executed. For example, we don't want to send a new email every time we want to test an email system.

<!-- ![Mocks](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*k7mwTF60slyMxRlm.png) -->

These three terms are usually used interchangeably in practice, but there are some subtle differences. You can find plenty of resources online that go into more detail on the differences if you're still unsure what they are (don't worry, even experienced software developers get it [wrong](https://martinfowler.com/articles/mocksArentStubs.html)).

## Instructions

Run the following commands to get started:
```
mvn install
mvn test
```
You might notice the tests are taking a very long time to run. Let's increase their performance using test doubles! Look through the provided files to see which methods you will need to test with which types of test doubles. You will find hints on how to proceed there.

All of your tests should be written in `AndrewWebServicesTest.java`. You will also need to implement a fake database in `InMemoryDatabase.java`. For mocks, we will use the [Mockito](https://site.mockito.org/) framework.

> Hint: Check the Mockito website for examples on how to use the framework

> Hint: The following functions from Mockito will be very useful: mock, verify, when