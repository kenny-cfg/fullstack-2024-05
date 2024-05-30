# Node and npm

## Basic usage

### To initialize a new `npm` project

* Make a new folder, either by cloning a brand new repository, or manually making a new folder locally (using `mkdir`, Finder, Windows Explorer, etc)
* Navigate to your new folder in the terminal
* `npm init`
* Answer the questions
  * You will probably just take the defaults for now. When you're a bit more experienced, you can delve into the meanings of the questions that are being asked.
* You'll notice a new `package.json` in the root of your project

### Installing a package

* Decide if you want to install as a dev dependency, or a prod dependency
  * Generally, dev dependencies are the ones that are only required while in development
  * If in doubt, look at the README.md file on the dependency you're looking at: that should guide you to whether you should be using it as a dev dependency or not
* Install a library using `npm install <library_name>` (for prod dependencies), or `npm install <library_name> --save-dev` (for dev dependencies)
* You notice a new entry in `package.json` for your library, a `package-lock.json` file which specifies exactly what versions of which libraries are installed and a `node_modules` folder where your libraries are stored

### Deleting a package

You can use `npm remove <library_name>` to remove an installed package. You can also just remove the relevant line in `package.json` and [refresh your virtual environment](#refreshing-your-virtual-environment)

### Refreshing your virtual environment

Sometimes your virtual environment can get corrupt (usually because your `package.json` has been updated without using `npm` directly, which usually happens by manual editing of the file, or pulling in changes from `git` that someone else has made).

`npm install` will install any packages that are missing from your `node_modules` folder.

if your `node_modules` needs a complete refresh (e.g. some of the files have become corrupt, you've accidentally manually edited the files inside `node_modules`, you've deleted a line in your `package.json`), a full refresh might be necessary.
* `rm -rf node_modules` to remove the `node_modules` folder
* `npm install` will read your `package.json` and install the latest version of all the packages specified within, and update your `package-lock.json` file
* `npm ci` will ready your `package-lock.json` file and install exactly the versions that are specified within

Generally, `npm ci` is only used on automatic build servers (or *continuous integration* servers): us mere mortals should keep our depenedencies up-to-date so that we reduce any vulnerabilities manually. If in doubt, `npm install`