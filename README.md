# add-objects

> Returns a function that combines two objects using given per-property functions

Small, dependency-free utility for combining two objects.

[![NPM][npm-icon] ][npm-url]

[![Build status][ci-image] ][ci-url]
[![semantic-release][semantic-image] ][semantic-url]
[![js-standard-style][standard-image]][standard-url]

## Install

Requires [Node](https://nodejs.org/en/) version 6 or above.

```sh
npm install --save add-objects
```

## Use

If you know how to use [R.evolve](http://ramdajs.com/docs/#evolve) you can use this function.

Give an object, where each property is an "adder" or "combinator" function. For example, if
we want to concatenate "name" properties, but add "age" properties in the objects we
could do the following:

```js
const addObjects = require('add-objects')
const R = require('ramda')
const adder = addObjects({
  name: R.concat,
  age: R.add
})
// combine two objects
const a = {
  name: 'a',
  age: 1
}
const b = {
  name: 'b',
  age: 2
}
adder(a, b)
// {name: "ab", age: 3}
```

This is very useful when reducing a list of objects for example

```js
// same code as above
const combined = [a, a, b, b].reduce(adder, {name: '', age: 0})
// {name: "aabb", age: 6}
```

### Small print

Author: Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt; &copy; 2017

* [@bahmutov](https://twitter.com/bahmutov)
* [glebbahmutov.com](https://glebbahmutov.com)
* [blog](https://glebbahmutov.com/blog)

License: MIT - do anything with the code, but don't blame me if it does not work.

Support: if you find any problems with this module, email / tweet /
[open issue](https://github.com/bahmutov/add-objects/issues) on Github

## MIT License

Copyright (c) 2017 Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt;

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

[npm-icon]: https://nodei.co/npm/add-objects.svg?downloads=true
[npm-url]: https://npmjs.org/package/add-objects
[ci-image]: https://travis-ci.org/bahmutov/add-objects.svg?branch=master
[ci-url]: https://travis-ci.org/bahmutov/add-objects
[semantic-image]: https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg
[semantic-url]: https://github.com/semantic-release/semantic-release
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg
[standard-url]: http://standardjs.com/
