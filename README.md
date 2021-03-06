# generator-rf [![Build Status](https://secure.travis-ci.org/taiansu/generator-rf.png?branch=master)](https://travis-ci.org/taiansu/generator-rf) [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/taiansu/generator-rf?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

> RF: a [React](http://facebook.github.io/react/)/[Flux](http://facebook.github.io/flux/) generator with webpack, dialects and some good stuffs.

### What's inside
* [React](http://facebook.github.io/react/)
* [Flux](http://facebook.github.io/flux/)
* [Jest](http://facebook.github.io/jest)
* [webpack](http://webpack.github.io/)
* SourceMap from webpack's [devtool](http://webpack.github.io/docs/configuration.html#devtool)
* Live-reload by [react-hot-loader](https://gaearon.github.io/react-hot-loader/)
* JS dialect in your favor:
    * [CoffeeScript](http://coffeescript.org/)
    * [LiveScript](http://livescript.net)
    * [Babel](https://babeljs.io/) (Formally Javascript 6to5)
    * vanilla JavaScript
* Have JSX in CoffeeScript/LiveScript by [coffee-react-transform](https://github.com/jsdf/coffee-react-transform)
* Stylesheet syntax in your favor:
    * [SASS/SCSS](http://sass-lang.com/)
    * [Less](http://lesscss.org/)
    * [Stylus](http://learnboost.github.io/stylus/)
    * pure CSS
* Optional [Bootstrap](http://getbootstrap.com/) Framework

### What 'RF' stands for

No, not the boring abbreviation of "React" and "Flux". It's actually the suffix of `rm -rf`. Now it sounds [dangerous](https://github.com/MrMEEE/bumblebee-Old-and-abbandoned/issues/123) and cooler, doesn't it?

## Installation

### Prerequisites

* [Node.js w/npm](http://nodejs.org/) or [iojs](https://iojs.org/) installed. I
  recommend install it by [nvm](https://github.com/creationix/nvm). Mac user can
  install it from [homebrew](http://brew.sh/).

> Note: Currently Jest only support v0.10.x of Node.js, and io.js v1.6.3 or above. Other
> node version can't run the test correctly.

### Install [Yeoman](http://yeoman.io)

```bash
npm install -g yo
```

### Install RF generator

```bash
npm install -g generator-rf
```

## Getting Started

### Intiate Project

For example, to create a project named "myapp", just type:

```bash
yo rf myapp
```

### Run it up

```bash
cd myapp && npm run dev
```

Then Open [http://localhost:8080](http://localhost:8080) in the browser and have fun!

> If you get error message like `Cannot GET /` on MS Windows, try `http://localhost:8080/index.html` instead. [Help wanted](https://github.com/taiansu/generator-rf/issues/12)

### Run the test suit
Don't forget to test your project by:

```bash
npm test
```

### Build for deploy

```
npm run build
```

## What RF generates:
    .
    └── myapp *
        ├── package.json
        ├── preprocessor.js
        ├── node_modules
        ├── src
        │   ├── assets
        │   │   ├── images
        │   │   └── stylesheets
        │   │       └── style.sass **
        │   ├── index.html
        │   └── scripts
        │       ├── actions
        │       │   └── __tests__
        │       ├── components
        │       │   ├── App.coffee **
        │       │   └── __tests__
        │       │       └── App-test.coffee **
        │       ├── constants
        │       │   └── __tests__
        │       ├── dispatcher
        │       │   ├── AppDispatcher.coffee **
        │       │   └── __tests__
        │       ├── main.coffee **
        │       ├── mixins
        │       │   └── __tests__
        │       └── stores
        │           └── __tests__
        └── webpack.config.js

* \* Won't create root directory if your current directory is identical with your project name. Check [--skip-root](#--skip-root-dont-create-root-directory) section for detail.
* \*\* Varied by your choices of the dialect and stylesheet syntax


## What `npm run build` gives:
    .
    └── myapp
        ├── build
        │   ├── bundle.js
        │   └── index.html
        └── ...

## Options

### --d: Dialect

By default, RF will generate codes in [CoffeeScript](http://coffeescript.org/). If you don't like it, use --d flag to change the dialect to generate.

* `ls` for [LiveScript](http://livescript.net)
* `babel` for [Babel](https://babeljs.io/) (Formally JavaScript 6to5)
* `js` for vanilla JavaScript

Example:

    yo rf myapp --d=ls

### --s: Stylesheet Syntax

RF generate [SASS](http://sass-lang.com/) (indented syntax) by default. Use --s flag to change it.

* `scss` for SCSS (Sassy CSS)
* `less` for LESS
* `stylus` for Stylus
* or `css` for CSS.

Example:

    yo rf myapp --s=scss

### --skip-bootstrap: Don't include Bootstrap framework stuffs

From 0.2.0, RF will include Bootstrap settings in the real __Webpack__ way. Turn them off by --skip-bootstrap flag.

Example:

    yo rf myapp --skip-bootstrap

### --skip-root: Don't create root directory

From 0.1.13, RF will create a root directory if current directory name is different from your appname, or generate files in current directory if they have same name. But if you're intentionally have them with different name, use --skip-root to generate files right in the current directory.

Example:

    yo rf trueName --skip-root

### --skip-test: Don't create \_\_tests\_\_ directory

For every sub-directories in `src/scripts`, RF will create a \_\_tests\_\_ directory
within. Use `skip-test` to skip that.

Example:

    yo rf myapp --skip-test

### --skip-install: Skip automatic package installation

Example:

    yo rf myapp --skip-install

## Contribute

* Fork this project
* run `npm install && npm test` and make sure all test are pass
* Make your changes with [a bit of test](http://yeoman.io/authoring/testing.html)
* For commit message of pull request, please check [these useful tips](http://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message) ahead.

## TODO

* Actions w/Constants, Store
* Custom template folder
* Component and Mixin generate command
* Isomorphic server script(?)

## License

MIT
