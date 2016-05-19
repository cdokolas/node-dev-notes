# Node.js development notes

## Introduction

This document is a personal note space, driven by my own research and preferences, about full-stack development with [Node.js](https://nodejs.org/).

My aim is to distill current and cutting-edge frameworks, tools and practices that I want to keep track of, investigate or use in Node.js projects. These involve items in the following general categories:

- Coding (IDEs, formatting, organization, documentation, frameworks, version control, etc.)
- Testing (unit, load, API, coverage)
- Security
- Deployment (configuration, load balancing, automation, monitoring/logging, etc.)

Currently, this is mostly server-oriented.

## Coding

### Code Analysis

- [ESLint](http://eslint.org/) (static analysis, lint) (with [airbnb rules](https://www.npmjs.com/package/eslint-config-airbnb))

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

