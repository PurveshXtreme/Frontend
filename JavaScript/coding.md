# JavaScript Practice Questions

## Table of Contents

### Array and String Operations
1. [Remove Falsy Values from Array](#1-remove-falsy-values-from-array)
2. [Reverse Words in Sentence](#2-reverse-words-in-sentence)
3. [Count Vowels in String](#3-count-vowels-in-string)

### DOM Manipulation
4. [Change Text Content by ID](#4-change-text-content-by-id)
5. [Highlight Elements by Class Name](#5-highlight-elements-by-class-name)
6. [Count Number of Paragraphs](#6-count-number-of-paragraphs)
7. [Change Style Using querySelector](#7-change-style-using-queryselector)
8. [Change Text Using querySelectorAll](#8-change-text-using-queryselectorall)

### Popup Boxes
9. [Display Alert Message](#9-display-alert-message)
10. [Confirm User Action](#10-confirm-user-action)
11. [Prompt User for Input](#11-prompt-user-for-input)
12. [Combine Alert, Confirm, and Prompt](#12-combine-alert-confirm-and-prompt)

### Event Handling
13. [Event Bubbling](#13-event-bubbling)

### Functions
14. [Function Declaration](#14-function-declaration)
15. [Function Expression](#15-function-expression)
16. [Arrow Function](#16-arrow-function)
17. [Anonymous Function](#17-anonymous-function)
18. [IIFE (Immediately Invoked Function Expression)](#18-iife-immediately-invoked-function-expression)

### Timers
19. [setTimeout - Basic Usage](#19-settimeout---basic-usage)
20. [setTimeout - Cancel Timeout](#20-settimeout---cancel-timeout)
21. [setInterval - Repeat Action](#21-setinterval---repeat-action)
22. [Countdown Timer](#22-countdown-timer)

### ES6 Features
23. [Rest Operator - Function Parameters](#23-rest-operator---function-parameters)
24. [Rest Operator - Array Destructuring](#24-rest-operator---array-destructuring)
25. [Rest Operator - Object Destructuring](#25-rest-operator---object-destructuring)
26. [Spread Operator - Array Copy](#26-spread-operator---array-copy)
27. [Spread Operator - Merge Arrays](#27-spread-operator---merge-arrays)
28. [Spread Operator - Function Arguments](#28-spread-operator---function-arguments)
29. [Spread Operator - Object Merge](#29-spread-operator---object-merge)

### Advanced Topics
30. [Closures - Counter Function](#30-closures---counter-function)
31. [Disable Button After Click](#31-disable-button-after-click)
32. [Form Validation](#32-form-validation)
33. [Local Storage - Save and Retrieve](#33-local-storage---save-and-retrieve)
34. [Merge Two Objects](#34-merge-two-objects)
35. [JSON Handling](#35-json-handling)
36. [Fetch API - Get Data](#36-fetch-api---get-data)
37. [Object Destructuring](#37-object-destructuring)
38. [Get Input Value and Display](#38-get-input-value-and-display)

---

## Array and String Operations

### 1. Remove Falsy Values from Array

**Task:** Return array containing only truthy values (removes false, 0, "", null, undefined, NaN)

```javascript
function removeFalsyValues(arr) {
    return arr.filter(Boolean);
}

// Test Cases
console.log(removeFalsyValues([0, 1, false, 2, '', 3, null, undefined, NaN, 4])); 
// [1, 2, 3, 4]

console.log(removeFalsyValues([false, 'hello', 0, 5, '', true])); 
// ['hello', 5, true]
```

---

### 2. Reverse Words in Sentence

**Task:** Reverse word order in sentence, keep letter order in each word

```javascript
function reverseWords(sentence) {
    return sentence.split(' ').reverse().join(' ');
}

// Test Cases
console.log(reverseWords("how are you"));          // "you are how"
console.log(reverseWords("JavaScript is fun"));    // "fun is JavaScript"
console.log(reverseWords("hello"));                // "hello"
```

---

### 3. Count Vowels in String

**Task:** Count total vowels (a, e, i, o, u) in string

```javascript
function countVowels(str) {
    let count = 0;
    const vowels = 'aeiouAEIOU';
    
    for(let i = 0; i < str.length; i++){
        if(vowels.includes(str[i])){
            count++;
        }
    }
    return count;
}

// Test Cases
console.log(countVowels("hello world"));       // 3
console.log(countVowels("JAVASCRIPT"));        // 3
console.log(countVowels("why"));               // 0
console.log(countVowels("Education"));         // 5
```

---

## DOM Manipulation

### 4. Change Text Content by ID

**Task:** Change text of element with id "title"

```html
<h2 id="title">Hello World</h2>

<script>
  let h2 = document.getElementById("title");
  h2.textContent = "Welcome to JavaScript!";
</script>
```

---

### 5. Highlight Elements by Class Name

**Task:** Change background color of all elements with class "highlight" to yellow

```html
<p class="highlight">Text 1</p>
<p class="highlight">Text 2</p>
<p>Normal text</p>

<script>
  let elements = document.getElementsByClassName("highlight");
  for (let i = 0; i < elements.length; i++) {
    elements[i].style.backgroundColor = "yellow";
  }
</script>
```

---

### 6. Count Number of Paragraphs

**Task:** Count total `<p>` elements and log count

```html
<p>Paragraph 1</p>
<p>Paragraph 2</p>
<p>Paragraph 3</p>

<script>
  let paragraphs = document.getElementsByTagName("p");
  console.log("Total paragraphs:", paragraphs.length);
</script>
```

---

### 7. Change Style Using querySelector

**Task:** Change background color of first button to green

```html
<button>Button 1</button>
<button>Button 2</button>

<script>
  let btn = document.querySelector("button");
  btn.style.backgroundColor = "green";
</script>
```

---

### 8. Change Text Using querySelectorAll

**Task:** Change all button texts to "Clicked!" when any button is clicked

```html
<button>Button 1</button>
<button>Button 2</button>
<button>Button 3</button>

<script>
  let btns = document.querySelectorAll("button");

  function onButtonClick() {
    for (let i = 0; i < btns.length; i++) {
      btns[i].textContent = "Clicked!";
    }
  }

  for (let i = 0; i < btns.length; i++) {
    btns[i].addEventListener("click", onButtonClick);
  }
</script>
```

---

## Popup Boxes

### 9. Display Alert Message

**Task:** Show alert "Welcome to the site!" on page load

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Alert Example</title>
  </head>
  <body>
    <h2>Alert Box Example</h2>
    <script>
      alert("Welcome to the site!");
    </script>
  </body>
</html>
```

---

### 10. Confirm User Action

**Task:** Ask "Do you want to continue?" and log response

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Confirm Example</title>
  </head>
  <body>
    <h2>Confirm Box Example</h2>
    <script>
      let confirmResult = confirm("Do you want to continue?");
      if (confirmResult) {
        console.log("User continued");
      } else {
        console.log("User cancelled");
      }
    </script>
  </body>
</html>
```

---

### 11. Prompt User for Input

**Task:** Ask for name and display greeting alert

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Prompt Example</title>
  </head>
  <body>
    <h2>Prompt Box Example</h2>
    <script>
      let name = prompt("Enter your name:");
      alert("Hello, " + name + "!");
    </script>
  </body>
</html>
```

---

### 12. Combine Alert, Confirm, and Prompt

**Task:** Ask for name, confirm greeting, then display

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Popup Combination</title>
  </head>
  <body>
    <h2>Combined Popup Example</h2>
    <script>
      let name = prompt("Enter your name:");
      let showGreeting = confirm("Do you want to see a greeting?");
      if (showGreeting) {
        alert("Hello, " + name + "! Welcome!");
      } else {
        alert("Okay, maybe next time!");
      }
    </script>
  </body>
</html>
```

---

## Event Handling

### 13. Event Bubbling

**Task:** Demonstrate event bubbling (child click triggers parent events)

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="parent">
      Parent Div
      <div id="child">
        Child Div
        <button id="btn">Click Me</button>
      </div>
    </div>

    <script>
      const parent = document.getElementById("parent");
      const child = document.getElementById("child");
      const btn = document.getElementById("btn");

      parent.addEventListener("click", function () {
        console.log("Parent clicked");
      });

      child.addEventListener("click", function () {
        console.log("Child clicked");
      });

      btn.addEventListener("click", function (event) {
        console.log("Button clicked");
        // event.stopPropagation(); // Uncomment to stop bubbling
      });
    </script>
  </body>
</html>
```

---

## Functions

### 14. Function Declaration

```javascript
function greet() {
  return "Hello!";
}

console.log(greet()); // "Hello!"
```

---

### 15. Function Expression

```javascript
const greet = function() {
  return "Hello!";
};

console.log(greet()); // "Hello!"
```

---

### 16. Arrow Function

```javascript
const greet = () => "Hello!";
console.log(greet()); // "Hello!"
```

---

### 17. Anonymous Function

```javascript
setTimeout(function() {
  console.log("This runs after 2 seconds");
}, 2000);
```

---

### 18. IIFE (Immediately Invoked Function Expression)

```javascript
(function() {
  console.log("This runs instantly!");
})();
```

---

## Timers

### 19. setTimeout - Basic Usage

**Task:** Run function once after delay

```javascript
// Example 1: Arrow Function
setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);

// Example 2: Named Function
function greet() {
  console.log("Hello after 3 seconds!");
}
setTimeout(greet, 3000);
```

---

### 20. setTimeout - Cancel Timeout

**Task:** Cancel scheduled timeout

```javascript
const timeoutId = setTimeout(() => {
  console.log("This will not run");
}, 4000);

clearTimeout(timeoutId);
```

---

### 21. setInterval - Repeat Action

**Task:** Run function repeatedly and stop after 5 iterations

```javascript
let count = 0;
const intervalId = setInterval(() => {
  count++;
  console.log("Tick:", count);

  if (count === 5) {
    clearInterval(intervalId);
    console.log("Stopped!");
  }
}, 1000);
```

---

### 22. Countdown Timer

**Task:** Create countdown from 5 to 0

```javascript
let seconds = 5;

const countdown = setInterval(() => {
  console.log(seconds);
  seconds--;

  if (seconds < 0) {
    clearInterval(countdown);
    console.log("Time's up!");
  }
}, 1000);
```

---

## ES6 Features

### 23. Rest Operator - Function Parameters

**Task:** Collect multiple arguments into array

```javascript
function sum(...numbers) {
  console.log(numbers); // [1, 2, 3, 4]
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

---

### 24. Rest Operator - Array Destructuring

**Task:** Extract first elements, collect rest

```javascript
const [first, second, ...rest] = [10, 20, 30, 40, 50];
console.log(first);  // 10
console.log(second); // 20
console.log(rest);   // [30, 40, 50]
```

---

### 25. Rest Operator - Object Destructuring

**Task:** Extract property, collect remaining properties

```javascript
const person = { name: "Alice", age: 25, city: "Pune" };
const { name, ...info } = person;

console.log(name); // Alice
console.log(info); // { age: 25, city: "Pune" }
```

---

### 26. Spread Operator - Array Copy

**Task:** Create copy of array

```javascript
const arr = [1, 2, 3];
const copy = [...arr];
console.log(copy); // [1, 2, 3]
```

---

### 27. Spread Operator - Merge Arrays

**Task:** Combine multiple arrays

```javascript
const a = [1, 2];
const b = [3, 4];
const merged = [...a, ...b];
console.log(merged); // [1, 2, 3, 4]
```

---

### 28. Spread Operator - Function Arguments

**Task:** Pass array elements as function arguments

```javascript
function add(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];
console.log(add(...numbers)); // 6
```

---

### 29. Spread Operator - Object Merge

**Task:** Merge objects (later properties override earlier ones)

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };

const merged = { ...obj1, ...obj2 };
console.log(merged); // { a: 1, b: 3, c: 4 }
```

---

## Advanced Topics

### 30. Closures - Counter Function

**Task:** Create counter function that increments value each time called

```javascript
function createCounter() {
  let count = 0;
  
  return function() {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

---

### 31. Disable Button After Click

**Task:** Disable button after it's clicked once

```html
<!DOCTYPE html>
<html>
  <body>
    <button id="myBtn">Click Me</button>

    <script>
      const btn = document.getElementById("myBtn");
      
      btn.addEventListener("click", function() {
        btn.disabled = true;
        btn.textContent = "Button Disabled";
      });
    </script>
  </body>
</html>
```

---

### 32. Form Validation

**Task:** Validate all input fields are filled before submission

```html
<!DOCTYPE html>
<html>
  <body>
    <form id="myForm">
      <input type="text" id="name" placeholder="Name" required>
      <input type="email" id="email" placeholder="Email" required>
      <input type="text" id="phone" placeholder="Phone" required>
      <button type="submit">Submit</button>
    </form>

    <script>
      const form = document.getElementById("myForm");
      
      form.addEventListener("submit", function(e) {
        e.preventDefault();
        
        const name = document.getElementById("name").value;
        const email = document.getElementById("email").value;
        const phone = document.getElementById("phone").value;
        
        if (name === "" || email === "" || phone === "") {
          alert("Please fill all fields!");
        } else {
          alert("Form submitted successfully!");
        }
      });
    </script>
  </body>
</html>
```

---

### 33. Local Storage - Save and Retrieve

**Task:** Save user's name to localStorage and retrieve it

```html
<!DOCTYPE html>
<html>
  <body>
    <input type="text" id="nameInput" placeholder="Enter your name">
    <button id="saveBtn">Save</button>
    <button id="getBtn">Get Name</button>
    <p id="display"></p>

    <script>
      const saveBtn = document.getElementById("saveBtn");
      const getBtn = document.getElementById("getBtn");
      const nameInput = document.getElementById("nameInput");
      const display = document.getElementById("display");
      
      saveBtn.addEventListener("click", function() {
        const name = nameInput.value;
        localStorage.setItem("userName", name);
        alert("Name saved!");
      });
      
      getBtn.addEventListener("click", function() {
        const savedName = localStorage.getItem("userName");
        display.textContent = savedName ? "Saved Name: " + savedName : "No name saved";
      });
    </script>
  </body>
</html>
```

---

### 34. Merge Two Objects

**Task:** Merge two objects into one

```javascript
function mergeObjects(obj1, obj2) {
  return { ...obj1, ...obj2 };
}

// Alternative using Object.assign()
function mergeObjectsAlt(obj1, obj2) {
  return Object.assign({}, obj1, obj2);
}

// Test Cases
const person = { name: "John", age: 30 };
const address = { city: "Mumbai", country: "India" };

console.log(mergeObjects(person, address));
// { name: "John", age: 30, city: "Mumbai", country: "India" }
```

---

### 35. JSON Handling

**Task:** Convert object to JSON string and parse back

```javascript
// Object to JSON
const user = {
  name: "Alice",
  age: 25,
  email: "alice@example.com"
};

const jsonString = JSON.stringify(user);
console.log(jsonString);
// {"name":"Alice","age":25,"email":"alice@example.com"}

// JSON to Object
const parsedUser = JSON.parse(jsonString);
console.log(parsedUser);
// { name: "Alice", age: 25, email: "alice@example.com" }
```

---

### 36. Fetch API - Get Data

**Task:** Fetch data from API and display in console

```javascript
fetch('https://jsonplaceholder.typicode.com/users/1')
  .then(response => response.json())
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Error:', error);
  });

// Using async/await
async function fetchUser() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchUser();
```

---

### 37. Object Destructuring

**Task:** Extract properties from object using destructuring

```javascript
const user = {
  name: "John",
  age: 30,
  email: "john@example.com",
  city: "Mumbai"
};

// Basic destructuring
const { name, age } = user;
console.log(name); // John
console.log(age);  // 30

// Destructuring with rename
const { email: userEmail } = user;
console.log(userEmail); // john@example.com

// Destructuring with default values
const { phone = "Not provided" } = user;
console.log(phone); // Not provided
```

---

### 38. Get Input Value and Display

**Task:** Get input field value and display in paragraph on button click

```html
<!DOCTYPE html>
<html>
  <body>
    <input type="text" id="userInput" placeholder="Enter text">
    <button id="displayBtn">Display</button>
    <p id="output"></p>

    <script>
      const input = document.getElementById("userInput");
      const btn = document.getElementById("displayBtn");
      const output = document.getElementById("output");
      
      btn.addEventListener("click", function() {
        const value = input.value;
        output.textContent = value;
      });
    </script>
  </body>
</html>
```
