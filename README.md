# How to migrate from React.js

Due to recent news, you or your company might consider moving away from React.js or any technology under Facebook’s BSD+Patents License. If you plan to or if you're trying to determine the scope of the migration we provided a table of contents to determine what you need to know.

Table of contents
=================

  * [The Issue](#the-issue)
  * [Effected Tech](#effected-tech)
    * [React to Preact](#react-to-preact)
    * [React to Vue](#react-to-vue)
    * [React to Angular](#react-to-angular)
    * [Flow to TypeScript](#flow-to-typescript)
    * [Jest to Mocha, Chai](#jest-to-mocha-chai)
    * [create-react-app](#create-react-app)
  * [Need help?](#need-help)


# The Issue
From what Facebook's lawyers are saying to their engineers who ask all of their open-source projects require their BSD+Patents License which, in Facebook's reasoning, this is meant to be a defense from people suring Facebook for patents. While this is an "old idea" for lawyers the result of introducing this again in the open-source community comes off as tone deaf of the original goal of open-source. Here is a technology lawyer's response to another technology lawyer who believes this isn't a huge issue.

```
I'm also a technology lawyer, i've written several of the patent grants used very widely, as well as having been responsible for open source licensing compliance at Google for a very long time .
If i thought this license would actually help i would support it in an instant. But so far
1. i don't believe it would. It's a very old idea, discussed to death, with a lot of downside, and a little upside.
2. they've ruined a lot of the possibility of getting people on board by doing it in a way that's fairly tone deaf.
As for the license itself:
You also have the same concern if you aren't large.
It's also not just going to yank your react license, it will yank your license to everything under this license.
This license will not have the effect of stopping patent litigation. Patent trolls don't use React, and most of the danger is still trolls.
If you really wanted to play that game, you'd be better off saying "if you sue us, you lose the right to use facebook the service". That might have some effect (but probably not a lot).
Instead, this license will have the main effect of further enabling the large to leverage the small. Hey, seems like you got technology i like, and hey, looks like the app you depend on for your livelihood uses react. it'd be a shame if you had to sue us for taking your stuff and lose your react license.
Do i think facebook will do that? Honestly, no. I doubt it. They may by accident. Do i think, if widely adopted, it would have that effect: 100% yes.
As for the origins, these kinds of broad termination clauses have been around forever. They aren't anything new. As i've said before, they were considered and explicitly rejected from most current licenses with patent grants.
Rather than come to a community of license authors, etc, and say "hey, we want to re-explore this, because we're seeing a problem", they did it this way. That's ... unlikely to be a successful mechanism (and in fact, i know a large number of corporate counsel who have banned it).
```

If any of this scares you (and it should) you're probably thinking about migrating. Don't worry I got you covered with the best migration paths.

# Effected Tech
Facebook's open-source is pretty vast covering everything from UI frameworks to creating their own language. We're going to focus in on four technologies: `React`, `Flow`, `Jest`, and `create-react-app`.


# React to Preact

* [Switching to Preact (from React)](https://preactjs.com/guide/switching-to-preact)
* [Using Preact Instead Of React](https://medium.com/@rajaraodv/using-preact-instead-of-react-70f40f53107c)
* [Differences to React](https://github.com/developit/preact/wiki/Differences-to-React)

# React to Vue

# React to Angular
# Flow to TypeScript
# Jest to Mocha, Chai
# create-react-app

# Need help?
