# Package Management

At some point in your programming career, you'll want to ~~cheat~~ use other people's code in your own project. node has a very large repository of code at your disposal that you can use for all manner of things. By far the most extensive repository (for all intents and purposes, you can regard this as a monopoly) is [npm](https://www.npmjs.com/)

This guide is supposed to be an introduction to 'vanilla' package management using `npm` for node. There are fancier package management tools out there (e.g. [`yarn`](https://yarnpkg.com/) for node), but both plain-old `npm` is widely used (and you are required to understand this before you use anything else).

The concepts outlined below are general enough to apply to almost any modern programming language, with a specific focus on how things work for node.

## How do they work?

Anything other than the most basic of projects will require you to bring in libraries from third-parties. In the root directory of your project, there might be a file that defines what libraries are needed to run your code, and what versions are acceptable (typically also a `lock` file that **locks in** the ***exact*** version of a module).

There are two approaches to where the code for these third-party libraries are stored.
* In a central, but local repository (e.g. for `mvn` in the Java world, all the third-party code can be found in `~/.m2/repository`)
* In a local folder (for Python in a folder called *the virtual environment*, in node a folder called `node_modules`)

In this course, you should only be concerned about the second approach as that is the one used for the languages that you are using. However, at some point in your career, you'll probably have to deal with languages that follow the first approach.
