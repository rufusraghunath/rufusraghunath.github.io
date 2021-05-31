---
title: "Developing and testing WebSocket-based applications using React and STOMP"
---

# Developing and testing WebSocket-based applications using React and STOMP

We recently added a real-time component to a complex application my team is working on. We have a React frontend and a Java SpringBoot backend, so naturally we looked for existing ways to seamlessly integrate [WebSocket](https://en.wikipedia.org/wiki/WebSocket#:~:text=WebSocket%20is%20a%20computer%20communications,WebSocket%20is%20distinct%20from%20HTTP.) into this tech stack. One developer-friendly way to do this is to leverage [STOMP](https://stomp.github.io/), a nice abstraction on top of WebSocket that handles a lot of vexing, message-related problems for you out of the box.

While there was good support for STOMP in the Java world, I was surprised to find very little for React, in particular for testing. I ended up hand-rolling a React STOMP client, as well as a mock STOMP broker for exercising said client in our automated tests.

Since I went to all this trouble, I thought I might as well extract the functionality into two libraries and open-source it. You can install [react-stomp-client](https://www.npmjs.com/package/react-stomp-client) and [mock-stomp-broker](https://www.npmjs.com/package/mock-stomp-broker) from npm, and find the source code on [GitHub](https://github.com/rufusraghunath/js-stomp-utils).
