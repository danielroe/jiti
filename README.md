# jiti

> Runtime typescript and ESM support for Node.js (CommonJS)

[![version][npm-v-src]][npm-v-href]
[![downloads][npm-d-src]][npm-d-href]
[![size][size-src]][size-href]

## Features

- Stable typescript and esm syntax support
- Provide sync interface to replace require
- Super slim and zero dependency
- Syntax detect to avoid extra transform
- CommonJS cache integration

## Usage

```js
const jiti = require('jiti')(__filename)

jiti('./path/to/file.ts')
```

## Compared to Alternatives

### [`standard-things/esm`](https://github.com/standard-things/esm)

- `+` Much more stable thanks to babel
- `+` Less low level operations
- `+` Typescript support
- `-` Slower
- `-` No source-map support at the moment

### [`babel-register`](https://babeljs.io/docs/en/babel-register)

- `+` Smaller install size (~1M vs ~11M with same plugins)
- `+` Configured out of the box
- `+` Smart syntax detect to avoid unnecessary trnaspilation
- `+` Does not ignores `node_modules`. ESM everywhere yay!
- `+` Embeddable

### [`esbuild`](https://github.com/evanw/esbuild)

- `+` No native dependency
- `+` More stable thanks to babel
- `-` Slower
- `+` Embeddable

### `ts-node`

- `+` Support both esm and typescript
- `/` No typechecking support / Faster
- `+` Smart syntax detect to avoid unnecessary transpilation

### Native ESM Support (MJS)

- It is not (yet) landed as a stable feature
- No typescript support
- Limitted to `.mjs` files with different executation context (no `__filename`, `require`, etc)

### Bundlers (`rollup`, `webpack`, `snowpack`, etc)

Meanwhile it would be much better making an optimized bundle to deploy to production or as npm package, using bundler setup and watching is frustrating during project development that's where `jiti` (or similar tools like `ts-node`) would be more convenient.

**Note:** However currently only babel transform is supported, configurable transform support is in the roadmap so using `esbuild` or other solutions would be possible.

## Development

- Clone Repo
- Run `yarn`
- Run `yarn build`
- Run `yarn dev`
- Run `node ./test/jiti.js`

## Roadmap

- [x] Basic working
- [x] Syntax detect and fallback to CJS require
- [x] Improve project build system
- [ ] Sourcemap support
- [ ] File system cache
- [ ] Add tests
- [ ] Configurable transform (esbuild)

## License

MIT. Made with 💖

<!-- Refs -->
[npm-v-src]: https://img.shields.io/npm/v/jiti?style=flat-square
[npm-v-href]: https://npmjs.com/package/jiti

[npm-d-src]: https://img.shields.io/npm/dm/jiti?style=flat-square
[npm-d-href]: https://npmjs.com/package/jiti

[github-actions-src]: https://img.shields.io/github/workflow/status/nuxt-contrib/jiti/ci/master?style=flat-square
[github-actions-href]: https://github.com/nuxt-contrib/jiti/actions?query=workflow%3Aci

[size-src]: https://packagephobia.now.sh/badge?p=jiti
[size-href]: https://packagephobia.now.sh/result?p=jiti
