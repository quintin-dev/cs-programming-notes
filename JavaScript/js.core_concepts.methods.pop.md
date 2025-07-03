
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: Pop
---

#javascript #programming #javascript #core-concepts

created: 1738107296077
updated: 1738275940329
---


<!--#region styles-->

<!--#endregion-->

## Definition

The `pop()` method removes the last element from an array and returns that element. This method changes the length of the array.

## Syntax

```js
arr.pop();
```

## Parameters

None

## Return Values

The removed element from the array.

## Examples

### Example 1

```js
const arr = [1, 2, 3, 4, 5];
const removedElement = arr.pop();

console.log(removedElement); // 5
console.log(arr); // [1, 2, 3, 4]
```

### Example 2

```js
const arr = ['apple', 'banana', 'cherry', 'date'];
const removedElement = arr.pop();

console.log(removedElement); // 'date'
console.log(arr); // ['apple', 'banana', 'cherry']
```

## Applicable To

-   Arrays
-   Typed Arrays

## Edge Cases

## Links