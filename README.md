# Skeletor: modern, modular UI build tools

## Table of Contents
  1. [Getting started](#getting-started)  
    - [What is Skeletor?](#what-is-skeletor)  
    - [Installation](#installation)  
  2. [Project setup](#project-setup)  
    - [Working with an existing Skeletor project](#working-with-an-existing-skeletor-project)  
    - [Starting a new Skeletor project](#starting-a-new-skeletor-project)  
      - [Manual configuration](#manual-configuration)
      - [Automatic configuration via Skeletor Wizard](#automatic-configuration-via-skeletor-wizard)
  3. [Ecosystem overview](#ecosystem-overview)

## Getting started

### What is Skeletor?
Skeletor is a highly customizable UI build tool ecosystem, created and maintained by the [DEG](http://www.degdigital.com) UI team. 

On its own, [Skeletor Core](https://github.com/deg-skeletor/skeletor-core) is just the task runner of the bunch (albeit a very configurable one, if we do say so ourselves). When configured to use its robust family of plugins and command line tools, it can easily handle the heavy lifting of almost any UI build process, including:

* Static site templating and generation
* CSS preprocessing
* JavaScript package management, transpilation, bundling and loading
* Image optimization
* Workflow and static asset management
* Local server/middleware creation 

### Installation
In order to run Skeletor from the command line, you'll want to install [Skeletor CLI](https://github.com/deg-skeletor/skeletor-cli) globally via NPM:

```shell
npm install -g @deg-skeletor/cli
```

*Hint: you may need to prefix this command with `sudo` (Mac OS, \*nix, etc.) or run your command shell as Administrator (Windows).*

## Project setup

### Working with an existing Skeletor project
Assuming the project has been set up with proper `package.json` and `skeletor.config.js` configurations, it's easy to start up an existing Skeletor project:

1. Change to the project's root directory (i.e., the directory that contains the project's `package.json` directory).
2. Type `npm install` to install project dependencies.
3. Type `skel` to run the project's "build" task.

That's it! Depending on the project, other tasks (such as `skel watch` or `skel serve`) or subtasks (i.e., CSS or JavaScript-specific subtasks) may also already be configured. But because Skeletor is modular, this will vary from project to project. Consult its `skeletor.config.js` file to know for sure.

### Starting a new Skeletor project

#### Manual configuration
Skeletor Core is just a delegator, which means it doesn't do a whole lot on its own. To make it useful, it needs:

*Plugins.* A typical Skeletor plugin does one thing and one thing well. That one thing could be anything. There are already plugins for file copying, PostCSS, Pattern Lab, Express, Rollup, and more. Go on, [have a look](#ecosystem-overview).

Plugins can be installed by listing them as [devDependencies](https://docs.npmjs.com/files/package.json#devdependencies) in your project's `package.json` file. Any plugins listed here will be installed to the project during an `npm install`.

*Configuration.* Skeletor needs a configuration object (stored in a `skeletor.config.js` file by default) to tell it what tasks and subtasks to run (based on the plugins you've installed), and how those tasks should work.

#### Automatic configuration via Skeletor Wizard
Yes, there is an auto-configurator called [Skeletor Wizard](https://github.com/deg-skeletor/skeletor-wizard) that's in active development. Yes, it kind of works already. No, we would not recommend using it in production quite yet. Sorry, Charlie.

## Ecosystem overview
All Skeletor repositories maintained by the DEG UI team are located at https://github.com/deg-skeletor/.

### Nuts and bolts
* [skeletor-core](https://github.com/deg-skeletor/skeletor-core/)
* [skeletor-cli](https://github.com/deg-skeletor/skeletor-cli/)
* [skeletor-wizard](https://github.com/deg-skeletor/skeletor-wizard/)

### Utilities
* [skeletor-plugin-watch](hhttps://github.com/deg-skeletor/skeletor-plugin-watch/)
* [skeletor-plugin-express](hhttps://github.com/deg-skeletor/skeletor-plugin-express/)
* [skeletor-plugin-copy](hhttps://github.com/deg-skeletor/skeletor-plugin-copy/)

### Language-specific plugins
* HTML/Static site generators
  - [skeletor-plugin-patternlab](https://github.com/deg-skeletor/skeletor-plugin-patternlab/)
* CSS
  - [skeletor-plugin-postcss](https://github.com/deg-skeletor/skeletor-plugin-postcss/)
  - [skeletor-plugin-stylelint](https://github.com/deg-skeletor/skeletor-plugin-stylelint/)
* JavaScript
  - [skeletor-plugin-rollup](https://github.com/deg-skeletor/skeletor-plugin-rollup/)
  - [skeletor-plugin-jspm](https://github.com/deg-skeletor/skeletor-plugin-jspm/)

### Developer tools
* [skeletor-sample-project](https://github.com/deg-skeletor/skeletor-sample-project/)
* [skeletor-plugin](https://github.com/deg-skeletor/skeletor-plugin/)
