# rfc-js-spread-optional
A proposal for JS spread operator on optional values.

Combines concepts from:
* https://github.com/tc39/proposal-optional-chaining
* https://github.com/tc39/proposal-object-rest-spread

JavaScript should support spreading objects that may be `null` or `undefined` with an optional spread operation, e.g., `...?`:

```js
const foo = options => ({
  myDefault: true,
  ...?options
})

foo()
foo({ myDefault: false })
```

Equivalent to:

```js
const foo = options => ({
  myDefault: true,
  ...(options == null ? {} : options)
})

foo()
foo({ myDefault: false })
```
