![ohmyfetch](https://user-images.githubusercontent.com/904724/101663230-bb578c80-3a4a-11eb-89eb-14cd3e08dd8c.png)

# 😱 ohmyfetch

[![npm version][npm-version-src]][npm-version-href]
[![Github Actions][github-actions-src]][github-actions-href]
[![Codecov][codecov-src]][codecov-href]
[![bundle][bundle-src]][bundle-href]
<!-- [![npm downloads][npm-downloads-src]][npm-downloads-href] -->

## 🚀 Quick Start

Install:

```bash
# npm
npm i ohmyfetch

# yarn
yarn add ohmyfetch
```

Import:

```js
// Universal (requires global.fetch)
import { $fetch } from 'ohmyfetch'

// NodeJS / Isomorphic
import { $fetch } from 'ohmyfetch/node'

// NodeJS / Isomorphic (CommonJS)
const { $fetch } = require('ohmyfetch/node')
```

![oh-my-fetch](https://media.giphy.com/media/Dn1QRA9hqMcoMz9zVZ/giphy.gif)


## Why?

### ✔️ Parse Response

- Smartly parse JSON and native values like `true` (using [destr](https://github.com/nuxt-contrib/destr))
- Fallback to text if cannot parse
- Secure against prototype pollution

```js
const { users } = await $fetch('/api/users')
```

### ✔️ Handle Errors

- Automatically throw errors when `response.ok` is `false`
- Friendly error message with compact stack (hiding internals)
- Parsed error body is available with `error.data`

```ts
await $fetch('http://google.com/404')
// FetchError: 404 Not Found (http://google.com/404)
//     at async main (/project/playground.ts:4:3)
```

### ✔️ Type Friendly

- Response can be type assisted

```ts
const { article } = await $fetch<Article>(`/api/article/${id}`)
// Auto complete working with article.id
```

### ✔️ Support baseURL

- Allow making factory functions to add baseURL
- Prepend baseURL with respecting trailing/leading slashes and query params for baseURL (using [ufo](https://github.com/nuxt-contrib/ufo))

```js
await $fetch('/config', { baseURL })
```

### ✔️ Universal

Supporting browsers, workers and NodeJS targets

## 📦 Bundler Notes

- All targets are exported with Module and CommonJS format and named exports
- No export is transpiled for sake of Modern syntax
  - You probably need to transpile `ohmyfetch` package with babel for ES5 support
- You need to polyfill `fetch` global for supporting legacy browsers like using [unfetch](https://github.com/developit/unfetch)

## ❓ FAQ

**Why export is called `$fetch` instead of `fetch`?**

Using the same name of `fetch` can be confusing since API is different but still it is a fetch so using closest possible alternative.

**Why not having default export?**

Default exports are always risky to be mixed with CommonJS exports.

This also guarantees we can introduce more utils without breaking the package and also encourage using `$fetch` name.

**Why not transpiled?**

By keep transpiling libraries we push web backward with legacy code which is unneeded for most of the users.

If you need to support legacy users, can optionally transpile the library to build pipelines.

## License

MIT. Made with 💖

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/ohmyfetch?style=flat-square
[npm-version-href]: https://npmjs.com/package/ohmyfetch

[npm-downloads-src]: https://img.shields.io/npm/dm/ohmyfetch?style=flat-square
[npm-downloads-href]: https://npmjs.com/package/ohmyfetch

[github-actions-src]: https://img.shields.io/github/workflow/status/nuxt-contrib/ohmyfetch/ci/main?style=flat-square
[github-actions-href]: https://github.com/nuxt-contrib/ohmyfetch/actions?query=workflow%3Aci

[codecov-src]: https://img.shields.io/codecov/c/gh/nuxt-contrib/ohmyfetch/main?style=flat-square
[codecov-href]: https://codecov.io/gh/nuxt-contrib/ohmyfetch

[bundle-src]: https://img.shields.io/bundlephobia/minzip/ohmyfetch?style=flat-square
[bundle-href]: https://bundlephobia.com/result?p=ohmyfetch

