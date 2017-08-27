![migration-off-react](https://user-images.githubusercontent.com/1016365/29734853-7adaff16-89a9-11e7-952e-2df421e52748.png)

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
  * [Jest to Mocha, Chai, Sinon](#jest-to-mocha-chai-sinon)
  * [create-react-app to other CLIs](#create-react-app-to-other-clis)


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

* `React`
Introducted as the V in MVC with the sole focus on rendering the view. The goal of React is to provide a developer with a simple API that others can build on top of much like how Node.js is for running JavaScript as a server. If you build anything on top of `React` you are affected.

* `Flow`
As we created large applications we start to run into very common errors such as typos or using a function incorrectly due to poor documentation. Using a typed language allows you to avoid testing for dealing with incorrect inputs or types. If you build anything with `Flow` you are affected.

* `Jest`
Zero configuration testing platform for applications is the main reason to use Jest over others. The idea here is that the testing frameworks knows you're most likely building an application so they provide you with all the essentials without having to configure your setup. If you test anything using `Jest` you are affected.

* `create-react-app`
Going from zero to hello-world may seem daunting due to decision fatigue. This CLI allows you to focus on your application and provides a large readme explaining everything you need to know about expanding from your hello-world. If you build anything on top of React you are affected.


# React to Preact
<img width="699" alt="screen shot 2017-08-25 at 2 38 20 pm" src="https://user-images.githubusercontent.com/1016365/29733688-3a889c1c-89a3-11e7-86e0-2a73ce8c8c50.png">

The quickest way to migrate out of React is to move to Preact and their helper package called [`preact-compat`](https://github.com/developit/preact-compat). Preact also provides the good parts of React's API without the overhead or bloat of the framework that never really changed after it's release. Building on these ideas, Preact was able to excel on areas such as higher progressive web application score using lighthouse. also has better support for web components compared to React. Other differences also include server-side rendering and performence which is better in Preact than the original. 

## Why
Preact has a familar API as React using pattern like ES6 classes and Functional Components without anything else like `React.createClass`, `Synthetic Events`, `PropType` validations, `React.Children`, and a lot of virtual-dom optimizations. At the same time the team behind Preact also provides a helper package for migration from React. Preact is highly optimized focusing in on the key parts that makes React so great while providing you with the best performance. This is why we think Preact is the perfect first choice when moving off of React to an MIT licensed framework.

Preact is a 3KB alternative to native React. This is accomplished mostly in part to lightening up the original React API and removing the Synthetic Events, PropType validations, and the ability call React.Children. React provides an optional add-on called, preact-compat if any of the before mentioned features are needed.

## Switch to Preact with just one command line
You can migrate from React to Preact with just one command using [`bye-react`](https://github.com/colinmcd94/bye-react). More specifically, this tool switches the project over to `preact-compat`, the "compatibility layer that makes React-based modules work with Preact, without any code changes".

```
$ npm install -g bye-react
$ bye-react
```
If you want to undo `bye-react` you can simply run.
```
$ bye-react --undo
```

This is the fastest way because to switch to Preact because the tool does 3 things.
* Transforms your build system if you use Webpack, Browserify, or the Babel React preset (or any combination thereof). If you don’t use any of these, this won't work. If you're not using any of these build tools then you probably should.
* It's not guaranteed to work in all cases so for some cases this is a great first step. Make sure you create a new branch if you do plan to migrate this way. You should be using a version of React that is compatible with the current stable release `15.6.11`. May interact in interesting and unfortunate ways with non-standard build pipelines (e.g. if you dynamically generate .babelrc or package.json, etc).
* Will delete comments inside `package.json` and `.babelrc` files. These files contain JSON-compliant data. To add the aliases, bye-react reads in the JSON, modifies it, and writes it back to disk. Comments are lost en route. If these are important to you then don't use bye-react.

There are two more methods in this [guide provided by Preact](https://preactjs.com/guide/switching-to-preact)

* [bye-react: one line CLI to migrate from React to Preact](https://github.com/colinmcd94/bye-react)
* [Switching to Preact (from React)](https://preactjs.com/guide/switching-to-preact)
* [Using Preact Instead Of React](https://medium.com/@rajaraodv/using-preact-instead-of-react-70f40f53107c)
* [Differences to React](https://github.com/developit/preact/wiki/Differences-to-React)

# React to Vue
<img width="857" alt="screen shot 2017-08-25 at 2 38 43 pm" src="https://user-images.githubusercontent.com/1016365/29733704-5371e116-89a3-11e7-941a-5a96ca81b3a7.png">

Unlike React Vue is a full framework offering a router, state solution, and even scoped styles out the box. In React you're always worried about choosing the right package for state, routing, styles, or any other missing part that React doesn't provide. Vue assumes you are creating a web application so they make sure to guide you along your way with a ton of documentation on all parts of the framework. They even go so far as to compare Vue to others and give you an idea as to why they made a certain design decision. This framework truely feels as it was built by the design of it's community because it was initially just like React (just the View) before it grew into a full web framework that it is known for today.

## Performance
Vue was created with performance first by design. Each part of Vue reminds you of how much thought was put into it's design in order to achieve it's performance from all the learnings the community found in React. For example their virtual-dom does all of the optimizations that you want in React but by default. Vue also made sure you can still use the framework by simply dropping a script tag in your index.html and easily get up and running without losing performance for file size.

## Scale
When talking about scale for the frontend you endup talking about how many engineers can work on the project without losing their minds with merge conflicts. This framework also likes to call itself progressive since you can easily scale the abtraction level high or as low as possible with a simple script tag. 

## Why
Vue allows you to use both JSX and Template but more of the time you will find yourself using the template syntax. Unlike React where you're always faced with decision fatigue, in Vue.js you are able to focus on your application code with a clear API that doesn't try to introduce any new terms. We this Vue.js is a great choice or migration and more so for green field projects. If you want to get up and running with your application in minutes you really should give Vue a try.

Resources:
* [Switching From React To Vue.js](https://vuejsdevelopers.com/2017/05/28/switch-from-react-to-vue-js/)
* [(Vue) Comparison with Other Frameworks](https://vuejs.org/v2/guide/comparison.html)

# React to Angular
<img width="815" alt="screen shot 2017-08-25 at 2 38 34 pm" src="https://user-images.githubusercontent.com/1016365/29733693-442bba1a-89a3-11e7-95de-4cafc89974eb.png">

When migrating to Angular from React there are a lot of differences that you need to be aware of. While some of the concepts of React are there with Angular there are just different architectural. Here's a quick list of differences.

## Design Differences

* bootstrapping
While in React this is as simple as importing a render function from react-dom in Angular we need to import not only the browser version of bootstrap but configure an internal runtime. Your main file for starting your framework is going to be completely different when switching.

* props
In Angular you have props but they're called Inputs and only allow values that doesn't include functions. As with react you're able to use unidirectional data flow in Angular using Inputs.

* prop-types
In Angular you're most likely using TypeScript which will tell you that you're using the input incorrectly so you won't need runtime type checking as it's in the build system and editor.

* styles
In React you have to find your own way to manage styles in a way that works with your team. In Angular this is solved by using the browser API to emulate scoped styles as if you're using the Shadow DOM. Rather than having to choose which style library works for you in Angular it's built-in.

* storing state
Both frameworks allow you to store local state within the component which affects rendering to his child components. Angular also provides you with ways to wire up any stort of store with it's services.

* event handlers
While in React you have hard coded events in Angular this isn't the case. In Angular you can use the framework's method of wiring up events that will work for any event name called Outputs. In both frameworks you can also get a refernce of the element to manually wire up the listener.

* state change
While in React you must use `setState` in order to make sure your changes are reflected in Angular you don't need such a thing. In Angular you simple change the value in your component and the changes are batched and reflected automaticly. Angular uses zone.js to track all asynchronous calls which also helps when doing server-side rendering.

* data binding with unidirectional data flow
Angular allows you to benefit from both one-way data binding as well as two-way data binding without losing out on the benefits of unidirectional data flow. This is one of the best features of Angular as you benefit with the experience from previous patterns without the performance loss.

* refs
React provides you with escape hatches where possible and Angular does the same with ElementRef. Angular also makes sure to prevent you for getting direct reference to the element can be garbage collected.

* component composition
Practically the same as React, in Angular you're able to compose many components within each other as well as use content projection. Angular also allows you to use native browser slot API for better interoperability and composition. You can also use native Shadow DOM API to truely encapsulate your component and styles.

* dynamic elements
In React we're able to use JavaScript for dynamic repeating elements. In Angular we use structural directives to declaratively tell the compiler how to wire up your dynamic elements

## Why
Angular is the second biggest framework right after React so there is already an established ecosystem. There is also a lot of opportunities for a company or engineer to become notable in the community. The project is backed by Google which is much larger than Facebook and the Angular Team is close with the Chrome Team so they're able to foresee future changes to chrome that will affect the framework. For example, the Angular framework was built to support web components and is optimised to work well in V8's VM due to patterns they discovered while talking to engineers at Google.


# Flow to TypeScript
<img width="892" alt="screen shot 2017-08-25 at 2 51 23 pm" src="https://user-images.githubusercontent.com/1016365/29734050-060b35e2-89a5-11e7-8b07-5318bcc530fd.png">

## Why
TypeScript is the leader in Typed JavaScript so naturally it's the best choice and it was even created back in 2012 so the codebase and community is very mature and growing compared to Flow. This is a great choice as the team has put a lot of thught into it's syntax and they also make sure to follow and changes to the JavaScript language which means you can think of this as a superset of JavaScript.

## Differences in usage and usability

|   | TypeScript            | Flow |
|---|------------------|--------|
| Leading Design Goal / North Star | identify errors in programs through [a balance between correctness and productivity](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Design-Goals) | enforce type soundness / safety |
| IDE integrations | top-notch | sketchy, must save file to run type-check; some IDEs have workarounds to run real-time |
| type-checking speed (w/o transpilation, *subjective, need benchmarks!*) | speed does not degrade much as the project grows | speed degrades with each additional file |
| autocomplete | <ul><li>both during declaration and usage</li><li>feels instantaneous</li><li>feels reliable</li></ul> | <ul><li>[only for usage](https://github.com/facebook/flow/issues/3074)</li><li>feels sluggish (often a second or more of delay)</li><li>feels unreliable (sometimes does not show up at all)</li></ul> |
| expressiveness | great (since TS @ 2.1) | great |
| type safety | very good (7 / 10) | great (8 / 10) |
| specifying generic parameters during call-time | yes [e.g.](http://www.typescriptlang.org/play/#src=function%20someFactory%3CT%3E()%20%7B%0D%0A%20%20return%20class%20%7B%0D%0A%20%20%20%20method(someParam%20%3A%20T)%20%7B%0D%0A%20%20%20%20%20%20%0D%0A%20%20%20%20%7D%0D%0A%20%20%7D%0D%0A%7D%0D%0A%0D%0A%2F%2F%20how%20to%20invoke%20this%20factory%20with%20a%20defined%20%3CT%3E%3F%0D%0A%0D%0Aconst%20SomeClass%20%3D%20someFactory%3C%7B%20whatever%3A%20string%20%7D%3E()%0D%0Aconst%20someInstance%20%3D%20new%20SomeClass()%0D%0AsomeInstance.method('will-error-here')%0D%0A) | no |
| specifying generic parameters for type definitions | yes | yes |
| typings for public libraries | plenty of well maintained typings | a handful of mostly incomplete typings |
| unique features | <ul><li>autocomplete for object construction</li><li>declarable `this` in functions (typing `someFunction.bind()`)</li><li>large library of typings</li><li>more flexible [type mapping via iteration](https://github.com/Microsoft/TypeScript/pull/12114)</li><li>namespacing</li></ul> | <ul><li>variance</li><li>existential types `*`</li><li>testing potential code-paths when types not declared for maximum inference</li><li>`$Diff<A, B>` type</li></ul> |
| type spread operator | [work in progress](https://github.com/Microsoft/TypeScript/pull/13470) | [shipped](https://github.com/facebook/flow/commit/ad443dc92879ae21705d4c61b942ba2f8ad61e4d) >=0.42 |
| ecosystem flexibility | [work in progress](https://github.com/Microsoft/TypeScript/issues/6508) | no extensions |
| programmatic hooking | architecture prepared, work in progress | work in progress |
| documentation and resources | <ul><li>very good docs</li><li>many books</li><li>videos</li><li>e-learning resources</li></ul> | <ul><li>incomplete, often vague docs</li><ul> |
| commercial support | no | no |
| error quality | good | good in some, vague in other cases |


Resources:
* [Migrating from Flow to Typescript](https://medium.com/@ckoster22/migrating-from-flow-to-typescript-b065796797db)
* [TypeScript vs Flow](https://github.com/niieani/typescript-vs-flowtype)

# Jest to Mocha, Chai, Sinon
<img width="559" alt="screen shot 2017-08-25 at 2 51 55 pm" src="https://user-images.githubusercontent.com/1016365/29734063-10bb26be-89a5-11e7-812b-60e3abecbdd4.png">

If you're using Jest it should be straight forward to switch to Mocha. Mocha is very flexibility by design but the downside is that it requires more configuration. One configuration is having to choose an assertion library such as Chai and Sinon for mocking. Another benefit of switching to Mocha is the community and large support with videos, blog posts, and libraries. Mocha also providers snapshot testing as yet another integration with either `snap-shot-it` on npm. With Mocha there will be a lot configuration initially but once you're all set and ready your workflow would be better off due to the community support.

resources:
* [React Testing – Jest or Mocha?](https://spin.atomicobject.com/2017/05/02/react-testing-jest-vs-mocha/)

# create-react-app to other CLIs
A great way to initially create your project is using a CLI since it allows you to focus on your application code rather than learning your build setup. The main difference between React's CLI compared to others is that the other CLIs have more feature while React's CLI create large documentation around their initial scaffold. 

## preact-cli
> Start building a Preact Progressive Web App in seconds 🔥

In this CLI you also get routes wired up by default as you're most likely going to create an application with them. Unlike the React CLI 

## vue-cli
> A simple CLI for scaffolding Vue.js projects.

Vue CLI provides you with template so at any point you and your company can create your own template starter. This means the CLI is already better than others because often people disagree with the initial setup.

## angular-cli
> CLI for Angular applications based on the ember-cli project.

A lot of patterns and conventions in Angular are automated with this CLI which allows you to focus more on the app


Resources:
* [preact-cli](https://github.com/developit/preact-cli)
* [vue-cli](https://github.com/vuejs/vue-cli)
* [angular-cli](https://github.com/angular/angular-cli)

