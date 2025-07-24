
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: Functions
---

#javascript #programming

created: 1735912593406
updated: 1738275940298
---


<!--#region styles-->

<!--#endregion-->

# Functions Syntax in JavaScript

A function is a block of code that performs a specific task. It is executed when "something" invokes it (calls it).

### Function Declaration Syntax

```js
function functionName(parameters) {
    // code to be executed
}
```

<b>where</b>

-   `functionName` is the name of the function. It is a unique identifier for the function. It is used to call the function. It is optional.

-   `parameters` are the values passed to the function. They are optional. A function can have zero or more parameters. They are separated by commas. They are used to pass values to the function.
-   `code to be executed` is the block of code that performs the task. It is enclosed in curly braces `{}`. It is mandatory. It is the code that is executed when the function is called.

#### Example

```js
function greet() {
    console.log('Hello, World!');
}
```

### Function Expression Syntax

A function expression is a function that is assigned to a variable. It is not hoisted. It is executed when the variable is called.

```js
const variableName = function (parameters) {
    // code to be executed
};
```

<b>where</b>

-   `variableName` is the name of the variable the function is being assigned to.

-   `const` is a keyword that declares a constant variable. It is mandatory.

#### Example

```js
const greet = function () {
    console.log('Hello, World!');
};
```

### Arrow Function Syntax

An arrow function is a shorter syntax for writing function expressions. It does not have its own `this`, `arguments`, `super`, or `new.target`. It is not hoisted. It is executed when the variable is called.

`this` when talking about functions in general refers to the object that the function is a method of. Arrow functions do not have their own `this`. They inherit `this` from the parent scope.

`arguments` is an array-like object that contains the arguments passed to the function. Arrow functions do not have their own `arguments`. They inherit `arguments` from the parent scope.

`super` is used to call functions on an object's parent. Arrow functions do not have their own `super`. They inherit `super` from the parent scope.

`new.target` is used to determine whether a function was called with the `new` operator. Arrow functions do not have their own `new.target`. They inherit `new.target` from the parent scope.

```js
const variableName = (parameters) => {
    // code to be executed
};
```

#### Example

```js
const greet = () => {
    console.log('Hello, World!');
};
```

> <b>IMPORTANT:</b> All functions in JavaScript return a value by default. If no return value is specified, the function returns `undefined`.
> The return statement does not only specify a value to be returned but also stops execution within a block.

### Function Constructor Syntax

A function constructor is a built-in function that creates a new function object. It is not recommended to use the function constructor to create functions. It is slower and less secure.

```js
const variableName = new Function('parameters', 'code to be executed');
```

<b>where</b>

-   `variableName` is the name of the variable the function is being assigned to.
-   `new` is a keyword that creates a new object. It is mandatory.
-   `Function` is a built-in function constructor. It is mandatory.

#### Example

```js
const greet = new Function('console.log("Hello, World!")');
```

### Self-Invoking Function Syntax

A self-invoking function is a function that runs as soon as it is defined. It is executed immediately. It is not hoisted.

```js
(function () {
    // code to be executed
})();
```

#### Example

```js
(function () {
    console.log('Hello, World!');
})();
```