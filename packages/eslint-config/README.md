
# Digita ESLint Configuration

This package provides a shareable ESLint configuration, used internally at Digita to adopt a uniform clean code style.

## Installation

In the root of your (mono)repo, install `@useid/eslint-config` as a development dependency. From NPM v7 onwards,, this will automatically add the following peer dependencies as well (if you use an earlier version, install these yourself). 

- `eslint`
- `eslint-plugin-deprecation`
- `eslint-plugin-import`
- `eslint-plugin-jest`
- `eslint-plugin-jest-formatting`
- `eslint-plugin-jsdoc`
- `eslint-plugin-no-null`
- `eslint-plugin-prefer-arrow`
- `eslint-import-resolver-typescript`
- `@typescript-eslint/eslint-plugin`
- `lint-staged`

When working in monorepo, install `eslint` as a development dependency in each subrepo as well.

In the root `package.json`, add the following `eslintConfig` and `lint-staged` objects.

```
"eslintConfig": {
  "extends": [
    "@useid/eslint-config"
  ]
}
```

```
"lint-staged": {
  "**/*.(js|ts)": [
    "eslint --fix"
  ]
}
```

## Auto-fix on save

Auto-fix-on-save functionality can be enabled with VSCode's `dbaeumer.vscode-eslint` plugin, using the following settings. It is enabled by default in our workspace files.

```
{
  "eslint.format.enable": true,
  "editor.defaultFormatter": "dbaeumer.vscode-eslint",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## Prettier & EditorConfig

The Prettier and EditorConfig projects also provide ways to ensure a uniform coding style. Often these are held to provide the visual style, limiting ESLint to lint for good coding practices. However, ESLint provides a lot more possibilities to fine-tune the visual aspect than either of these projects do. Moreover, all functionality provided by these projects can be subsumed by ESLint rules. We therefore adopt ESLint as a single point of truth. Rules subsuming functionality of Prettier (`P`) and EditorConfig (`EC`) have been indicated as such in comments.


## Only lint staged files

For efficiency, either in your scripts or in you git hooks, you can run `lint-staged`, which is initially set up for `.ts` and `.js` files with `eslint`, but can be extended with different commands for other extensions.
