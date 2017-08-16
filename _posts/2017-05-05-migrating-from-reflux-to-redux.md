Migrating from Reflux to Redux
==============

I recently helped my team move a large codebase from [Reflux](https://github.com/reflux/refluxjs) to [Redux](http://redux.js.org/) (I have written exensively about my experience on [ThoughtWorks' <i>Insights</i> blog](https://www.thoughtworks.com/insights/blog/advocating-software-quality-metro)). Both are JavaScript-based state-management tools. This was an interesting technical challenge, and a fun one.

Because Reflux and Redux both follow the basic [Flux](https://github.com/facebook/flux) architecture pattern of unidirectional data flow, we can incrementally take over the Reflux state cycle with Redux:

1. Complete Reflux cycle
2. Action handling (e.g. async) in Reflux, but keep all state in Redux. Reflux store action listeners dispatch Redux actions with the results of remote API calls and no longer call `this.trigger`. React components receive props mapped to Redux state and no longer listen to Reflux stores. At this point, Reflux essentially acts as async middleware for Redux.
3. Action handling (e.g. async) in Redux, with appropriate middleware. Reflux store action listeners now do nothing but straight away dispatch corresponding Redux actions.
4. Complete Redux cycle – stop dispatching Reflux actions from React components and start directly dispatching Redux actions.

![Redux Migration - Technical Diagram](/assets/redux-migration.png)

Thus, you can break the refactor up into bite-sized chunks and spread it out over time if required (e.g. due to other high-priority work/new scope coming in), keeping your app fully functional at every stage.