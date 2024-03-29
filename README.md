# Lyra

This repo is constructed using yarn workspaces and consists of the 4 sections:

- the browser extension (`/extension`)
- the client-facing SDK (`/@stellar/lyra-sdk`)
- the docs (`/docs`)
- some shared files that the above use (`/@lyra/*`)

## Getting Started

```
yarn
yarn start
```

This will start up multiple watching builds in parallel:

- The `@stellar/lyra-api` npm module
- The docs, serving on `localhost:3000`
- A dev server with the webapp running in the extension, serving on
  `localhost:9000`
- The actual built extension, able to be installed in Chrome, in `build/`

Each of these will build in response to editing their source.

These can be started individually with `yarn start:\<workspace name\>` where
`\<workspace name\>` is one of:

- `lyra-api`
- `docs`
- `extension`

```
yarn build
```

This will produce final output for the docs, the `@stellar/lyra` npm module, and
the extension.

`yarn build:\<workspace name\>`, like the equivalent start commands, will build
an individual workspace.

### Useful URLs:

[The popup webapp](http://localhost:9000/#/)

[The `getPublicKey` playground](http://localhost:3000/docs/playground/getPublicKey)
[The `signTransaction` playground](http://localhost:3000/docs/playground/signTransaction)

It's important to note that these two won't interact with the _dev server_ popup
UI on `localhost:9000` — you'll need to re-install the unpacked extension each
time you make a change.

## Importing a workspace

In some cases, you will want to import a workspace into another. For example, in
`extension` we need to import `@lyra/constants`. To do this, simply add
`@lyra/constants` to the dependencies list in package.json in `extension`. Yarn
symlinks all the workspaces, so doing so will allow you to import files from the
`@lyra/constants` workspace as if it were a published npm package.
