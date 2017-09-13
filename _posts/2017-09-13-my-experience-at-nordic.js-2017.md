My Experience at Nordic.js 2017
==============

I was up in Stockholm last week for [Nordic.js](http://nordicjs.com/) and I figured I’d share some of my takeaways. I didn’t go a great job of taking notes, but I did come away with some strong impressions.

![MPJ gets a tattoo](/assets/mpj_tattoo.jpg)

The conference was co-hosted by rising star Mattias Petter Johansson of [FunFunFunction](https://www.youtube.com/channel/UCO1cgjhGzsSYb1rsB4bFe4Q), which was cool since his show is awesome. The most bizarre moment of the conference came when MPJ randomly decided to get a tattoo and livestream it to the screen instead of appearing on stage towards the end of the second day. Talk about commitment…

There seemed to be a strong focus on diversity and equality on the part of the organisers. Talks were extremely well balanced, both in the gender of the presenters (it felt very close to parity), and in terms of the tech/community balance of topics. The second day also featured an optional “equality pep talk” breakfast to kick off the day. Even the color scheme of the event and the design of the venue seemed to be aiming for gender inclusivity - the palette was dominated by pastel shades and pink was very much in evidence. Of course, the audience was still mostly white dudes by a pretty huge margin, which had some interesting consequences (see notes on Karolina Szczur’s talk below).

Here are my notes on my favourite talks:

<br/>

<h3>The Hilarious Misadventures of Being a Platform Downstream from Your Language</h3>
*[Myles Borins](https://github.com/MylesBorins) (TC39 Delegate & Google Developer Advocate for Node.js)*

Borins is an interesting guy. He has a degree in art and another in music, and has been contributing to OSS on the side forever. He somehow ended up getting hired by IBM to work on Node full-time, and now he’s doing the same thing for Google instead. He was also on Node's Technical Steering Committee for a while before [stepping down in protest](https://medium.com/@mylesborins/effective-immediately-i-am-stepping-down-from-the-nodejs-tsc-3df37c6ccbae) in due to the committee’s inaction in a recent code of conduct controversy.

In this talk, Borins described his involvement with the ECMAScript Technical Committee (TC39). The TC39 is comprised of various interest groups, including all the major browser vendors and technical experts (such as Borins, representing Node). They meet once a month in various locations, and it takes a minimum of four meetings to get a new feature approved. You need a full spec, an implementation in a major browser, as well as total committee consensus to become part of the standard - this is why it takes so long for new features to enter the language. Going to these meetings is expensive (voting members pay USD 70,000 per year) and essentially a full-time job for feature champions, who have to take on the role of developer, manager, and  diplomat all at once. This bars most JS community members from impacting ECMA directly, but you can assist the champion for the features you care most about, e.g. by writing tests, working on the spec, etc.

<br />
<h3>Best Practices for Reusable UI Components</h3>
*[Mars Jullian](https://github.com/marsjosephine) (Netflix)*

Netflix is apparently betting heavily on UI component libraries that can be shared and reused between teams. Julian had a key role in developing their approach to this, and she kindly shared her key takeaways:

- Use React for your libraries. It’s easier to repurpose for other frameworks than vice-versa.
- Your component should physically begin at its visible edge (i.e. no margin or border, potentially no padding)
- Enough local state to work an an independent unit
- Tightest possible type-checking on props (including object/array shapes)
- Fewer props - make the component easy to understand and reduce cognitive load. Use smart rendering instead of extra props - e.g. don’t render a list if the prop comes in as `null` or empty instead of passing an additional `shouldRenderList` prop
- Pass specific props to children; don’t blindly pass on all props (since this would allow unintended behaviour to be applied to children from the outside)

<br/>
<h3>Reactive Web Animations with RxJS</h3>
*[David Khourshid](https://github.com/davidkpiano) (Microsoft)*

As a functional programming buff and [ReactiveX](http://reactivex.io/) enthusiast, this was awesome. Not only does Khourshid have wicked UI skills, his reactive model of animations really makes a lot of sense. He demoed an observable model of animation-triggering events using [RxJS](https://github.com/Reactive-Extensions/RxJS), which could then have all the usual reactive transformations applied to them, such as merging, mapping, filtering, before yielding the desired visual effect.

The coolest thing? With this approach you can unit test your animations as pure functions!

<br/>
<h3>Beyond the Bubble</h3>
*[Ben Schwarz](https://github.com/benschwarz) (Calibre)*

> We need to stop optimising for $3000 MacBooks.
> We set out to build the world wide web, not the wealthy Western web.

While we think of performance as less and less relevant these days, this is a very biased and unrealistic point of view. There are tens of millions of first-time internet users entering the market every year in India alone, with the vast majority being mobile-only. These users do not typically enjoy the latest/most performant devices, nor the fastest connections, nor the cheapest data plans. So slow/large applications can be crippling from both a usability and financial perspective.

The most critical information, such as main text content, should be available instantly, independent of styling and interactivity status (e.g. if you visit The Guardian’s site with JS turned off, you should still be able to read the news). According to Schwarz we need to be paying particular attention to load order here, particularly with webfonts, which get loaded lazily (only when text tries to be rendered that wants to use that font). Single page apps, which require all JS to have been downloaded, processed, and run in order for text to be rendered, can cause quite a delay for a webfont to be loaded and text to be displayed.

In these cases, we can play around with load order using the preload tag (and I suppose you could come up with some server side pre-rendering solution, too). In any case, “time to first paint" and "time to interactive” should not be the same thing. We can keep ourselves honest by doing regular, realist perf audits using the the excellent Chrome devtools and mediocre (realistic) devices.

<br/>
<h3>Who Cares Why Undefined Is Not a Function</h3>
*[Tereza Sokol](https://github.com/terezka) (NoRedInk)*

Can essentially be summarised as “[Elm’s](http://elm-lang.org/) pure functional approach and solid type checking gives you back the time you waste looking for the cause of unhelpful JS error messages”.

<br/>
<h3>Sociolinguistics and the Javascript Community: A Love Story</h3>
*[Harriet Lawrence](https://github.com/harrietgrace) (Buildkite)*

Coming from a dev background, Lawrence is a technical writer at Buildkite, a CI tool maker based out of Melbourne, Australia. She’s also currently getting her Master’s in Sociolinguistics, focusing on tech communities, so she’s got a real passion for and deep knowledge of the intersection between language and culture, particularly in the tech space.

I would summarise her message as “words matter”. The way we talk about our work and communities in public forums (e.g. Github) can really make a difference in how likely outsiders are to join and feel empowered/valued, and how likely existing members are to continue contributing. In addition to obviously not being an asshole, Lawrence suggests that we can create productive environments by creating a community that accepts weakness (e.g. by tweeting something like “this thing was really hard and I thought I’d never get it but hey, looks like I’ve learned something”) and that recognises effort and progress (e.g. merging a PR from a new contributor by saying “nice use of technique X, you’re really getting the hang of this tech stack” rather than “cool, merged”).

Chatting with her afterwards, I asked her about what to do when someone just refuses to accept that their behaviour/language matters or has an impact on the community, since this seems to happen a lot (see Node’s recent code of conduct debacle for an example). She told me that there are some people who will just never be persuaded and have that empathy, and that these people will sadly keep creating a toxic environment for others. In those cases, Lawrence says that nowadays she just stops working with the individuals in question.

<br/>
<h3>Building Inclusive Communities</h3>
*[Karolina Szczur](https://github.com/thefoxis) (Developer, designer & conference organizer)*

This was a very well-done intro to privilege, diversity, and inclusion. While I personally didn’t hear anything particularly new here, it appeared that the topic was new and uncomfortable to quite a few audience members. A number of people got up and left during this presentation, and while I can’t say for sure, it did seem to be only men who did this. Afterwards, Szczur [tweeted an email](https://twitter.com/fox/status/906375321045405696) she received from a male conference attendee, saying that he felt discriminated against, remarking that “this is not Trump’s America”, and claiming that “we don’t have [gender inequality] in Sweden”.

Clearly we still have quite a way to go, but well done to Karolina for meeting the exhausting task of educating.