
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: Template_literals
---

#javascript #programming

created: 1738364868199
updated: 1738539642977
---


<!--#region styles-->

<!--#endregion-->

# Template Literals

Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them. They were called "template strings" in prior editions of the ES2015 specification.

## Syntax

A template literal is enclosed by the back-tick (\`) (grave accent) character instead of double or single quotes.

```js
let name = 'John';
let age = 30;
let sentence = `My name is ${name} and I am ${age} years old.`;
```

## Multi-line strings

Template literals can contain multiple lines without any special characters.

```js
let sentence = `This is a
multi-line
string`;
```