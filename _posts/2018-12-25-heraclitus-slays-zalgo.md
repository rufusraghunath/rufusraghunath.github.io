---
title: "Heraclitus Slays Zalgo"
---

# Heraclitus Slays Zalgo

<iframe src="https://www.youtube.com/embed/C3GvXp4Detk?start=1572" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br />

This is a 5-minute lightning talk I gave at [Fullstack Fest 2018](https://www.youtube.com/playlist?list=PLe9psSNJBf75O6abYvvjxhm36_QU9H-f2), which combines my trademark uneducated armchair philosphy with some JS jargon.

The Greek philosopher Heraclitus once said:

> Upon those that step into the same river, different and again different waters flow.

I take this to mean that there is no such thing as true identity. There is no river, because what we perceive as the river is in fact always changing. This statement inspired me to look at the different ways we have handled asynchronicity in the JavaScript ecosystem\*, because I believe that letting go of identity has allowed us to remove a whole class of bugs that occur when we model reality in a way that presupposes that there exist mutable entities that remain "the same" even as their observable values change.

In this talk, I discuss how the problem of ["releasing Zalgo"](http://blog.izs.me/post/59142742143/designing-apis-for-asynchrony) (h͢e̴ ̵wh͝o ẁa̧i̛t̕s͟ ̵b͠ȩhi̷n̡d t͡h̵e͡ ͡wall) when working with APIs that are _unpredicably_ asynchronous no longer applies when using Promises. Since correct use of a `Promise` involves lifting all operations that depend on the resolved value into the context of the value (using `.then()`), your program cannot end up in an inconsistent state. This is in contrast to earlier approaches, such as using callbacks, that would have involved modifying outside state (a mutable identity) that is referred to by other parts of the program, thus creating the potential for a race condition.

Apologies up-front that I'm not particularly polished or easy to follow here. I decided to do this talk on a whim, and it essentially became a brain-dump of things I had been thinking about recently ¯\\_(ツ)_/¯

Here are the articles and talks I refer to:

- [_Are We There Yet?_](https://www.infoq.com/presentations/Are-We-There-Yet-Rich-Hickey), by Rich Hickey
- [_Designing APIs for Asynchrony_](http://blog.izs.me/post/59142742143/designing-apis-for-asynchrony), by Isaac Schlueter
- [_Intentionally unleashing Zalgo with synchronous promises_](https://medium.com/@bluepnume/intentionally-unleashing-zalgo-with-promises-ab3f63ead2fd), by Daniel Brain

\* In this example I'm talking about callbacks and Promises, but the same principle applies outside the JavaScript ecosystem.
