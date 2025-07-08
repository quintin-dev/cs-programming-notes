
> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---
title: Split
---

#javascript #programming #javascript #core-concepts

created: 1736634481961
updated: 1738275940323
---


<!--#region styles-->

<!--#endregion-->

## Definition

The `split()` method is used to split a string into an array of substrings, and returns the new array. The method takes two parameters: a separator and an optional limit. The separator is used to specify where to split the string, and the limit is used to specify the maximum number of splits to make.

## Syntax

```js
string.split(separator, limit);
```

## Parameters

-   `separator`: The separator to use when splitting the string. This can be a string or a regular expression. If the separator is an empty string, the string is split into an array of each character. If the separator is omitted, the entire string is returned as the first element of the array. The separator is case-sensitive.

-   `limit`: An optional parameter that specifies the maximum number of splits to make. If the limit is provided, the resulting array will have a maximum length of limit - 1. If the limit is not provided, the entire string is split. If the limit is 0, the method returns an empty array.

## Examples

```js
const str = 'Hello,World,JavaScript';
const arr = str.split(',');
console.log(arr); // Output: ['Hello', 'World', 'JavaScript']

const str2 = 'Hello,World,JavaScript';
const arr2 = str2.split(',', 2);
console.log(arr2); // Output: ['Hello', 'World']
```

in this example, the `split()` method is used to split a string into an array of substrings. The first example splits the string `Hello,World,JavaScript` using a comma as the separator, resulting in an array with three elements: `['Hello', 'World', 'JavaScript']`. The second example splits the same string using a comma as the separator and a limit of 2, resulting in an array with two elements: `['Hello', 'World']`.

## Applicable To

The `split()` method is applicable to all JavaScript strings.

## Return Values

-   The `split()` method returns an array of substrings. If the string is empty, the method returns an array with one empty string as the only element.

-   If the separator is an empty string, the method returns an array of each character in the string.
-   If the separator is not found in the string, the method returns an array with the entire string as the only element.
-   If the limit is 0, the method returns an empty array.
-   If the limit is not provided, the method returns an array with all the splits.
-   If the limit is greater than the number of splits, the method returns an array with all the splits.

## Edge Cases

-   If the separator is not found in the string, the method returns an array with the entire string as the only element. For example, `str.split('!')` will return `['Hello,World,JavaScript']`.
-   If the separator is an empty string, the method returns an array of each character in the string. For example, `str.split('')` will return `['H', 'e', 'l', 'l', 'o', ',', 'W', 'o', 'r', 'l', 'd', ',', 'J', 'a', 'v', 'a', 'S', 'c', 'r', 'i', 'p', 't']`.
-

## Links

-   [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
-   [W3Schools](https://www.w3schools.com/jsref/jsref_split.asp)
-   [JavaScript.info](https://javascript.info/array-methods#split)
-   [Can I Use](https://caniuse.com/?search=split)