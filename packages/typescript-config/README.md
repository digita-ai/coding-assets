
# Digita Typescript Configuration

This package provides a Typescript configurations, one for building and one for testing, used internally at Digita to adopt a uniform build mechanism.

## Installation

In each Typescript package, install `@useid/typescript-config` as a development dependency. From NPM v7 onwards, this will automatically add the following peer dependencies as well (if you use an earlier version, install these yourself). 

- `typescript`
- `@types/node`
- `ts-node`

Put the following in the `tsconfig.json`.

```
{
  "extends": "@useid/typescript-config/tsconfig.json",
  "compilerOptions": {
    "baseUrl": "./lib",
    "outDir": "./dist",
    "module": "commonjs"
  }
}
```

Put the following in the `tsconfig.spec.json`.

```
{
  "extends": "@useid/typescript-config/tsconfig.spec.json",
  "compilerOptions": {
    "baseUrl": "./lib",
    "outDir": "./dist",
    "module": "commonjs"
  },
  "include": [ 
      "lib" 
  ],
  "exclude": [
      "dist",
      "node_modules",
      "**/*.spec.ts"
  ]
}
```

In each of the above config files, change the `baseUrl` (base for relative imports) and `outDir` (output directory for builds) to the relevant paths, and change the necessary `include`/`exclude` globs. Also set the `module` type to `commonjs` for Node.js packages or to the desired ECMAScript version (e.g. `es2020`) for browser packages. Overwrite any of the preset directives if needed.