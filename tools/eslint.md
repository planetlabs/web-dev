# ESLint

[ESLint](http://eslint.org/) is an extremely flexible, unopinionated-by-default linter for JavaScript.  You configure [linter rules](http://eslint.org/docs/rules/) in a `.eslintrc` file at the root of your project.  ESLint can be run before (or as part of) your tests to ensure that your project standards are followed.  In addition, you can configure your editor to run the rules, helping you avoid common mistakes and conform to coding standards as you develop.

## `eslint-config-planet`

The [`eslint-config-planet` package](https://github.com/planetlabs/eslint-config-planet) is a shared ESLint configuration that suggests rules for all Planet web development projects.  You can install the shared configuration and ESLint with the following:

    npm install --save-dev eslint eslint-config-planet

After that, add a `.eslintrc` file to the root of your project that looks like this:

```json
{
  "extends": "planet"
}
```

If there are rules that you cannot follow (or otherwise disagree with), you can override them in your `.eslintrc` file.  For example, if you want your project to allow mixed quotes (instead of enforcing single quotes), your `.eslintrc` could look like this:

```json
{
  "extends": "planet",
  "rules": {
    "quotes": 0
  }
}
```

(This turns off the [`quotes` rule](http://eslint.org/docs/rules/quotes).)

See the [`eslint-config-planet` readme](https://github.com/planetlabs/eslint-config-planet) for more detail on the available profiles.  And please submit a pull request if there is a new profile that you think would be worth supporting.

## Running the linter

After installing and configuring ESLint, you'll want to run it on your JavaScript source files.  Since you've got a locally installed version of `eslint`, a good way to run it is by adding a [`package.json` script](https://docs.npmjs.com/misc/scripts) - all locally installed binaries are available on your path when running an `npm` script.

If you don't already have any tests for your project, the first thing you might want to do is run the linter as a testing step.  You can do this by adding the following to your `package.json`:

```json
  "scripts": {
    "test": "eslint src"
  }
```

Now you can run the linter on all the files in your `src` directory like this:

    npm test

As you add real tests to your project, you can move linting to a "pretest" script.  For example, assuming you use [`mocha`](http://mochajs.org/) to run your tests, your `package.json` scripts might look like this:

```json
  "scripts": {
    "pretest": "eslint src",
    "test": "mocha"
  }
```

Now `npm test` will run the inter first, and if that succeeds, `mocha` will run next.

## Editor configuration

You can set up your editor to run ESLint as you develop.  See the [editors page](../editors/) to find detail on configuring your favorite editor.
