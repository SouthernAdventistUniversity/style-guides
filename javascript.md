# Javascript Style Guide

## Table of Contents
1. [Formatting](#formatting)
2. [Lanuage Features](#language-features)
3. [Naming](#naming)
4. [JSDoc](#jsdoc)

## 1. Formatting

### 1.1 Braces
Braces are required for all control structures (i.e. `if`, `else`, `for`, `do`, `while`, as well as any others), even if the body contains only a single statement. The first statement of a non-empty block must begin on its own line.

**Exception:** A simple `if` statement that can fit on one line (with no `else`).
`if  (shortCondition()) foo();`

### 1.2 Vertical Whitespace
A single blank line should appear:
1. Between class methods, object literals, and back-to-back function declarations.

### 1.3 Horizontal Whitespace
Trailing (at the end of a line) whitespace is forbidden.

Internal whitespace (single ASCII space) should appear in the following places:
1.  Separating any reserved word (such as  `if`,  `for`, or  `catch`) except for  `function`  and  `super`, from an open parenthesis (`(`) that follows it on that line.
2.  Separating any reserved word (such as  `else`  or  `catch`) from a closing curly brace (`}`) that precedes it on that line.
3.  Before any open curly brace (`{`), with two exceptions:
    1.  Before an object literal that is the first argument of a function or the first element in an array literal (e.g.  `foo({a: [{c: d}]})`).
4.  On both sides of any binary or ternary operator.

### 1.4 Horizontal Alignment
**Permitted, but discouraged:** additional spaces to horizontally align tokens between one line and the next.
```js
{
	tiny: 42, // this is great
	longer: 435, // this too 
};
{
	tiny:   42, // permitted, but future edits
	longer: 435, // may leave it unaligned
};
```

## 2. Language Features

### 2.1 Local Variable Declaration
#### 2.1.1 Use `const` and `let`
Declare all local variables with either `const` or `let`. Use const by default, unless a variable needs to be reassigned. The `var` keyword must not be used.

#### 2.1.2 One variable per declaration
Every local variable declaration declares only one variable: declarations such as  `let a = 1, b = 2;`  are not used.

#### 2.1.3 Declare types as needed
JSDoc type annotations may be added either on the line above the declaration, or else inline before the variable name if no other JSDoc is present.

Example:
```js
const /** !Array<number> */ data = [];

/**
 * Some description.
 * @type {!Array<number>}
 */
const data = [];
```

### 2.2 Array/Object Literals

#### 2.2.1 Use Trailing Commas
Include a trailing comma whenever there is a line break between the final element and the closing bracket.

Example:
```js
const values = [
	'first value',
	'second value',
];

// or

const values = {
	'first': value,
	'second': value,
};
```

#### 2.2.2 Do not use `Array` or `Object` constructors
`Array()` is error prone and `Object` is not used to maintain consistency.

**Use literals instead.**

Example:
```js
const foo = ['a', 'b'];

// or

const bar = {a: 0, b: 1};
```

#### 2.2.3 Object Keys
Object literals may represent either  _structs_  (with unquoted keys and/or symbols) or  _dicts_  (with quoted and/or computed keys). Do not mix these key types in a single object literal.

**Disallowed:**
```js
{
	width: 42, // struct-style unquoted key
	'maxWidth': 43, // dict-style quoted key
}
```

This also extends to passing the property name to functions, like  `hasOwnProperty`. In particular, doing so will break in compiled code because the compiler cannot rename/obfuscate the string literal.

**Disallowed:**
```js
/** @type {{width: number, maxWidth: (number|undefined)}} */
const o = {width: 42};
if (o.hasOwnProperty('maxWidth')) {
...
}
```

**This is best implemented as:**
```js
/** @type {{width: number, maxWidth: (number|undefined)}} */
const o =  {width: 42};
if (o.maxWidth != null) {
...
}
```
