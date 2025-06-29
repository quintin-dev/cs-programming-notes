
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: forEach
---

#javascript #programming #javascript #core-concepts

created: 1737650770269
updated: 1738275940343
---


<!--#region styles-->

<!--#endregion-->

## Definition

The `forEach()` method executes a provided function once for each array element.

## Syntax

```js
array.forEach(function(currentValue, index, arr), thisValue)


```

## Parameters

-   `currentValue`: The current element being processed in the array.

-   `index`: The index of the current element being processed in the array.
-   `arr`: The array `forEach()` was called upon.
-   `thisValue`: A value to be passed to the function to be used as its "this" value.
-   `function`: A function to execute for each element, taking three arguments:
    -   `currentValue`: The current element being processed in the array.
    -   `index`: The index of the current element being processed in the array.
    -   `arr`: The array `forEach()` was called upon.

## Return Values

The `forEach()` method does not return anything.

## Examples

```js
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));
```

## Applicable To

The `forEach()` method is applicable to all arrays.

## Edge Cases

-   If the array is modified during iteration, other elements might be skipped.
-   If the array is sparse, the index will not be visited for those elements.

## Links

-   [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)