# Optional Destructuring for JavaScript

## Status
Current Stage:
* Stage 0

## Authors
* Thomas Dias-Santos (@banou26)

## Overview and motivation

When destructuring, one has to verify that the variable is an object:

```javascript
const { address: { street } = {} } = user || {}
```

The Optional Destructuring allows a developer to handle undefined values without repeating themselves in assigning default object values:

```javascript
const ?{ address: ?{ street } } = user
```

## Syntax

The Optional Chaining operator is spelled `?{` or `?[`. It may appear in two positions:
```javascript
?{ prop } = object // optional destructuring assigment on an object
?[ prop ] = array  // optional destructuring assigment on an array
```

## Semantics

### Base case
If the value of the destructured variable is undefined, we evaluate the destructuring with an empty object/array instead of undefined.
```js
const ?{ a } = undefined
a // undefined

const { a: ?{ b } } = {}
b // undefined

const ?[ a ] = undefined
a // undefined

const [ ?[ a ] ] = []
a // undefined
```
