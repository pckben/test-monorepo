# test-monorepo

How do we get here?

```
$ mkdir test-monorepo
$ cd test-monorepo
$ yarn set version berry
$ yarn init
$ yarn add -D typescript
$ yarn dlx @yarnpkg/sdks vscode
$ code .
```

- Ensure that this folder is not empty: `.yarn/sdks/typescript`
- Press `ctrl + shift + p`
- Enter `TypeScript: Select TypeScript Version...`
- Choose `Use Workspace Version`
- Open `package.json` and add the following:

```
{
  ...
  "workspaces": [
    "packages/*"
  ]
  ...
}
```

Now create the packages:

```
$ mkdir -p packages/my-lib packages/my-lib-examples
$ cd packages/my-lib
$ yarn init
$ cd ../my-lib-examples
$ yarn init
$ yarn add my-lib
```

Now my-lib-examples can reference exports from my-lib and VSCode can follow the definitions.

Final conclusions: sometimes it didn't work, I still don't know why. Perhaps due to a global cache somewhere in the system.