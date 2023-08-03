
# Digita Jest Configuration

This package provides a Jest preset configuration, used internally at Digita to adopt a uniform testing habit.

## Installation

In the root of your (mono)repo, install `@useid/jest-config` as a development dependency. From NPM v7 onwards,, this will automatically add the following peer dependencies as well (if you use an earlier version, install these yourself). 

- `jest`
- `jest-extended`
- `jest-mock-extended`
- `jest-coverage-thresholds-bumper`
- `@types/jest`
- `ts-jest`

It will also suggest the following optional dependencies.

- `@testing-library/jest-dom`
- `jest-fetch-mock`

When working in monorepo, install `jest` and `jest-coverage-thresholds-bumper` as development dependencies in each subrepo as well.

In each `package.json`, add the following `jest` object.

```
"jest": {
    "coverageThreshold": {
        "global": {
            "branches": 0,
            "functions": 0,
            "lines": 0,
            "statements": 0
        }
    },
    "displayName": "core",
    "preset": "@useid/jest-config",
    "rootDir": "lib"
}
```

Coverage thresholds will automatically be raised when running tests. Optionally, you can tell Jest to look for tests in multiple directories by setting and extending the `"roots": [ "<rootDir>" ]` list. You can also switch testing environment between `node` and `jsdom` with `"testEnvironment": "node"`, and set configuration for these environments with `"testEnvironmentOptions": { /* ... */ }`.

## Testing from the root of a monorepo

When using git hooks in a monorepo, you might want to run Jest from the root `node_modules` of your repository, without having the test search for relative paths in the wrong place. To prevent this, add the following `jest` object to the root `package.json`, pointing to all packages where you wish to run Jest.

```
"jest": {
    "preset": "@useid/jest-config",
    "projects": [
        "./packages/*/package.json"
    ]
}
```