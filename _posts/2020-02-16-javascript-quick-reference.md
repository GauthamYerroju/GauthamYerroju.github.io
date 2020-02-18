---
date: '2020-02-16 22:00 -0800'
last_modified_at: '2020-02-16 22:00 -0800'
published: false
title: JavaScript Quick Reference
---
# JavaScript Quick Reference

This is a list of some of JavaScript's behavior. A list of things of which I'm not quite sure when someone asks. Like closures, some scope quirks, the "this" keyword, etc.

__Sources:__
- [CSS-Tricks on Scope and Closure](https://css-tricks.com/javascript-scope-closures)
- [Scope tutorial by Hammad Ahmed on Scotch.io](https://scotch.io/tutorials/understanding-scope-in-javascript)

## Variable Declarations

### 1. var

Good old var. Problem is, allows me to redeclare the same variables twice.

```
var a = 'foo'
var a = 'bar' // No error thrown and this can be anywhere in the code.
```

### 2. let

Let fixes this problem. Redeclaring the same variable throws an error.

```
let a = 'foo'
let a = 'bar' // Oops! Error!
```

### 3. const

Same as let, except the variable cannot be reassigned.

```
const a = {}
a.first = 'foo' // This is ok
a = {second: 'bar'} // Oops! Error!
```

### within block scope

let and const are limited to block scope unlike var.

```
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

```
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

When I define a function insude another function, the inner function is called a closure. It has access go the parameters and the scope of the outer function. When this inner function is returned, it still has access to the outer function. Weird zombie shite, but that's JS for you.

```
function outer() {
  let name = 'Hiesenberg'
  return function sayMyName() {
    console.log('You are ' + name);
  }
}

let whoAmI = outer()
// outer finished executing here, but...
whoAmI.sayMyName() // prints 'You are Hiesenberg', accessing gth ename variable of outer()
```

This trick is apparently used to implement private variables in JS.

```
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


## Context and this

TODO