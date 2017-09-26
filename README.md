# Node.js development notes

## Introduction

This document is a personal note space, driven by my own research and preferences, about full-stack development with [Node.js](https://nodejs.org/).

My aim is to distill current and cutting-edge frameworks, tools and practices that I want to keep track of, investigate or use in Node.js projects. These involve items in the following general categories:

- Coding (IDEs, formatting, organization, documentation, frameworks/libraries, version control, etc.)
- Testing (unit, load, API, coverage)
- Security
- Deployment (configuration, load balancing, automation, monitoring/logging, etc.)

Currently, this is mostly server-oriented.

## Coding

### Project/Source management and Code review

- [Fossil](https://www.fossil-scm.org/) is a distributed SCM, issue tracking system and wiki.
- [Gerrit Code Review](https://www.gerritcodereview.com/) instead of [gitflow](http://nvie.com/posts/a-successful-git-branching-model/) (read [Abandoning Gitflow and GitHub in favour of Gerrit](https://www.beepsend.com/2016/04/05/abandoning-gitflow-github-favour-gerrit/))
- [OpenProject](https://www.openproject.org/) (will test a deployment)
- [Tuleap](https://www.tuleap.org/) (looked promissing at first, but way too complicated and restrictive to deploy; practically needs it's own server)

### Code style/analysis

- [editorconfig](http://editorconfig.org/) and [atom module](https://atom.io/packages/editorconfig) for consistent code style on the IDE This keeps preferred formatting styles in a `.editorconfig` project-local file and very vcs-friendly!
- [atom-beautify](https://atom.io/packages/atom-beautify) (conflicts with `editorconfig`?) This works very well, but I have to look into: unifying formatting conventions with ESLint and possibly keeping settings in a project-local config file.
- [markdown-preview](https://github.com/atom/markdown-preview) and [markdown-preview-plus](https://atom.io/packages/markdown-preview-plus) for previewing markdown documents (Not sure of proper "github-flavored" formatting; _Brackets_ seems to better handle this with paragraphs inside lists being properly rendered AFAICT.)
- [ESLint](http://eslint.org/) (static analysis, lint) (with [airbnb rules](https://www.npmjs.com/package/eslint-config-airbnb)) I think this may be the most important component for writing clean ES6 code.
- [Flow](http://flowtype.org/) (static type checker) Looks interesting
- [JSHint](http://jshint.com/about/) (static analysis)
- [complexity-report](https://github.com/escomplex/complexity-report) (?)

### Documentation

- Javascript code documentation with [JSDoc](http://usejsdoc.org/) (anything else available?)

### Frameworks/Libraries

#### Full-stack

- [MERN](mern.io) MongoDB-Express-React-NodeJS (+Redux+WebPack)
- [Meteor](meteor.com)

#### Server

##### Express

I like the [Express](http://expressjs.com/) framework, a "fast, unopinionated, minimalist web framework for Node.js".

With that, there are a few options that can be selected...

**Templating engines for Express**

- Handlebars

  Handlebars is like Mustache but with limited logic added, which gives you the ability to handle simple cases where you would otherwise need to generate extra data to feed the template with.

- Jade

  Jade is the classic templating engine for Express. It's a little weird and some features can be confusing. Also, it's not friendly to classic HTML developers as the syntax is not much like HTML.

- Mustache/Hogan
- React (with [express-react-views](https://github.com/reactjs/express-react-views)). More about React below.
- [EJS](http://ejs.co/) (a simple templating engine)

Sources:

- [Comparing JavaScript Templating Engines: Jade, Mustache, Dust and More](https://strongloop.com/strongblog/compare-javascript-templates-jade-mustache-dust/) (an old post at StrongLoop)
- [Isomorphic React Apps with React-Engine](https://www.paypal-engineering.com/2015/04/27/isomorphic-react-apps-with-react-engine/)
- [Isomorphic JavaScript: The Future of Web Apps](http://nerds.airbnb.com/isomorphic-javascript-future-web-apps/)
- [Node.js template showdown – 5 options compared](https://www.bearfruit.org/2014/01/20/node-js-template-showdown-5-options-compared/)

##### Meteor

"a large, opinionated Node.js framework"

#### Client (Web Browser)

##### Frontend tools (for development)

- [Browserify](http://browserify.org/)

  - [Frontend Dependency Management with Browserify](http://word.bitly.com/post/101360133837/browserify)

- Webpack

  - [Browserify vs Webpack](https://medium.com/@housecor/browserify-vs-webpack-b3d7ca08a0a9)

Also read:

- ["npm vs bower vs browserify vs gulp vs grunt vs webpack"](http://stackoverflow.com/a/35064297/243572)

#### Web Components (and related stuff)

I'm now mainly on the pro-Vue camp for the sole reason that Vue is highly regarded and is considered a much simpler solution than React.

I was previously on the pro-React camp for the following reasons:

- JSX is better (being JS-with-HTML instead of the other way around, or separating them needlessly)
- Server-side pre-render gives [isomorphic apps](http://nerds.airbnb.com/isomorphic-javascript-future-web-apps/)
- Cleaner HTML (HTML is _HTML!_)
- ...?

With React, one should use:

- [Flux](https://facebook.github.io/flux/) as an architecture
- [react-router](https://github.com/reactjs/react-router) for routing
- [Redux](http://redux.js.org/) to control state transitions (a Flux implementation?)

Interesting reads from the front lines:

- [Angular 2 versus React: There Will Be Blood](https://medium.freecodecamp.com/angular-2-versus-react-there-will-be-blood-66595faafd51#.ojybr1i6u)
- [React vs Angular 2 - compare the incomparable?](http://blog.scalac.io/2016/02/16/react-vs-angular-2.html)
- [FullStackReact](https://www.fullstackreact.com) (site dedicated to full stack development with react; need to go over the whole [yelp clone article](https://www.fullstackreact.com/articles/react-tutorial-cloning-yelp/))

Important: There seems to be a proliferation of new, interesting frameworks trending:

- [vue.js](https://vuejs.org/) is a contender for the 1st place in front-end frameworks and, AFAICT, tries to fill in the gap between functionality and ease-of-use in React
- [Polymer](https://www.polymer-project.org/) by Google

#### ORM - data access

- [loopback-datasource-juggler](https://github.com/strongloop/loopback-datasource-juggler/), part of the LoopBack tools (_"An ORM/ODM that provides a common set of interfaces for interacting with databases, REST APIs, and other types of data sources."_)
- [sails.js](http://sailsjs.org/) ? (rant by Kavin Burke [here](https://kev.inburke.com/kevin/dont-use-sails-or-waterline/))

The Loopback stack (libraries) looks pretty good; a bit better than sails.js. I wonder if it is modular enough to get cherry-picked... a serving of ORM for starters and we'll see what else combines well with the rest.

Some more info:

- [How to Implement Node + React Isomorphic JavaScript & Why it Matters](https://strongloop.com/strongblog/node-js-react-isomorphic-javascript-why-it-matters/) (strongloop)

#### GraphQL

- [loopback-graphql](https://github.com/Tallyb/loopback-graphql) looks incomplete and I've experienced a bug as well ([#90](https://github.com/Tallyb/loopback-graphql/issues/90))

- [Relay and GraphQL](https://facebook.github.io/react/blog/2015/02/20/introducing-relay-and-graphql.html) (GraphQL for React)

  also: [Learn Relay](https://learnrelay.org/)

#### Data Visualization (Graphs)

- D3 (how well does it integrate with React?)

### i18n

- [Globalize](https://github.com/jquery/globalize)

## Testing

- [Tape](https://github.com/substack/tape) (unit testing)
- [Instanbul](https://github.com/gotwarlost/istanbul) (code coverage)
- [Jest](https://facebook.github.io/jest/) (by Facebook)
- [Supertest](https://github.com/tj/supertest) (HTTP testing)

## Security

- [Production Best Practices: Security](http://expressjs.com/en/advanced/best-practice-security.html) (Express site)
- [Hacksplaining](https://www.hacksplaining.com/) ("Comprehensive Security Training for Developers")

## Deployment

### Configuration

- [nconf](https://github.com/indexzero/nconf)
- see various answers at [How to store Node.js deployment settings/configuration files?](https://stackoverflow.com/questions/5869216/how-to-store-node-js-deployment-settings-configuration-files)

### Node.js process management

- [nodemon](http://nodemon.io/) _for dev_
- [forever](https://github.com/foreverjs/forever) _for prod_
- [PM2](https://www.npmjs.com/package/pm2)
- StrongLoop Process Manager (part of [strongloop](https://www.npmjs.com/package/strongloop) tools)

--------------------------------------------------------------------------------

# Base setup (with atom)

Notes on setting-up a development environment with Atom

## Initial Atom setup

### General

- add package "atom-beautify"

### linter

- add package "linter"
- add package "linter-eslint"

### react

- add package "react"

## For each project

### linter setup

- eslint with airbnb rules (no react)

  ```
  npm i --save-dev eslint-config-airbnb-base eslint-plugin-import eslint
  ```

  add `"extends": "airbnb-base"` to `.eslintrc`

- eslint with airbnb rules (with react)

  ```
  npm i --save-dev eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y eslint
  ```

  add `"extends": "airbnb"` to `.eslintrc` and `"react"` to `plugins` array

--------------------------------------------------------------------------------

# Sources

- [The State Of JavaScript](http://stateofjs.com/2016/introduction/) 2016 survey
- [Why I use Tape Instead of Mocha & So Should You](https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4)
- [How to store Node.js deployment settings/configuration files?](https://stackoverflow.com/questions/5869216/how-to-store-node-js-deployment-settings-configuration-files) (various answers)
- [Process managers for Express apps](http://expressjs.com/en/advanced/pm.html)
- [Eric Elliott's "Essential JavaScript Links"](https://github.com/ericelliott/essential-javascript-links)
- [The top rising JavaScript trends to watch in 2017](https://medium.com/commit-push/the-top-rising-javascript-trends-to-watch-in-2017-86d8e87db3b3)
