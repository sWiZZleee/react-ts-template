# sWiZZleee's React & TypeScript Template

This template is meant to serve as a simple boilerplate for me and anyone else who wants to quickly scaffold a [React](https://reactjs.org) w/ [TypeScript](https://www.typescriptlang.org) project. I have attempted to keep things flexible, simple and clean to allow developers a much clear path to customization and setting up their codebase the way they like it.

This project and especially the README.md has a lot more work that needs to be put into it but at this point in time I am happy to work of this template how it is and work on adjusting other specifics and minor details later on. If you feel like contributing or suggesting any changes that you would like to see or use please feel free to make a PR or contact me directly.

- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Serving the App](#serving-the-app)
  - [Building the App](#building-the-app)
- [Changing Style Guide](#changing-style-guide)
- [Changing Development Hooks (Husky)](#changing-development-hooks-husky)
- [Technologies](#technologies)

## Getting Started

Instructions on how to get started with this project.

### Installation

To get started with this template first off open up a terminal and clone the repository:

```bash
git clone https://github.com/sWiZZleee/react-ts-template.git
cd react-ts-template
```

Next we want to install the required dependencies to run and develop our application, while still inside the project's root directory in your terminal run either of the below commands depending on your choice of package manager.

```bash
npm install
# yarn install
```

### Serving the App

After cloning the project and installing all it's dependencies we can immediately start development with no extra setup required, to start a development server to serve the application with [Parcel](https://parceljs.org) you can run either of the below commands depending on your choice of package manager.

```bash
npm start
# yarn start
```

*Note:*
This setup using the `start` command to serve a development server is definitely not ready to be pushed into any production scenario, but it gets myself and other developers up and running fairly quickly.

### Building the App

A compiled production ready copy of our [React](https://reactjs.org) Application can be bundled with [Parcel](https://parceljs.org) easily using the build command, run either of the below commands depending on your choice of package manager.

``` bash
npm build
# yarn build
```

## Changing Style Guide

Configured automatically is [ESLint](https://eslint.org) with the [TUIL](https://github.com/patrickkempff/eslint-config-tuil) style guide which is, "An ESLint shareable config for TypeScript that has TypeScript with Standard, Jest and React best practises.". This works great with what I like to develop with personally straight out of the box but of course not everyone is a fan of this, to change the config to your preferred style edit the `.eslintrc.json' file in the root of the project's directory.

```json
{
  "extends": ["tuil/recommended"], // <-- Put your style guide in this line
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "settings": {
    "react": {
      "version": "detect"
    }
  }
}
```

As this is a [TypeScript](https://www.typescriptlang.org) project I of course could and maybe should of used TSLint but as this configuration is quite similar to the one I use for regular [React](https://reactjs.org) development without [TypeScript](https://www.typescriptlang.org) and secondly it seems good choice to leave it in there as it one has the capability to both JavaScript and [TypeScript](https://www.typescriptlang.org) which means pulling this template doesn't simply limit you to only using [TypeScript](https://www.typescriptlang.org).

## Changing Development Hooks ([Husky](https://github.com/typicode/husky))

This template is configured out of the box to tap in to git hooks using [Husky](https://github.com/typicode/husky), currently it runs both the [Lint-Staged](https://github.com/okonet/lint-staged) and `npm run test` commands. The [Lint-Staged](https://github.com/okonet/lint-staged) package will allow us to run linters against our staged git files, the configuration is defined within our `package.json` file.

```json
"lint-staged": {
    "*.{js,ts,tsx}": [
      "npm run lint:fix",
      "git add"
    ]
  }
```

Once having [Lint-Staged](https://github.com/okonet/lint-staged) setup to do the work that we need it to we setup the `.huskyrc.js` file to tap into the git hooks we want to work with to accelerate our development processes.

```javascript
const tasks = arr => arr.join(" && ");

module.exports = {
  hooks: {
    "pre-commit": tasks(["lint-staged", "npm run test"]),
  }
};
```

## Technologies

- [React](https://reactjs.org)
- [TypeScript](https://www.typescriptlang.org)
- [Parcel Bundler](https://parceljs.org) (Building and serving the application)
- [ESLint](https://eslint.org) (Configured to handle our TypeScript)
- [Husky](https://github.com/typicode/husky) (Tap into git hooks and improve developer workflow)
- [Lint-Staged](https://github.com/okonet/lint-staged) (Run linting on staged git files, used in conjunction with [Husky](https://github.com/typicode/husky) to run on the pre-commit hook)
- [Jest](https://jestjs.io) (Testing)