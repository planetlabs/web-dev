# Node

## Installation

You should be able to find an installer for your system by visiting https://nodejs.org/.

Installing nodejs in Ubuntu requires adding a PPA, but for your Vagrant or Productions server provisioning, you can use the [nodejs ansible role](https://github.com/planetlabs/planet_roles/tree/master/nodejs) in planet_roles.

## Managing multiple versions of Node

When working with a variety of Node-based projects, you may find the need to have multiple versions of Node installed.  If you find yourself in this situation, you can use the [Node Version Manager](https://github.com/creationix/nvm) (`nvm`).  `nvm` provides an easy way to install new versions, switch between versions, and manage which version you run by default.  See the [project readme](https://github.com/creationix/nvm) for easy instructions on getting set up.  This works even if you have already installed Node with the official nodejs.org installers.

After installing `nvm`, you can configure which version runs by default by adding a line like the following to your `~/.profile`:

    nvm use 0.12 > /dev/null

Note that this assumes you have the target version installed (e.g. with `nvm install 0.12`).

## `npm`

Your installation of Node comes with `npm` as a package manager.  Typically, `npm` is used to install or publish packages hosted in the https://www.npmjs.com/ registry.  You should be able to find a front- or back-end package to meet virtually any development need in the repository.  `npm` can also be used to install packages from a local filesystem or from GitHub.

Since `npm` may be updated more often that you install new versions of Node, you can use `npm` to update itself.

    npm update --global npm

### Installing project dependencies

After creating a directory for your project, the first thing you'll want to do is create a `package.json` file that will list your project dependencies (among other things).  Run the following and answer the prompts to create a `package.json` file:

    npm init

Even if you don't plan on publishing your project to the https://www.npmjs.com/ registry, you'll want to have this `package.json` file.  If you are concerned about accidentally publishing a package, you can add `"private": true` to your `package.json` to ensure that it is not published publicly.  The registry also supports publishing [private packages](https://www.npmjs.com/private-modules).

### Development dependencies

Development dependencies are things like a test runner, linter, minifier, etc. that you use in development, but are not required by any consumers of your package.  Development dependencies go in the `devDependencies` section of your `package.json` file.  You can install a package and save it as a development dependency with the following command (for the [`eslint` package](https://www.npmjs.com/package/eslint)):

    npm install --save-dev eslint

One of the nice things about `npm` is that it installs packages **locally** by default.  This means that you can have many projects living in harmony on your system without conflicting global package versions.  Your dependencies are saved in the `node_modules` directory at the root of your project.  You'll want to add `/node_modules/` to your project's `.gitignore` to keep dependencies out of a Git repository.

### Runtime dependencies

If your project has dependencies that are required at runtime, you can install them as above, but with the `--save` flag instead of `--save-dev`.  These depdendencies will be listed in the `dependencies` section of your `package.json`.  Typically, you'll only have runtime dependencies when building services or desktop apps - browser-based applications will have a build step where you bundle your dependencies for deployment.

### Global depdendencies

As mentioned above, `npm` installs packages locally by default.  In some cases, you might want to have a Node based utility available globally.  However, this is rare, and global installs should be avoided if possible.  Test runners, linters, minifiers, etc. can all be installed locally and are still accessible from your editor or when running `package.json` scripts or other build steps.

Some exceptions to the "avoid global installs" recommendation:

  * [`node-inspector`](https://www.npmjs.com/package/node-inspector) - Great visual debugger for Node based services/apps (uses Blink Developer Tools).
  * Open a pull request if you have other suggestions.
