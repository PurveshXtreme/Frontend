![JAVASCRIPT](https://media.geeksforgeeks.org/wp-content/uploads/20250910122507209741/ygfds.webp)

---
---

## 📘 Table of Contents

1. [Operators & Comparisons](#operators--comparisons)
2. [Variables & Scope](#variables--scope)
3. [Data Types & Type Checking](#data-types--type-checking)
4. [JavaScript Fundamentals](#javascript-fundamentals)
5. [DOM Manipulation & HTML Access](#dom-manipulation--html-access)
6. [Operators & Special Syntax](#operators--special-syntax)
7. [Functions & Scope](#functions--scope)
8. [The 'this' Keyword](#the-this-keyword)
9. [Asynchronous JavaScript](#asynchronous-javascript)
10. [Prototypes & Object Concepts](#prototypes--object-concepts)
11. [ES6+ Features](#es6-features)
12. [Advanced Concepts](#advanced-concepts)
13. [State Management](#state-management)
14. [File Operations](#file-operations)

---
---


# 📋 **Operators & Comparisons**

---

## **Q1. What is the difference between == and === in JavaScript?**

In JavaScript, the `==` and `===` operators are used to compare two values, but they work differently in how they treat data types.

| Operator | Name | Type Conversion | Example | Result |
|-----------|------|------------------|----------|---------|
| `==` | Loose Equality | Performs type coercion | `5 == "5"` | ✅ `true` |
| `===` | Strict Equality | No type coercion (compares type + value) | `5 === "5"` | ❌ `false` |

### ✅ Example:
```javascript
console.log(5 == "5");  // true → because "5" is converted to number
console.log(5 === "5"); // false → because types differ (number vs string)
```

**Explanation:**
- `==` → converts both values to a common type before comparing (loose check).
- `===` → checks both **value** and **data type** without conversion (strict check).

---

## **Q2. What would be the result of `3 + 2 + "7"`?**

### 🧩 Code Example:
```javascript
let result = 3 + 2 + "7";
console.log(result);
```

### 🧠 Output:
```
57
```

### 🔍 Explanation:
- Step 1: `3 + 2` → both are numbers → result = `5`
- Step 2: `5 + "7"` → `"7"` is a string, so JS converts `5` to `"5"` → concatenation happens → `"57"`

💡 **Hence, the output is the string `"57"`.**

---

## **Q7. What’s the return-value difference between `x++` and `++x`?**

Both increment the variable by `1`, but differ in **when** they return the value.

| Expression | Name | Operation Order | Returned Value |
|-------------|------|------------------|----------------|
| `x++` | Post-increment | Returns old value → then increments | Old value |
| `++x` | Pre-increment | Increments first → then returns new value | New value |

### ✅ Example:
```javascript
let x = 5;
console.log(x++); // Output: 5 (old value)
console.log(x);   // Output: 6

let y = 5;
console.log(++y); // Output: 6 (new value)
console.log(y);   // Output: 6
```

---

## **Q26. What is the output of this snippet?**

### 🧩 Code Example:
```javascript
const a = [1, 2, 3];
const b = [1, 2, 3];

console.log(a == b, a === b);
```

### 🧠 Output:
```
false false
```

### 🔍 Explanation:
- In JavaScript, arrays are **reference types** (objects).
- Even though `a` and `b` contain the same elements, they are stored at **different memory locations**.
- When comparing objects (including arrays), JavaScript compares **references**, not contents.

Hence:
- `a == b` → ❌ `false`
- `a === b` → ❌ `false`

✅ **To compare array contents**, use:
```javascript
JSON.stringify(a) === JSON.stringify(b); // true
```

---
---

