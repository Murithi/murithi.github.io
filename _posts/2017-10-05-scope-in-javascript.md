---
layout: post
title: "Scope in Javascript"
date: 2017-10-16
author: Murithi M'Inoti
comments: true
---

Scope can be said to be a set of rules that indicate where we should look for a variable. It defines the area where variables are available. A variable will normally belong to a certain context of execution. In this context certain variables- *values and expressions* are "visible" and or can be refered to. Outside of this, the variable can't be used. 



## Variable scope
Normally variables in Javascript will either be defined in global or local scope. A variable declared outside a function is global. Otherwise, variables are limited to the local scope of the function in which they are defined. 


### Global Scope

A variable declared as global lives throughout run-time. It is accessible and alterable in any scope as the global scope is a parent to all scopes in the execution. 

```javascript
            //carname is  accessible here
            var carname="Mercedes Benz";

            function car() {
                console.log(carname); // Mercedes Benz
                //carname is accessible from within here
            }

            console.log(carname); // Mercedes Benz
            //carname is  accessible here
```
### Local Scope

While global scope is useful in programming, it's not always good practise. Following the "<a href="https://en.wikipedia.org/wiki/Principle_of_least_privilege" target="_blank">Principle of Least Privilege</a>" in software design, we apply scope-hiding techniques. This entails declaring variables nested inside blocks or functions. This creates what we call local scope. 

Local scope is available only within the function wherein it's defined. Variables living here have their scope recreated with every call of the function during runtime. The variables remain inaccessible unless reference is within the local scope of the function. 

```javascript
            //carname is not accessible here
            function car() {
                var carname = 'Mercedes Benz';
                //carname is accessible from within here
                console.log(carname); // Mercedes Benz
            }
            //carname is not accessible here
            console.log(carname); // ReferenceError: carname is not defined

```
As you can see the variable *carname* declared within the function is not reachable from outside the function. Thus a functional has it's local scope and variables within it cannot be accessed from outside.

### Function Scope
Javascript has lexical scoping with functions. Within lexical scopes, a variable name's scope is restricted to that function, within the function definition. It lives and is bound here, and outside the function it can't be referenced.
_It is important to note that curly braces **{}**  in Javascript do not create a new scope. This is because (prior to the ECMA 6 standard) curly braces do not create a new scope. Only through the creation a new function is a new scope created._

Function scope does not exist until a function is called. 

``` javascript
            //Function scope
            var carname = 'Mercedes Benz';
            function car(carname) {
                console.log(carname);
            }
            //carname is not accessible here
            car('BMW'); // BMW
            console.log(carname); // Mercedes Benz
            car('Rolls Royce'); // Rolls Royce
            console.log(carname); // Mercedes Benz
            car('Volvo'); // Volvo

```
After each time the function *car* is called a new scope is created and prints out the outputs in the variable *carname*. Thus each time the function is called a new scope has a different output as seen above *BMW*, *Mercedes Benz*. The global variable *carname* retains it's values all the while.

### Block scope
Block scope is just a block of code. Block are executed immediately, as opposed to functions that have to be called. Blocks in Javascript would include if-statements, loops etc. Prior to ECMAScript 6 (ES6/ES2015) Javascript had no block scopes. A block prior to this would have worked as follows.
```javascript
            // Blocks in Javascript don't create scope
            var carname="Mercedes Benz";
            if (true){
                var carname = "Volvo";
                console.log(carname); // Volvo
            }
            console.log(carname); // Volvo

``` 
The way to create block scope was through Immediately Invoked Function Expressions (IIFE) pattern. 
```javascript
            //IIFE Demo
            var carname = 'Mercedes Benz';
            (function car(carname) {
                var carname = 'Volvo';
                console.log(carname);// Volvo
            })()
            //carname prints out the global scope value
            console.log(carname); // Mercedes Benz

```
The output of *carname* within the function is changed within the function expression, without affecting global variable *carname*.

ECMAScript 6 (ES6/ES2015) introduced light-weight blocks using the *let* and *const* keywords. This still refers to the local scope but within the block. Thus access to a variable is confined to the scope of the block in which it's defined. This scope is also only created during runtime anytime the block is executed in the stack and accessibility is only from within the block.


```javascript
            //Block Scope Demo
            var carname="Mercedes Benz";
            if (true)  {
                
                let carname = "Volvo";
                let vehiclename = "Volvo";
                //vehiclename is only accessible from within here
                console.log(carname); //Volvo 
                
            }
            console.log(carname); //Mercedes Benz
            console.log(vehiclename); //Uncaught ReferenceError: vehiclename is not defined
```
The *vehiclename* variable is only accessible inside the block scope.

### That's it!
We've covered the basics regarding scope in this post. There's always more to learn, but this should be sufficient to help you grasp the basics. Happy coding!