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


#  **Operators & Comparisons**

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

# Variables & Scope

---

### **Q8 - What’s the difference between `var`, `let`, and `const` and what is the Temporal Dead Zone (TDZ)?**

JavaScript provides three ways to declare variables — **`var`**, **`let`**, and **`const`**, but they differ in **scope**, **hoisting behavior**, and **re-assignment rules**.

| Keyword | Scope Type | Re-declaration | Re-assignment | Hoisting | Block Scope |
|----------|-------------|----------------|----------------|-----------|--------------|
| `var`   | Function / Global | ✅ Allowed | ✅ Allowed | ✅ (initialized with `undefined`) | ❌ |
| `let`   | Block | ❌ Not Allowed (in same block) | ✅ Allowed | ⚠️ Hoisted but uninitialized (TDZ) | ✅ |
| `const` | Block | ❌ Not Allowed | ❌ Not Allowed | ⚠️ Hoisted but uninitialized (TDZ) | ✅ |

#### ✅ Example:

```javascript
// var: function or global scope, can be re-declared and updated
var x = 10;
var x = 20; // re-declaration allowed
console.log("var:", x); // 20

// let: block scope, can be updated but not re-declared in same block
let y = 30;
// let y = 40; // ❌ Error - can't re-declare in same block
y = 40; // ✅ update allowed
console.log("let:", y); // 40

// const: block scope, cannot be reassigned
const z = 50;
// z = 60; // ❌ Error - can't reassign
console.log("const:", z); // 50
```

#### ⚡ Temporal Dead Zone (TDZ)

The **Temporal Dead Zone** is the period between entering a scope and the actual declaration of a `let` or `const` variable.  
During this time, accessing the variable results in a **ReferenceError**, even though the variable is hoisted.

```javascript
// TDZ example
console.log(a); // ❌ ReferenceError (a is in TDZ)
let a = 10;

console.log(b); // ✅ undefined (var is initialized during hoisting)
var b = 10;
```

---

### **Q9 - What is a Variable Scope in JavaScript?**

A **variable’s scope** determines **where** it can be accessed or modified in your code.

#### 🧭 Types of Scope:

1. **Global Scope** – Declared outside any function or block and accessible everywhere.  
2. **Local Scope** – Declared inside a function or block; accessible only within it.  
3. **Function Scope** – Variables declared with `var` inside a function exist only in that function.  
4. **Block Scope** – Variables declared with `let` or `const` are confined to that block (`if`, `for`, `{}` etc.).

#### ✅ Example:
```javascript
var globalVar = "I'm global";

function example() {
  let localVar = "I'm local";
  console.log(globalVar); // ✅ accessible
  console.log(localVar);  // ✅ accessible
}
example();

console.log(globalVar); // ✅ accessible
// console.log(localVar); ❌ ReferenceError (not accessible outside)
```

---

### **Q10 - What is the difference between Lexical and Dynamic Scoping?**

#### 🧩 **Lexical Scoping (Static Scoping)**

- Scope is **determined by where variables are written** in the code.  
- JavaScript uses **lexical scoping**.  
- Functions can access variables from the outer scope **where they are defined**, not from where they are called.

```javascript
let name = "Outer";

function outer() {
  let name = "Inner";
  function show() {
    console.log(name);
  }
  show(); // Output: Inner (lexical scope)
}

outer();
```

#### 🔄 **Dynamic Scoping (Not used in JS)**

- Scope depends on **the call stack at runtime**, not the code position.  
- Used in some languages like **Bash** or **older Lisp**.  
- The called function would use variables from the **caller’s environment**, not its own lexical scope.

---

### **Q40 - What is Lexical Scope in JavaScript?**

**Lexical scope** means a variable’s accessibility is determined by its **position in the source code**, not during execution.

- Functions can access variables in their **own scope** and **outer scopes**, but not inner ones.
- Inner functions “remember” the environment where they were defined — this concept also underlies **closures**.

#### ✅ Example:
```javascript
let outer = "I am outside!";

function inner() {
    console.log(outer); // ✅ Accessible due to lexical scoping
}

inner(); // Output: I am outside!
```

---

### **Q44 - What is called Variable Typing in JavaScript?**

**Variable typing** in JavaScript means a variable can **hold values of different data types** at different times — JavaScript is **dynamically typed**.

#### ✅ Example:
```javascript
let geek = 42;             // Number
geek = "GeeksforGeeks";    // String
console.log(geek);         // Output: GeeksforGeeks
```

📘 This flexibility makes JavaScript easy to use but can also lead to unexpected type coercions.

---
---
