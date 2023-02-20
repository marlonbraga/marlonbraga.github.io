---
layout: post
title: Readability in unit tests
lang: en
ref: 4
date: 2023-02-04 15:09:00
description: Tips to increase the readability of unit tests
tags: test code
categories: sample posts
disqus_comments: true
---

## Why readability and tests?

Unit testing is more than automatic code validation. It also serves as documents showing what to expect and what not to expect from the method's behavior.

That's why it's especially interesting that the code is **readable**.

Furthermore, unit tests are also code. Therefore, they are also sustaining maintenance. This maintenance should be as simple and fast as any other piece of code in the solution.


## Nomenclature
Names matter in testicles too.
During test suite execution, it is the name of the test method that will be displayed next to a pass or fail message.

   ![Test Suite](/assets/img/2023-02-04-legibilidade-em-testes/execution_suit_tests.png)

The most readable way to name a test is the Given/When/Then pattern.

Being that
`Given` is a precondition.
`When` is an action.
`So` is an expected result.

Ex:
```c#
[fact that]
void BankAccount_Transfer_BalanceIsReduced(){
      //...
}
```

It is not necessary to go into too much detail. This is the name of the test. If you want to know details, read his code.

## Test cleaning

> What makes a test clean? Three things: readability, readability and readability. (...) What makes the testicles readable? The same thing that makes all codes readable: clarity, simplicity and consistency of expression. In a test you want to say a lot with as few expressions as possible.
>
> -- Uncle Bob, Clean Code

### One assertion per test
Tests that come to a single conclusion are easier to understand.

### One single concept per test
One test for each example specification. We don't want long methods that test several things one after the other.



## Code structure
Despite being intuitive, the AAA (Arrange-Act-Assert) pattern remains a great form of organization within the test method.
The idea is that the `preparation of the test` piece of code is separated from the `performing the test` piece of code from the `test verification` piece.
In practice, the coder knows where everything is without even starting to read the code.

```c#
// arrange
var repository = Substitute.For<IClientRepository>();
var client = new Client(repository);
// act
client.Save();
// assert
mock.Received.SomeMethod();
```


## Tools

There are some tools that can help you achieve the desired readability.

- <a href="https://www.nuget.org/packages/NSubstitute">NSustitute</a>
- <a href="https://www.nuget.org/packages/FluentAssertions">FluentAssetion</a>

### Substitute
**NSustitute** is an alternative to **Moq**.
With it, reading and writing the most common codes are closer to natural language. Moq is a good mocking tool in several ways. But test readability is not one of them.

While Moq makes use of the lambda operation for the simplest situations, a mock written with NSubstitute comes closer to natural language.

```c#
//❌with Moq
mockUser.Setup(foo => foo.Address.Street).Returns(street);
mock.Setup(x => x.SearchById(It.IsAny<int>())).Returns((int i) => userList.Skip(1).Take(1).First());
mock.Setup(x => x.SearchById(2)).Returns((int i) => userList.First());

//✔️with NSubstitute
mockUser.Address.Street.Returns(street);
mock.SearchById(Arg.Any<int>()).Returns(userList.Skip(1).Take(1).First();
mock.SearchById(2).Returns(userList.First());
```

### Fluent Assessment
**FluentAssetion** is an alternative to **System.Assert**.
This package follows the same idea as the previous one. However treated for the Assert phase of the test.

The highlight is on the name of the methods. When combined, reading is fluid exactly as you would read a business rule in English.

```c#
//❌with Assert
actual string = "ABCDEFGHI";
Assert.Contains("EF", real);
Assert.StartsWith("EF", real);
Assert.AreEqual(9, real.Length);

//✔️with FluentAssetion
actual string = "ABCDEFGHI";
real.Should().StartWith("AB").And.EndWith("HI").And.Contain("EF").And.HaveLength(9);
```


package manager
```
NuGet\Install-Package NSubstitute -Version 4.4.0
NuGet\Install-Package NSubstitute.Analyzers.CSharp -Version 1.0.16
NuGet\Install-Package FluentAssertions -Version 6.9.0

```

## Why not use SpecFlow?

It's like the saying goes:
>"For those who only know how to use a hammer, every problem is a nail."

SpecFlow is a very interesting and useful tool.
However, it is productive when used for the purpose for which it was created. When it runs away from it, it gets in the way more than it helps.

SpecFlow is a BDD tool. This consists of making specifications by example with **Gherkin**, a common language for QA, Developer and PO. This is very useful in an *End-To-End test* and even an *Integrated test*. But the *unit test* is made and maintained only by the Developer. Therefore, it is necessary that the language of a unit test is more technical. Using Gherkin to describe functionality in a technical language is more counterproductive than using traditional tests.

But let's talk more about **BDD+Specflow** in another opportunity.

The idea is that, for now, we leave SpecFlow out of our unit tests.