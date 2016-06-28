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

### General

### Code style/analysis

- [editorconfig](http://editorconfig.org/) and [atom module](https://atom.io/packages/editorconfig) for consistent code style on the IDE
This keeps preferred formatting styles in a `.editorconfig` project-local file and very vcs-friendly!
- [atom-beautify](https://atom.io/packages/atom-beautify) (conflicts with `editorconfig`?)
  This works very well, but I have to look into: unifying formatting conventions with ESLint and possibly keeping settings in a project-local config file.
- [markdown-preview](https://github.com/atom/markdown-preview) and  [markdown-preview-plus](https://atom.io/packages/markdown-preview-plus) for previewing markdown documents
	(Not sure of proper "github-flavored" formatting; *Brackets* seems to better handle this with paragraphs inside lists being properly rendered AFAICT.)
- [ESLint](http://eslint.org/) (static analysis, lint) (with [airbnb rules](https://www.npmjs.com/package/eslint-config-airbnb))
  I think this may be the most important component for writing clean ES6 code.
- [Flow](http://flowtype.org/) (static type checker)
  Looks interesting
- [JSHint](http://jshint.com/about/) (static analysis)
- [complexity-report](https://github.com/escomplex/complexity-report) (?)

### Frameworks/Libraries

#### Web Components (and related stuff)

I'm mainly on the pro-React camp for the following reasons:

- JSX is better (being JS-with-HTML instead of the other way around, or separating them needlessly)
- Server-side pre-render
- Cleaner HTML (HTML is *HTML!*)
- ...?

With React, one should use:

- [Flux](https://facebook.github.io/flux/) as an architecture
- [react-router](https://github.com/reactjs/react-router) for routing
- [Redux](http://redux.js.org/) to control state transitions (a Flux implementation?)

Interesting reads from the front lines:

- [Angular 2 versus React: There Will Be Blood](https://medium.freecodecamp.com/angular-2-versus-react-there-will-be-blood-66595faafd51#.ojybr1i6u)
- [React vs Angular 2 - compare the incomparable?](http://blog.scalac.io/2016/02/16/react-vs-angular-2.html)
- [FullStackReact](https://www.fullstackreact.com) (site dedicated to full stack development with react; need to go over the whole [yelp clone article](https://www.fullstackreact.com/articles/react-tutorial-cloning-yelp/))

#### ORM - data access

- [loopback-datasource-juggler](https://github.com/strongloop/loopback-datasource-juggler/), part of the LoopBack tools (*"An ORM/ODM that provides a common set of interfaces for interacting with databases, REST APIs, and other types of data sources."*)

#### GraphQL

- [Relay and GraphQL](https://facebook.github.io/react/blog/2015/02/20/introducing-relay-and-graphql.html) (GraphQL for React)

#### Data Visualization (Graphs)

- D3 (how well does it integrate with React?)

### i18n

- [Globalize](https://github.com/jquery/globalize)

## Testing

- [Tape](https://github.com/substack/tape) (unit testing)
- [Instanbul](https://github.com/gotwarlost/istanbul) (code coverage)
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

---

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

- [Why I use Tape Instead of Mocha & So Should You](https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4)
- [How to store Node.js deployment settings/configuration files?](https://stackoverflow.com/questions/5869216/how-to-store-node-js-deployment-settings-configuration-files) (various answers)
- [Process managers for Express apps](http://expressjs.com/en/advanced/pm.html)
- [Eric Elliott's "Essential JavaScript Links"](https://github.com/ericelliott/essential-javascript-links)
