---
date: '2020-02-16 22:00 -0800'
last_modified_at: '2020-02-16 22:00 -0800'
published: false
title: JavaScript Quick Reference
---
## JavaScript Quick Reference

This is a list of some of JavaScript's behavior. A list of things of which I'm not quite sure when someone asks. Like closures, some scope quirks, the "this" keyword, etc.

### Variable Declarations

#### 1. var

Good old var. Problem is, allows me to redeclare the same variables twice.

```
var a = 'foo'
var a = 'bar' // No error thrownm and this can be anywhere in the code.
```

#### 2. let

Let fixes this problem. Redeclaring the same variable throws an error.

```
let a = 'foo'
let a = 'bar' // Oops! Error!
```

#### 3. const

Same as let, except the variable cannot be reassigned.

```
const a = {}
a.first = 'foo' // This is ok
a = {second: 'bar'} // Oops! Error!
```

__Conclusion:__ Default to const. If reassign is necessary, use let. Only use var in old environments where let/const aren't available.

### Scope

Source: [CSS-Tricks on Scope and Closure](https://css-tricks.com/javascript-scope-closures)

