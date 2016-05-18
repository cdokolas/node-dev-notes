# node.js development

## General

- [Eric Elliott's "Essential JavaScript Links"](https://github.com/ericelliott/essential-javascript-links)

## Testing

- [Tape](https://github.com/substack/tape) (unit testing)
- [Instanbul](https://github.com/gotwarlost/istanbul) (code coverage)
- [Supertest](https://github.com/tj/supertest) (HTTP testing)

## Code Analysis

- [ESLint](http://eslint.org/) (static analysis, lint) (with [airbnb rules](https://www.npmjs.com/package/eslint-config-airbnb))

## i18n

- [Globalize](https://github.com/jquery/globalize)

## Security

- [Production Best Practices: Security](http://expressjs.com/en/advanced/best-practice-security.html) (Express site)
- [Hacksplaining](https://www.hacksplaining.com/) ("Comprehensive Security Training for Developers")

## Configuration

- [nconf](https://github.com/indexzero/nconf)
- see various answers at [How to store Node.js deployment settings/configuration files?](https://stackoverflow.com/questions/5869216/how-to-store-node-js-deployment-settings-configuration-files)

## node process management (for development only)

- [nodemon](http://nodemon.io/) _for dev_
- [forever](https://github.com/foreverjs/forever) _for prod_
- [PM2](https://www.npmjs.com/package/pm2)
- StrongLoop Process Manager (part of [strongloop](https://www.npmjs.com/package/strongloop) tools)

## Base setup (with atom)

### Initial Atom setup

#### General

- add package "atom-beautify"

#### linter

- add package "linter"
- add package "linter-eslint"

#### react

- add package "react"

### For each project

#### linter setup

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

## Sources

- [Why I use Tape Instead of Mocha & So Should You](https://medium.com/javascript-scene/why-i-use-tape-instead-of-mocha-so-should-you-6aa105d8eaf4)
- [How to store Node.js deployment settings/configuration files?](https://stackoverflow.com/questions/5869216/how-to-store-node-js-deployment-settings-configuration-files) (various answers)
- [Process managers for Express apps](http://expressjs.com/en/advanced/pm.html)
