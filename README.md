class: center, middle

# A 10 minute crash course in Functional Programming with JavaScript

reMarkable #WebDevs

---

class: middle

# Functional vs Imperative

## Imperative

Describes the detailed procedural steps to achieve something. **How to do something.** *Algorithmic programming.*

## Functional

Composing the problem as a set of functions, which data flows through. **What to do.**  *Declarative programming.*

---

class: center, middle

# JavaScript Paradigms

Imperative  
Object-oriented  
Functional

---

class: center, middle

# Functional Principles

Pure functions  
No side effects  
Function composition  
No shared state  
Immutable state

*+ Others (First class functions, Recursion, Strict/Non-strict evaluation, Referential transparency, Monads, ...)*

---

class: center, middle

# Pure Functions

A function that given the same inputs, should always return the same output without any side effects.

---

class: middle

# Side Effects

A side effect is any change to application state that is observable from outside a called function, other than its return value.

This includes, but are not limited to:

* Writing to disk, screen or the console
* Doing network calls
* Modifying external variables (globals, etc)

---

class: center, middle

# Function Composition

Function composition is simply combining two or more functions together to form a new function: `f(g(x))`

---

class: center, middle

# Shared State

Shared state is any variable that is shared between scopes, or property on objects that are shared across scopes.

Shared state could lead to timing issues, as the order of function calls matter, and you need to take into account all shared states of a function in order to understand what it does (increased complexity).

---

class: center, middle

# Immutability

An immutable object can not be changed after it has been created  
`const` != immutable  
`Object.freeze()` creates superficially imuutable objects

---

class: middle

# Imperative vs. Declarative

## Imperative

```js
const addOne = numbers => {
    const results = [];
    for (let n=0; n<numbers.length; n++) {
        results.push(numbers[n] + 1);
    }
    return results;
};

addOne([1, 2, 3]); //=> [2, 3, 4]
```

## Declarative

```js
const addOne = numbers => numbers.map(n => n + 1);
addOne([1, 2, 3]); //=> [2, 3, 4]
```

---

class: center, middle

# Higher Order Functions

High order functions is how you write reusable (and generic) code in functional programming.

It typically take a function as a parameter, or returns another function (or both).

The React equivalent is the *High Order Component*, which is a component (function) returns a new component.

---

class: middle

# Partial Application & Curry

Partial application means that you bind some of the arguments of a function, and returns the partially applied function.

When you take a function with multiple parameters as input and returns a function with **only one** parameter, that is a *curried function*.

```js
const addX = x => numbers => numbers.map(n => n + x);
const addOne = addX(1);
addOne([1, 2, 3]); //=> [2, 3, 4]
```

---

# Lodash/FP

Functional wrapping over the more generic Lodash library:

```js
import { pipe, curry, map, join, split } from 'lodash/fp';

const toLowerCase = str => str.toLowerCase();

const toSlug = pipe(
    split(' '),
    map(toLowerCase),
    join('-')
);

toSlug('Sluggy Mac Slug Face'); //=> 'sluggy-mac-slug-face'
```

https://github.com/lodash/lodash/wiki/FP-Guide

---

# Rambda

Pure functional library:

```js
import R from 'rambda';

const toSlug = R.pipe(
    R.split(' '),
    R.map(R.toLower),
    R.join('-')
);

toSlug('Sluggy Mac Slug Face'); //=> 'sluggy-mac-slug-face'
```

http://ramdajs.com/

---

# Further reading...

* https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
* https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0
* https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8
* https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976
* https://medium.com/javascript-scene/10-tips-for-better-redux-architecture-69250425af44
* https://hackernoon.com/why-functional-programming-matters-c647f56a7691
* https://www.sitepoint.com/functional-programming-with-ramda/
* https://github.com/lodash/lodash/wiki/FP-Guide
* http://ramdajs.com/
