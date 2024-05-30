# TypeScript setup

TypeScript is a very useful addition to the JavaScript ecosystem, but can be a little fiddly to set up. This is complicated by the fact that `npm` is often installed in such a way that you cannot install programs globally (not looking at any system in particular, Apple). Moreover, the most recent advice from `node` themselves is to use `npx` to run `npm` commands rather than installing them globally.

## Why you should not install stuff globally

* Node [themselves](https://docs.npmjs.com/downloading-and-installing-packages-globally) don't recommend it
* Other developers touching your code will most likely also have to globally install packages, which may not be possible
* It may not be possible to install packages globally on your machine because
  * It's really fiddly
  * You don't have permissions (this is often true on corporate machines)

## New TypeScript project setup

* Set up a new [`npm` project](./npm.md#to-initialize-a-new-npm-project)
* Navigate to your project
* `npm install typescript --save-dev` to install the TypeScript library to your project
* `npm install ts-node --save-dev` to install the direct `ts-node` engine to your project (so you can run your code without having to compile it to JavaScript first)
* Add a `start` script to your `package.json` with value `ts-node ./index.ts` so that your `package.json` looks like this
```
...
  
  "scripts": {
    "start": "ts-node ./index.ts",
    "test": "echo \"Error: no test specified\" && exit 1"
...
```
* Add an `index.ts` file at the root of your repository, and fill it with wonderful, delightul code
* `npm start` will run your code

## TypeScript compiler configuration

Often, you will require tighter control over how your TypeScript project behaves. This is probably more relevant when you want to productionize your code (i.e. translate it into JavaScript to run in the target environment), but you mostly won't need to do this.

Once you have your TypeScript project set up as [above](#new-typescript-project-setup), you can simply issue a `tsc` command to initialize the configuration.

```
npx tsc --init
```

This will create a `.tsconfig` file in the root of your repository. There are approximately 7,000 options in this file, and playing with them can be... haphazard. You generally don't have to touch this file.
