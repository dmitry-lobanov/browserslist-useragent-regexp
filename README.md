
# browserslist-useragent-regexp

[![NPM version][npm]][npm-url]
[![Node version][node]][node-url]
[![Dependency status][deps]][deps-url]
[![Build status][build]][build-url]
[![Coverage status][coverage]][coverage-url]
[![Greenkeeper badge][greenkeeper]][greenkeeper-url]

[npm]: https://img.shields.io/npm/v/browserslist-useragent-regexp.svg
[npm-url]: https://www.npmjs.com/package/browserslist-useragent-regexp

[node]: https://img.shields.io/node/v/browserslist-useragent-regexp.svg
[node-url]: https://nodejs.org

[deps]: https://img.shields.io/david/browserslist/browserslist-useragent-regexp.svg
[deps-url]: https://david-dm.org/browserslist/browserslist-useragent-regexp

[build]: http://img.shields.io/travis/com/browserslist/browserslist-useragent-regexp.svg
[build-url]: https://travis-ci.com/browserslist/browserslist-useragent-regexp

[coverage]: https://img.shields.io/coveralls/browserslist/browserslist-useragent-regexp.svg
[coverage-url]: https://coveralls.io/r/browserslist/browserslist-useragent-regexp

[greenkeeper]: https://badges.greenkeeper.io/browserslist/browserslist-useragent-regexp.svg
[greenkeeper-url]: https://greenkeeper.io/

A utility to compile [browserslist query](https://github.com/browserslist/browserslist#queries) to a RegExp to test browser useragent. Simplest example: you can detect supported browsers on client-side.

1) Create `.browserslistrc` config, for example with [environments](https://github.com/browserslist/browserslist#environments), like this:

```
last 2 versions
not dead
```

2) Add script to `package.json`:

```json
{
  "scripts": {
    "supportedBrowsers": "echo \"module.exports = $(browserslist-useragent-regexp --allowHigherVersions);\" > supportedBrowsers.js"
  }
}
```

3) Run this script, to compile RegExp:

```bash
npm run supportedBrowsers
# or
yarn supportedBrowsers
```

`supportedBrowsers.js`:

```js
module.exports = /((CPU[ +]OS|iPhone[ +]OS|CPU[ +]iPhone)[ +]+(11[_\.]3|11[_\.]([4-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})[_\.]\d+|12[_\.]0|12[_\.]([1-9]|\d{2,})|(1[3-9]|[2-9]\d|\d{3,})[_\.]\d+)(?:[_\.](\d+))?.*Outlook-iOS-Android)|(^UCWEB.*; (iPad|iPh|iPd) OS (11_3|11_([4-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})_\d+|12_0|12_([1-9]|\d{2,})|(1[3-9]|[2-9]\d|\d{3,})_\d+)(?:_(\d+))?;)|((CPU[ +]OS|iPhone[ +]OS|CPU[ +]iPhone|CPU IPhone OS)[ +]+(11[_\.]3|11[_\.]([4-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})[_\.]\d+|12[_\.]0|12[_\.]([1-9]|\d{2,})|(1[3-9]|[2-9]\d|\d{3,})[_\.]\d+)(?:[_\.](\d+))?)|((iPhone|iPad|iPod).*Mac OS X.*Version\/(11\.3|11\.([4-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})\.\d+|12\.0|12\.([1-9]|\d{2,})|(1[3-9]|[2-9]\d|\d{3,})\.\d+))|((Fennec)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)\.?([ab]?\d+[a-z]*))|((Fennec)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)(pre))|((Fennec)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+))|((?:Mobile|Tablet);.*(Firefox)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+))|((Namoroka|Shiretoko|Minefield)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)\.(\d+(?:pre)?))|((Namoroka|Shiretoko|Minefield)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)([ab]\d+[a-z]*)?)|((OperaMini)(?:\/att)?\/?\d+?(?:\.\d+)?(?:\.(\d+))?)|((Opera)\/.+Opera Mobi.+Version\/(46\.0|46\.([1-9]|\d{2,})|(4[7-9]|[5-9]\d|\d{3,})\.\d+))|((Opera)\/(46\.0|46\.([1-9]|\d{2,})|(4[7-9]|[5-9]\d|\d{3,})\.\d+).+Opera Mobi)|(Opera Mobi.+(Opera)(?:\/|\s+)(46\.0|46\.([1-9]|\d{2,})|(4[7-9]|[5-9]\d|\d{3,})\.\d+))|((Opera)\/9.80.*Version\/(57\.0|57\.([1-9]|\d{2,})|(5[8-9]|[6-9]\d|\d{3,})\.\d+)(?:\.(\d+))?)|((?:Mobile Safari).*(OPR)\/(46\.0|46\.([1-9]|\d{2,})|(4[7-9]|[5-9]\d|\d{3,})\.\d+)\.(\d+))|((?:Chrome).*(OPR)\/(57\.0|57\.([1-9]|\d{2,})|(5[8-9]|[6-9]\d|\d{3,})\.\d+)\.(\d+))|((SamsungBrowser)\/(7\.2|7\.([3-9]|\d{2,})|7\.4|7\.([5-9]|\d{2,})|([8-9]|\d{2,})\.\d+|8\.2|8\.([3-9]|\d{2,})|(9|\d{2,})\.\d+))|(; wv\).+(Chrome)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)\.(\d+)\.(\d+))|((CrMo)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)\.(\d+)\.(\d+))|((Chrome)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)\.(\d+)\.(\d+) Mobile(?:[ \/]|$))|( Mobile .*(Chrome)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)\.(\d+)\.(\d+))|((Chrome)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)\.(\d+).* MRCHROME)|((Edge)\/(17(?:\.0)?|17(?:\.([1-9]|\d{2,}))?|(1[8-9]|[2-9]\d|\d{3,})(?:\.\d+)?))|((HeadlessChrome)((?:\/71\.0\.(\d+))?|(?:\/71\.([1-9]|\d{2,})\.(\d+))?|(?:\/(7[2-9]|[8-9]\d|\d{3,})\.\d+\.(\d+))?))|((OperaMini)\/\d+\.\d+(?:\.(\d+))?)|((Opera)\/(57\.0|57\.([1-9]|\d{2,})|(5[8-9]|[6-9]\d|\d{3,})\.\d+)(?:\.(\d+))?)|((Chromium|Chrome)\/(71\.0|71\.([1-9]|\d{2,})|(7[2-9]|[8-9]\d|\d{3,})\.\d+)(?:\.(\d+))?)|((IEMobile)[ \/](11\.0|11\.([1-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})\.\d+))|((Version)\/(11\.1|11\.([2-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})\.\d+|12\.0|12\.([1-9]|\d{2,})|(1[3-9]|[2-9]\d|\d{3,})\.\d+)(?:\.(\d+))?.*Safari\/)|((Trident)\/(7)\.(0))|((Firefox)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)\.(\d+))|((Firefox)\/(64\.0|64\.([1-9]|\d{2,})|(6[5-9]|[7-9]\d|\d{3,})\.\d+)(pre|[ab]\d+[a-z]*)?)|(([MS]?IE) (11\.0|11\.([1-9]|\d{2,})|(1[2-9]|[2-9]\d|\d{3,})\.\d+))/;
```

4) Import RegExp from created file:

```js
const supportedBrowsers = require('./supportedBrowsers');

if (supportedBrowsers.test(navigator.userAgent)) {
    alert('Your browser is supported.');
}
```

## Install

```bash
npm i -D browserslist-useragent-regexp
# or
yarn add -D browserslist-useragent-regexp
```

## Why?

As was written in article ["Smart Bundling: Shipping legacy code to only legacy browsers"](https://www.smashingmagazine.com/2018/10/smart-bundling-legacy-code-browsers/): you can determinate, which bundle you should give to browser from server with [`browserslist-useragent`](https://github.com/browserslist/browserslist-useragent). But in this case you must have your own server with special logic. Now, with `browserslist-useragent-regexp`, you can move that to client-side.

Development was inspired by [this proposal from Mathias Bynens](https://twitter.com/mathias/status/1105857829393653761).

[Demo](https://browserslist.github.io/browserslist-useragent-regexp/demo.html) ([sources](https://github.com/browserslist/browserslist-useragent-regexp/blob/7cf6afb7da2b6c77179abb8b8bd1bbcb61cf376a/docs/demo.html#L17-L29), [build script](https://github.com/browserslist/browserslist-useragent-regexp/blob/7cf6afb7da2b6c77179abb8b8bd1bbcb61cf376a/examples/buildDemo.js#L61-L74)).

## CLI

```bash
npx browserslist-useragent-regexp [query] [...options]
# or
yarn exec -- browserslist-useragent-regexp [query] [...options]
```

| Option | Description | Default |
|--------|-------------|---------|
| query | Manually provide a browserslist query. Specifying this overrides the browserslist configuration specified in your project. | |
| &#x2011;&#x2011;help, -h | Print this message. | |
| &#x2011;&#x2011;verbose, -v | Print additional info about RegExps. | |
| &#x2011;&#x2011;ignorePatch | Ignore differences in patch browser numbers. | `true` |
| &#x2011;&#x2011;ignoreMinor | Ignore differences in minor browser versions. | `false` |
| &#x2011;&#x2011;allowHigherVersions | For all the browsers in the browserslist query, return a match if the useragent version is equal to or higher than the one specified in browserslist. | `false` |
| &#x2011;&#x2011;allowZeroSubverions | Ignore match of patch or patch and minor, if they are 0. | `false` |

## JS API basics

Module exposes two main methods:

### [getUserAgentRegExps(options)](https://browserslist.github.io/browserslist-useragent-regexp/modules/_useragentregexp_useragentregexp_.html#getuseragentregexps)

Compile browserslist query to [RegExps for each browser](#regexp-info-object).

### [getUserAgentRegExp(options)](https://browserslist.github.io/browserslist-useragent-regexp/modules/_useragentregexp_useragentregexp_.html#getuseragentregexp)

Compile browserslist query to one RegExp.

> [Description of all methods you can find in Documentation.](https://browserslist.github.io/browserslist-useragent-regexp/index.html)

#### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| browsers | `string \| string[]` | — | Manually provide a browserslist query (or an array of queries). Specifying this overrides the browserslist configuration specified in your project. |
| env | `string` | — | When multiple browserslist [environments](https://github.com/ai/browserslist#environments) are specified, pick the config belonging to this environment. |
| ignorePatch | `boolean` | `true` | Ignore differences in patch browser numbers. |
| ignoreMinor | `boolean` | `false` | Ignore differences in minor browser versions. |
| allowHigherVersions | `boolean` | `false` | For all the browsers in the browserslist query, return a match if the useragent version is equal to or higher than the one specified in browserslist. |
| allowZeroSubverions | `boolean` | `false` | Ignore match of patch or patch and minor, if they are 0. |

#### RegExp info object

| Property | Type | Description |
|----------|------|-------------|
| family | `string` | Browser family. |
| requestVersions | `[number, number, number][]` | Versions provided by browserslist. |
| regExp | `RegExp` | RegExp to match useragent with family and versions. |
| sourceRegExp | `RegExp` | Original useragent RegExp, without versions. |
| resultVersion | `[number, number, number] \| null` | Useragent version of RegExp. |

## Other

- [Supported browsers](https://github.com/browserslist/browserslist-useragent#supported-browsers)
- [Notes](https://github.com/browserslist/browserslist-useragent#notes)
- [When querying for modern browsers](https://github.com/browserslist/browserslist-useragent#when-querying-for-modern-browsers)
