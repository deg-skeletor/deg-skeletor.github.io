# Skeletor: modern, modular UI build tools
Skeletor is a highly customizable UI build tool ecosystem, created by the [DEG](http://www.degdigital.com) UI team. 

On its own, [Skeletor Core](https://github.com/deg-skeletor/skeletor-core) is just the task runner of the bunch (albeit a very configurable one, if we do say so ourselves). When configured to use its robust family of plugins and command line tools, it can easily handle the heavy lifting of almost any UI build process, including:

* Static site templating and generation
* CSS preprocessing
* JavaScript package management, transpilation, bundling and loading
* Image optimization
* Workflow and static asset management
* Local server/middleware creation 

## Table of Contents
  1. [Getting started](#getting-started)  
    - [Installation](#installation)  
    - [Working with an existing Skeletor project](#working-with-an-existing-skeletor-project)  
    - [Starting a new Skeletor project](#starting-a-new-skeletor-project)  

## Getting started

### Installation
In order to run Skeletor from the command line, you'll want to install [Skeletor CLI](https://github.com/deg-skeletor/skeletor-cli) globally via NPM:

```shell
npm install -g @deg-skeletor/cli
```

*Hint: you may need to prefix this command with `sudo` (Mac OS, \*nix, etc.) or run your command shell as Administrator (Windows).*

Skeletor CLI will automatically install Skeletor Core and [Skeletor Wizard](https://github.com/deg-skeletor/skeletor-wizard) as dependencies.

### Working with an existing Skeletor project
Assuming the project has been set up with proper `package.json` and `skeletor.config.js` configurations, it's easy to start up an existing Skeletor project:

1. Change to the project's root directory (i.e., the directory that contains the project's `package.json` directory).
2. Type `npm install` to install project dependencies.
3. Type `skel` to run the project's "build" task.

That's it! Depending on the project, other tasks (such as `skel watch` or `skel serve`) or subtasks (such as HTML, CSS or JS-specific taks) may also already be configured. But because Skeletor is modular, this will vary from project to project. Consult its `skeletor.config.js` file to know for sure.

### Starting a new Skeletor project