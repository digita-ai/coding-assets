
# Digita Lerna Configuration

This package provides an extendable Lerna configuration, used internally at Digita to adopt a uniform monorepo setup.

## Installation

In the root of your (mono)repo, install `@useid/lerna-config` as a development dependency. From NPM v7 onwards, this will automatically add `lerna` as a peer dependency as well (if you use an earlier version, install this yourself). Also add a `lerna.json` file extending this configuration and containing an initial version number (see example below). Lerna will find this and fill in the whole base config on the first release, so when updating the version of this config, you have to explicitly add the `extends` property again.

```
{
    "extends": "@useid/lerna-config",
    "version": "0.1.0"
},
```
