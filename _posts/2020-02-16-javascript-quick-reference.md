---
date: '2020-02-16 22:00 -0800'
last_modified_at: '2020-02-16 22:00 -0800'
published: true
title: JavaScript Quick Reference
---
This is a (updating) list of some of JavaScript's behaviorthat I keep forgetting. Like closures, some scope quirks, the "this" keyword, etc. This is a quick reference I can check when I need to.

__Sources:__
- [CSS-Tricks on Scope and Closure](https://css-tricks.com/javascript-scope-closures)
- [Scope tutorial by Hammad Ahmed on Scotch.io](https://scotch.io/tutorials/understanding-scope-in-javascript)

## Variable Declarations

### 1. var

Good old var. Problem is, allows me to redeclare the same variables twice.

```javascript
var a = 'foo'
var a = 'bar' // No error thrown and this can be anywhere in the code.
```

### 2. let

let fixes this problem. Redeclaring the same variable throws an error.

```javascript
let a = 'foo'
let a = 'bar' // Oops! Error!
```

### 3. const

Same as let, except the variable cannot be reassigned.

```javascript
const a = {}
a.first = 'foo' // This is ok
a = {second: 'bar'} // Oops! Error!
```

### Within block scope

let and const are limited to block scope unlike var.

```javascript
if (true) {
  let foo = 1
  var bar = 2
}

console.log(foo) // Error, foo is limited to the scope of the if block
console.log(var) // prints 2. Not limited to block scope
```

__Conclusion:__ Default to const. If reassign is necessary, use let. Only use var in old environments where let/const aren't available.

## Scope

Global, local and function scopes work as I would expect. Just remember function hoisting.

### Function hoisting

Functions declared later can be called earlier. Functions are essentially hoisted to to the top and made available in current scope.

Note that function hoisting doesn't work when assigning anonymous functions.

```javascript
yo()    // Works
heyo()  // Doesn't work

function yo() {
  console.log('Yo.')
}

let heyo = function() {
  console.log('Heyo!')
}
```

## Closures

When I define a function inside another function, the inner function is called a closure. It has access go the parameters and the scope of the outer function. When this inner function is returned, it still has access to the outer function. Weird zombie shite, but that's JS for you.

```javascript
function outer() {
  let name = 'Hiesenberg'
  return function sayMyName() {
    console.log('You are ' + name);
  }
}

let whoAmI = outer()
// outer finished executing here, but...
whoAmI.sayMyName() // prints 'You are Hiesenberg', accessing the "name" variable of outer()
```

This trick is apparently used to implement private variables in JS.

```javascript
function foo() {
  let privateVar = 1
  return {
    getVar: function() {
      return privateVar
    },
    setVar: function(value) {
      privateVar = value
    }
  }
}

let bar = foo()
bar.getVar() // prints 1
bar.setVar(2)
bar.getVar() // prints 2
```

I still need to find an example of where this is useful, and put it in the context of OO in JS.
