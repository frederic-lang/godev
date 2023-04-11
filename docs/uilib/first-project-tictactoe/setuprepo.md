---
sidebar_position: 2
---

# Set up your repository

1. Create the folder of your project

```bash
mkdir tictactoe
```

2. Init the npm project

```bash
npm init
```

Choose `0.0.1` version as your package is in _alpha_ version. We will go on `1.*.*` once your project is in _stable_ version.

Set entry point to `src/index.js` and not `index.js` since `src` will be our main folder to develop our library.

Edit your `package.json` file and add

```json
"type" : "module"
```

field in order to define your package as an ES module.

:::tip
you can define your package as ES or CommonJs module, ES module are now more spread and used by the community, it would not make compatibility issue (apart internet explorer).
:::

You can copy the ISC [license](https://en.wikipedia.org/wiki/ISC_license) as a LICENSE file in your folder. It will confirm your are the author of the project.

3. Import Rollup & React dependencies

```bash
pnpm i -D rollup
```

4. set up the Vite app

```bash
mkdir app
cd app
pnpm create vite@latest vite-project --template react
pnpm i
```

5. define Vite config

in order to import the library into your app, you need to add an _alias_ field to your `defineConfig`.

```js
//vite.config.js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { resolve } from "path";

// https://vitejs.dev/config/
export default defineConfig({
  resolve: {
    alias: [
      {
        find: "lib",
        replacement: resolve(__dirname, "../", "lib"),
      },
    ],
  },
  plugins: [react()],
});
```
