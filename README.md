# Svelte TypeScript Template

## Feature Support

- [x] TypeScript
- [x] SCSS/SASS
- [x] VS Code

## Use TypeScript in Svelte

### Create App `svelte-typescript-app`

```bash
npx degit sveltejs/template svelte-typescript-app
```

```bash
cd svelte-typescript-app
```

### Setup to TypeScript

```bash
node scripts/setupTypeScript.js
```

### Adding TypeScript to an existing project

```bash
npm i -D tslib @rollup/plugin-typescript @tsconfig/svelte typescript svelte-preprocess svelte-check
```

### Change file `rollup.config.js`

```js
// import sveltePreprocess from 'svelte-preprocess'; // Remove
import autoPreprocess from 'svelte-preprocess'; // Add
import typescript from '@rollup/plugin-typescript'; // Add

export default {
  plugins: [
    svelte({
      // preprocess: sveltePreprocess({ sourceMap: !production }), // Remove
      preprocess: autoPreprocess(), // Add
    }),
    typescript({ sourceMap: !production }), // Add
  ],
};
```

### In file `rollup.config.js` Must have

```json
{
  "extends": "@tsconfig/svelte/tsconfig.json",

  "include": ["src/**/*", "src/node_modules"],
  "exclude": ["node_modules/*", "__sapper__/*", "public/*"]
}
```

### Editor Support (Install Extension)

Any editor using an LSP can be supported. The [VS Code extension](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) has been our primary focus, but there is work in progress on Atom, and Vim via coc-svelte has been updated with the latest LSP.

After install extension. adjust your VS Code settings

```json
"[svelte]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "svelte.svelte-vscode"
  },
```

### CI Checks

```bash
npx svelte-check
```

### Run App

```bash
npm run dev
```

see <http://localhost:8080>

## If see error close VS Code and reopen

Ref:
[Svelte <3 TypeScript](https://svelte.dev/blog/svelte-and-typescript)
[VS Code format svelte](https://github.com/sveltejs/language-tools/issues/225#issuecomment-673271334)

## Use Scss in Svelte

### Install package Node V14 use node-sass@4

```bash
npm i -D node-sass@4
```

### Setting up a svelte-config.js

```js
const preprocess = require('svelte-preprocess');

module.exports = {
  preprocess: preprocess(),
};
```

### Restart the svelte language server

Restart the svelte language server
You will need to tell svelte-vscode to restart the svelte language server in order to pick up the new configuration.

Hit `ctrl-shift-p` or `cmd-shift-p` on mac, type `svelte restart`, and select `Svelte: Restart Language Server`. Any errors you were seeing should now go away and you're now all set up!

### Set the Format on `<style>` Tags

```scss
<style lang="scss">
/* ... */
</style>
```

Ref:
[SCSS/Less Support](https://github.com/sveltejs/language-tools/blob/master/docs/preprocessors/scss-less.md)
[Add SASS to Svelte JS with svelte-preprocess](https://linguinecode.com/post/add-sass-svelte-js)

_Psst — looking for a more complete solution? Check out [SvelteKit](https://kit.svelte.dev), the official framework for building web applications of all sizes, with a beautiful development experience and flexible filesystem-based routing._

_Looking for a shareable component template instead? You can [use SvelteKit for that as well](https://kit.svelte.dev/docs#packaging) or the older [sveltejs/component-template](https://github.com/sveltejs/component-template)_

---

## svelte app

This is a project template for [Svelte](https://svelte.dev) apps. It lives at <https://github.com/sveltejs/template>.

To create a new project based on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit sveltejs/template svelte-app
cd svelte-app
```

_Note that you will need to have [Node.js](https://nodejs.org) installed._

## Get started

Install the dependencies...

```bash
cd svelte-app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:8080](http://localhost:8080). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

If you're using [Visual Studio Code](https://code.visualstudio.com/) we recommend installing the official extension [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode). If you are using other editors you may need to install a plugin in order to get syntax highlighting and intellisense.

## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).

## Single-page app mode

By default, sirv will only respond to requests that match files in `public`. This is to maximise compatibility with static fileservers, allowing you to deploy your app anywhere.

If you're building a single-page app (SPA) with multiple routes, sirv needs to be able to respond to requests for _any_ path. You can make it so by editing the `"start"` command in package.json:

```js
"start": "sirv public --single"
```

## Using TypeScript

This template comes with a script to set up a TypeScript development environment, you can run it immediately after cloning the template with:

```bash
node scripts/setupTypeScript.js
```

Or remove the script via:

```bash
rm scripts/setupTypeScript.js
```

If you want to use `baseUrl` or `path` aliases within your `tsconfig`, you need to set up `@rollup/plugin-alias` to tell Rollup to resolve the aliases. For more info, see [this StackOverflow question](https://stackoverflow.com/questions/63427935/setup-tsconfig-path-in-svelte).

## Deploying to the web

### With [Vercel](https://vercel.com)

Install `vercel` if you haven't already:

```bash
npm install -g vercel
```

Then, from within your project folder:

```bash
cd public
vercel deploy --name my-project
```

### With [surge](https://surge.sh/)

Install `surge` if you haven't already:

```bash
npm install -g surge
```

Then, from within your project folder:

```bash
npm run build
surge public my-project.surge.sh
```
