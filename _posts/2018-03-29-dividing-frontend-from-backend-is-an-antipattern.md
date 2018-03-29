Dividing Frontend from Backend is an Antipattern
===========

_This article was [originally published](https://www.thoughtworks.com/insights/blog/dividing-frontend-backend-antipattern) on [ThoughtWorks Insights](https://www.thoughtworks.com/insights)._

We software developers have historically used the terms “frontend” and “backend” to describe work on client-side (e.g., browser) and server-side applications, respectively. This conceptual split has evolved into the creation of specialized developer roles for each, which is still the norm throughout the industry. In practice, this is an arbitrary split that is too often used to avoid work we don’t want to do. It creates team dynamics that make it unnecessarily difficult to integrate client and server-side functionality and deliver quality software. This is particularly harmful in modern teams, which face increasingly complex client-side work.

And yet, I come across the frontend/backend mindset regularly, even at the most technologically progressive companies. After spending a year introducing modern JavaScript on my [previous project](https://www.thoughtworks.com/insights/blog/advocating-software-quality-metro), I was told to stop focusing on frontend because “we’re application developers”. Every developer I’ve ever met who has exceptional ability in client-side work has similar stories to tell. This dismissive attitude speaks both of a failure to understand how much JavaScript and the whole frontend ecosystem [have evolved](https://stateofjs.com/2017/introduction/) in recent years, and of a close-mindedness that makes it hard for our teams to adapt and deliver software to the expectations of the modern market.

Dividing frontend from backend is an antipattern. If you are someone who still feels that there is merit to a hard distinction between these roles, this article is for you.

We already do the same work in the frontend and the backend
---------

What does a frontend dev actually do that’s so different from a backender? The feeling seems to be that backend devs have historically done the more 'serious' programming, thinking about meaningful issues such as testability, maintainability, persistence, asynchronicity, state management, and API design, while their frontend colleagues flitted about making things look pretty. If frontend devs did any serious coding at all, it was probably some hacky, half-understood jQuery, cobbled together from various Stack Overflow posts. Many folks still think along these lines.

Here’s the reality: JavaScript has absolutely exploded in the past few years. Nowadays, with the advent of ever more complex client-side applications (think responsive, immersive, offline-enabled experiences), significant chunks of functionality are moving from the backend to the frontend. We now think about the same problems in the front as in the back. The issues I listed earlier (testability, maintainability, persistence, asynchronicity, state, API design) are now the daily bread of client-side developers.

But we don’t just share the same problems — we also solve them in a similar way. Functional abstractions are emerging as universally useful, such that we can often use the same concepts and syntax in the client and the server. Just look at [ReactiveX](http://reactivex.io/), now implemented in so many languages that you could easily build a project on the same reactive abstractions in the front and the back. Then there’s the revolution of [declarative rendering](https://reactjs.org/blog/2013/06/05/why-react.html#reactive-updates-are-dead-simple), which has made the view layer far more testable and stable. On the architecture side, microfrontends have become so popular that we’ve [added them](https://www.thoughtworks.com/radar/techniques/micro-frontends) to the ThoughtWorks [Technology Radar](https://www.thoughtworks.com/radar) alongside their backend equivalent, microservices. It doesn’t make sense to keep the distinction between frontend and backend development when we’re all doing such similar work.

We need to build broad frontend capability to future-proof our companies
---------

Client-side engineering is a serious business need. JavaScript is taking over the world, and we can’t afford excellent and experienced devs thinking of User Interface (UI) and User Experience (UX) work as outside of their area of concern. At ThoughtWorks, we are seeing more and more engagements that involve a revamp or total rewrite of our client’s browser and mobile applications to align with the needs of modern consumers. In other words, actively building and maintaining client-side capability is critical to surviving in today’s market — not to mention tomorrow’s.

You might think that the correct solution here is to simply hire more engineers into traditional 'UI Developer' roles. But it’s not, for two reasons. Firstly, recruiting and retaining experts is [famously challenging](https://medium.com/javascript-scene/why-hiring-is-so-hard-in-tech-c462c3230017) in the tech industry. Thus, our focus should instead be on enabling our existing workforces in frontend development — particularly given the similarity of modern frontend and backend work. Secondly, having dedicated UI Developers promotes problematic team dynamics. How many of us have been on teams where all or most frontend architecture and development was relegated to “that JavaScript person”? This can lead to information silos, less solid testing, and an overall reduction in code quality, which in turn poses a serious business risk.

At the end of the day, a lot of us simply dislike styling and other areas of frontend that come uncomfortably close to design. Last year I heard a conference speaker quip that she shouldn’t have to care about something as unimportant as 'presentation logic'. We have evolved a culture of disdain for frontend which protects us from having to learn since it’s not 'real coding' anyway. It’s an attitude that makes it hard to keep up with the market and continue to create meaningful products for humans.

We should care about how our programs consumed
---------

Ironically, the crown jewel of backend quality is and always has been user interface design. Every design pattern ever invented, every book on architecture ever written, every DRY refactoring ever performed: all tools to help the authors of code enhance the productivity and happiness of the readers of code. Whether you’re creating an inheritance hierarchy, an API, or an ecosystem of microservices, you’re creating it for someone. If you’d be embarrassed to release an un-RESTful API or a class with leaky abstractions, then you care about user interfaces. So we already think of software quality in terms of user experience — it’s just that the users happen to be other developers.

As proud craftspeople, we should care about how our programs are consumed, whether through an API or a UI. At ThoughtWorks, we think of our roles as fluid and non-exclusive areas of championship. For example, while we usually have dedicated QAs on our teams, we consider quality to be everyone’s responsibility. In the same way, we should take collective responsibility for the full stack of technologies we use, and thus ultimately for the quality of the product we produce. Successful engineering organizations understand this. Tech legend Kent Beck, the inventor of [Extreme Programming](https://en.wikipedia.org/wiki/Extreme_programming) and signatory to the original [Agile Manifesto](http://agilemanifesto.org/), has [said](https://soundcloud.com/thoughtworks/is-tdd-dead-episode-3-feedback?in=thoughtworks/sets/is-tdd-dead#t=17:28) that hanging on his office wall is a poster bearing the following sacred mantra: “Nothing at Facebook is somebody else’s problem”.

Stay open-minded
---------

Contemporary frontend work has evolved in complexity to the extent that we should no longer separate frontend from backend roles. Frontend engineers now solve the same kinds of problems as their backend counterparts, using the same kinds of solutions, and it is harmful to continue arbitrarily dividing us.

To be clear, I’m not saying that we all need to be experts in everything. That would be impossible. Today’s technology stack goes down a long way, so being a genuinely balanced full-stack dev is probably not the most realistic of goals — but staying open-minded is. While it is perfectly valid to dislike a particular technology, such as CSS, the industry's culture of contempt for frontend work feeds into the outdated divide between frontend and backend, and detracts from building fast-moving, competitive teams and companies.

Think of yourself as a developer first. [Investigate frontend technologies](https://frontendmasters.com/books/front-end-handbook/2017/), pair with UI specialists, evangelize your colleagues. Your team, your company, and your users will thank you.

_Thanks to Nathan Zeplowitz, Luke Belliveau, and Robin Weston for their excellent constructive feedback._