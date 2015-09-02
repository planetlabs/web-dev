# Atom Editor

Download and install Atom from https://atom.io/.  See below for recommended packages and settings.  Find settings for individual packages on the "Packages" panel in Atom's settings (`⌘,`).

## Packages

### `linter-eslint`

Install the [`linter`](https://atom.io/packages/linter) package in addition to [`linter-eslint`](https://atom.io/packages/linter-eslint).  See the [guide on ESLint](../tools/eslint.md) for additional details on the linter and using a shared linter configuration.

Settings:

 * **Disable When No Eslintrc File In Path** - Checking this keeps ESLint from running when you open projects without a `.eslintrc` file.  (`disableWhenNoEslintrcFileInPath: true` in `config.scon`.)

### `language-babel`

[Grammar](https://atom.io/packages/language-babel) for JSX, ES2015, and more.  Especially useful if you want nice syntax highlighting on React projects that use JSX.

Settings:

 * Turn off everything about transpiling, unless you really want your editor to transpile - typically this is left to a separate build step.  (`transpileOnSave: false` `babelMapsAddUrl: false` `createTargetDirectories: false` in `config.scon`.)

### `docblockr`

[Makes it easier](https://atom.io/packages/docblockr) to write nicely formatted comment blocks.
