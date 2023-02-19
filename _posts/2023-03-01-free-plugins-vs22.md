---
layout: post
title: Free plugins for VS 2022
lang: en
ref: 11
date: 2023-02-19 01:00:00
description: More productivity with VisualStudio 22 without paying more
tags: formatting code
categories: sample-posts
disqus_comments: true
---

Visual Studio 2022 looks great. But it can gain very interesting features when you add plugins to it.

The most complete and famous plugin we have is [ReSharper](https://www.jetbrains.com/pt-br/resharper/). However, it is not the most... economical choice.

Here are 3 choices of free plugins for those who don't want to give up productivity but are ~~penny-pincher~~ interested in idea of saving money.

## FineCodeCoverage
Do you do automated tests? Good job. But do you know how much of your code is covered by tests and which lines are unprotected?

With this plugin you can check the code coverage of each class and method directly from VS22.

The [FineCodeCoverage](https://marketplace.visualstudio.com/items?itemName=FortuneNgwenya.FineCodeCoverage) also indicates in the editor if the line of code is covered or not by some test. The color of the colored bar to the left of the line numbering indicates its coverage status.
  - green: line covered by test
  - red: line not covered by test
  - yellow: line partially covered by test

  > Marketplace: [FineCodeCoverage](https://marketplace.visualstudio.com/items?itemName=FortuneNgwenya.FineCodeCoverage)  
  > GitHub: [Repository](https://github.com/FortuneN/FineCodeCoverage)

![coveraged-line](/assets/img/2023-03-01-plugin-free-vs22/coveraged-line.png)
![coveraged-percentage](/assets/img/2023-03-01-plugin-free-vs22/coveraged-percentage.png)

## CodeMaintainability 2022
Visual Studio performs quality check of your code through `Analyser > Calculate Code Metrics`.
However, [CodeMaintainability 2022](https://marketplace.visualstudio.com/items?itemName=ognjen-babic.CodeMaintainability2022) allows this visualization directly in the editor. Displaying in the signature of each method its **maintenance index** and an icon indicating the "health" of its code.

Clicking on the index indicator displays other measurements of code quality for that method.

![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/code-maintenability.png)

The only thing missing was the **cognitive complexity** metric to be complete.

  > Marketplace: [CodeMaintainability 2022](https://marketplace.visualstudio.com/items?itemName=ognjen-babic.CodeMaintainability2022)


## CodeMaid
Visual Studio is able to make some refactoring suggestions in your code. The [CodeMaid](https://marketplace.visualstudio.com/items?itemName=SteveCadwallader.CodeMaidVS2022) plugin increases the IDE's native repertoire and enables a wider range of refactorings to make your code more clean and simple.

In addition, the plugin also has features such as:
- Detection of *code smells*
- General code cleanup
- Configuration of cleaning rules
- Spades: Class structure screen
- Build loading bar

  > Marketplace: [CodeMaid](https://marketplace.visualstudio.com/items?itemName=SteveCadwallader.CodeMaidVS2022)  
  > GitHub: [Repository](https://github.com/codecadwallader/codemaid)

### Miscellaneous Resources
![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-menu.png)
### Build loading bar:
![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-buildbar.png)
### Spades - Class structure
![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-spades.png)
### Configuration of options and rules
![code-maintenability](/assets/img/2023-03-01-plugin-free-vs22/codemaid-options.png)