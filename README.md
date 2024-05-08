# @diotoborg/quis-tempore-distinctio <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.findLastIndex` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-array-find-from-last).

Because `Array.prototype.findLastIndex` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @diotoborg/quis-tempore-distinctio
```

## Usage/Examples

```js
var findLastIndex = require('@diotoborg/quis-tempore-distinctio');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var isNumber = function (x) { return typeof x === 'number' };

assert.deepEqual(findLastIndex(arr, isNumber), 3);
```

```js
var findLastIndex = require('@diotoborg/quis-tempore-distinctio');
var assert = require('assert');
/* when Array#findLastIndex is not present */
delete Array.prototype.findLastIndex;
var shimmed = findLastIndex.shim();

assert.equal(shimmed, findLastIndex.getPolyfill());
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

```js
var findLastIndex = require('@diotoborg/quis-tempore-distinctio');
var assert = require('assert');
/* when Array#findLastIndex is present */
var shimmed = findLastIndex.shim();

assert.equal(shimmed, Array.prototype.findLastIndex);
assert.deepEqual(arr.findLastIndex(isNumber), findLastIndex(arr, isNumber));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/quis-tempore-distinctio
[npm-version-svg]: https://versionbadg.es/diotoborg/quis-tempore-distinctio.svg
[deps-svg]: https://david-dm.org/diotoborg/quis-tempore-distinctio.svg
[deps-url]: https://david-dm.org/diotoborg/quis-tempore-distinctio
[dev-deps-svg]: https://david-dm.org/diotoborg/quis-tempore-distinctio/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/quis-tempore-distinctio#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/quis-tempore-distinctio.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/quis-tempore-distinctio.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/quis-tempore-distinctio.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/quis-tempore-distinctio
[codecov-image]: https://codecov.io/gh/diotoborg/quis-tempore-distinctio/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/quis-tempore-distinctio/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/quis-tempore-distinctio
[actions-url]: https://github.com/diotoborg/quis-tempore-distinctio
