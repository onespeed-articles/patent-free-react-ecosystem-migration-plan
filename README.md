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
The quickest way to migrate out of React is to move to Preact and their helper package called [`preact-compat`](https://github.com/developit/preact-compat). 

* [bye-react: one line CLI to migrate from React to Preact](https://github.com/colinmcd94/bye-react)
* [Switching to Preact (from React)](https://preactjs.com/guide/switching-to-preact)
* [Using Preact Instead Of React](https://medium.com/@rajaraodv/using-preact-instead-of-react-70f40f53107c)
* [Differences to React](https://github.com/developit/preact/wiki/Differences-to-React)

# React to Vue
Unlike React Vue is a full framework offering a router, state solution, and even scoped styles out the box. 

Resources:
* [Switching From React To Vue.js](https://vuejsdevelopers.com/2017/05/28/switch-from-react-to-vue-js/)
* [(Vue) Comparison with Other Frameworks](https://vuejs.org/v2/guide/comparison.html)

# React to Angular
There aren't any resources online for migration from React to Angular. If you're interested in this you can contact us at patrick@onespeed.io and we can help your project migrate over to Angular

# Flow to TypeScript

Resources:
* [Migrating from Flow to Typescript](https://medium.com/@ckoster22/migrating-from-flow-to-typescript-b065796797db)
* [TypeScript vs Flow](https://github.com/niieani/typescript-vs-flowtype)

# Jest to Mocha, Chai, Sinon
If you're using Jest it should be straight forward to switch to Mocha. Mocha is very flexibility by design but the downside is that it requires more configuration. One configuration is having to choose an assertion library such as Chai and Sinon for mocking. Another benefit of switching to Mocha is the community and large support with videos, blog posts, and libraries. Mocha also providers snapshot testing as yet another integration with either `snap-shot` on npm. With Mocha there will be a lot configuration initially but once you're all set and ready your workflow would be better off due to the community support.

resources:
* [React Testing – Jest or Mocha?](https://spin.atomicobject.com/2017/05/02/react-testing-jest-vs-mocha/)

# create-react-app
A great way to initially create your project is using a CLI since it allows you to focus on your application code rather than learning your build setup. The main difference between React's CLI compared to others is that the other CLIs have more feature while React's CLI create large documentation around their initial scaffold. 

Resources:
* [preact-cli](https://github.com/developit/preact-cli)
* [vue-cli](https://github.com/vuejs/vue-cli)
* [angular-cli](https://github.com/angular/angular-cli)

# Need help?
If you or your company needs help with migrate we offer migration services ranging from code-reviews to us handling the full migration of your app to any of other technology that fits your needs. We also provide training for your team to jump in the new code base to quickly be production. 
