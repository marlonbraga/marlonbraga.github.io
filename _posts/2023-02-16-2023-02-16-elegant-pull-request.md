---
layout: post
title: Making elegant Pull Requests
lang: en
ref: 10
date: 2023-02-16 15:09:00
description: What should we write in our PR description?
tags: formatting code
categories: sample-posts
disqus_comments: true
---

Reviewing someone else's code can be a thankless task. Especially when it contains a bible of significant and risky changes.

However, if there is still love in your heart, there is a way to make life easier for the unfortunate creature who will have to review this almost infinite amount of changes in a code, which, by the way, was not written by him.
you can choose to create a good Readme to help you in this task.
~Do small pull requests~
Make a relevant description of your Pull Request.

What would it be relevant to put in a PR description?


## Goal
Why was it necessary to create this PR?
What problems does it solve?
- Print if it has a GUI
- User story/functional requirement/use case link

Ex.:

```
The purpose of these changes is the refactoring of the `GameService` class.
More specifically, the `SaveGame` method.
```

## Design decisions
But why did you need to create a new class instead of using the existing one?
Why separate a piece of code from a class?
Did you really need that much interface?
Why are these new classes in that directory and not in the root folder?

No. Code reviewers are not fortune tellers. The code design decisions aren't obvious, and it wouldn't be elegant to let him spend time trying to decipher choices you could write in a few characters.
What is relevant is the following:

- Which Interfacesm classes or methods were changed/created
- What was the purpose of making each change?
- What decisions were taken
- What design principle was considered to make this decision? SOLID?

A basic class diagram can save you precious time if you really want people to understand what you've done.

Ex.:

> To allow the creation of unit tests, it was necessary to adapt the class to the principle of Inversion of Control (SOLID).
> All database context calls removed from service class for new DAO classes `CreatureRepository` , `PlayersRepository`, `ExperiencePointsRepository`. The `DungeonBuilderService` class starts to depend on its abstractions, allowing the necessary decoupling to carry out unit tests.

  ![Class diagram](/assets/img/2023-02-16-pull-request-elegant/class-diagram.png)

## Code Quality Metrics
Assure the reviewer that you cared about keeping your code maintainable instead of messing around just to get the job done faster.

Facts don't care about anyone's opinion.
Metrics tell the facts and trump the opinion of your most picky reviewers. It's a way around the "writing style" objection. After all, should we sacrifice our code maintainability rating for a reviewer's whim?
Do aesthetic preferences matter as much as a drop in class coupling or a method that was born with low cognitive complexity?
Obs.: (If your code is violating any pre-established agreement or standard by the team, it is not a matter of opinion. You should change it)

A screenshot of the Visual Studio Code Analyzer is welcome. But a simple table will do.

Ex.:

> Resulting code demonstrated greater readability.
> - Increased maintainability index *(from 24 to 51)*
> - Decrease in Class Coupling *(from 16 to 10)*
> - Reduction of Cyclomatic Complexity *(from 47 to 5)*
> - Reduction of lines of code *(from 133 to 35)*
>
> Part of this improvement was due to *method extraction* creating `ConverterModelParaEntidade()`.

| **METRIC** | **INDICATOR** | **COMPARATIVE** |
| -------------------------- |:-------------:|:------ ---------:|
| Maintainability Index | 51 | + 27% |
| Cyclimatic Complexity | 5 | - 42% |
| Class Coupling | 0 | - 6% |
| Lines of code | 35 | - 98 |

![Code_metrics](/assets/img/2023-02-16-pull-request-elegante/code-metrics.png)

As a code professional, it's better to be recognized for the quality of my work than the speed with which I deliver. This is a great way to show off.

## Tests
Yes. It is necessary to know if this is working and if it is breaking something.
Running automated tests are useful for showing that you've done the bare minimum expected of you. But a more detailed analysis can give an overall picture of the quality of what you've done specifically.
Some important information is:
- How many automated tests were created
- What is the percentage of changed code coverage
- How many code streams are being tested
- Performance Variation
- What manual tests were performed

Ex.:
> - 2 new ones