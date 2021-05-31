---
title: "Introducing Kelda.js: A thread pool for the browser, built on top of Web Workers"
---

# Introducing Kelda.js: A thread pool for the browser, built on top of Web Workers

<iframe src="https://www.youtube.com/embed/IMo0K22IRAo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br />

## ABSTRACT

The browser is the most resource-constrained environment we are likely to write code for. In this talk, Rufus will present his new open-source library, Kelda.js, which allows you to comfortably do threading in the browser without messing around with Web Workers yourself. We’ll talk about the challenges of building on top of the Web Worker API and dive into the tradeoffs Kelda makes to deliver something usable. We’ll also take a detailed look at several alternative patterns for optimizing JavaScript performance in the browser runtime, such as virtualised scrolling, to help you identify a good usecase. You almost certainly don’t need a browser thread pool - but if you do, there’s Kelda!
