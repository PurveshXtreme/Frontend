## 💻 What is JavaScript?

**JavaScript** is a high-level, interpreted **programming language** primarily used to make **web pages interactive and dynamic**.

It is one of the core technologies of the web, alongside **HTML** and **CSS**.

---

### ✅ Key Features:

- **Dynamically typed**: You don't need to declare variable types.
- **Event-driven**: Supports responding to user events like clicks or keypresses.
- **Single-threaded**: Executes code in a single thread but can handle async tasks using callbacks, promises, and `async/await`.
- **Interpreted**: Code is executed directly without the need for compilation.
- **Object-oriented**: Supports objects, prototypal inheritance, and classes (from ES6).
- **Lightweight and fast**: Built for running in browsers with minimal overhead.

---

### 🌐 Where is JavaScript Used?

- Frontend development (in the browser)
- Backend development (Node.js)
- Mobile apps (React Native)
- Desktop apps (Electron)
- Game development
- Automation & scripting

---

### 🔑 Summary:
> **JavaScript** is the backbone of modern web development. It runs in browsers, allows dynamic content, and powers everything from simple form validation to full-scale web apps.



## 1. 🔍 Are JavaScript and Java Related?

Although they share similar names, **Java** and **JavaScript** are **completely different** languages with distinct use cases and features.

---

### 🧠 Key Differences Between Java and JavaScript:

| Feature                      | Java                                  | JavaScript                            |
|-----------------------------|----------------------------------------|----------------------------------------|
| **Type System**             | Statically typed                      | Dynamically typed                      |
| **Execution**               | Compiled (to bytecode) + interpreted  | Interpreted (in browser or Node.js)   |
| **Platform**                | Runs on JVM                           | Runs in browser or Node.js            |
| **Inheritance**             | Class-based inheritance               | Prototype-based inheritance           |
| **Concurrency**             | Supports multi-threading              | Single-threaded (with event loop)     |
| **Typing**                  | Strongly typed                        | Weakly typed                          |
| **Object Orientation**      | Fully object-oriented                 | Object-oriented but more flexible     |
| **Garbage Collection**      | Handled by JVM                        | Handled by browser or Node.js         |

---

### 📌 Summary:
> **Java** is a statically typed, class-based, compiled language used for general-purpose programming.  
> **JavaScript** is a dynamically typed, interpreted scripting language primarily used for web development.

Despite the name similarity, they have very different **syntax**, **use cases**, and **execution environments**.


## 2. 🔢 What are Data Types in JavaScript?

In JavaScript, data types are mainly categorized into **two types**:

---

### 🔹 1. Primitive Data Types

The predefined data types provided by JavaScript language are known as primitive data type. Primitive data types are also known as in-built data types.

These are the **basic, immutable** data types built into the language.  
They hold **single values** and are stored by **value**.

| Type       | Description                             |
|------------|-----------------------------------------|
| `Number`   | Numeric values (e.g., `5`, `3.14`)       |
| `String`   | Sequence of characters (e.g., `"hello"`) |
| `Boolean`  | Logical values: `true` or `false`        |
| `Undefined`| A variable declared but not assigned     |
| `Null`     | Represents intentional "no value"        |
| `Symbol`   | Unique and immutable value (ES6)         |
| `BigInt`   | For large integers beyond `Number` range |

---

### 🔸 2. Non-Primitive (Reference) Data Types

The data types that are derived from primitive data types are known as non-primitive data types. It is also known as derived data types or reference data types.

Objects
These are **complex types** derived from primitive types.  
They are stored and accessed by **reference**.

| Type        | Description                                 |
|-------------|---------------------------------------------|
| `Object`    | Key-value pairs (e.g., `{ name: "Purvesh" }`) |
| `Array`     | List-like object (e.g., `[1, 2, 3]`)         |
| `Function`  | Reusable blocks of code                     |

---

### 🧠 Summary:

- **Primitive Types**: Immutable, stored by value
- **Non-Primitive Types**: Mutable, stored by reference

```js
// Primitive Example
let a = 10;
let b = a;
b = 20;
console.log(a); // 10

// Reference Example
let obj1 = { name: "JS" };
let obj2 = obj1;
obj2.name = "React";
console.log(obj1.name); // "React"
```

> Knowing the difference between **primitive** and **reference** types is key to avoiding unexpected bugs in JavaScript.


## 4. What would be the result of 3+2+"7"?
Here, 3 and 2 behave like an integer, and "7" behaves like a string. So 3 plus 2 will be 5. Then the output
will be 5+"7" = 57.



## 🔍 Difference Between Client-Side and Server-Side Languages

Client-side and server-side languages are both essential in web development, but they serve **different purposes** and run in **different environments**.

---

### ⚖️ Key Differences:

| Feature                  | Client-Side Language                         | Server-Side Language                       |
|--------------------------|----------------------------------------------|--------------------------------------------|
| **Execution Location**   | Runs in the user's **browser**               | Runs on the **web server**                 |
| **Examples**             | JavaScript, HTML, CSS                        | PHP, ASP, Node.js, Python (Django), Java   |
| **Speed**                | Faster (no server interaction needed)        | Slower (requires server processing)        |
| **Access to Server**     | Cannot access server/database directly       | Can access server resources & databases    |
| **Security**             | Less secure (code visible to user)           | More secure (code hidden from user)        |
| **Use Cases**            | UI updates, form validation, animations      | Data processing, authentication, APIs      |
| **Internet Required?**   | Can work offline (if cached)                 | Requires internet/server to work           |
| **Visibility**           | Code is visible in browser DevTools          | Code is hidden from the user               |

---

### ✅ Summary:

- **Client-Side Languages** (like JavaScript) handle what users see and interact with directly.
- **Server-Side Languages** (like ASP, PHP, Node.js) handle the logic, database operations, and response generation on the server before sending to the client.

> 📌 JavaScript is faster for UI interactions because it doesn’t rely on the server to execute logic.


## 6. Which is faster in JavaScript and ASP script?

JavaScript is faster compared to ASP Script. JavaScript is a client-side scripting language and does not depend on the server to execute. The ASP script is a server-side scripting language always dependable on the server.


## 7. ➖ What is Negative Infinity in JavaScript?

**Negative Infinity** is a special numeric value in JavaScript that represents the lowest possible number — it is smaller than any other number.

---

### 📌 Key Points:

- Represented as: `-Infinity`
- Type: `number`
- It is a property of the global object (`window.NEGATIVE_INFINITY` in browsers)
- Returned when a **number becomes smaller than the minimum floating point number**

---

### ✅ Examples:

```js
console.log(-Infinity);           // -Infinity
console.log(typeof -Infinity);   // "number"
console.log(Number.NEGATIVE_INFINITY); // -Infinity

console.log(-1 / 0);             // -Infinity (division by zero)
console.log(Math.log(0));        // -Infinity
console.log(Number.MIN_VALUE * -2); // -Infinity
```

---

### 🔍 Use Cases:
- Handling edge cases in calculations
- Checking overflow conditions
- Comparing values with very small numbers

---

### 🔑 Summary:
> **Negative Infinity (`-Infinity`)** in JavaScript represents a value smaller than all other numbers. It's typically the result of **underflow** or **division by negative zero**, and is treated as a number type in JS.


## 8. 📜 Is it Possible to Break JavaScript Code into Several Lines?

### ✅ Yes, JavaScript allows breaking code into multiple lines for better readability.

However, **how** you break the line matters — incorrect line breaks can lead to **syntax errors** or unexpected results.

---

### 🔹 Breaking Strings with `\n` (Newline Character)

You can break **string content** using `\n` for newline within a string:

```js
console.log("A Online Computer Science Portal\nfor Geeks");
```

Output:
```
A Online Computer Science Portal
for Geeks
```

---

### 🔹 Breaking Statements Across Lines (Correct Way)

JavaScript automatically adds semicolons in some cases (called *Automatic Semicolon Insertion*), but it’s safer to break lines **between operators or commas**:

```js
let gfg = 10,
    GFG = 5,
    Geeks = gfg + GFG;

console.log(Geeks); // 15
```

---

### ❌ Incorrect Line Breaks

Breaking the line **improperly** (e.g., between a variable name and assignment) can lead to bugs:

```js
let x
= 5;
console.log(x); // 5 ✅ Works due to ASI but not recommended
```

---

### 🧠 Summary:
> JavaScript allows multi-line code for readability, but be cautious with line breaks to avoid ambiguity. Use `\n` for breaking strings and break expressions at safe syntax points.


## 9. What are "truthy" and "falsy" values in JavaScript

Falsy: false, 0, "" (empty string), null, undefined, NaN

Truthy: Everything else (e.g., any non-empty string, any non-zero number, objects, arrays

## 10. ❓ What are Undeclared and Undefined Variables in JavaScript?

In JavaScript, both **undeclared** and **undefined** variables refer to variables that are not properly initialized — but they are **not the same**.

---

### 🔹 1. **Undefined Variable**

- A variable is **declared** but **not assigned** any value.
- The default value of such a variable is `undefined`.

```js
let x;
console.log(x); // undefined
```

---

### 🔹 2. **Undeclared Variable**

- A variable that has **not been declared** using `let`, `const`, or `var`.
- Accessing it directly causes a **ReferenceError**.

```js
console.log(y); // ❌ ReferenceError: y is not defined
```

> ⚠️ If you assign a value to a variable without declaring it, it becomes **implicitly global** (not recommended):

```js
function test() {
  z = 10; // Implicit global
}
test();
console.log(z); // 10 ✅ But bad practice!
```

---

### 🧠 Summary Table:

| Term         | Declared? | Assigned Value? | Throws Error?      | Scope       |
|--------------|-----------|------------------|---------------------|-------------|
| **Undefined**| ✅ Yes     | ❌ No            | ❌ No               | Local or global |
| **Undeclared**| ❌ No     | ❌ No            | ✅ Yes (ReferenceError) | Global (if assigned) |

---

### ✅ Pro Tip:
Always declare variables using `let`, `const`, or `var` to avoid unexpected bugs and global leaks.



## 12. 🌍 What Are Global Variables in JavaScript?

### 🔹 Definition:
Global variables are variables declared **outside of any function or block**, making them accessible **throughout the program** — in any function or scope.

---

### 🔹 How to Declare Global Variables:

```js
let petName = "Rocky"; // Global variable

function myFunction() {
  console.log("Inside myFunction - petName:", petName);
}

myFunction();

console.log("Outside myFunction - petName:", petName);
```

### ✅ Output:
```
Inside myFunction - petName: Rocky
Outside myFunction - petName: Rocky
```

---

### 🔍 Characteristics of Global Variables:

- Available throughout the entire script or file.
- Can be accessed and modified inside **any function or block**.
- Automatically become properties of the `window` object (in browsers) when declared with `var`.

---

### ⚠️ Problems with Global Variables:

| Problem                              | Explanation                                                                 |
|--------------------------------------|-----------------------------------------------------------------------------|
| ❌ Hard to Debug                      | Any part of the code can modify them, making bugs harder to track.         |
| 🔁 Namespace Pollution                | Too many global variables can cause **name collisions** and unpredictable behavior. |
| 🤝 Poor Modularity                   | Functions become **tightly coupled** to the global scope, reducing reusability.     |
| 🔓 Security Risk                     | Global variables can be unintentionally accessed or modified.              |

---

### ✅ Best Practices:
- Use `let` or `const` to **restrict scope**.
- Avoid declaring variables in the global scope unless absolutely necessary.
- Use **modules** or **closures** to encapsulate variables.

```js
// Safer approach using IIFE
(function() {
  const localVar = "Safe!";
  console.log(localVar); // Safe!
})();
```

> 🔐 Minimizing global variables helps make your JavaScript code more modular, testable, and easier to maintain.



## ⚠️ What Happens If You Declare a Variable Without `var`, `let`, or `const`?

### ✅ In Non-Strict Mode:

If you assign a value to a variable without declaring it using `var`, `let`, or `const`, **JavaScript will implicitly create a global variable**, even if it's inside a function.

```js
function test() {
  x = 10; // No var/let/const
}
test();

console.log(x); // ✅ Output: 10 (global variable)
```

- This creates `x` as a global variable attached to the `window` object in browsers.
- It’s accessible anywhere in the code after the function is called.

---

### 🚫 In Strict Mode:

If `"use strict"` is enabled, assigning a variable without declaration will throw a `ReferenceError`.

```js
"use strict";

function test() {
  x = 10; // ❌ ReferenceError
}
test();
```

---

### 📌 Summary Table:

| Mode           | Behavior                                |
|----------------|-----------------------------------------|
| **Non-strict** | Implicit global variable is created     |
| **Strict**     | ❌ Throws `ReferenceError`               |

---

### 🛡️ Best Practice:

> Always use `let`, `const`, or `var` to declare variables.  
> Avoid using undeclared variables to prevent global pollution and hard-to-debug issues.



## 13. ❓ What is `null` in JavaScript?

### 🔹 Definition:

The NULL value represents that no value or no object. It is known as empty value/object.

`null` is a **special primitive value** in JavaScript that represents the **intentional absence of any object value** or **no value at all**.

It is often used to:
- Indicate that a variable should be empty.
- Reset an object or variable.
- Represent an unknown or empty value.

---

### ✅ Example:

```js
let user = null;
console.log(user); // null
console.log(typeof user); // "object" (this is a known quirk in JavaScript)
```

---

### 🧠 Key Points:

| Feature                | Description                                |
|------------------------|--------------------------------------------|
| Type                   | Primitive (but `typeof null` returns `"object"`) |
| Purpose                | Represents "no value", "empty", or "unknown" |
| Common Usage           | To reset a variable or signify emptiness   |

---

### ❗ Note:
> Although `typeof null` returns `"object"`, this is a **long-standing bug in JavaScript**, and it doesn't mean `null` is an object.

---

### ✅ When to Use `null`:
- To clear a variable:
  ```js
  let data = { name: "John" };
  data = null; // Clear the object
  ```
- As a placeholder before assigning actual data.
- To check if a variable has been intentionally emptied:
  ```js
  if (user === null) {
    console.log("No user assigned.");
  }
  ```

---

### 🔁 `null` vs `undefined`:

| Value        | Meaning                       | Assigned By         |
|--------------|-------------------------------|---------------------|
| `null`       | Intentionally empty            | Developer (explicit)|
| `undefined`  | Not assigned any value         | JavaScript (default)|

---

> ✅ `null` is used when you **intentionally want a variable to be empty**, unlike `undefined` which typically means "not assigned yet".


## 14. 🗑️ How to Delete a Property in JavaScript?

### 🔹 Using the `delete` Keyword:

In JavaScript, the `delete` operator is used to **remove a property** from an object completely — including its key and value.

---

### ✅ Example:

```js
let gfg = {
  Course: "DSA",
  Duration: 30
};

delete gfg.Course;

console.log(gfg); // Output: { Duration: 30 }
```

- `gfg.Course` is removed entirely from the object.
- Only `Duration` remains in the object.

---

### 🧠 Notes:
- `delete` works only on **object properties**, not on variables or array items (safely).
- It **returns `true`** if the property was successfully deleted.

```js
let obj = { a: 1 };
console.log(delete obj.a); // true
```

---

### ⚠️ Best Practice:
Avoid using `delete` on arrays — it removes the item but **leaves a hole** in the array.

```js
let arr = [1, 2, 3];
delete arr[1];
console.log(arr); // [1, empty, 3]
```

> ✅ Use `splice()` for arrays instead:
```js
arr.splice(1, 1); // Removes 1 element at index 1
```

---

> ✅ Use `delete` when you want to remove a **property completely** from an object.



## 16. 💬 What is a Prompt Box in JavaScript?

### 🔹 Definition:
A **prompt box** is a built-in browser dialog that allows users to **input a value or text**. It's often used to gather simple input from the user before proceeding with an action or loading a page.

---

### ✅ Syntax:

```js
let userInput = prompt("Please enter your name:");
console.log(userInput);
```

---

### 🧠 How It Works:

- Displays a popup with:
  - A **message** (the prompt).
  - A **text input field**.
  - "OK" and "Cancel" buttons.
- Returns:
  - A **string** with the user's input if they press **OK**.
  - `null` if they press **Cancel**.

---

### ✅ Example:

```js
let age = prompt("Enter your age:");
if (age !== null) {
  console.log("You entered age:", age);
} else {
  console.log("Prompt was cancelled.");
}
```

---

### ⚠️ Notes:
- `prompt()` **pauses JavaScript execution** until the user responds.
- It's a **blocking UI element**, so it’s generally avoided in modern UX design.
- Not customizable — UI/UX varies between browsers.

---

> ✅ Use `prompt()` only for **quick demos, debugging, or simple input** — not in production UIs.


## #317. 🔑 What is the `this` Keyword in JavaScript?

### 🔹 Definition:
In JavaScript, `this` refers to the **execution context** — it defines **how a function is called** and **what object it is bound to**.

It can change depending on:
- **Where** and **how** the function is invoked
- Whether you're in **strict mode**
- Whether you're using **arrow functions** or **regular functions**

---

### 🧠 Key Points:

| Context                         | `this` Refers To                                      |
|----------------------------------|--------------------------------------------------------|
| In a method (object function)    | The object that owns the method                       |
| In a function (non-strict mode)  | The global object (`window` in browsers)              |
| In a function (strict mode)      | `undefined`                                           |
| In an event handler              | The DOM element that triggered the event              |
| In an arrow function             | The `this` value of its enclosing lexical context     |
| Inside a class constructor       | The instance of the class                             |

---

### ✅ Example 1: In Object Method

```js
const person = {
  name: "Purvesh",
  greet: function () {
    console.log("Hello, " + this.name);
  }
};

person.greet(); // "Hello, Purvesh"
```

Here, `this` refers to the `person` object.

---

### ✅ Example 2: In Regular Function (non-strict)

```js
function showThis() {
  console.log(this);
}

showThis(); // In browser, logs: window object
```

---

### ✅ Example 3: Arrow Function

```js
const person = {
  name: "Purvesh",
  greet: () => {
    console.log("Hello, " + this.name);
  }
};

person.greet(); // "Hello, undefined" — because arrow functions don't bind `this`
```

---

### 🔐 Summary:

- `this` behaves **dynamically** based on the call-site.
- Use **arrow functions** to inherit `this` from the parent scope.
- In **classes**, `this` usually refers to the instance.

> 🔧 Pro Tip: Confused about `this`? Use `console.log(this)` inside different functions to see how it behaves!


## 18. ⏱️ Explain the Working of Timers in JavaScript. Also Explain the Drawbacks (if any).

### 🔹 What Are Timers?
Timers in JavaScript are used to **delay the execution** of code or to **repeat code at specific intervals**. They are built on the concept of the **event loop** and are executed **asynchronously**.

JavaScript provides two main timer functions:
- `setTimeout()` — Runs code **once** after a specified delay.
- `setInterval()` — Runs code **repeatedly** at specified intervals.

---

### ✅ Examples:

#### 🔸 `setTimeout` (One-time delay):

```js
setTimeout(() => {
  alert("Time's up!");
}, 2000); // Executes after 2 seconds
```

#### 🔸 `setInterval` (Repeats code):

```js
const intervalId = setInterval(() => {
  console.log("Running every second");
}, 1000);
```

#### 🔸 `clearInterval` (Stops interval):

```js
clearInterval(intervalId); // Stops the above interval
```

---

### 🧠 Drawbacks of Using Timers:

| Issue | Description |
|-------|-------------|
| ⌛ Inaccuracy | Timers are not 100% precise — delays may happen due to the event loop or heavy computations. |
| 🔄 Unnecessary Repetition | `setInterval` keeps running even if the task is complete unless you manually stop it with `clearInterval()`. |
| 🧵 Blocking | If the main thread is busy (JavaScript is single-threaded), the timer callback will be delayed. |
| ❌ Memory Leaks | Not clearing intervals properly can cause memory leaks or performance issues. |

---

### 📝 Summary:

| Function      | Purpose                         |
|---------------|----------------------------------|
| `setTimeout()` | Runs code once after a delay     |
| `setInterval()`| Repeats code at fixed intervals |
| `clearInterval()` | Stops an interval timer       |

> ⚠️ Use timers carefully, especially inside loops or large apps, to avoid performance issues or memory leaks.


## 19. 🆚 Difference Between ViewState and SessionState

| Feature         | ViewState                              | SessionState                                |
|------------------|-----------------------------------------|----------------------------------------------|
| 🔹 Scope         | Specific to a **single page**            | Available across **multiple pages**           |
| 🧠 Purpose       | Maintains the **state of controls** on the same page | Maintains **user session data** across the website |
| 📍 Storage Location | Stored in the **page itself** (as a hidden field) | Stored on the **server**                     |
| 🔁 Lifecycle     | Lost when the user navigates to another page | Exists for the **entire session** duration   |
| 🔒 Security      | Less secure (can be viewed from page source) | More secure (stored on server side)          |
| 📦 Data Size     | Limited to the size of the page           | Can store larger, complex data                |
| 🛠️ Use Case      | Persist form data between postbacks       | Store user login info, shopping cart, etc.    |

---

### ✅ Summary:

- **ViewState** is best for retaining UI state (like checkbox status) **within the same page**.
- **SessionState** is ideal for storing **user-specific data** across multiple pages during a session.

> 🧠 Note: These concepts are primarily relevant to server-side web frameworks like ASP.NET.


## 21. 🔄 Does JavaScript Support Automatic Type Conversion?

### ✅ Yes, JavaScript supports **automatic type conversion**, also known as **type coercion**.

This means JavaScript will **implicitly convert** one data type to another when required during operations or comparisons.

---

### 🔹 Example 1: String + Number

```js
let result = "5" + 2;
console.log(result); // "52" — number is converted to string
```

### 🔹 Example 2: Subtracting Strings

```js
let result = "5" - "2";
console.log(result); // 3 — both strings are converted to numbers
```

### 🔹 Example 3: Boolean to Number

```js
let result = true + 1;
console.log(result); // 2 — true becomes 1
```

---

### ⚠️ Note:

- JavaScript uses **loosely typed** or **dynamic typing**.
- Automatic type conversion can sometimes lead to **unexpected behavior**, especially with `==`.

---

### 🔐 Tip:

Use **strict equality (`===`)** to avoid unwanted type coercion.

```js
console.log(0 == false);  // true  → coerced
console.log(0 === false); // false → no coercion
```

> 🧠 JavaScript's flexibility with types is powerful, but be cautious with comparisons and operations across types.


## 22. 📄 What is a Template Literal in JavaScript?

### 🔹 Definition:
A **template literal** is a modern way to define strings in JavaScript, introduced in **ES6**.  
It allows:
- ✅ **Multi-line strings**
- ✅ **String interpolation** (embedding variables/expressions)
- ✅ **Improved readability**

---

### 🔧 Syntax:
Template literals are enclosed using **backticks** (`` ` ``) instead of single (`'`) or double (`"`) quotes.

You can embed expressions using `${...}`.

---

### ✅ Example 1: Basic Template Literal

```js
const name = "Purvesh";
const greeting = `Hello, ${name}!`;
console.log(greeting); // Output: Hello, Purvesh!
```

---

### ✅ Example 2: Multi-line String

```js
const message = `This is line 1
This is line 2
This is line 3`;
console.log(message);
```

---

### ✅ Example 3: Embedding Expressions

```js
const a = 5, b = 10;
console.log(`The sum of a and b is ${a + b}.`); // Output: The sum of a and b is 15.
```

---

### 📌 Summary:

| Feature            | Description                              |
|--------------------|------------------------------------------|
| Backticks (`)      | Used instead of quotes                   |
| `${}`              | Embed variables or expressions           |
| Multi-line support | Allows strings over multiple lines       |
| Introduced in      | ECMAScript 6 (ES6)                       |

> Template literals are cleaner and more flexible than traditional string concatenation.


## 23. 🧠 What is a Higher-Order Function in JavaScript?

### 🔹 Definition:
A **Higher-Order Function (HOF)** is a function that either:
- ✅ **Takes one or more functions** as arguments, or
- ✅ **Returns another function** as its result.

This concept is a key feature of **functional programming** and promotes code reusability and abstraction.

---

### ✅ Examples of Higher-Order Functions:

#### 🔸 1. `map()` – Takes a function as an argument

The map() method is a higher-order function in JavaScript that creates a new array by applying a function to each element of an existing array. It's a clean and efficient way to transform arrays without modifying the original one.

```js
const nums = [1, 2, 3];
const squared = nums.map(num => num * num);
console.log(squared); // [1, 4, 9]
```

#### 🔸 2. `filter()` – Also accepts a function

The filter() method in JavaScript is another handy higher-order function. It creates a new array with only the elements that pass a certain test

```js
const nums = [1, 2, 3, 4];
const even = nums.filter(num => num % 2 === 0);
console.log(even); // [2, 4]
```

#### 🔸 3. Returning a function

```js
function greet(msg) {
  return function(name) {
    return `${msg}, ${name}!`;
  };
}

const sayHello = greet("Hello");
console.log(sayHello("Purvesh")); // Hello, Purvesh!
```

---

### 📌 Summary:

| Feature                  | Description                                      |
|--------------------------|--------------------------------------------------|
| Takes function as input  | Accepts callback functions                      |
| Returns function         | Can return new functions                        |
| Enables                  | Functional programming, abstraction, reusability |
| Common examples          | `map()`, `filter()`, `reduce()`, custom HOFs     |

> 🧠 Higher-order functions make JavaScript powerful and expressive, allowing elegant solutions to complex problems.



## 24. ➖ What is the `reduce()` Function in JavaScript?

### 🔹 Definition:
The `reduce()` method in JavaScript is a **higher-order array function** used to **accumulate or reduce** all elements of an array into a **single value** (like a sum, product, object, etc.).

---

### 🔧 Syntax:
```js
array.reduce(callback, initialValue)
```

- `callback`: A function that takes `(accumulator, currentValue)`
- `initialValue`: (Optional) The initial value of the accumulator

---

### ✅ Example 1: Sum of Array Elements

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // Output: 10
```

---

### ✅ Example 2: Counting Occurrences

```js
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana'];
const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});
console.log(count); 
// Output: { apple: 2, banana: 2, orange: 1 }
```

---

### ✅ Example 3: Flattening an Array

```js
const nested = [[1, 2], [3, 4], [5]];
const flat = nested.reduce((acc, curr) => acc.concat(curr), []);
console.log(flat); // Output: [1, 2, 3, 4, 5]
```

---

### 📌 Summary:

| Feature        | Description                                 |
|----------------|---------------------------------------------|
| Purpose        | Reduces array to a single value             |
| Returns        | The final accumulated result                |
| Use Cases      | Sum, max, average, flatten, grouping, etc.  |
| Type           | Higher-order function                       |

> 🧠 `reduce()` is extremely powerful for transforming arrays into any kind of final result.



## 24. 🔁 What are All the Looping Structures in JavaScript?

JavaScript provides several **looping constructs** to execute a block of code repeatedly based on certain conditions. Here are the main types:

---

### 🔹 1. `while` Loop

Runs **as long as** the condition is `true`.

```js
let i = 0;
while (i < 5) {
  console.log(i); 
  i++;
}
// Output: 0 1 2 3 4
```

> ✅ Checks the condition **before** running the block.

---

### 🔹 2. `for` Loop

Used when the number of iterations is known.

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// Output: 0 1 2 3 4
```

> ✅ Combines initialization, condition, and increment in one line.

---

### 🔹 3. `do...while` Loop

Runs the block **at least once**, then checks the condition.

```js
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
// Output: 0 1 2 3 4
```

> ✅ Example of an **exit-controlled loop**.

---

### 🔹 4. `for...in` Loop

Iterates over **enumerable properties** of an object.

```js
const person = { name: 'John', age: 25 };
for (let key in person) {
  console.log(key, person[key]);
}
// Output: name John, age 25
```

> 🛑 Not recommended for arrays.

---

### 🔹 5. `for...of` Loop

Iterates over **iterable objects** like arrays, strings, etc.

```js
const arr = ['a', 'b', 'c'];
for (let item of arr) {
  console.log(item);
}
// Output: a b c
```

> ✅ Works well with arrays and other iterables.

---

### 📌 Summary Table

| Loop Type     | Description                                  | Use Case Example                     |
|---------------|----------------------------------------------|--------------------------------------|
| `while`       | Runs while condition is true                 | Infinite scroll until user stops     |
| `for`         | Predefined number of iterations              | Looping from 0 to N                  |
| `do...while`  | Runs at least once                           | Menu prompt until valid input        |
| `for...in`    | Loops over object properties                 | Inspect object keys/values           |
| `for...of`    | Loops over iterable elements                 | Iterate through array or string      |

> 🧠 Choose the right loop based on your data type and control needs!


## 25. 📌 What is Lexical Scope in JavaScript?

Lexical scope means that **a variable's accessibility is determined by where it is written in the code** (i.e., its position in the source code). In JavaScript:

- Functions are **lexically scoped**.
- Inner functions have access to variables declared in their outer (parent) scopes.

### ✅ Example:

```js
let outer = "I am outside!";
function inner() {
    console.log(outer); // Accessible due to lexical scope
}
inner(); // Output: I am outside!
```

🧠 The `inner()` function can access `outer` because it is defined **inside** the scope where `outer` exists.

---

## 26. 🤔 Lexical Scoping vs `this` Keyword

Lexical scope affects **variable lookup**, but the `this` keyword behaves **differently**. The value of `this` is **determined by how a function is called**, not where it is defined.

### ✅ Example:

```js
const obj = {
    name: "JavaScript",
    greet: function () {
        console.log(this.name);
    }
};

obj.greet(); // Output: JavaScript
```

- Here, `this` refers to `obj` because `greet()` is called as a method of `obj`.
- Even though `greet` is defined inside `obj`, the value of `this` depends on the **call site**, not lexical scope.

---

### 📌 Summary:

| Concept          | Controlled By        | Affects                         |
|------------------|----------------------|----------------------------------|
| Lexical Scope    | Code structure       | Variable accessibility           |
| `this` keyword   | Function invocation  | Context (`who` is calling)       |

> ✅ Lexical scope = **"Where was it written?"**  
> ✅ `this` = **"How was it called?"**


## 28. 🔤 What is Variable Typing in JavaScript?

**Variable typing** in JavaScript refers to the language's ability to let variables hold values of **any type**, and allow those types to **change at runtime**.

JavaScript is a **dynamically typed** language, meaning:

- You **don’t need to declare a variable’s type**.
- You can **reassign a variable** with a value of a **different type**.

### ✅ Example:

```js
let Geeks = 42;               // Geeks is a number
Geeks = "GeeksforGeeks";      // Now Geeks is a string
```

🧠 This behavior is called **dynamic or variable typing**, and it allows more flexibility but also requires careful handling to avoid type-related bugs.

> ⚠️ Use tools like **TypeScript** if you want to add static typing on top of JavaScript.



## 29. 🔼 What is Hoisting in JavaScript?

**Hoisting** is JavaScript's default behavior of **moving declarations to the top** of the current scope (global or function) **before code execution**.

- **Variable** and **function declarations** are hoisted.
- **Initializations are not hoisted**.

### ✅ Example:

```js
console.log(a); // Output: undefined
var a = 5;
```

- JavaScript interprets it as:
  ```js
  var a;        // declaration is hoisted
  console.log(a); // undefined
  a = 5;        // initialization remains in place
  ```

---

### 🧠 Key Points:

| Keyword     | Hoisted?       | Initialized? | Temporal Dead Zone |
|-------------|----------------|--------------|---------------------|
| `var`       | ✅ Yes          | ❌ No         | ❌ No               |
| `let` / `const` | ✅ Yes      | ❌ No         | ✅ Yes              |
| `function`  | ✅ Yes (entire function) | ✅ Yes | ❌ No               |

- **`let` and `const`** are hoisted but stay in the **Temporal Dead Zone (TDZ)** until the code execution reaches the declaration.
- **Function declarations** are fully hoisted with their definitions.

### ⚠️ Avoid confusion by always declaring variables and functions at the top of their scope!

## 33. What is the use of void(0) ?

The void(0) is used to call another method without refreshing the page during the calling time parameter “zero” will be passed.

## 33. 🌀 What is the Use of `void(0)` in JavaScript?

The `void(0)` expression in JavaScript evaluates an expression and **returns `undefined`**.

It is commonly used to **prevent a page from refreshing or redirecting**, especially when using links that **shouldn’t navigate anywhere**.

### ✅ Common Use Case:
Used in anchor (`<a>`) tags to prevent default navigation.

```html
<a href="javascript:void(0)">Click me</a>
```

- `void(0)` ensures nothing happens when the link is clicked.
- Useful when triggering JavaScript functions via links **without refreshing the page**.

### 🧠 Example:
```html
<a href="javascript:void(0)" onclick="alert('Hello!')">Click Me</a>
```

### ⚠️ Note:
- The `void` operator **discards the result** of the expression.
- `void 0` and `void(0)` are the same; both return `undefined`.
```js
console.log(void 0); // undefined
```



## 37. 🔒 What is ‘Strict Mode’ in JavaScript and How Can It Be Enabled?

**Strict Mode** is a feature introduced in **ECMAScript 5** that enforces a **stricter set of rules** for writing JavaScript. It helps catch **common coding mistakes**, prevents the use of certain unsafe features, and makes your code more secure and optimized.

### ✅ Benefits of Strict Mode:
- Eliminates silent JavaScript errors by throwing exceptions.
- Prevents the use of undeclared variables.
- Disallows duplicate parameter names.
- Secures `this` context in functions (defaults to `undefined` instead of global object).
- Makes assignments to read-only properties throw errors.

### ✅ How to Enable Strict Mode:

#### 1. Globally (entire script):
```js
"use strict";

x = 10; // ❌ ReferenceError: x is not defined
```

#### 2. Locally (inside a function):
```js
function demo() {
  "use strict";
  y = 5; // ❌ ReferenceError: y is not defined
}
```

### ⚠️ Note:
- `"use strict"` must be the **first statement** in the script or function.
- Not using strict mode can lead to bugs that are harder to detect and debug.


## 39. 🔒 How to Explain Closures in JavaScript and When to Use Them?

A **closure** in JavaScript is created when a **function retains access to its lexical scope** even after the outer function has finished executing.

In simple terms, **closures allow a function to “remember” variables from its parent’s scope** even when that parent function is no longer in the call stack.

### ✅ Example of a Closure:
```js
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

### 🔧 Why and When to Use Closures:
- To **preserve state** in asynchronous or callback-based code.
- To **encapsulate private data** (simulate private variables).
- For **function factories** that return customized functions.
- To implement **data hiding and security** in JavaScript modules.

### 📌 Key Points:
- Closures are powerful for writing modular and maintainable code.
- They form the basis for many JavaScript patterns, including **currying**, **memoization**, and **module patterns**.


## 44. How many ways an HTML element can be accessed in JavaScript code? 

There are four possible ways to access HTML elements in JavaScript which are:

getElementById() Method: It is used to get the element by its id name.

getElementsByClass() Method: It is used to get all the elements that have the given classname.

getElementsByTagName() Method: It is used to get all the elements that have the given tag name.

querySelector() Method: This function takes CSS style selector and returns the first selected element.


## 45. 🔁 What is Event Bubbling in JavaScript?

**Event bubbling** is a type of event propagation in the DOM where an event **starts from the innermost (target) element** and **bubbles up** to its ancestors in the hierarchy.

### 📌 How It Works:
When an event is triggered on a nested element:
1. The **target (inner)** element handles the event first.
2. Then the event propagates **upwards** to the parent, grandparent, and so on.
3. Each ancestor can also handle the same event if an event listener is attached.

### ✅ Example:
```html
<div id="outer">
  <button id="inner">Click Me</button>
</div>

<script>
  document.getElementById("outer").addEventListener("click", () => {
    console.log("Outer Div Clicked");
  });

  document.getElementById("inner").addEventListener("click", () => {
    console.log("Button Clicked");
  });
</script>
```

### 🧠 Output When Button is Clicked:
```
Button Clicked
Outer Div Clicked
```

### 🔍 Use Case:
- Useful for **delegating events** to a parent instead of assigning them individually to many child elements.

### 🚫 To Stop Bubbling:
Use `event.stopPropagation()` in the event handler.

```js
event.stopPropagation(); // Stops the event from bubbling up
```



## 46. 💾 What is Memoization in JavaScript?

**Memoization** is an optimization technique used to speed up function execution by **caching previously computed results**.

### 📌 How It Works:
- When a function is called, the arguments are checked in a cache.
- If the result for those arguments exists, it returns the cached value.
- Otherwise, it computes the result and stores it in the cache for future use.

### ✅ Use Case:
- Useful in **expensive computations** like recursive functions (e.g., Fibonacci) or **repeated calls with the same input**.

### 🔁 Example:

```js
function memoize(fn) {
  const cache = {};
  return function (...args) {
    const key = JSON.stringify(args);
    if (cache[key]) {
      console.log("Fetching from cache:", key);
      return cache[key];
    }
    console.log("Calculating result:", key);
    const result = fn(...args);
    cache[key] = result;
    return result;
  };
}

// Expensive function
function slowAdd(a, b) {
  return a + b;
}

const memoizedAdd = memoize(slowAdd);

console.log(memoizedAdd(2, 3)); // Calculates and caches
console.log(memoizedAdd(2, 3)); // Returns from cache
```

### 🧠 Benefits:
- Reduces redundant calculations.
- Improves performance in data-heavy apps.

### 🚨 Note:
- Memoization is **most effective for pure functions** (same input → same output, no side effects).


## 47. 🔍 What is the Difference Between `==` and `===` in JavaScript?

In JavaScript, both `==` and `===` are comparison operators, but they behave differently when comparing values.

| Operator | Name               | Behavior                                                             |
|----------|--------------------|----------------------------------------------------------------------|
| `==`     | Loose Equality      | Compares values **after type coercion** (different types may be converted) |
| `===`    | Strict Equality     | Compares **both value and type** (no type conversion)               |

### 📌 Example:

```js
console.log(5 == "5");   // true  → types are coerced: "5" becomes 5
console.log(5 === "5");  // false → number !== string

console.log(null == undefined);  // true
console.log(null === undefined); // false

console.log(true == 1);   // true
console.log(true === 1);  // false
```

### ✅ Best Practice:
Use `===` (strict equality) to avoid unexpected type coercion and ensure more predictable comparisons.



## 48. 🌟 Explain the Concept of Promises and How They Work

A **Promise** in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

### 📌 States of a Promise:
- **Pending**: The initial state, before the result is known.
- **Fulfilled**: The operation completed successfully.
- **Rejected**: The operation failed.

### 🛠️ Creating a Promise:
```js
const myPromise = new Promise((resolve, reject) => {
  const success = true;
  if (success) {
    resolve("Operation successful!");
  } else {
    reject("Operation failed!");
  }
});
```

### ✅ Handling Promises:
```js
myPromise
  .then(result => {
    console.log(result); // "Operation successful!"
  })
  .catch(error => {
    console.error(error); // "Operation failed!"
  });
```

### 🔁 Chaining Promises:
```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

### 🧠 Benefits:
- Cleaner async code (compared to nested callbacks)
- Supports chaining for sequential operations
- Works well with async/await

### 🚫 Avoid Callback Hell:
Promises provide a more elegant solution for handling async operations than deeply nested callbacks.
