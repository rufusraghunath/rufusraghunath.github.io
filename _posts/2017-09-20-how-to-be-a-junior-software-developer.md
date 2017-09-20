How to Be a Junior Software Developer
===========

_This article was [originally published](https://www.thoughtworks.com/insights/blog/how-be-junior-software-developer) on [ThoughtWorks Insights](https://www.thoughtworks.com/insights)._

Introduction
---------

In my time as a junior at ThoughtWorks, I was blessed to have opportunities to grow and develop my skills on several interesting projects, with the help of some amazing people. In this article, I want to share the strategy I used to maximize my professional development. If you’re in a similar position, I hope this will help you make your first steps into tech successful. If you’re a senior or team lead, I hope that this will help you to support juniors in growing and becoming productive. If you’re a company, I hope that this will provide some context for how to hire and staff junior developers.

Learning to learn
---------

I think it’s important to realize that, as a junior, your main value to an employer is most likely your potential, not your current ability. ThoughtWorks certainly didn’t hire me because they thought my technical interview solution should be pushed to production anywhere. So rather than focusing on delivering software 100% of the time, focus on up-skilling. Practice self-reflection and seek feedback to identify your weaknesses. Use whatever resources are available to you to improve your knowledge and skill set. Ask for help from seniors, ask for code reviews, pair program. Understand the context in which you are working - talk to business analysts, QAs, stakeholders, ask questions. Don’t stop moving, cultivate a humble 'always learning' attitude. Gain perspective on alternative ways to do things.

Learning itself is a skill that can be developed. I did not join ThoughtWorks with a particularly broad range of technical skills, and so, every project I joined brought a panic-inducing flood of new programming languages, new tools, new frameworks, and new concepts crashing down on me (and that’s not even mentioning business-related skills). These are the moments when [impostor syndrome](https://en.wikipedia.org/wiki/Impostor_syndrome) is at its strongest and undermines your self-belief the most. After a while, though, you begin to spot the pattern. It goes something like this:


1. Enthusiasm
2. Bafflement
3. Superficial comprehension
4. Frustration, having your expectations violated
5. Working knowledge, productivity
6. Rinse and repeat

Stage 3 is the most dangerous since in it you’re unaware of your own failure to understand what you’re doing. Better to be frustrated and proactive in seeking help than to cheerfully cook up vats of spaghetti code without knowing any better. Ironically, one can be quite 'productive' in stage 3. Get out of stage 3 by seeking feedback on your work and developing a relationship with your ignorance. Embrace it as a temporary given.

Once you’ve gone through this cycle a few times and ended up able to ship respectable production code in a new technology, you develop a 'can do' attitude towards learning. You become confident in your ability to pick up new things quickly and start to enjoy it. And, more importantly, you can make a plausible, evidence-based case for this to business stakeholders when needed. I have found that even senior developers sometimes end up lacking this panache because their roles have been too one-sided and have not required them to stretch. So, continuously extract yourself from your comfort zone and put yourself in the situation of having to learn new things - this experience will become your primary advantage as a junior developer, particularly if you work as a consultant. Set the tone for the rest of your career.

Adding value as a junior
---------

Learning is all very well, but at some point, you need to get into the grind and rhythm of delivering software. Apart from your daily work, which will probably involve small and de-risked chunks of responsibility, I strongly recommend that you seek out independent areas in which you can add value to your team and turn them into pet projects.

For example, on my first project, we used C# in the back and React + Redux in the front. Since I hadn't used any of these before, the barrier to entry to productivity was fairly high. I was lucky to have a tech lead who understood the importance of delegating other useful tasks to me, to keep me confident and productive while learning to use our core delivery stack. In this case, we were using an incomplete [open-source build monitor tool for Visual Studio Online](https://github.com/elrob/build-mon), so it became my task to finish implementing it.
For context, I had no idea how build pipelines worked, and as it turned out, the monitor was written in Clojure, which has a paradigm that is hilariously different to the object-orientation I was used to. So for a month, I spent my nights producing horribly imperative Clojure code and watching talks by Rich Hickey. By the end, our team had a working build monitor and I had discovered my love of functional programming.

My next project was working on a Java microservices platform using Docker, Kubernetes, and Cassandra. Once again, a new tech stack. This time, I bridged the time needed to get ramped up on the new tools and concepts by making myself useful in the UI. I used my previous experience to help advocate for and execute a [migration of critical business flows from Reflux to Redux](https://www.thoughtworks.com/insights/blog/advocating-software-quality-metro). This increased the testability of our JavaScript and reduced the complexity of our inherited codebase, which in turn resulted in improved velocity and stability.

In both cases, I needed time to learn and become productive. By identifying things I could do, I was nevertheless able to start delivering genuine value to my teams quickly. These pet projects helped me build credibility and trust with my team and stakeholders, improved my confidence and reduced impostor syndrome, and allowed me to experiment with taking the lead on something (which is a whole world of learning unto itself).

There is always some extra utility to produce or something to refactor. While pursuing pet projects is particularly helpful for your development and team relationships as a junior, it’s a habit that I’ll continue to cultivate. It’s just so fun!

Choosing pet projects
---------

Sadly, there’s no such thing as a free lunch. Like everything, the utility of pet projects comes at a cost. You may be uncertain or confused about where to start. You may not feel supported, or you may feel pressured to deliver functionality. You might be worried about the extra time, work, and effort required.

From experience, I can confirm that those are all real and valid challenges. In addition, expect to be continually frustrated and have your expectations of how things are supposed to work continually violated. To ameliorate these issues, I suggest that you pick projects that:

- Are small
- Have clear goals (definitions of 'done')
- Add value/will be appreciated
- Are likely to be supported once you advertise them (e.g. by team, company, community)
- Are fun/rewarding in their own right

Moreover, embrace both failure and ignorance. Suspend your disbelief that it will work tomorrow. Suspend your disbelief that you will understand it tomorrow.

And, of course, give yourself time off as well. Taking on pet projects is helpful and fun, but the expectation certainly shouldn’t be that you have to put in extra work beyond what you’re paid to do. Choose to do so when it makes sense for you, and when you have the space for it in your life. You can also speak to your team to see if they'll allow you time to work on pet projects within work hours, which is definitely possible if there’s a clear value-add.

Conclusion
---------

One of the key tenets of the [Agile Manifesto](http://agilemanifesto.org/) is to prefer 'responding to change over following a plan'. Continuous Improvement, Continuous Delivery. Produce a version of the product, observe its shortcomings, collect feedback, reassess requirements, produce the next version. Iterate in small chunks, never impose a grand vision based on outdated information. As a junior developer, it's useful to think of yourself in the same way.

Keep learning.<br />
\#juniordevforlife