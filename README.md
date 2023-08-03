
# use.id Coding Assets Repository

This repository provides a standard configuration for repositories and packages, used internally at use.id and Digita to adopt a uniform clean coding environment. It contains the following configuration packages:

- [`commitlint-config`](./packages/commitlint-config#readme)
- [`eslint-config`](./packages/eslint-config#readme)
- [`jest-config`](./packages/jest-config#readme)
- [`lerna-config`](./packages/lerna-config#readme)
- [`typescript-config`](./packages/typescript-config#readme)

## Installation

The installation instructions of each configuration can be found in the separate packages of this repo. Make sure your (mono)repo root contains an `.nvmrc` containing the desired version of Node.js (in our case: `14`), and an `.npmrc` with the following NPM configuration, containing a token for our Github Packages repository.

```
registry=https://registry.npmjs.org/

@useid:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${NPM_TOKEN}
always-auth=true
```

## Git hooks

The Git hooks of this repository also serve as an instantly copyable base for new (mono)repos. We use Husky to share them via Git. Set it up by installing `husky` in the repo root and adding `husky install` as `postinstall` script to the root `package.json`. Then copy the `.husky` directory from this repo, and make sure to make the hooks themselves executable (e.g. `chmod a+x .husky/*`).
