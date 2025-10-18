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

## 📘 Data Types & Type Checking

---

### **Q11 - What is the use of `isNaN`, and how is it different from `Number.isNaN()`?**

In JavaScript, both are used to check whether a value is **NaN (Not a Number)** — but they behave differently due to **type coercion**.

| Function | Description | Type Coercion | Example |
|-----------|--------------|----------------|----------|
| `isNaN(x)` | Converts the input to a number first, then checks if it’s `NaN`. | ✅ Yes | `isNaN("foo") → true` |
| `Number.isNaN(x)` | Returns `true` **only if** the value is **exactly `NaN`**. | ❌ No | `Number.isNaN("foo") → false` |

#### ✅ Examples:

```javascript
Number.isNaN(NaN);             // true
Number.isNaN("foo");           // false  (string, not NaN)
isNaN("foo");                  // true   (coerces "foo" → NaN)

Number.isNaN(undefined);       // false
isNaN(undefined);              // true   (undefined → NaN)

Number.isNaN("");              // false
isNaN("");                     // false  ("" → 0)

Number.isNaN(0/0);             // true   (is NaN)
isNaN(0/0);                    // true
```

---

### **Q13 - What is Negative Infinity?**

**Negative Infinity** (`-Infinity`) is a constant value that represents the **lowest possible numeric value** in JavaScript.  
It occurs when a number is **divided by zero in a negative direction**.

#### ✅ Example:
```javascript
console.log(-1 / 0); // -Infinity
console.log(Number.NEGATIVE_INFINITY); // -Infinity
```

🧠 **Notes:**
- No number is smaller than `-Infinity`.
- It is of type `number`.
- It can be compared, e.g., `(-Infinity < 0)` returns `true`.

---

### **Q14 - Why is `typeof null === "object"`?**

This is a **long-standing bug** in JavaScript’s original design that cannot be fixed without breaking compatibility.

- `null` is a **primitive value**, not an object.
- Historically, values in memory were tagged; `null` had a zero tag (same as an object reference), so it mistakenly reports as `"object"`.

#### ✅ Example:
```javascript
typeof null; // "object"
```

💡 **Tip:**  
Always check for `null` using:
```javascript
if (value === null) { ... }   // safer
```

---

### **Q16 - What are “Truthy” and “Falsy” values in JavaScript?**

JavaScript evaluates values in a Boolean context (like `if` statements).  
Some values are **falsy**, and everything else is **truthy**.

| Falsy Values | Meaning |
|---------------|----------|
| `false` | Boolean false |
| `0`, `-0`, `0n` | Zero or BigInt zero |
| `""`, `''`, ```` | Empty string |
| `null` | No value |
| `undefined` | Not assigned |
| `NaN` | Not a number |

Everything else (non-empty strings, non-zero numbers, objects, arrays, etc.) is **truthy**.

#### ✅ Example:
```javascript
if ("hello") console.log("Truthy!");  // ✅ Executed
if (0) console.log("Falsy!");         // ❌ Not executed
```

---

### **Q17 - What are Undeclared and Undefined Variables?**

| Term | Description | Example |
|------|--------------|----------|
| **Undefined** | A variable that has been **declared but not assigned** any value. | `let x; console.log(x); // undefined` |
| **Undeclared** | A variable that has **never been declared** using `var`, `let`, or `const`. Accessing it causes a **ReferenceError**. | `console.log(y); // ReferenceError` |

#### ✅ Example:
```javascript
let a;
console.log(a); // undefined

console.log(b); // ❌ ReferenceError: b is not defined
```

🧠 **Note:**  
`typeof undeclaredVar` returns `"undefined"` instead of throwing an error:
```javascript
console.log(typeof undeclaredVar); // "undefined"
```

---

### **Q21 - What do you mean by Null in JavaScript?**

`null` is a **primitive value** representing **no value** or **no object**.  
It’s an **intentional absence** of any object or value.

#### ✅ Example:
```javascript
let data = null; // explicitly no value
console.log(data); // null
console.log(typeof data); // "object" (historical bug)
```

---

### **Q24 - What is the difference between `null` and `undefined` in JavaScript?**

| Feature | `undefined` | `null` |
|----------|--------------|--------|
| Type | Primitive | Primitive |
| Meaning | Variable declared but not assigned | Explicitly no value |
| Assigned by | JavaScript engine | Developer |
| Use case | Default placeholder | Intentional emptiness |

#### ✅ Example:
```javascript
let x;
console.log(x); // undefined

let y = null;
console.log(y); // null
```

🧠 **Analogy:**
- `undefined` → “value not assigned yet”
- `null` → “value intentionally empty”

---

### **Q35 - Does JavaScript support automatic type conversion?**

✅ **Yes.**  
JavaScript automatically converts values between types when needed — this is called **type coercion**.

#### ✅ Example:
```javascript
console.log("5" + 1);  // "51" (number → string)
console.log("5" - 1);  // 4   (string → number)
console.log(true + 1); // 2   (boolean → number)
```

🧠 **Note:**  
Automatic type conversion makes JavaScript flexible but can cause **unexpected results**, especially during equality checks (`==`).

---
---

## 📘 JavaScript Fundamentals

---

### **Q3 - What’s new in ECMAScript 2025 (ES2025)?**

ECMAScript 2025 introduces several **new features** to improve functionality, readability, and asynchronous handling:

- **`Promise.withResolvers()`** → Returns a promise along with its `resolve` and `reject` functions, simplifying asynchronous control.
- **Immutable Array Methods** → New methods like `findLast()`, `toReversed()`, and `toSorted()` return **new arrays** instead of mutating originals.
- **RegExp `v` flag** → Improves **Unicode handling** in regular expressions.
- **Hashbang Grammar** → Officially allows `#!` at the start of JS files for **CLI scripts**.

---

### **Q4 - Is JavaScript compiled or interpreted?**

- JavaScript is **mostly interpreted**, but modern engines use **Just-In-Time (JIT) compilation** for better performance.
- Execution flow:
  1. Browser reads code line by line and interprets it.
  2. Modern engines (like Chrome’s **V8**) convert parts of code into machine code during runtime for **faster execution**.

---

### **Q5 - Are JavaScript and Java related?**

No — they are **completely different languages**. Despite the similar names, they differ in syntax, typing, and usage.

| Feature | Java | JavaScript |
|---------|------|------------|
| Typing | Strongly typed, compile-time type checking | Loosely typed, dynamic type checking |
| Purpose | Enterprise applications, object-oriented | Web scripting, dynamic interactive pages |
| Runtime | Runs on JVM or browser | Originally browser only, now also server-side via Node.js |
| Objects | Class-based | Prototype-based |

---

### **Q29 - Is JavaScript statically typed or dynamically typed?**

JavaScript is **dynamically typed**:

- Variable types are determined **at runtime**.
- You do not need to declare the type when creating a variable; JavaScript infers it automatically.

#### ✅ Example:
```javascript
let value = 42;    // number
value = "Hello";   // string
```

---

### **Q39 - Is JavaScript single-threaded or multi-threaded?**

- JavaScript is **single-threaded** — it runs on a single main thread, executing one command at a time.
- **Asynchronous features** (like `setTimeout`, Promises, and async/await) allow handling **multiple tasks efficiently** without blocking the main thread.

#### ✅ Example:
```javascript
console.log("Start");

setTimeout(() => {
    console.log("Async task");
}, 0);

console.log("End");

// Output:
// Start
// End
// Async task
```

---

### **Q54 - What is the difference between synchronous and asynchronous execution in JavaScript?**

| Execution Type | Description | Example |
|----------------|-------------|---------|
| **Synchronous** | Code runs **line by line**, blocking subsequent code until current execution finishes. | `console.log("A"); console.log("B");` → Output: A B |
| **Asynchronous** | Code runs **independently of the main thread**, allowing other operations to continue while waiting. | `setTimeout(() => console.log("C"), 1000); console.log("D");` → Output: D C |

- **Synchronous** → predictable sequence, may cause blocking.
- **Asynchronous** → non-blocking, used for I/O operations, timers, and network requests.

---
---

