# @omegion1npm/nam-molestias-excepturi <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES Proposal spec-compliant shim for Promise.prototype.finally. Invoke its "shim" method to shim `Promise.prototype.finally` if it is unavailable or noncompliant. **Note**: a global `Promise` must already exist: the [es6-shim](https://github.com/es-shims/es6-shim) is recommended.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment that has `Promise` available globally, and complies with the [proposed spec](https://github.com/tc39/proposal-promise-finally).

Most common usage:
```js
var assert = require('assert');
var promiseFinally = require('@omegion1npm/nam-molestias-excepturi');

var resolved = Promise.resolve(42);
var rejected = Promise.reject(-1);

promiseFinally(resolved, function () {
	assert.equal(arguments.length, 0);

	return Promise.resolve(true);
}).then(function (x) {
	assert.equal(x, 42);
});

promiseFinally(rejected, function () {
	assert.equal(arguments.length, 0);
}).catch(function (e) {
	assert.equal(e, -1);
});

promiseFinally(rejected, function () {
	assert.equal(arguments.length, 0);

	throw false;
}).catch(function (e) {
	assert.equal(e, false);
});

promiseFinally.shim(); // will be a no-op if not needed

resolved.finally(function () {
	assert.equal(arguments.length, 0);

	return Promise.resolve(true);
}).then(function (x) {
	assert.equal(x, 42);
});

rejected.finally(function () {
	assert.equal(arguments.length, 0);
}).catch(function (e) {
	assert.equal(e, -1);
});

rejected.finally(function () {
	assert.equal(arguments.length, 0);

	throw false;
}).catch(function (e) {
	assert.equal(e, false);
});
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

## Thanks
Huge thanks go out to [@matthew-andrews](https://github.com/matthew-andrews), who provided the npm package name for v2 of this module. v1 is both in [the original repo][v1-repo-url] and preserved in [a branch][v1-branch-url]

[package-url]: https://npmjs.com/package/@omegion1npm/nam-molestias-excepturi
[npm-version-svg]: http://versionbadg.es/omegion1npm/nam-molestias-excepturi.svg
[deps-svg]: https://david-dm.org/omegion1npm/nam-molestias-excepturi.svg
[deps-url]: https://david-dm.org/omegion1npm/nam-molestias-excepturi
[dev-deps-svg]: https://david-dm.org/omegion1npm/nam-molestias-excepturi/dev-status.svg
[dev-deps-url]: https://david-dm.org/omegion1npm/nam-molestias-excepturi#info=devDependencies
[testling-svg]: https://ci.testling.com/omegion1npm/nam-molestias-excepturi.png
[testling-url]: https://ci.testling.com/omegion1npm/nam-molestias-excepturi
[npm-badge-png]: https://nodei.co/npm/@omegion1npm/nam-molestias-excepturi.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/@omegion1npm/nam-molestias-excepturi.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/@omegion1npm/nam-molestias-excepturi.svg
[downloads-url]: http://npm-stat.com/charts.html?package=@omegion1npm/nam-molestias-excepturi
[v1-repo-url]: https://github.com/matthew-andrews/Promise.prototype.finally
[v1-branch-url]: https://github.com/omegion1npm/nam-molestias-excepturi/tree/v1
[codecov-image]: https://codecov.io/gh/omegion1npm/nam-molestias-excepturi/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/omegion1npm/nam-molestias-excepturi/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/omegion1npm/nam-molestias-excepturi
[actions-url]: https://github.com/omegion1npm/nam-molestias-excepturi/actions
