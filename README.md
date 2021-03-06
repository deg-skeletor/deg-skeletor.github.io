# Skeletor: modern, modular UI build tools

## Table of Contents
  1. [Getting started](#getting-started)  
    - [What is Skeletor?](#what-is-skeletor)  
    - [Installation](#installation)  
    - [Using the CLI](#using-the-cli)  
  2. [Project setup](#project-setup)  
    - [Starting a new Skeletor project](#starting-a-new-skeletor-project)  
      - [Automatic configuration via Orko](#automatic-configuration-via-orko)
      - [Manual configuration](#manual-configuration)
    - [Working with an existing Skeletor project](#working-with-an-existing-skeletor-project)  
  3. [Ecosystem overview](#ecosystem-overview)

## Getting started

### What is Skeletor?
Skeletor is a highly customizable UI build tool ecosystem, created and maintained by the [DEG](http://www.degdigital.com) UI team. 

On its own, [Skeletor Core](https://github.com/deg-skeletor/skeletor-core) is just the task runner of the bunch (albeit a very flexible and powerful one, if we do say so ourselves). When configured to use its [robust family of plugins and command line tools](#ecosystem-overview), it can easily handle the heavy lifting of almost any UI build process, including:

* Static site templating and generation
* CSS preprocessing
* JavaScript package management, transpilation, bundling and loading
* Image optimization
* Workflow and static asset management
* Linting and testing
* Local server/middleware hosting 

Skeletor's modularity and core API means anyone can write and configure their own plugins, too!

### Installation
In order to run Skeletor from the command line, you'll want to install [Skeletor CLI](https://github.com/deg-skeletor/skeletor-cli) globally via NPM:

```shell
npm install -g @deg-skeletor/cli
```

*Hint: you may need to prefix this command with `sudo` (Mac OS, \*nix, etc.) or run your command shell as Administrator (Windows).*

### Using the CLI
Once a [project has been set up](#project-setup), you can use the following syntax in the command line to control Skeletor:

```shell
skel
```
By default, typing `skel` with no arguments will run the first task in the config file's `tasks` array, and all of its configured subtasks. Subtasks will often be language-specific, such as `html`, `css` or `js`. The default task can be configured by adding `isDefaultTask: true` to the task you'd like to be default.

```shell
skel [taskName]
```
Typing `skel [taskName]` will run the specified task, as well as all of its configured subtasks. Available tasks will vary based on project configuration, but could include `build`, `serve`, `watch` or `export`.

```shell
skel [taskName] --only [subtaskA,subtaskB]
```
Typing `skel [taskName]` with the `--only` flag will only run the specified subtasks configured for the given task. For example, `skel export --only html,css` would only export HTML and CSS files, but would not export JavaScript files, even if this is a configured subtask of the `export` task.

```shell
skel [taskName] --except [subtaskA,subtaskB]
```
Typing `skel [taskName]` with the `--except` flag will run all configured subtasks, except for the specified subtask. For example, `skel build --except css` would build HTML and JavaScript files (assuming those are the configured subtasks of the `build` task), but would not build CSS files, even if this is a configured subtask.

## Project setup

### Starting a new Skeletor project

#### Automatic configuration via Orko
Orko is the scaffolding tool for Skeletor. By running Orko at the beginning of a project, you can build out an entire Skeletor-enabled UI project, preconfigured to work with the platform of your choice. All Orko documentation can be found on its [GitHub page](https://github.com/deg-skeletor/orko).

#### Manual configuration
Skeletor Core is just a task delegator, which means it doesn't do a whole lot on its own. To make it useful, it needs:

**Plugins.** A typical Skeletor plugin does one thing and one thing well. That one thing could be anything. There are already plugins for file copying, PostCSS, Pattern Lab, Express, Rollup, and more. Go on, [have a look](#ecosystem-overview).

Plugins can be installed by listing them as [devDependencies](https://docs.npmjs.com/files/package.json#devdependencies) in your project's `package.json` file. Any plugins listed here will be installed to the project during an `npm install`.

**Configuration.** Once plugins have been installed, Skeletor needs a configuration object (stored in a `skeletor.config.js` file by default) to tell it what tasks and subtasks to run, and how those tasks should work.

A Skeletor configuration object consists of an array of `tasks`. A `task` consists of either `plugins` or `subTasks`. A `subTask` is itself a `task` with its own `plugins` or `subTasks` properties.

A sample configuration object might look like the following:
```js
{
    tasks: [
        {
            /* a task to build all the code in a project */
            name: 'build',
            subTasks: [
                {
                    /* a sub-task to build the CSS code */
                    name: 'css', 
                    plugins: [
                        {
                            /* a plugin to process CSS via PostCSS */
                            name: '@deg-skeletor/plugin-postcss',
                            config: {
                                //Plugin-specific config
                            }
                        }
                    ]
                },
                {
                    /* a sub-task to build static files */
                    name: 'static',
                    plugins: [
                        {
                            /* a plugin to copy static files from one directory to another */
                            name: '@deg-skeletor/plugin-copy',
                            config: {
                                //Plugin-specific config
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

### Working with an existing Skeletor project
Assuming the project has been set up with proper `package.json` and `skeletor.config.js` configurations, it's easy to start up an existing Skeletor project:

1. Change to the project's root directory (i.e., the directory that contains the project's `package.json` directory).
2. Type `npm install` to install project dependencies.
3. Type `skel` to run the project's "build" task.

That's it! Depending on the project, other tasks (such as `skel watch` or `skel serve`) or subtasks (i.e., CSS or JavaScript-specific subtasks) may also already be configured. But because Skeletor is modular, this will vary from project to project. Consult its `skeletor.config.js` file to know for sure.

## Ecosystem overview
All Skeletor repositories maintained by the DEG UI team are located at [https://github.com/deg-skeletor/](https://github.com/deg-skeletor/).

### Nuts and bolts
* [skeletor-core](https://github.com/deg-skeletor/skeletor-core/)
* [skeletor-cli](https://github.com/deg-skeletor/skeletor-cli/)
* [skeletor-wizard](https://github.com/deg-skeletor/skeletor-wizard/)

### Utilities
* [skeletor-plugin-watch](https://github.com/deg-skeletor/skeletor-plugin-watch/)
* [skeletor-plugin-express](https://github.com/deg-skeletor/skeletor-plugin-express/)

### Language-specific plugins
* HTML/Static site generators
  - [skeletor-plugin-patternlab](https://github.com/deg-skeletor/skeletor-plugin-patternlab/)
* CSS
  - [skeletor-plugin-postcss](https://github.com/deg-skeletor/skeletor-plugin-postcss/)
  - [skeletor-plugin-stylelint](https://github.com/deg-skeletor/skeletor-plugin-stylelint/)
* JavaScript
  - [skeletor-plugin-rollup](https://github.com/deg-skeletor/skeletor-plugin-rollup/)
  - [skeletor-plugin-jspm](https://github.com/deg-skeletor/skeletor-plugin-jspm/)
* Static assets
  - [skeletor-plugin-copy](https://github.com/deg-skeletor/skeletor-plugin-copy/)

### Developer tools
* [skeletor-sample-project](https://github.com/deg-skeletor/skeletor-sample-project/)
* [skeletor-plugin](https://github.com/deg-skeletor/skeletor-plugin/)
