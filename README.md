# `stylelint-processor-styled-components`

Lint your [styled components](https://github.com/styled-components/styled-components) with [stylelint](http://stylelint.io/)!

[![Build Status][build-badge]][build-url]
[![Coverage Status][coverage-badge]][coverage-url]
[![Join the community on Spectrum](https://withspectrum.github.io/badge/badge.svg)](https://spectrum.chat/styled-components/stylelint-processor)
[![Greenkeeper][greenkeeper-badge]][greenkeeper-url]

![Video of project in use](http://imgur.com/br9zdHb.gif)

## Setup

You need:

- `stylelint` (duh)
- This processor, to extract styles from `styled-components`
- The [`stylelint-config-styled-components`](https://github.com/styled-components/stylelint-config-styled-components) config to disable stylelint rules that clash with `styled-components`
- Your favorite `stylelint` config! (for example [`stylelint-config-recommended`](https://github.com/stylelint/stylelint-config-recommended))

```
(npm install --save-dev
  stylelint
  stylelint-processor-styled-components
  stylelint-config-styled-components
  stylelint-config-recommended)
```

Now use those in your `.stylelintrc` and run stylelint with your JavaScript files!

```json
{
  "processors": ["stylelint-processor-styled-components"],
  "extends": [
    "stylelint-config-recommended",
    "stylelint-config-styled-components"
  ]
}
```

> **NOTE:** The processor works with Flow- and TypeScript-typed files too! (we'll assume TypeScript usage if your files end in `.ts` or `.tsx`)

## [Documentation](https://www.styled-components.com/docs/tooling#stylelint)

**Further documentation for this processor lives on [the styled-components website](https://www.styled-components.com/docs/tooling#stylelint)!**

- [Setup](https://www.styled-components.com/docs/tooling#setup)
- [Webpack](https://www.styled-components.com/docs/tooling#webpack)
- [Interpolation tagging](https://www.styled-components.com/docs/tooling#interpolation-tagging)
- [Tags](https://www.styled-components.com/docs/tooling#tags)
- [sc-custom](https://www.styled-components.com/docs/tooling#sc-custom)
- [Syntax Notes](https://www.styled-components.com/docs/tooling#syntax-notes)

## F.A.Q.

### Why does it throw `Unexpected token`? Even thought the file didn't import `styled-components`.

You can custom babel plugins by `option.parserPlugins` now. An API example is [our test](https://github.com/styled-components/stylelint-processor-styled-components/blob/master/test/options.test.js#L211). But if someone can implement #231, that will be much better.

An alternative cause of this and other syntax errors could be an outdated `@babel/parser` subdependency, especially when linting TypeScript files with newer TypeScript syntax. In order to update the `@babel/parser` subdependency, edit your yarn.lock or package-lock.json file and remove the outdates `"@babel/parser"` entry, and run `npm install` again.

### Why does it throw unexpected lint errors?

The processor can not always parse interpolations with right things. But you can use [interpolation-tagging](https://www.styled-components.com/docs/tooling#interpolation-tagging) to help it. If you have ideas to make it more intelligent, feel free to send a PR or share your solution by an new issue.

### I don't want specified tagged template literal to be parsed, i.e. `css`.

You can set `option.strict`. More examples are in [#258](https://github.com/styled-components/stylelint-processor-styled-components/pull/258).

## License

Licensed under the MIT License, Copyright © 2017 Maximilian Stoiber. See [LICENSE.md](./LICENSE.md) for more information!

Based on Mapbox' excellent [`stylelint-processor-markdown`](https://github.com/mapbox/stylelint-processor-markdown), thanks to @davidtheclark!

[build-badge]: https://travis-ci.org/styled-components/stylelint-processor-styled-components.svg?branch=master
[build-url]: https://travis-ci.org/styled-components/stylelint-processor-styled-components
[coverage-badge]: https://coveralls.io/repos/github/styled-components/stylelint-processor-styled-components/badge.svg?branch=master
[coverage-url]: https://coveralls.io/github/styled-components/stylelint-processor-styled-components?branch=master
[greenkeeper-badge]: https://badges.greenkeeper.io/styled-components/stylelint-processor-styled-components.svg
[greenkeeper-url]: https://greenkeeper.io/
