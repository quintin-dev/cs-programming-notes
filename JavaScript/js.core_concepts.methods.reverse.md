
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: Reverse
---

#javascript #programming #javascript #core-concepts

created: 1737412588691
updated: 1738427141489
---


<!-- #region styles -->

<!-- #endregion -->

## Definition

The `reverse()` method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.

## Syntax

```js
arr.reverse();
```

## Parameters

None

## Return Values

The reversed array.

## Examples

```js
const arr = [1, 2, 3, 4, 5];
arr.reverse();
console.log(arr); // [5, 4, 3, 2, 1]
```

## Applicable To

-   JavaScript Arrays
-   JavaScript Typed Arrays

## Edge Cases

### Edge Case 1

```js
const arr = [1, 2, 3, 4, 5];
arr.reverse();
console.log(arr); // [5, 4, 3, 2, 1]
```

## Links

-   [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)