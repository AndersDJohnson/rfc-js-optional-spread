# rfc-js-spread-optional
A proposal for JS spread operator on optional array values.

Combines concepts from:
* https://github.com/tc39/proposal-object-rest-spread
* https://github.com/tc39/proposal-optional-chaining
* https://github.com/tc39-transfer/proposal-nullish-coalescing

Just like for objects, JavaScript could support spreading arrays that may be `null` or `undefined` with an optional spread operation, e.g., `...?` or  `...token?` or `?...`:

```js
const foo = more => [
  'one',
  ...?more
]

foo()
// yields `['one']`

foo(['two'])
// yields `['one', 'two']`
```

or:

```js
const foo = more => [
  'one',
  ...?more
]
```

or:

```js
const foo = more => [
  'one',
  ...more?
]
```

Equivalent to:

```js
const foo = more => [
  'one',
  ...(more == null ? [] : more)
]
```
