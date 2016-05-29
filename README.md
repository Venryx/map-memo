map-memo
===

Generic memoization using `Map` and `WeakMap`.

---

### What/Why?

Memoization in JavaScript has typically been limited to arguments
with primitive values, or by utilizing hacks such as stringifying objects.

By storing arguments using a series of nested cache objects backed by `Map`
and `WeakMap`, `map-memo` is able to memoize functions with *any*
argument types.

---

### Example

```js
'use strict';

const memoize = require('map-memo');

function loop( fn, n ) {
  let v;

  for ( let i = 0; i < n; ++i ) {
    v = fn( i );
  }

  return v;
}

let mem = memoize( loop );

console.log( mem( Math.sqrt, 1e9 ) ); // slow
console.log( mem( Math.sqrt, 1e9 ) ); // fast!
```
