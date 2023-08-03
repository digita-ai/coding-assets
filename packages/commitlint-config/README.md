
# Digita Commitlint Configuration

This package provides a shareable Commitlint configuration, used internally at Digita to adopt a uniform commit message style.

## Installation

In the root of your (mono)repo, install `@useid/commitlint-config` as a development dependency. From NPM v7 onwards,, this will automatically add `@commitlint/cli` as a peer dependency as well (if you use an earlier version, install this yourself). Add the following `commitlint` object to the `package.json`.

```
"commitlint": {
    "extends": [
        "@useid/commitlint-config"
    ]
}
```

In a pre-commit git hook (e.g. with Husky), call `./node_modules/.bin/commitlint --edit $1`, or use Commitlint in any other way that fits your project. For an example of a git hook, check the `.husky/pre-commit` script of this repository.