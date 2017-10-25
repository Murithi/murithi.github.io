---
layout: post
title: "Closure in Javascript"
date: 2017-10-16
author: Murithi M'Inoti
comments: true
---

Scope refers to the context of execution, the context in which values and expressions are "visible" and or can be refered to. Outside of this, the variable can't be used. Scope can be said to be a set of rules that indicate where we should look for a variable. 

Scope is layered in hierarchy in Javascript. This means that child scopes have access to parent scopes, but not vice versa. 

## Variable scope
Normally variables in Javascript will either be defined in global or local scope. A variable declared outside a function is global. Otherwise, variables are limited to the local scope of the function in which they are defined. 


### Global Scope

A variable declared as global lives throughout run-time. It is accessible and alterable in any scope as the global scope is a parent to all scopes in the execution. 

```javascript
//carname is  accessible here
var carname="Mercedes Benz";

function car() {
    console.log(carname);
    //carname is accessible from within here
}
//carname is  accessible here
```
### Local Scope

Local scope is available only within the function wherein it's defined. Variables living here have their scope recreated with every call of the function during runtime. The variables remain inaccessible unless reference is within the local scope of the function. 

```javascript
//carname is not accessible here
function car() {
    var carname="Mercedes Benz";
    //carname is accessible from within here
}
//carname is not accessible here
```

### Block scope
ECMAScript 6 (ES6/ES2015) introduced light-weight blocks using the *let* and *const* keywords. This still refers to the local scope but within the block. Thus access to a variable is confined to the scope of the block in which it's defined. This scope is also only created during runtime anytime the block is executed in the stack and accessibility is only from within the block.


```javascript
//carname is not accessible here
if (true)  {
    var carname="Mercedes Benz";
    let vehiclename = "Mercedes Benz";
    //carname is accessible from within here
    console.log(carname); //Mercedes 
    console.log(vehiclename); //Mercedes Benz
}
console.log(carname); //Mercedes Benz
console.log(vehiclename); //Uncaught ReferenceError: vehiclename is not defined
```
The *vehiclename* variable is only accessible inside the block scope.

### Lexical Scoping

Javascript has lexical scoping with functions. Within lexical scopes, a variable name's scope is restricted to that function, within the function definition. It lives and is bound here, and outside the function it can't be referenced.
_It is important to note that curly braces **{}**  in Javascript do not create a new scope. This is because (prior to the ECMA 6 standard) curly braces do not create a new scope. Only through the creation a new function is a new scope created._

Lexical scope is sometimes referred to as Static Scope, as opposed to Dynamic Scope.

Dynamic Scope on the other hand has a variable name defined within a function but it's scope is the time period of the functions exection. A local definition of the variable is first sought, then followed by a lookup on the call stack for the variable definition.

