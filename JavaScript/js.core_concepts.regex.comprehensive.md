# Regular Expressions (Regex) in JavaScript - Comprehensive Guide

## Overview

Regular Expressions (regex or regexp) are powerful pattern-matching tools that enable search, validation, extraction, and replacement operations on strings. In JavaScript, regex is implemented through the built-in `RegExp` object and can be created using literal notation or constructor syntax. Modern JavaScript has significantly enhanced regex capabilities, making it competitive with other programming languages.

## Why Regular Expressions Matter in JavaScript

### Core Use Cases

- **Input Validation**: Email addresses, phone numbers, passwords, credit cards
- **Data Extraction**: Parsing URLs, extracting numbers, capturing specific patterns
- **Text Processing**: Find and replace operations, data cleaning, formatting
- **Pattern Matching**: Log analysis, search functionality, content filtering
- **Security**: Input sanitization, preventing injection attacks

### Industry Relevance

- **Frontend Development**: Form validation, user input processing
- **Backend Development**: Log parsing, data validation, API input sanitization
- **Data Processing**: Text mining, content analysis, data transformation
- **DevOps**: Configuration parsing, log analysis, automated text processing

## Core Implementation

### Creating Regular Expressions

#### Literal Syntax (Recommended for Static Patterns)

```javascript
// Basic pattern
let pattern = /hello/;

// With flags
let pattern = /hello/gi; // global, case-insensitive

// Complex pattern
let emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
```

#### Constructor Syntax (For Dynamic Patterns)

```javascript
// Static pattern
let pattern = new RegExp("hello");

// With flags
let pattern = new RegExp("hello", "gi");

// Dynamic pattern from user input (ES2025 improvement)
let userInput = "search term";
let safePattern = new RegExp(RegExp.escape(userInput), "i");
```

### Essential Methods

#### String Methods

```javascript
let text = "The quick brown fox jumps over the lazy dog";
let pattern = /[aeiou]/g;

// Find all matches
let matches = text.match(pattern);
// ['e', 'u', 'i', 'o', 'o', 'u', 'o', 'e', 'e', 'a', 'o']

// Find first match with details
let firstMatch = text.match(/quick/);
// ['quick', index: 4, input: 'The quick brown fox...', groups: undefined]

// Test if pattern exists
let hasVowels = pattern.test(text); // true

// Replace patterns
let noVowels = text.replace(pattern, "*");
// "Th* q**ck br*wn f*x j*mps *v*r th* l*zy d*g"

// Split by pattern
let words = text.split(/\s+/);
// ['The', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']

// Find index of pattern
let index = text.search(/fox/); // 16
```

#### RegExp Methods

```javascript
let pattern = /\w+/g;
let text = "Hello World";

// Execute pattern (with state)
let result;
while ((result = pattern.exec(text)) !== null) {
  console.log(`Found ${result[0]} at index ${result.index}`);
}
// Found Hello at index 0
// Found World at index 6

// Test pattern
let isValid = /^\d{3}-\d{2}-\d{4}$/.test("123-45-6789"); // true
```

## Key Patterns & Best Practices

### Character Classes and Quantifiers

```javascript
// Character classes
let digits = /\d+/g; // One or more digits
let words = /\w+/g; // One or more word characters
let whitespace = /\s+/g; // One or more whitespace
let anything = /.+/g; // One or more any character

// Custom character sets
let hexColor = /#[0-9a-fA-F]{6}/; // Hex color codes
let vowels = /[aeiouAEIOU]/g; // Vowels only
let notDigits = /[^\d]/g; // Anything except digits

// Quantifiers
let optional = /colou?r/g; // 'color' or 'colour'
let range = /\d{3,5}/; // 3 to 5 digits
let exact = /\d{5}/; // Exactly 5 digits
let minimum = /\d{3,}/; // 3 or more digits
let zeroOrMore = /\d*/; // Zero or more digits
let oneOrMore = /\d+/; // One or more digits
```

### Advanced Features

#### Capturing Groups

```javascript
// Basic capturing
let datePattern = /(\d{4})-(\d{2})-(\d{2})/;
let match = "2025-08-23".match(datePattern);
// match[0] = "2025-08-23" (full match)
// match[1] = "2025" (year)
// match[2] = "08" (month)
// match[3] = "23" (day)

// Named capturing groups
let namedPattern = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;
let namedMatch = "2025-08-23".match(namedPattern);
// namedMatch.groups.year = "2025"
// namedMatch.groups.month = "08"
// namedMatch.groups.day = "23"

// Non-capturing groups
let nonCapturing = /(?:Mr|Mrs|Ms)\.\s+(\w+)/;
let name = "Mr. Smith".match(nonCapturing);
// name[1] = "Smith" (only the name is captured, not the title)
```

#### Lookahead and Lookbehind

```javascript
// Positive lookahead
let strongPassword =
  /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;
// Must contain: lowercase, uppercase, digit, special char, min 8 chars

// Negative lookahead
let notJavaScript = /\bJava(?!Script)\b/; // "Java" but not "JavaScript"

// Positive lookbehind
let dollarAmount = /(?<=\$)\d+/; // Numbers preceded by $

// Negative lookbehind
let notNegativeNumbers = /(?<!-)\d+/; // Numbers not preceded by -
```

### ES2025 Enhanced Features

#### Inline Modifier Flags

```javascript
// Apply flags to specific sections (ES2025)
const beatlesSearchRegex = /(?i:Love)|(?-i:Day)/;
// Case-insensitive "Love", case-sensitive "Day"

let lyrics = ["All You Need Is Love", "A Hard Day's Night", "love me do"];
let matches = lyrics.filter((lyric) => beatlesSearchRegex.test(lyric));
// Matches: "All You Need Is Love", "love me do" (not "A Hard Day's Night")
```

#### RegExp.escape() for Security

```javascript
// Prevent regex injection attacks (ES2025)
function createSearchPattern(userInput) {
  let escapedInput = RegExp.escape(userInput);
  return new RegExp(escapedInput, "gi");
}

// Safe handling of user input
let userSearch = "user.input[with]special*chars";
let safePattern = createSearchPattern(userSearch);
// Automatically escapes special regex characters
```

## Real-World Applications

### Email Validation

```javascript
const emailRegex =
  /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\.[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$/;

function validateEmail(email) {
  return emailRegex.test(email);
}

console.log(validateEmail("user@example.com")); // true
console.log(validateEmail("invalid.email")); // false
```

### URL Parsing

```javascript
const urlRegex = /^(https?):\/\/([^\/\s]+)(\/[^\s]*)?$/;

function parseURL(url) {
  let match = url.match(urlRegex);
  if (match) {
    return {
      protocol: match[1],
      domain: match[2],
      path: match[3] || "/",
    };
  }
  return null;
}

console.log(parseURL("https://example.com/path"));
// { protocol: "https", domain: "example.com", path: "/path" }
```

### Phone Number Formatting

```javascript
function formatPhoneNumber(phone) {
  // Remove all non-digits
  let cleaned = phone.replace(/\D/g, "");

  // Apply US phone format
  let match = cleaned.match(/^(\d{3})(\d{3})(\d{4})$/);
  if (match) {
    return `(${match[1]}) ${match[2]}-${match[3]}`;
  }
  return phone; // Return original if invalid
}

console.log(formatPhoneNumber("1234567890")); // "(123) 456-7890"
console.log(formatPhoneNumber("123-456-7890")); // "(123) 456-7890"
```

### Data Extraction

```javascript
function extractHashtags(text) {
  let hashtagRegex = /#[\w]+/g;
  return text.match(hashtagRegex) || [];
}

function extractMentions(text) {
  let mentionRegex = /@[\w]+/g;
  return text.match(mentionRegex) || [];
}

let tweet = "Learning #JavaScript and #WebDev with @teacher @mentor!";
console.log(extractHashtags(tweet)); // ["#JavaScript", "#WebDev"]
console.log(extractMentions(tweet)); // ["@teacher", "@mentor"]
```

## Common Pitfalls & Performance Considerations

### Catastrophic Backtracking Prevention

```javascript
// ❌ Problematic - can cause catastrophic backtracking
let badRegex = /^(\w+\s?)*$/;

// ✅ Better - more specific and efficient
let goodRegex = /^(\w+\s)*\w*$/;

// ❌ Avoid nested quantifiers
let dangerous = /^(a+)+$/;

// ✅ Use possessive quantifiers or atomic groups when available
let safer = /^a+$/;
```

### Memory and Performance

```javascript
// ❌ Don't recreate regex in loops
function processItems(items) {
  for (let item of items) {
    if (/^\d+$/.test(item)) {
      // Creates new regex each iteration
      // process
    }
  }
}

// ✅ Define regex outside loop
function processItems(items) {
  const digitRegex = /^\d+$/;
  for (let item of items) {
    if (digitRegex.test(item)) {
      // Reuses compiled regex
      // process
    }
  }
}
```

## Gotchas & Best Practices

### Global Flag State Management

```javascript
let globalRegex = /test/g;

// ❌ Global regex maintains state - can cause issues
console.log(globalRegex.test("test")); // true
console.log(globalRegex.test("test")); // false (lastIndex moved)

// ✅ Reset lastIndex or create new instances
globalRegex.lastIndex = 0;
console.log(globalRegex.test("test")); // true

// ✅ Or use string methods that reset automatically
console.log("test".match(/test/g)); // ["test"] - always works
```

### Escaping Special Characters

```javascript
// ❌ Unescaped special characters
let pattern = /3.14/; // Matches "3X14", "3 14", etc.

// ✅ Properly escaped
let pattern = /3\.14/; // Matches only "3.14"

// ✅ Use RegExp.escape() for dynamic patterns (ES2025)
let userInput = "3.14";
let pattern = new RegExp(RegExp.escape(userInput));
```

### Unicode and Internationalization

```javascript
// ✅ Use Unicode flag for proper character handling
let unicodeRegex = /\p{L}+/u; // Matches letters in any language
let emojiRegex = /\p{Emoji}/u; // Matches emoji characters

console.log("café".match(/\p{L}+/u)); // ["café"]
console.log("🎉".match(/\p{Emoji}/u)); // ["🎉"]
```

## Currency & Verification

### Latest Information Sources

- **Last Verified:** August 23, 2025
- **ES2025 Features:** RegExp.escape(), inline modifier flags
- **Browser Support:** Modern browsers (Chrome 90+, Firefox 88+, Safari 14+)
- **Node.js Support:** v16+ for full ES2025 regex features

### Version Compatibility

```javascript
// Check for ES2025 regex features
if (typeof RegExp.escape === "function") {
  // Use modern secure escaping
  let pattern = new RegExp(RegExp.escape(userInput));
} else {
  // Fallback for older environments
  let pattern = new RegExp(userInput.replace(/[.*+?^${}()|[\]\\]/g, "\\$&"));
}
```

## Related Concepts

- [[js.core_concepts.strings]] - String manipulation methods
- [[js.core_concepts.methods.match]] - String.match() method details
- [[js.core_concepts.methods.replace]] - String.replace() method details
- [[js.security.input_validation]] - Using regex for security
- [[js.performance.optimization]] - Regex performance considerations

## References

- [MDN Regular Expressions Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions) - Comprehensive official documentation
- [JavaScript.info Regex Tutorial](https://javascript.info/regular-expressions) - Detailed learning resource with examples
- [ECMAScript 2025 Specification](https://tc39.es/ecma262/) - Official language specification
- [RegExr Interactive Tool](https://regexr.com/) - Test and visualize regex patterns
- [Regex101](https://regex101.com/) - Advanced regex testing and explanation tool
