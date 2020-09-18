# 👽 Nuxt-Alias-Module
[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![Circle CI][circle-ci-src]][circle-ci-href]
[![Codecov][codecov-src]][codecov-href]
[![Standard JS][standard-js-src]][standard-js-href]
![License][license-src]

> It automatically creates an alias for the components and page of the path

## Infos
- [📖 **Release Notes**](./CHANGELOG.md)

## Install
⚠️ If you are using Nuxt older than **v2.9** you have to install module as a dependency (No --dev or --save-dev flags) and also use `modules` section in` nuxt.config.js` instead of `buildModules`.

Install with npm:

```bash
npm i nuxt-alias
```

nuxt.config.js:

```js
module.exports = {
  buildModules: [
    'nuxt-alias'
  ],
  nuxtAlias: {
    /* module options */
  }
}
```

<br>

## Options

### `rootDir`
Set the parent folder name to configure alias
Setting `rootDir` creates an alias based on the structure of the set folder
`rootDir` is a subfolder of `srcDir`, which is the setting of `nuxt.config.js`

- Type: `Array`
- Default: `*`
- Example:
```js
nuxtAlias: {
  rootDir: ['components']
}
```

### `ignoreDir`
Set folder name to ignore `alias` configuration. For `ignoreDir`, enter the parent path folder name of `.vue`

- Type: `Array`
- Example:
```js
nuxtAlias: {
  ignoreDir: ['folder-A']
}
```

### `transformDir`
Convert alias that are automatically created according to the folder structure.
`transformDir` is a function and automatically generated alias is passed as a parameter.

- Type: `Function`
- Example:
```js
nuxtAlias: {
  transformDir: orgAlias => orgAlias.replace('folder', 'transform-alias')
}
```

## Usage
Alias is designated by the name of the parent folder of the inserted component. However, no alias are specified if the folder set in `rootDir` or the very subfolder of the `srcDir` is alias.

Folder structure :
```bash
- components
  └ folder-A
    └ component-A.vue
  └ folder-B
    └ folder-C
      └ component-B.vue
  └ component-C.vue
```

nuxt.config.js :
```js
module.exports = {
  buildModules: [{
    'nuxt-alias'
  }],
  nuxtAlias: {
    rootDir: ['components'],
    ignoreDir: ['folder-A']
  }
}
```

index.vue :
```js
import ComponentA from 'folder-A/component-A' // An error is generated because it is a ignored folder.
import ComponentB from 'folder-C/component-B'
import ComponentC from '~/components/component-C' // If the srcDir immediate subfolder is alias, it does not specify alias.

export default {
  name: 'index',
  components: {
    ComponentA,
    ComponentB,
    ComponentC
  }
}
```

<br>

## License

[MIT License](./LICENSE)

Copyright (c) [Dev.DY](https://kdydesign.github.io/)

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/nuxt-alias?style=flat-square
[npm-version-href]: https://npmjs.com/package/nuxt-alias
[npm-downloads-src]: https://img.shields.io/npm/dt/nuxt-alias?style=flat-square
[npm-downloads-href]: https://npmjs.com/package/nuxt-alias
[circle-ci-src]: https://img.shields.io/circleci/project/github/kdydesign/nuxt-alias-module/master.svg?style=flat-square
[circle-ci-href]: https://circleci.com/gh/kdydesign/nuxt-alias-module/tree/master
[codecov-src]: https://img.shields.io/codecov/c/github/kdydesign/nuxt-alias-module.svg?style=flat-square
[codecov-href]: https://codecov.io/gh/kdydesign/nuxt-alias-module
[david-dm-src]: https://david-dm.org/kdydesign/nuxt-alias-module/status.svg?style=flat-square
[david-dm-href]: https://david-dm.org/kdydesign/nuxt-alias-module
[standard-js-src]: https://img.shields.io/badge/code_style-standard-brightgreen.svg?style=flat-square
[standard-js-href]: https://standardjs.com
[license-src]: https://img.shields.io/npm/l/nuxt-alias?style=flat-square
