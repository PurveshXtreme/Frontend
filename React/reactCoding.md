- [JSONPlaceholder](https://jsonplaceholder.typicode.com)
- [CodeSandbox: damp-monad-p45s4w](https://codesandbox.io/p/sandbox/damp-monad-p45s4w?file=%2Fsrc%2FApp.js%3A34%2C11)

# Table of Contents

- [React Counter](#react-counter)
- [React Toggle Switch – Two Approaches](#react-toggle-switch--two-approaches)
- [React To-Do List Example](#react-to-do-list-example)
- [React API Call](#react-api-call)
- [Search Filter](#search-filter)
- [Dropdown](#dropdown)
- [Implement a Tabs Component](#implement-a-tabs-component)
- [Create a Modal Component](#create-a-modal-component)
- [React Image Carousel](#react-image-carousel)
- [React Star Rating Component](#react-star-rating-component)
- [React Real-Time Search](#react-real-time-search)
- [Display Top 10 Items of a Large Array in React](#display-top-10-items-of-a-large-array-in-react)
- [React Multi-Step Form](#react-multi-step-form)
- [Simple Form](#simple-form)
- [React Context API – Global State Example](#react-context-api--global-state-example)
- [React Custom Hook – Fetch & Cache API Data](#react-custom-hook--fetch--cache-api-data)
- [React Countdown Timer](#react-countdown-timer)
- [Simple React Form with Validation](#simple-react-form-with-validation)
- [Dynamic Styling — React Button Color Changer](#dynamic-styling--react-button-color-changer)
- [Debounced Search in React](#debounced-search-in-react)
- [Progress Bar in React](#progress-bar-in-react)
- [React Router Example](#react-router-example)
  



---
---

# React Counter 

## Code Overview
This is a simple **counter app** built using React functional components and the `useState` hook.  
It demonstrates **state management** and **two different ways of declaring functions** in React.

```javascript
import { useState } from "react";

export default function App() {
  const [count, setCount] = useState(0);

  // Arrow function syntax
  const incrementCount = () => {
    setCount(count + 1);
  };

  // Function declaration syntax
  function decrementCount() {
    setCount(count - 1);
  }

  return (
    <div className="App">
      <div>Counter : {count}</div>
      <button onClick={incrementCount}>Increment</button>
      <button onClick={decrementCount}>Decrement</button>
    </div>
  );
}
```

---

## Key Points

### useState
- `useState` is a **React hook** used to create a state variable and its setter.
- `count` is the current value.
- `setCount` is used to **update the state** and re-render the component.

### Function Declaration vs Arrow Function
| Feature               | Arrow Function (`()=>`)          | Function Declaration (`function`) |
|-----------------------|---------------------------------|---------------------------------|
| Syntax                | `const fn = () => {}`           | `function fn() {}`              |
| Hoisting              | Not hoisted                     | Hoisted                         |
| `this` context        | Inherits parent `this`          | Own `this`                      |


---
---

# React Toggle Switch – Two Approaches

## Approach 1 – Using String State

```javascript
import { useState } from "react";

export default function App() {
  const [toggle, setToggle] = useState("OFF");

  const change = () => {
    setToggle(toggle === "OFF" ? "ON" : "OFF");
  };

  return (
    <div>
      <div>{toggle}</div>
      <button onClick={change}>Toggle</button>
    </div>
  );
}
```

---

## Approach 2 – Using Boolean State

```javascript
import { useState } from "react";

export default function App() {
  const [toggle, setToggle] = useState(false);

  const change = () => {
    setToggle(!toggle);
  };

  return (
    <div>
      <div>{toggle ? "ON" : "OFF"}</div>
      <button onClick={change}>Toggle</button>
    </div>
  );
}
```
**Ternary Operator:** A concise one-line conditional: `condition ? valueIfTrue : valueIfFalse` (e.g., `toggle ? "ON" : "OFF"`).


---
---


#  React To-Do List Example

```javascript
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [list, setList] = useState([]);
  const [text, setText] = useState("");

  const addTodo = () => {
    if (text) {
      setList([...list, { text, completed: false }]);
      setText("");
    }
  };

  const removeTodo = (index) => {
    const newtodo = [...list];
    newtodo.splice(index, 1);
    setList(newtodo);
  };

  const toggleTodo = (index) => {
    const newtodo = [...list];
    newtodo[index].completed = !newtodo[index].completed;
    setList(newtodo);
  };

  return (
    <div className="App">
      <h1>Todo List</h1>
      <input
        type="text"
        placeholder="add todo"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <button onClick={addTodo}>Add</button>
      <ul>
        {list.map((l, index) => (
          <li key={index} style={{ textDecoration: l.completed ? "line-through" : "none" }}>
            {l.text}
            <button onClick={() => removeTodo(index)}>Remove</button>
            <button onClick={() => toggleTodo(index)}>Toggle</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## 📌 Notes

- `useState` is used to store the **list of todos** and the **input text**.
- `[...list, newItem]` creates a **new array** by spreading the existing items and adding a new one.  
  This is **immutable update** pattern in React.
- `.map()` iterates over the `list` array to render `<li>` elements dynamically in the `<ul>`.
- `splice(index, 1)` removes an item from an array at a specific index.
- `list[index].completed = !list[index].completed` toggles the **completion status**.
# 📝 Common JavaScript Array Methods – Syntax

| Method | Syntax | Description |
|--------|--------|-------------|
| `push` | `arr.push(element1, element2, ...)` | Adds one or more elements to the **end** of the array. |
| `pop` | `arr.pop()` | Removes the **last element** of the array and returns it. |
| `shift` | `arr.shift()` | Removes the **first element** of the array and returns it. |
| `unshift` | `arr.unshift(element1, element2, ...)` | Adds one or more elements to the **start** of the array. |
| `splice` | `arr.splice(startIndex, deleteCount, item1, item2, ...)` | Removes, replaces, or adds elements at a specific **position**. |
| `slice` | `arr.slice(startIndex, endIndex)` | Returns a **new array** containing elements from `startIndex` to `endIndex - 1`. |
| `map` | `arr.map((element, index, array) => { ... })` | Creates a **new array** by applying a function to each element. |
| `filter` | `arr.filter((element, index, array) => { ... })` | Creates a **new array** with elements that **pass a test**. |
| `forEach` | `arr.forEach((element, index, array) => { ... })` | Executes a function for **each element**; does not return a new array. |
| `find` | `arr.find((element) => condition)` | Returns the **first element** that satisfies the condition. |
| `findIndex` | `arr.findIndex((element) => condition)` | Returns the **index of the first element** that satisfies the condition. |
| `includes` | `arr.includes(element)` | Checks if the array **contains a specific element**, returns true/false. |
| `indexOf` | `arr.indexOf(element)` | Returns the **first index** of the element, or -1 if not found. |
| `concat` | `arr1.concat(arr2, arr3, ...)` | Returns a **new array** by merging arrays. |
| `reverse` | `arr.reverse()` | Reverses the array **in place**. |
| `sort` | `arr.sort((a, b) => a - b)` | Sorts the array **in place** based on a comparison function. |
| `join` | `arr.join(separator)` | Combines array elements into a **string** with a separator. |
| `reduce` | `arr.reduce((acc, curr) => ..., initialValue)` | Reduces the array to a **single value** by applying a function. |

> ✅ **Tip:** Use methods like `map`, `filter`, `reduce` to **avoid mutating** the original array and follow React’s **immutable state update** practices.


---
---

# React API Call 

---

## Approach 1 – Using Fetch with `.then()`

```javascript
import "./styles.css";
import { useState, useEffect } from "react";

export default function App() {
  const [loading, setLoading] = useState(true);
  const [data, setData] = useState();

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then((json) => {
        setData(json);
        setLoading(false);
      });
  }, []);

  if (loading) return <div>Loading...</div>;

  return (
    <div className="App">
      <ul>
        {data.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

### Notes:
- **`useEffect`**: Runs after the component mounts. Dependency array `[]` ensures it runs **once**.
- **`fetch`**: Native browser API to make HTTP requests. Returns a **promise**. Use `.then()` to handle response and parse JSON.

---

## Approach 2 – Using Fetch with `async/await`

```javascript
import { useState, useEffect } from "react";

export default function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    // Define an async function inside useEffect
    const fetchData = async () => {
      const res = await fetch("https://jsonplaceholder.typicode.com/users");
      const json = await res.json();
      setData(json);
    };

    fetchData(); // Call the async function
  }, []);

  return (
    <div>
      <h1>Users List</h1>
      <ul>
        {data.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

### Notes:
- `async/await` makes **asynchronous code look synchronous**, easier to read.
- Still uses **`fetch`**, so JSON parsing is manual (`res.json()`).
- `useEffect` dependency array `[]` ensures this runs **once** after mount.

---

## Approach 3 – Using Axios with `async/await`

```javascript
import { useState, useEffect } from "react";
import axios from "axios";

export default function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users"
        );
        setData(response.data); // Axios automatically parses JSON
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    };

    fetchData();
  }, []);

  return (
    <div>
      <h1>Users List</h1>
      <ul>
        {data.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

### Notes:
- **Axios**: Third-party library for HTTP requests.
  - Automatically parses JSON.
  - Handles errors more clearly with `try/catch`.
  - Supports features like **timeouts**, **interceptors**, **cancellation**.
- Dependency array `[]` in `useEffect` ensures fetch runs once on mount.

---

## 🔹 Fetch vs Axios

| Feature                  | Fetch                        | Axios                         |
|---------------------------|------------------------------|-------------------------------|
| JSON Parsing              | Manual (`res.json()`)        | Automatic                     |
| Error Handling            | Only network errors by default | Handles HTTP errors too      |
| Browser Support           | Native API                   | Needs library                 |
| Features                  | Basic GET/POST               | Timeout, interceptors, cancel tokens |
| Syntax                    | `.then()` or `async/await`   | `async/await` recommended    |


---
---

# Search Filter

```jsx
import "./styles.css";
import { useState, useEffect } from "react";

export default function App() {
  const [data, setData] = useState([]);
  const [filteredData, setFilteredData] = useState([]);
  const [text, setText] = useState("");
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then((res) => res.json())
      .then((json) => {
        setData(json);
        setFilteredData(json);
        setLoading(false);
      });
  }, []);

  const handleSearch = () => {
    const updatedData = data.filter((item) =>
      item.title.toLowerCase().includes(text.toLowerCase())
    );
    setFilteredData(updatedData);
  };

  if (loading) return <div>Loading...</div>;

  return (
    <div className="App">
      <h2>🔍 Search To-Do Titles</h2>
      <input
        type="text"
        placeholder="Enter keyword..."
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <button onClick={handleSearch}>Search</button>

      <ul>
        {filteredData.map((todo) => (
          <li key={todo.id}>{todo.title}</li>
        ))}
      </ul>
    </div>
  );
}
```

---
---

# Dropdown

```jsx
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [open, setOpen] = useState(false);
  const list = ["apple", "mango", "lemon", "watermelon", "banana"];

  return (
    <div className="App">
      <button
        onClick={() => {
          setOpen(!open);
        }}
      >
        Toggle Dropdown
      </button>

      {open && list.map((item, index) => <li key={index}>{item}</li>)}
    </div>
  );
}
```

**📝 Notes**
- `useState(false)` → initializes dropdown as closed.  
- `setOpen(!open)` → toggles the dropdown on button click.  
- `{open && ...}` → conditional rendering (shows list only if `open` is true).  
- Always include a **key** when mapping elements (`key={index}`) for stable rendering.

---
---


# Implement a Tabs Component

**Problem:**  
Create a tabs component where each tab displays different content when selected.  

**Solution:**  
```jsx
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [active, setActive] = useState(0);

  const tabs = [
    { title: "Home", content: "This is Home page" },
    { title: "Profile", content: "This is Profile page" },
    { title: "Settings", content: "This is Settings page" },
  ];

  return (
    <div className="App">
      {tabs.map((tab, index) => (
        <button key={index} onClick={() => setActive(index)}>
          {tab.title}
        </button>
      ))}

      <div>{tabs[active].content}</div>
    </div>
  );
}
```

**📝 Notes:**
- `useState(0)` keeps track of which tab is **currently active** (default = first tab).  
- The `map()` function dynamically renders tab buttons.  
- Clicking a button updates `active` to that tab’s index.  
- `{tabs[active].content}` displays only the content for the selected tab.

---
---

# Create a Modal Component

**Problem:**  
Create a reusable modal component that can be opened and closed, and display any content passed to it.

**Solution:**  
```jsx
import "./styles.css";
import { useState } from "react";

function Modal({ isOpen, onClose, children }) {
  if (!isOpen) return null; // don't render when closed

  return (
    <div className="modal-overlay">
      <div className="modal-content">
        {children}
        <button onClick={onClose}>Close</button>
      </div>
    </div>
  );
}

export default function App() {
  const [open, setOpen] = useState(false);

  return (
    <div className="App">
      <button onClick={() => setOpen(true)}>Open Modal</button>

      <Modal isOpen={open} onClose={() => setOpen(false)}>
        <h2>Hello from Modal!</h2>
        <p>This is a reusable modal component.</p>
      </Modal>
    </div>
  );
}
```

**📝 Notes:**
- `Modal` is **reusable** — you can pass any content via `children`.
- The `isOpen` prop controls whether the modal is visible.
- Returning `null` prevents rendering when the modal is closed.
- Basic CSS (for `.modal-overlay` and `.modal-content`) is used to center the modal and dim the background.

---
---

# React Image Carousel

## Code Example

```javascript
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [active, setActive] = useState(0);
  const images = [
    "https://picsum.photos/id/1015/600/400",
    "https://picsum.photos/id/1016/600/400",
    "https://picsum.photos/id/1018/600/400",
    "https://picsum.photos/id/1020/600/400",
    "https://picsum.photos/id/1024/600/400",
    "https://picsum.photos/id/1025/600/400",
  ];

  const goNext = () => {
    setActive((active + 1) % images.length);
  };

  const goPrev = () => {
    // ✅ Important: add images.length before modulo to handle negative indices
    setActive((active - 1 + images.length) % images.length);
  };

  return (
    <div className="App">
      <div className="carousel">
        <button onClick={goNext}> next </button>
        <img src={images[active]} alt="carousel" />
        <button onClick={goPrev}> prev </button>
      </div>
    </div>
  );
}
```

---

## Notes

- `images` array contains the URLs of carousel images.
- `active` state keeps track of the **currently visible image**.
- `goNext`: `(active + 1) % images.length` ensures **cycling forward** through the images.
- `goPrev`: `(active - 1 + images.length) % images.length` is important because:
  - Directly doing `(active - 1) % images.length` can produce **negative numbers**.
  - Adding `images.length` ensures the modulo operation always gives a **valid positive index**.
- Clicking **Next** or **Prev** updates the `active` state, causing the displayed image to change.

---
---

# React Star Rating Component

## Code Overview
This is a simple **star rating component** built using React functional components and `useState`.  
It allows users to rate from **1 to 5 stars**, and dynamically updates the displayed rating.

```javascript
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [rating, setRating] = useState(-1);

  const rates = ["★", "★★", "★★★", "★★★★", "★★★★★"];
  const arr = [1, 2, 3, 4, 5];

  return (
    <div className="App">
      <div>{rating === -1 ? "please rate us" : rates[rating]}</div>

      {arr.map((item) => {
        return (
          <button
            onClick={() => {
              setRating(item - 1);
            }}
          >
            {item}
          </button>
        );
      })}
    </div>
  );
}
```

---

## Notes

- `useState(-1)` is used to track the **selected rating**. `-1` indicates no rating selected.
- `rates` array contains **display strings for stars**.
- `arr.map()` is used to render buttons dynamically for each rating.
- `setRating(item - 1)` ensures correct **0-based indexing** when accessing `rates`.
- Conditional rendering:
  ```javascript
  {rating === -1 ? "please rate us" : rates[rating]}
  ```
  - Displays `"please rate us"` when no rating is selected.
  - Displays the **selected star rating** otherwise.

---
---

# React Real-Time Search 

This is a **real-time search** implementation in React using functional components and `useState`/`useEffect` hooks. The list of todos is fetched from an API, and the search input filters the list **on-the-fly** without using extra state for filtered data.

```javascript
import "./styles.css";
import { useState, useEffect } from "react";

export default function App() {
  const [data, setData] = useState([]);
  const [query, setQuery] = useState("");
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then((res) => res.json())
      .then((json) => {
        setData(json);
        setLoading(false);
      });
  }, []);

  const filteredDate = loading
    ? []
    : data.filter((item) =>
        item.title.toLowerCase().includes(query.toLowerCase())
      );

  if (loading) return <div>loading...</div>;

  return (
    <div className="App">
      <div>Real time search</div>
      <input
        type="text"
        placeholder="search"
        onChange={(e) => {
          setQuery(e.target.value);
        }}
      />

      {filteredDate.map((item) => {
        return <div key={item.id}>{item.title}</div>;
      })}
    </div>
  );
}
```

---

## 📌 Notes

- `useState` is used for **API data**, **search query**, and **loading state**.
- `useEffect` is used to **fetch data on component mount** (`[]` dependency array ensures it runs only once).
- The **filtered list** is derived dynamically using `.filter()` based on the current query.
- This approach avoids storing **redundant state** for filtered data, making the component simpler.
- `.toLowerCase()` is used for **case-insensitive search**.

---
---

# Display Top 10 Items of a Large Array in React

**Problem:**  
You have a large array of data (100+ items). In a React component, display **only the first 10 items**.

---

## Key Points

- Render only a subset of the array using **array slicing**.
- Use `.slice(0, 10)` to get the first 10 elements.
- Map over the sliced array inside JSX.

---

## Example

```javascript
import React from "react";

export default function App() {
  const largeArray = Array.from({ length: 100 }, (_, i) => `Item ${i + 1}`);

  // Get first 10 items
  const firstTenItems = largeArray.slice(0, 10);

  return (
    <div>
      <h1>Top 10 Items</h1>
      <ul>
        {firstTenItems.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```

**Notes:**

- `.slice(start, end)` does not modify the original array.
- Always provide a unique `key` prop when mapping in React.

---
---

# React Multi-Step Form 

```javascript
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [step, setStep] = useState(1);

  const stepOne = () => {
    return (
      <>
        <div>this is step one</div>
        <button
          onClick={() => {
            setStep(step + 1);
          }}
        >
          go to next step
        </button>
      </>
    );
  };

  const stepTwo = () => {
    return (
      <>
        <div>this is step 2</div>
        <button
          onClick={() => {
            setStep(step + 1);
          }}
        >
          go to next step
        </button>
      </>
    );
  };

  const stepThree = () => {
    return (
      <>
        <div>this is the last step</div>
        <button type="submit">Submit</button>
      </>
    );
  };

  const handleSubmit = () => {
    console.log("form submitted");
  };

  return (
    <div className="App">
      <form onSubmit={handleSubmit}>
        {step === 1 && stepOne()}
        {step === 2 && stepTwo()}
        {step === 3 && stepThree()}
      </form>
    </div>
  );
}
```

---
---

# Simple Form

This example demonstrates a **controlled form** in React, where the input fields are controlled via state and **cleared after submission**.

```javascript
import "./styles.css";
import { useState } from "react";

export default function App() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault(); // Prevent page reload
    console.log("Form submitted");
    console.log("Name: " + name);
    console.log("Email: " + email);

    // Clear input fields after submission
    setName("");
    setEmail("");
  };

  return (
    <div className="App">
      <form onSubmit={handleSubmit}>
        <div>Fill the form</div>

        <input
          type="text"
          placeholder="Enter your name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />

        <input
          type="email"
          placeholder="Enter email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />

        <button type="submit">Submit form</button>
      </form>
    </div>
  );
}
```

---

## ✅ Key Points

- **Controlled Inputs:** The `value` of inputs is tied to React state (`name` and `email`).
- **Prevent Default:** `event.preventDefault()` prevents page reload on form submission.
- **Clearing Inputs:** After submitting, calling `setName("")` and `setEmail("")` resets the input fields.
- **onChange Handler:** Updates state whenever the user types in the input field.

---
---

# React Context API – Global State Example

This example shows how to use **React Context API** to manage and share a global state (like a list of posts) across components **without prop drilling**.

---

## 📘 Code Example

```javascript
import React, { createContext, useState, useContext } from "react";

// 1️⃣ Create Context
const PostContext = createContext();

// 2️⃣ Create Provider Component
export const PostProvider = ({ children }) => {
  const [posts, setPosts] = useState([
    { id: 1, title: "React Basics" },
    { id: 2, title: "Understanding useState" },
  ]);

  const addPost = (newTitle) => {
    setPosts([...posts, { id: posts.length + 1, title: newTitle }]);
  };

  return (
    <PostContext.Provider value={{ posts, addPost }}>
      {children}
    </PostContext.Provider>
  );
};

// 3️⃣ Custom Hook to use Context
export const usePosts = () => useContext(PostContext);

// 4️⃣ Example Component to Display Posts
const PostList = () => {
  const { posts } = usePosts();

  return (
    <div>
      <h2>All Posts</h2>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
};

// 5️⃣ Example Component to Add a New Post
const AddPost = () => {
  const { addPost } = usePosts();
  const [text, setText] = useState("");

  return (
    <div>
      <input
        type="text"
        placeholder="New Post Title"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <button onClick={() => addPost(text)}>Add Post</button>
    </div>
  );
};

// 6️⃣ Main App Component
export default function App() {
  return (
    <PostProvider>
      <div className="App">
        <h1>React Context API Example</h1>
        <AddPost />
        <PostList />
      </div>
    </PostProvider>
  );
}
```

---
---

# ⚙️ React Custom Hook – Fetch & Cache API Data

This example shows how to create a **custom React hook** (`useFetch`) that fetches data from an API and **caches** it to prevent unnecessary re-fetching.

---

## 📘 Code Example

```javascript
import { useState, useEffect } from "react";

const cache = {}; // simple in-memory cache

// 🧩 Custom Hook
export const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    if (!url) return;

    const fetchData = async () => {
      // ✅ Check cache first
      if (cache[url]) {
        setData(cache[url]);
        setLoading(false);
        return;
      }

      try {
        setLoading(true);
        const res = await fetch(url);
        const result = await res.json();
        cache[url] = result; // ✅ Save in cache
        setData(result);
      } catch (err) {
        setError(err);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [url]);

  return { data, loading, error };
};

// 🧠 Example Component using the custom hook
export default function App() {
  const { data, loading, error } = useFetch(
    "https://jsonplaceholder.typicode.com/posts"
  );

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error fetching data 😢</p>;

  return (
    <div>
      <h1>Fetched Posts</h1>
      <ul>
        {data.slice(0, 5).map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## 📝 Notes

- `useFetch(url)` handles:
  - ✅ Fetching data asynchronously
  - ✅ Storing it in a **cache** to reuse
  - ✅ Managing **loading** and **error** states
- The cache prevents multiple API calls for the same URL.
- Can be reused in any component just by calling `useFetch(url)`.

---
---

# React Countdown Timer

This example shows how to create a **countdown timer** component in React that starts from a given number of seconds and counts down to zero.

---

## 📘 Code Example

```javascript
import { useState, useEffect } from "react";

export default function CountdownTimer() {
  const [timeLeft, setTimeLeft] = useState(10); // countdown starts from 10 seconds

  useEffect(() => {
    if (timeLeft <= 0) return; // stop when timer hits 0

    const timer = setInterval(() => {
      setTimeLeft((prev) => prev - 1);
    }, 1000);

    // 🧹 Cleanup to prevent memory leaks
    return () => clearInterval(timer);
  }, [timeLeft]);

  return (
    <div style={{ textAlign: "center", marginTop: "30px" }}>
      <h1>Countdown Timer</h1>
      <h2>{timeLeft > 0 ? timeLeft : "Time's up!"}</h2>
    </div>
  );
}
```

---

## 🧠 How It Works

- `timeLeft` → state variable storing remaining seconds.
- `useEffect` → runs a timer (`setInterval`) that decrements `timeLeft` every second.
- When `timeLeft` reaches `0`, the countdown stops automatically.
- Cleanup function inside `useEffect` ensures old timers are cleared.

---
---

# Simple React Form with Validation

This example shows a **basic React form** with **validation** for empty fields and email format.

---

## 📘 Code Example

```javascript
import { useState } from "react";

export default function SimpleForm() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [error, setError] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();

    // basic validation
    if (!name || !email) {
      setError("All fields are required!");
      return;
    }

    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
      setError("Please enter a valid email address!");
      return;
    }

    setError("");
    console.log("Form submitted successfully!");
    console.log("Name:", name);
    console.log("Email:", email);

    setName("");
    setEmail("");
  };

  return (
    <div style={{ textAlign: "center", marginTop: "30px" }}>
      <h2>Simple Form</h2>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          placeholder="Enter name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <br />
        <input
          type="email"
          placeholder="Enter email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
        <br />
        <button type="submit">Submit</button>
      </form>

      {error && <p style={{ color: "red" }}>{error}</p>}
    </div>
  );
}
```

---
---

# Dynamic Styling — React Button Color Changer

## 🧩 Problem
Create a **button** that changes its **background color** every time it’s clicked.

### 🧠 Concepts Tested
- Inline Styling  
- Dynamic State Updates (`useState`)

---

## ✅ Example Code

```javascript
import { useState } from "react";

export default function App() {
  const colors = ["red", "green", "blue", "orange", "purple"];
  const [colorIndex, setColorIndex] = useState(0);

  const changeColor = () => {
    setColorIndex((prev) => (prev + 1) % colors.length);
  };

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
      <button
        onClick={changeColor}
        style={{
          backgroundColor: colors[colorIndex],
          color: "white",
          padding: "10px 20px",
          border: "none",
          borderRadius: "8px",
          cursor: "pointer",
          fontSize: "16px"
        }}
      >
        Click Me
      </button>
    </div>
  );
}
```

---
---

# Debounced Search in React

## 🧩 Problem  
Implement a **search bar** that waits for **500ms after typing stops** before making an API call.

### 🧠 Concepts Tested
- **Debouncing**  
- **useEffect**  
- **Performance Optimization**

---

## ✅ Example Code

```javascript
import { useState, useEffect } from "react";

export default function App() {
  const [query, setQuery] = useState("");
  const [results, setResults] = useState([]);

  useEffect(() => {
    const handler = setTimeout(() => {
      if (query) {
        // Simulate API call
        console.log("Fetching data for:", query);
        setResults([`Result for "${query}"`]);
      }
    }, 500);

    // Cleanup function to cancel previous timeout
    return () => {
      clearTimeout(handler);
    };
  }, [query]);

  return (
    <div className="App" style={{ textAlign: "center", marginTop: "50px" }}>
      <h3>Debounced Search</h3>
      <input
        type="text"
        placeholder="Search..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        style={{
          padding: "8px",
          width: "200px",
          borderRadius: "6px",
          border: "1px solid #ccc",
        }}
      />
      <div style={{ marginTop: "20px" }}>
        {results.map((item, index) => (
          <div key={index}>{item}</div>
        ))}
      </div>
    </div>
  );
}
```

---
---

# Progress Bar in React

## 🧩 Problem  
Build a **progress bar** that fills based on a **percentage input value**.

### 🧠 Concepts Tested  
- **Dynamic styling**  
- **Props usage**  
- **Controlled inputs**

---

## ✅ Example Code

```javascript
import { useState } from "react";

function ProgressBar({ value }) {
  return (
    <div
      style={{
        width: "100%",
        backgroundColor: "#e0e0e0",
        borderRadius: "10px",
        overflow: "hidden",
        marginTop: "10px",
      }}
    >
      <div
        style={{
          width: `${value}%`,
          height: "20px",
          backgroundColor: value < 50 ? "orange" : "green",
          transition: "width 0.3s ease-in-out",
        }}
      ></div>
    </div>
  );
}

export default function App() {
  const [progress, setProgress] = useState(0);

  return (
    <div className="App" style={{ textAlign: "center", marginTop: "50px" }}>
      <h3>📊 Progress Bar Example</h3>
      <input
        type="number"
        value={progress}
        onChange={(e) => {
          const val = Math.min(100, Math.max(0, e.target.value));
          setProgress(val);
        }}
        placeholder="Enter progress (0-100)"
        style={{
          padding: "8px",
          width: "200px",
          borderRadius: "6px",
          border: "1px solid #ccc",
        }}
      />

      <ProgressBar value={progress} />
      <p>{progress}% completed</p>
    </div>
  );
}
```

---
---

# React Router Example

### Problem:
Create a simple multi-page React app with navigation using React Router.

### Concepts Tested:
Routing, navigation, and component rendering.

---

### 🧩 Code Example

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";

function Home() {
  return <h2>🏠 Home Page</h2>;
}

function About() {
  return <h2>ℹ️ About Page</h2>;
}

function Contact() {
  return <h2>📞 Contact Page</h2>;
}

export default function App() {
  return (
    <Router>
      <div>
        <nav>
          <Link to="/">Home</Link> |{" "}
          <Link to="/about">About</Link> |{" "}
          <Link to="/contact">Contact</Link>
        </nav>

        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </Router>
  );
}
```

---

### ⚙️ Steps to Run
1. Install React Router:
   ```bash
   npm install react-router-dom
   ```
2. Run your React app:
   ```bash
   npm start
   ```

Now, clicking on the links navigates between pages **without reloading the page** — that’s client-side routing in React 🚀

---
---
