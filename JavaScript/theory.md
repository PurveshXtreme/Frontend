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

# Data Types & Type Checking

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

# JavaScript Fundamentals

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

# DOM Manipulation & HTML Access

---

### **Q6 - How many ways can an HTML element be accessed in JavaScript?**

JavaScript provides multiple methods to access HTML elements:

1. **`getElementById()`** → Selects an element by its **unique ID**.
2. **`getElementsByClassName()`** → Selects all elements with the specified **class name**.
3. **`getElementsByTagName()`** → Selects all elements with the given **tag name**.
4. **`querySelector()`** → Returns the **first element** that matches a **CSS selector**.
5. **`querySelectorAll()`** → Returns **all elements** matching a CSS selector (NodeList).

#### ✅ Example:
```javascript
const elementById = document.getElementById("myId");
const elementsByClass = document.getElementsByClassName("myClass");
const elementsByTag = document.getElementsByTagName("div");
const firstQuery = document.querySelector(".myClass");
const allQuery = document.querySelectorAll(".myClass");
```

---

### **Q34 - How to submit a form using JavaScript?**

You can submit a form programmatically using the `.submit()` method.

#### ✅ Example:
```javascript
// Accessing the first form in the document
document.forms[0].submit();
```

- This triggers the form submission **without requiring a user click**.
- Ensure proper validation before programmatic submission.

---

### **Q47 - What are the types of pop-up boxes available in JavaScript?**

JavaScript supports three types of **pop-up dialog boxes**:

1. **Alert Box** → Displays a simple message.
2. **Confirm Box** → Asks for **user confirmation** (OK/Cancel).
3. **Prompt Box** → Requests **user input**.

#### ✅ Example:
```javascript
alert("Hello!");              // Alert
let confirmResult = confirm("Are you sure?"); // Confirm
let name = prompt("Enter your name:");       // Prompt
```

---

### **Q68 - What is event bubbling and capturing in JavaScript? Explain event delegation.**

#### **Event Bubbling**
- Events start from the **target element** and **bubble up** to parent elements.
- Default mode in JavaScript event handling.

```javascript
parent.addEventListener("click", () => console.log("Parent clicked"));
child.addEventListener("click", () => console.log("Child clicked"));
```
- Clicking on the child triggers:  
  `Child clicked → Parent clicked`

#### **Event Capturing**
- Events **start from the outermost element** and go **down to the target element**.
- Set by passing `{ capture: true }` in `addEventListener`.

```javascript
parent.addEventListener("click", () => console.log("Parent clicked"), true);
```

#### **Event Delegation**
- Technique to attach a **single event listener** to a parent element, instead of multiple child elements.
- Uses **event bubbling** to handle events from child elements dynamically.

```javascript
document.getElementById("parent").addEventListener("click", (e) => {
    if(e.target && e.target.matches("button.className")) {
        console.log("Button clicked:", e.target.textContent);
    }
});
```

✅ **Advantages:**
- Efficient for dynamic elements.
- Reduces memory consumption.
- Easier to manage.

---
---

# Operators & Special Syntax

---

### **Q12 - What does this code log? (Array Sparse Elements)**

```javascript
const arr = [1, 2, 3];
arr[10] = 99;
console.log(arr.length); // Output: 11
```

**Explanation:**

- Assigning a value to `arr[10]` creates **empty slots** from index 3 to 9.
- The `length` property is automatically updated to **highest index + 1** → `10 + 1 = 11`.
- Sparse arrays contain **undefined/empty elements** in unassigned indexes.

---

### **Q15 - Is it possible to break JavaScript code into several lines?**

Yes, JavaScript **allows breaking statements into multiple lines**, but care must be taken to avoid **automatic semicolon insertion issues**.

#### Using newline in a string:
```javascript
console.log("A Online Computer Science Portal\nfor Geeks");
```

#### Breaking expressions over multiple lines:
```javascript
let gfg = 10, GFG = 5,
    Geeks = gfg + GFG;
console.log(Geeks); // 15
```

✅ **Tip:** Avoid splitting statements where **JavaScript might insert semicolons automatically**, as it may cause runtime errors.

---

### **Q18 - What will be the result of this expression? (Nullish Coalescing)**

```javascript
console.log(null ?? 'default');      // 'default'
console.log(undefined ?? 'default'); // 'default'
console.log(false ?? 'default');     // false
```

**Explanation:**

- The **nullish coalescing operator (`??`)** returns the **right-hand value only if the left-hand side is `null` or `undefined`**.
- It **does not treat `false`, `0`, or `""` as nullish**.

---

### **Q22 - How to delete property-specific values?**

The `delete` operator removes a **property from an object**, along with its value.

```javascript
let gfg = { Course: "DSA", Duration: 30 };
delete gfg.Course;
console.log(gfg); // { Duration: 30 }
```

✅ **Note:** You cannot delete variables declared with `let`, `const`, or `var`.

---

### **Q25 - What are template literals and when do you use them?**

Template literals are **strings enclosed in backticks (`)** with enhanced features:

1. **Expression Interpolation** → `${expression}`
2. **Multi-line strings** → Preserve line breaks naturally
3. **Tagged templates** → Customize string processing (e.g., i18n, sanitization)

#### ✅ Example:
```javascript
const name = "Geeks";
const msg = `Hello, ${name}!
Your total is $${(19.99 * 2).toFixed(2)}.`;

console.log(msg);
/* Output:
Hello, Geeks!
Your total is $39.98.
*/
```

---

### **Q36 - What is a template literal in JavaScript?**

- A **template literal** allows **multi-line strings** and **embedded expressions**.
- Uses **backticks** (`) instead of single/double quotes.
- Supports `${}` to insert **variables or expressions** inside strings.

#### ✅ Example:
```javascript
let a = 5, b = 10;
console.log(`Sum of ${a} + ${b} = ${a + b}`); // Sum of 5 + 10 = 15
```

---

### **Q55 - What are default parameters in JavaScript functions? (extra)**

Default parameters allow a function to **assign default values** to arguments if no value or `undefined` is passed.

#### ✅ Example:
```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet("Alice"); // Hello, Alice!
greet();        // Hello, Guest!
```

- Useful for **avoiding `undefined` values**.
- Can be combined with **expressions or other parameters**.

---
---

# Functions & Scope

---

### **Q20 - What are global variables? How are these variables declared, and what are the problems associated with them?**

- **Global variables** are declared **outside any function** and have **global scope**.
- They can be accessed and modified by **any function** in the program.

#### ✅ Example:
```javascript
let petName = "Rocky"; // Global Variable

myFunction();

function myFunction() {
    console.log("Inside myFunction - Type of petName:", typeof petName);
    console.log("Inside myFunction - petName:", petName);
}

console.log("Outside myFunction - Type of petName:", typeof petName);
console.log("Outside myFunction - petName:", petName);

/* Output:
Inside myFunction - Type of petName: string
Inside myFunction - petName: Rocky
Outside myFunction - Type of petName: string
Outside myFunction - petName: Rocky
*/
```

- **Problems with global variables:**
  - Harder to debug and maintain.
  - Can be accidentally overwritten by other functions.
  - Breaks modularity and increases dependency across code.

---

### **Q37 - What is a higher-order function in JavaScript?**

A **higher-order function** is a function that:

- Takes **one or more functions as arguments**, or
- Returns a **function** as its result.

They enable **reusable and abstract code**, often used in functional programming.

#### Examples:
```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2); // map is higher-order
const evens = numbers.filter(num => num % 2 === 0); // filter is higher-order
```

---

### **Q38 - What is the difference between `call()` and `apply()` methods?**

Both methods **invoke a function with a specified `this` value** but differ in how they pass arguments:

| Method | Arguments | Execution |
|--------|-----------|-----------|
| **call()** | Individual arguments | Invokes the function immediately |
| **apply()** | Arguments as an **array** | Invokes the function immediately |

#### Example:
```javascript
function greet(greeting, punctuation) {
    console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "Alice" };

greet.call(person, "Hello", "!");      // Hello, Alice!
greet.apply(person, ["Hi", "!!"]);     // Hi, Alice!!
```

---

### **Q50 - How do `call`, `apply`, and `bind` change `this`?**

- **`call`** → Invokes the function **immediately**, sets `this` to the first argument; passes remaining arguments individually.
- **`apply`** → Invokes the function **immediately**, sets `this` to the first argument; passes remaining arguments as an **array**.
- **`bind`** → Returns a **new function** with `this` permanently set; can pre-fill arguments, but does **not execute immediately**.

#### Example:
```javascript
function greet(greeting) {
    console.log(`${greeting}, ${this.name}`);
}

const person = { name: "Alice" };
const greetAlice = greet.bind(person, "Hello"); // bind returns a function
greetAlice(); // Hello, Alice
```

---

### **Q53 - How to explain closures in JavaScript and when to use it?**

A **closure** is created when an **inner function retains access to the outer function’s variables**, even after the outer function has executed.

- Provides **encapsulation** and **private variables**.
- Useful for **maintaining state** and **functional patterns**.

#### Example:
```javascript
function foo() { 
    let b = 1; 
    function inner() { 
        return b; 
    } 
    return inner; 
} 

let get_func_inner = foo(); 

console.log(get_func_inner()); // 1
console.log(get_func_inner()); // 1
console.log(get_func_inner()); // 1
```

---

### **Q56 - What is an IIFE (Immediately Invoked Function Expression)? Why and when is it used?** (extra)

- An **IIFE** is a function that runs **immediately after its definition**.
- Commonly used to **create private scopes** and **avoid polluting the global namespace**.

#### Example:
```javascript
(function() {
    let privateVar = "I am private";
    console.log(privateVar);
})(); // I am private
```

---

### **Q57 - What is the difference between function declaration and function expression?** (extra)

| Feature | Function Declaration | Function Expression |
|---------|-------------------|-------------------|
| Syntax | `function foo() {}` | `const foo = function() {};` |
| Hoisting | Hoisted, can be called **before definition** | Not hoisted, must be defined before use |
| Name | Must have a name | Can be anonymous |
| Usage | Standard function | Assignable to variables, can be passed as arguments |

---

### **Q58 - What are arrow functions, and how are they different from regular functions?** (extra)

- **Arrow functions** are a concise syntax for defining functions:

```javascript
const add = (a, b) => a + b;
```

- **Differences from regular functions:**
  1. **`this` is lexically scoped** (inherits from surrounding context).
  2. Cannot be used as **constructors** (`new` keyword fails).
  3. No `arguments` object; use **rest parameters** instead.
  4. Syntax is **more concise**, especially for single expressions.

```javascript
const obj = {
    value: 10,
    regular: function() { console.log(this.value); },
    arrow: () => { console.log(this.value); }
};

obj.regular(); // 10
obj.arrow();   // undefined (lexical this)
```

---
---

# The 'this' Keyword

---

### **Q30 - What is the 'this' keyword in JavaScript?**

- The `this` keyword **stores the current execution context** of the code.
- Its value changes depending on **how and where the function is invoked**.

#### Examples:

```javascript
// 1. Global scope
console.log(this); // window (in browser)

// 2. Inside an object method
const obj = {
  name: "JS",
  say() {
    console.log(this.name);
  }
};
obj.say(); // "JS"

// 3. Regular function
function test() {
  console.log(this);
}
test(); // window (or undefined in strict mode)

// 4. Arrow function
const arrow = () => console.log(this);
arrow(); // inherits from outer scope (global -> window)

// 5. Constructor function
function Person(name) {
  this.name = name;
}
const p = new Person("Alice");
console.log(p.name); // "Alice"
```

> **Key takeaway:** `this` changes based on **function type**, **invocation method**, and **execution context**.

---

### **Q41 - What is the `this` keyword, and how does the call-site affect it?**

The value of `this` depends on the **call-site** (how and where a function is called).

- **Global / Function context**:
  - Non-strict mode → `this` refers to the global object (`window` in browsers)
  - Strict mode → `this` is `undefined`
- **Object method** → `this` refers to the object that owns the method
- **Constructor function / class** → `this` refers to the newly created instance
- **Explicit binding** → `call()`, `apply()`, or `bind()` can set `this` explicitly
- **Arrow functions** → `this` is **lexically inherited** from surrounding scope

---

### **Q42 - How does lexical scoping work with the `this` keyword in JavaScript?**

- **Lexical scoping** affects variable resolution based on the **location in source code**.
- **`this` behavior** is determined dynamically by **how a function is called**, not by its lexical position.

#### Example:

```javascript
const obj = {
    name: "JavaScript",
    greet: function () {
        console.log(this.name);
    }
};
obj.greet(); // "JavaScript"
```

- Here, `this` refers to `obj` because the function is called as an **object method**.
- Lexical scoping affects variable lookups, but **does not alter `this` behavior**.

---
---

# Asynchronous JavaScript

---

### **Q31 - Explain the working of timers in JavaScript. Also explain the drawbacks of using the timer, if any.**

JavaScript provides timers to schedule tasks **after a delay** or **at regular intervals**. Timers are part of the **Web APIs (browser)** or **Node.js environment**, not the JS engine itself.

#### 1. `setTimeout`

- Executes a function **once** after a specified delay (in milliseconds).

```javascript
setTimeout(() => {
  console.log("Runs after 2 seconds");
}, 2000);
```

#### 2. `setInterval`

- Executes a function **repeatedly** at a specified interval until cleared.

```javascript
let count = 0;
const intervalId = setInterval(() => {
  count++;
  console.log("Runs every 1 second");
  if (count === 3) clearInterval(intervalId); // stop after 3 runs
}, 1000);
```

#### 3. `clearTimeout` / `clearInterval`

- Used to stop a scheduled timer.

```javascript
const id = setTimeout(() => console.log("Won't run"), 3000);
clearTimeout(id); // cancels the timer
```

**Drawbacks:**

- Timers are **not precise** due to event loop delays.
- Can **waste resources** if misused.
- Must be **cleared properly** to avoid memory leaks.

---

### **Q32 - What will be logged by this code?**

```javascript
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), i * 100);
}
```

**Output:**

```
0
1
2
```

**Explanation:**

- Using `let i` in the loop gives **each callback its own i binding**.
- The timeouts fire at 0ms, 100ms, and 200ms, logging `0`, `1`, `2`.

---

### **Q52 - Explain the concept of promises and how they work**

- A **Promise** is an object representing the **result of an asynchronous operation**.
- States:
  - **Pending:** Operation not completed yet
  - **Fulfilled / Resolved:** Operation successful
  - **Rejected:** Operation failed
- Created using `new Promise(executor)` where `executor` receives `resolve` and `reject` callbacks.

```javascript
const promise = new Promise((resolve, reject) => {
  let success = true;
  if (success) resolve("Done");
  else reject("Error");
});

promise
  .then((result) => console.log(result))
  .catch((err) => console.error(err));
```

- Promises can be **chained** using `.then()` and `.catch()` for sequential asynchronous tasks.

---

### **Q59 - Explain how the JavaScript event loop works** (extra)

- The **event loop** allows JS to handle **asynchronous operations** despite being single-threaded.
- Steps:
  1. JS executes all **synchronous code** on the **call stack**.
  2. Asynchronous tasks (e.g., timers, I/O) are sent to **Web APIs**.
  3. Once completed, tasks are placed in the **task queue** (macrotasks or microtasks).
  4. The **event loop** moves tasks from the queue to the stack **when the stack is empty**.

---

### **Q60 - What are microtasks and macrotasks in JavaScript? Give examples** (extra)

- **Macrotasks:** Larger tasks scheduled in the **task queue**.
  - Examples: `setTimeout`, `setInterval`, `setImmediate` (Node.js)
- **Microtasks:** High-priority tasks executed **before the next macrotask**, after the current synchronous code.
  - Examples: `Promise.then`, `MutationObserver`

**Execution order:**
1. Execute synchronous code
2. Execute all microtasks
3. Execute one macrotask
4. Repeat

---

### **Q61 - What is the call stack, and how does it work with asynchronous operations?** (extra)

- The **call stack** is a LIFO structure holding **functions currently executing**.
- Synchronous functions are **pushed to the stack** and popped when completed.
- Asynchronous tasks (e.g., timers, Promises) are handled outside the stack and **added to the task queue**.
- The **event loop** ensures that async tasks are executed **only when the stack is empty**.

---
---

# Prototypes & Object Concepts

---

### **Q62 - What is prototypal inheritance in JavaScript?** (extra)

- **Prototypal inheritance** is a feature in JavaScript where **objects can inherit properties and methods from other objects**.
- Every object has an internal link to another object called its **prototype**.
- If a property or method is not found on the object itself, JS looks for it in the **prototype chain**.

```javascript
const parent = {
  greet() {
    console.log("Hello from parent!");
  }
};

const child = Object.create(parent);
child.greet(); // "Hello from parent!"
```

- `child` inherits the `greet` method from `parent` through the prototype chain.

---

### **Q63 - What is the difference between `__proto__` and `prototype`?** (extra)

| Property | Description |
|----------|-------------|
| `prototype` | Exists only on **functions**. Defines the object that will become the **prototype** of instances created by the constructor function. |
| `__proto__` | Exists on **all objects**. Points to the object’s **actual prototype** from which it inherits properties. |

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.sayHello = function() { console.log("Hello!"); };

const p = new Person("Alice");
console.log(p.__proto__ === Person.prototype); // true
```

---

### **Q64 - What are constructor functions and how do they differ from ES6 classes?** (extra)

- **Constructor functions** are regular functions used with the `new` keyword to create objects.

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function() {
  console.log(`Hi, I am ${this.name}`);
};

const p1 = new Person("Alice");
p1.greet(); // Hi, I am Alice
```

- **ES6 classes** are **syntactic sugar** over constructor functions with cleaner syntax:

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hi, I am ${this.name}`);
  }
}

const p2 = new Person("Bob");
p2.greet(); // Hi, I am Bob
```

---
---

# ES6+ Features

---

### **Q65 - What are destructuring assignments and when are they used?** (extra)

- **Destructuring assignment** allows you to unpack values from arrays or properties from objects into distinct variables.
- It makes code cleaner and reduces the need for multiple assignments.

**Array Destructuring:**

```javascript
const arr = [1, 2, 3];
const [a, b, c] = arr;
console.log(a, b, c); // 1 2 3
```

**Object Destructuring:**

```javascript
const user = { name: "Alice", age: 25 };
const { name, age } = user;
console.log(name, age); // Alice 25
```

**Use Cases:**
- Extracting multiple properties from objects/arrays in a concise way.
- Swapping variables without temporary variables.
- Function parameters extraction.

---

### **Q66 - What are rest and spread operators in JavaScript?** (extra)

- **Spread Operator (`...`)**: Expands an iterable (array/object) into individual elements.

```javascript
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];
console.log(arr2); // [1, 2, 3, 4]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };
console.log(obj2); // { a: 1, b: 2, c: 3 }
```

- **Rest Operator (`...`)**: Collects multiple elements into a single array, often used in function parameters.

```javascript
function sum(...numbers) {
  return numbers.reduce((acc, n) => acc + n, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

**Use Cases:**
- Spread: Copying arrays/objects, merging arrays, passing arguments.
- Rest: Collecting remaining elements, variadic functions.

---

### **Q67 - What is the difference between named and default exports in ES6 modules?** (extra)

- **Named Exports**: Multiple values can be exported from a file. Must be imported with the same name inside `{}`.

```javascript
// utils.js
export const add = (a, b) => a + b;
export const sub = (a, b) => a - b;

// main.js
import { add, sub } from './utils.js';
```

- **Default Export**: Only one value can be exported as default. Can be imported with any name.

```javascript
// math.js
export default function multiply(a, b) {
  return a * b;
}

// main.js
import multiplyFunc from './math.js';
console.log(multiplyFunc(2, 3)); // 6
```

---
---

# Advanced Concepts

---

### **Q27 - Can closures leak memory?**

JavaScript **closures** capture variables from their outer scope. However, if not managed properly, they can sometimes cause **memory leaks**.

- **Memory Leak Possibility:** Closures can retain references to variables or objects that are no longer needed, preventing the garbage collector from freeing memory.

---

### **Q28 - Does JavaScript allow multiple inheritance?**

- **Single Inheritance:** JavaScript classes allow extending only **one parent class**.
- **Prototypes:** Objects can inherit from **one prototype** at a time.
- **Mixins:** To mimic multiple inheritance, JavaScript uses **mixins**, which copy properties/methods from other objects or classes.

---

### **Q45 - What is hoisting in JavaScript?**

**Hoisting** is the behavior where variable and function **declarations** are moved to the top of their scope before code execution.

```javascript
console.log(a); // undefined
var a = 5;
```

- Only **declarations** are hoisted, not initializations.
- `var`, `let`, `const`, and **functions** behave differently under hoisting.

---

### **Q48 - What are JavaScript modules, and how do you import/export them?**

JavaScript modules allow splitting code into reusable pieces.

```javascript
// file1.js
export const greet = () => "Hello";

// file2.js
import { greet } from './file1';
console.log(greet()); // "Hello"
```

- **Modules** prevent global namespace pollution.
- Use `export` to share variables/functions and `import` to use them in another file.

---

### **Q49 - Explain the concept of memoization in JavaScript**

**Memoization** is an optimization technique that **caches the results of expensive function calls** for repeated use with the same inputs.

```javascript
const memo = {};
function fibonacci(n) {
  if (memo[n]) return memo[n];
  if (n <= 1) return n;
  memo[n] = fibonacci(n-1) + fibonacci(n-2);
  return memo[n];
}
```

- Reduces repeated computations.
- Improves performance for functions with heavy or repeated calculations.

---

### **Q51 - What is the ‘Strict’ mode in JavaScript and how can it be enabled?**

**Strict Mode** places a program in a stricter operating context.

```javascript
"use strict";

x = 3.14; // Error: x is not declared
```

- Prevents **silent errors**.
- Disallows **undeclared variables**.
- Makes debugging easier.
- Enabled by adding `"use strict";` at the top of a script or function.

---
---

# File Operations

---

### **Q43 - Explain how to read and write a file using JavaScript**

In JavaScript, **file operations** are primarily handled in a **Node.js environment** using the built-in `fs` (File System) module. Browsers do **not** have direct access to the file system for security reasons.

---

### **1. Import the `fs` module**

```javascript
const fs = require('fs');
```

---

### **2. Reading a File**

**Asynchronous Reading (Preferred)**

```javascript
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

**Synchronous Reading**

```javascript
try {
  const data = fs.readFileSync('example.txt', 'utf8');
  console.log(data);
} catch (err) {
  console.error(err);
}
```

- `'utf8'` specifies the **encoding**.
- Asynchronous reading does not block the event loop, while synchronous does.

---

### **3. Writing to a File**

**Asynchronous Writing**

```javascript
const content = "Hello, JavaScript File Handling!";

fs.writeFile('output.txt', content, 'utf8', (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log("File written successfully!");
});
```

**Synchronous Writing**

```javascript
try {
  fs.writeFileSync('output.txt', content, 'utf8');
  console.log("File written successfully!");
} catch (err) {
  console.error(err);
}
```

- Writing **overwrites** the file by default.
- Use `fs.appendFile` or `fs.appendFileSync` to **append** data instead of replacing it.

---
---
