# Lage monorepo starter project

This repo contains a monorepo built using [lage](https://microsoft.github.io/lage/). It contains two packages `a` and `b`. This utilizes `npm workspaces`.

You can create a similar repo by executing the following command on your terminal:

```bash
npm init
npm init -w ./packages/a
npm init -w ./packages/b
npm install
npm install lage
npx lage init
```

`lage` generates a default config file `lage.config.js` which looks like the following:

```js
module.exports = {
 "pipeline": {
   "build": ["^build"],
   "test": ["build"],
   "lint": []
 }
};
```

## Customize the root level `package.json`

Modify the `package.json` to use lage scripts.

```json
{
 "name": "getting-started-with-lage",
 "scripts": {
   "build": "lage build",
   "lint": "lage lint",
   "test": "lage test"
 },
 "workspaces": [
   "packages/a",
   "packages/b"
 ]
}
```

## Add some test script

Install `Jest` to run the tests.

```bash
npm install --save-dev jest -w a
npm install --save-dev jest -w b
```

Now add some testable code within both packages. Invoking `npm test` should now execute the the pipeline, and cache the results of the individual tasks.



