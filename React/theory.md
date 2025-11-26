

## Table of Contents

- [What is React?](#what-is-react)
- [Working of React](#working-of-react)
- [Reconciliation](#reconciliation)
- [Features of React](#features-of-react)
- [Challenges in React](#challenges-in-react)
- [React vs Angular](#react-vs-angular)
- [How JSX Works](#how-jsx-works)
- [What is Babel](#what-is-babel)
- [Diffing Algorithm](#diffing-algorithm)
- [React DOM](#react-dom)
- [Code Splitting and Bundling](#code-splitting-and-bundling)
- [React Components](#react-components)
- [Types of Components](#types-of-components)
- [Props in React](#props-in-react)
- [State in React](#state-in-react)
- [ReactJS Pure Components](#reactjs-pure-components)
- [React Lifecycle](#react-lifecycle)
- [Functional Components vs Class Components](#functional-components-vs-class-components)
- [Conditional Rendering](#conditional-rendering)
- [Keys in React](#keys-in-react)
- [Memoization in React](#memoization-in-react)
- [React.memo vs useMemo](#reactmemo-vs-usememo)
- [Parameters of memo](#parameters-of-memo)
- [useEffect in React](#useeffect-in-react)
- [Routing in React](#routing-in-react)
- [Pure Components](#pure-components)
- [useRef Hook](#useref-hook)
- [Callback Refs](#callback-refs)
- [Context API](#context-api)
- [useReducer Hook](#usereducer-hook)
- [useReducer vs useState](#usereducer-vs-usestate)
- [React Profiler](#react-profiler)
- [Tic Tac Toe - Component Tree & State Management](#tic-tac-toe---component-tree--state-management)
- [What is a Dispatcher?](#what-is-a-dispatcher)
- [Flux Architecture](#flux-architecture)
- [Higher-Order Components (HOCs)](#higher-order-components-hocs)
- [React Portals](#react-portals)
- [React Strict Mode](#react-strict-mode)
- [SSR and CSR](#ssr-and-csr)

---

## What is React?

ReactJS is a component-based JavaScript library used to build dynamic and interactive user interfaces. It simplifies the creation of single-page applications (SPAs) with a focus on performance and maintainability.

It is developed and maintained by Facebook.
The latest version of React is React 19.
Uses a virtual DOM for faster updates.
Supports a declarative approach to designing UI components.
Ensures better application control with one-way data binding.

---

## Working of React

React builds a Virtual DOM (a copy of the real DOM in memory).

When your app changes (like a button click), React creates a new Virtual DOM.

It compares the old and new Virtual DOMs to find what changed (this is called reconciliation).

React then updates only the changed part in the real browser DOM.

---

## Reconciliation

Reconciliation in React is the process of comparing the previous Virtual DOM with the new Virtual DOM to identify what has changed.
Once the differences (called "diffs") are found, React updates only those specific parts in the real DOM — making updates fast and efficient instead of re-rendering the whole UI.

---

## Features of React

React offers several powerful features that make it one of the most popular libraries for building modern web applications:

**Virtual DOM:**
React uses a Virtual DOM to optimize performance. It compares the new Virtual DOM with the previous one and updates only the changed parts in the actual DOM, making UI updates fast and efficient.

**Component-Based Architecture:**
React follows a component-based structure where the UI is divided into reusable, modular components. This improves code reusability, maintainability, and scalability.

**JSX (JavaScript XML):**
React uses JSX, which allows writing HTML-like syntax directly in JavaScript. It makes the code more readable and easier to write and debug.

**One-Way Data Binding:**
React uses unidirectional data flow, meaning data flows from parent to child via props. This makes the application more predictable and easier to debug.

**State Management:**
React handles dynamic data efficiently using useState for functional components and this.state for class components, allowing real-time UI updates without reloading the page.

**React Hooks:**
Hooks like useState, useEffect, and useContext let functional components manage state and side effects without the need for classes, making code cleaner and more modern.

**React Router:**
React Router enables client-side routing in single-page applications, allowing for seamless navigation without full-page reloads.

Overall, these features make React fast, scalable, and developer-friendly for building complex web applications.

---

## Challenges in React

**Limitations of React**

**SEO Challenges:** Since React is a client-side library, SEO optimization can be difficult for pages with heavy dynamic content. However, tools like Next.js can be used to render React applications server-side for better SEO.

**Steep Learning Curve:** React's ecosystem is vast, and learning how to work with tools like Redux and React Router and understanding component lifecycle methods can be challenging for beginners.

**Boilerplate Code:** Setting up and maintaining state management libraries like Redux or Context API can involve writing boilerplate code, especially for large applications.

---

## React vs Angular

| Feature                      | React                            | Angular                               |
|-----------------------------|-----------------------------------|----------------------------------------|
| Type                        | JavaScript **library**            | JavaScript **framework**               |
| Data Binding                | One-way data binding              | Two-way data binding                   |
| Templating                  | JSX (JavaScript XML)              | HTML templates with Angular directives |
| DOM Handling                | Uses **Virtual DOM**              | Uses **Real DOM**                      |

---

## How JSX Works

When React processes JSX code, it converts it into JavaScript using Babel. This JavaScript code then creates real HTML elements in the browser's DOM, which is how your web page gets displayed.

---

## What is Babel

Babel is a JavaScript compiler that converts modern JavaScript code (like ES6+ and JSX) into a backwards-compatible version that older browsers can understand.

---

## Diffing Algorithm

The diffing algorithm in React is used to compare the old Virtual DOM with the new Virtual DOM to find out what has changed.

Instead of reloading the whole UI, it identifies only the changed parts and updates them in the real DOM — making updates fast and efficient.

---

## React DOM

ReactDom is a core part of React responsible for rendering the elements on DOM efficiently from the virtualDOM. It also provides method for dynamically access and manage the DOM of the application.

---

## Code Splitting and Bundling

**🔗 Bundling:**
Bundling is the process of combining all your JavaScript files and dependencies into one or more files (bundles) to load in the browser. Tools like Webpack or Rollup do this to make your app faster and easier to deploy.

**✂️ Code Splitting:**
Code splitting is a technique that lets you split your bundle into smaller chunks and load them only when needed. This improves performance by reducing the initial load time and enables lazy loading of components.

In simple terms:

Bundling puts everything together; code splitting makes sure you only load what's needed, when it's needed.

---

## React Components

React components are independent, reusable building blocks in a React application that define what gets displayed on the UI. They accept inputs called props and return React elements describing the UI.

---

## Types of Components

### 1. Functional Components

Functional components are simpler and preferred for most use cases. They are JavaScript functions that return React elements. With the introduction of React Hooks, functional components can also manage state and lifecycle events.

**Stateless or Stateful:** Can manage state using React Hooks.
**Simpler Syntax:** Ideal for small and reusable components.
**Performance:** Generally faster since they don't require a 'this' keyword.

```javascript
function Greet(props) {
    return <h1>Hello, {props.name}!</h1>;
}
```

### 2. Class Components

Class components are ES6(ECMAScript) classes that extend React.Component. They include additional features like state management and lifecycle methods.

**State Management:** State is managed using the this.state property.
**Lifecycle Methods:** Includes methods like componentDidMount, componentDidUpdate, etc.

```javascript
class Greet extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}!</h1>;
    }
}
```

---

## Props in React

Props (short for properties) are read-only inputs passed from a parent component to a child component. They enable dynamic data flow and reusability.

Props are immutable.
They enable communication between components.

```javascript
function Greet(props) {
    return <h2>Welcome, {props.username}!</h2>;
}

// Usage
<Greet username="Anil" />;
```

---

## State in React

The state is a JavaScript object managed within a component, allowing it to maintain and update its own data over time. Unlike props, state is mutable and controlled entirely by the component.

State updates trigger re-renders.
Functional components use the useState hook to manage state.

```javascript
function Counter() {
    const [count, setCount] = React.useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => 
                setCount(count + 1)}>Increment</button>
        </div>
    );
}
```

---

## ReactJS Pure Components

ReactJS Pure Components are similar to regular class components but with a key optimization. They skip re-renders when the props and state remain the same. While class components are still supported in React, it's generally recommended to use functional components with hooks in new code for better performance and simplicity.

### How Does a Pure Component Work?

A PureComponent works by implementing the shouldComponentUpdate() lifecycle method with a shallow comparison of props and state. This method determines whether a component needs to re-render. When the component's state or props are updated, React performs the shallow comparison and decides if the component should update.

---

## React Lifecycle

🔄 The React lifecycle refers to the three main phases a class component goes through:

### 1. Mounting (Component is created and added to the DOM)

**constructor()** – Initializes state and props.

**render()** – Returns JSX to display.

**componentDidMount()** – Runs after the component is rendered; used for API calls or setup.

### 2. Updating (When props or state change)

**getDerivedStateFromProps()** – Updates state based on new props.

**shouldComponentUpdate()** – Decides whether to re-render.

**render()** – Re-renders the UI.

**getSnapshotBeforeUpdate()** – Captures data before the update (like scroll position).

**componentDidUpdate()** – Runs after the component updates.

### 3. Unmounting (Component is removed from the DOM)

**componentWillUnmount()** – Clean up (like removing event listeners or canceling API calls).

In functional components, React Hooks like useEffect are used to handle all lifecycle phases: mounting, updating, and unmounting — replacing traditional class lifecycle methods.

---

## Functional Components vs Class Components

| Feature              | Functional Components                                                  | Class Components                                                       |
|----------------------|------------------------------------------------------------------------|------------------------------------------------------------------------|
| **State Management** | Uses Hooks like `useState`, `useReducer`                               | Uses `this.state` and `this.setState()`                                |
| **Lifecycle Methods**| Uses `useEffect` and other Hooks                                       | Uses methods like `componentDidMount`, `componentWillUnmount`, etc.    |
| **Rendering**        | Returns JSX directly from the function                                 | Uses a `render()` method                                               |
| **Performance**      | Faster and lightweight due to simpler structure                        | Slightly heavier due to class instance overhead                        |
| **Hooks**            | Can use React Hooks like `useState`, `useEffect`                       | Cannot use Hooks                                                       |
| **this Keyword**     | Does not use `this`                                                    | Uses `this` to access props, state, and methods                        |
| **Code Complexity**  | Less boilerplate, easier to read and write                             | More boilerplate, especially with state and method bindings            |
| **Event Handling**   | Simple and direct event handling                                       | Requires method binding (e.g., `this.handleClick = this.handleClick.bind(this)`) |

---

## Conditional Rendering

Conditional Rendering in React means showing different UI elements based on certain conditions, like the value of state or props.

🔹 Example:
```jsx
{isLoggedIn ? <Welcome /> : <Login />}
```

If isLoggedIn is true, it shows the Welcome component; otherwise, it shows Login.

In short: Conditional rendering lets you display different content in the UI based on logic or user interaction.

---

## Keys in React

🔑 Keys in React are unique identifiers used to help React efficiently update and render elements in a list of items.

### 📌 Why are Keys Important?

When rendering lists, React uses keys to:

- Track which items changed, were added, or removed
- Avoid unnecessary re-renders
- Improve performance during UI updates

🔁 Example:
```jsx
const users = ['Alice', 'Bob', 'Charlie'];

function UserList() {
  return (
    <ul>
      {users.map((name, index) => (
        <li key={name}>{name}</li> // 'key' helps React identify each <li>
      ))}
    </ul>
  );
}
```

---

## Memoization in React

🧠 Memoization is a performance optimization technique used in React to avoid re-computing or re-rendering components or values if the inputs haven't changed.

### 📦 Common Memoization Tools in React:

**React.memo()**

Used to memoize functional components

Prevents re-rendering if props don't change

```jsx
const MyComponent = React.memo(function MyComponent(props) {
  return <div>{props.name}</div>;
});
```

**useMemo()**

Used to memoize computed values

```jsx
const result = useMemo(() => expensiveCalculation(x), [x]);
```

**useCallback()**

Used to memoize functions, so they don't get recreated on every render

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## React.memo vs useMemo

### 🧩 1. React.memo

🔄 *Used to prevent unnecessary re-renders of functional components.*

- It wraps a component to memoize the entire component.
- React will only re-render the component if its props change.

✅ **Example:**
```jsx
const MyComponent = React.memo(function MyComponent({ name }) {
  console.log("Rendering MyComponent");
  return <div>{name}</div>;
});
```

🧠 **Think of `React.memo` as:**  
*"Only re-render this component if its props actually changed."*

---

### 🧠 2. useMemo

⚙️ *Used to memoize expensive computed values inside a component.*

- It caches the result of a function and recomputes it only if dependencies change.
- Helpful for performance-heavy calculations or derived data.

✅ **Example:**
```jsx
const expensiveValue = useMemo(() => {
  return heavyCalculation(count);
}, [count]);
```

🧠 **Think of `useMemo` as:**  
*"Only recalculate this value if one of the dependencies changes."*

---

## Parameters of memo

React.memo takes a component and an optional custom comparison function.
If props didn't change (or are equal based on areEqual), React skips re-rendering.

---

## useEffect in React

🔁 `useEffect` lets you run side effects (e.g. data fetching, event listeners, timers) in functional components.  
You can control **when it runs** using the **dependency array**.

---

### 🧩 Different Ways to Use `useEffect`

✅ **1. Run on Every Render**
```jsx
useEffect(() => {
  console.log('Runs after every render');
});
```
🟡 *No dependency array → runs after every render (including first and updates).*

---

✅ **2. Run Only Once (on Mount)**
```jsx
useEffect(() => {
  console.log('Runs only on mount');
}, []);
```
🟢 *Empty array → runs only once when the component mounts.*

---

✅ **3. Run on Specific State/Prop Changes**
```jsx
useEffect(() => {
  console.log('Runs when count changes');
}, [count]);
```
🔁 *With dependencies → runs only when `count` changes.*

---

✅ **4. Cleanup on Unmount**
```jsx
useEffect(() => {
  const timer = setInterval(() => console.log('Tick'), 1000);
  return () => {
    clearInterval(timer);
    console.log('Cleaned up on unmount');
  };
}, []);
```
🧹 *Return a function from `useEffect` to clean up (e.g., timers, subscriptions).*

---

### 🧠 Summary Table:

| Use Case                  | Syntax                                       | Runs When                             |
|---------------------------|----------------------------------------------|----------------------------------------|
| Every render              | `useEffect(() => { ... });`                 | After every render                     |
| On mount (only once)      | `useEffect(() => { ... }, []);`             | Only when component mounts             |
| On specific value change  | `useEffect(() => { ... }, [x]);`            | When `x` changes                       |
| With cleanup on unmount   | `useEffect(() => { return () => {...}; }, []);` | On unmount                        |

---

## Routing in React

### 🌐 How Does Routing Work in React?

In React, **routing** is handled using libraries like **React Router**, which allow you to build **single-page applications (SPAs)** with multiple views (or "pages")—without reloading the browser.

---

### 🔧 Key Concepts in React Routing (using `react-router-dom`):

#### ✅ 1. **BrowserRouter**
Wraps your entire app and enables routing using the browser's URL.

```jsx
import { BrowserRouter } from "react-router-dom";

<BrowserRouter>
  <App />
</BrowserRouter>
```

---

#### ✅ 2. **Routes & Route**
Defines which component to render for each URL path.

```jsx
import { Routes, Route } from "react-router-dom";

<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

---

#### ✅ 3. **Link / NavLink**
Used instead of `<a>` tags to navigate between routes **without reloading the page**.

```jsx
import { Link } from "react-router-dom";

<Link to="/about">Go to About</Link>
```

---

#### ✅ 4. **useNavigate (Programmatic Navigation)**
Used to navigate through routes **in JavaScript** (e.g., after a form submit).

```jsx
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();
navigate("/home");
```

---

### 🧠 Behind the Scenes:
- React Router **intercepts URL changes** and loads the corresponding component.
- It **prevents full-page reloads**, keeping your app fast and seamless.
- Works based on the concept of **client-side routing**, not server-side.

---

### ✅ Example:

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | 
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

> Routing in React (via React Router) allows navigation between components based on the URL, enabling multi-page-like behavior in a single-page app—without refreshing the page.

---

## Pure Components

### 📌 What is a Pure Component?

A **Pure Component** in React is a component that **only re-renders when its props or state change**.  
It automatically implements `shouldComponentUpdate()` with a shallow comparison of props and state.

- Available only in **class components** (`React.PureComponent`).
- Helps improve performance by avoiding unnecessary re-renders.

---

## useRef Hook

### 📌 What is `useRef`? What are some use cases?

`useRef` is a **React Hook** that returns a **mutable object** which persists across component renders.  
It's mainly used to:

- **Access DOM elements**
- **Store values** that don't trigger a re-render when changed

---

### ✅ Syntax:
```jsx
const refContainer = useRef(initialValue);
```

---

### 🧠 Common Use Cases:

#### 1. **Accessing DOM elements**
```jsx
const inputRef = useRef(null);

useEffect(() => {
  inputRef.current.focus();
}, []);

return <input ref={inputRef} />;
```
🔍 Useful for directly interacting with DOM nodes (like focus, scroll, etc.)

---

#### 2. **Storing previous values**
```jsx
const prevCount = useRef();

useEffect(() => {
  prevCount.current = count;
}, [count]);
```
📌 Keeps track of the previous state value without causing re-renders.

---

#### 3. **Persistent values (like timers, intervals)**
```jsx
const timerRef = useRef();

useEffect(() => {
  timerRef.current = setInterval(() => {
    console.log("Tick");
  }, 1000);

  return () => clearInterval(timerRef.current);
}, []);
```
🧠 You can store identifiers or values that need to persist across renders **without causing a re-render**.

---

### 🔑 Summary:
- `useRef` does **not** cause re-renders when updated.
- It's perfect for **non-UI data** that needs to survive across renders.

---

## Callback Refs

### 📌 What are Callback Refs?

**Callback Refs** are an alternative way to assign refs in React using a **callback function** instead of the `useRef()` or `createRef()` API.

Instead of passing a ref object, you pass a **function** that receives the DOM node (or component instance) as its argument.

---

### ✅ Syntax:
```jsx
function MyComponent() {
  const setRef = (node) => {
    if (node) {
      // Access the DOM node or component instance
      node.focus();
    }
  };

  return <input ref={setRef} />;
}
```

❓ What does focus() do?
node.focus() is a native DOM method that puts the keyboard cursor inside the input field, making it ready to type.

---

### 🧠 When to Use Callback Refs?

- When you need **more control** over how the ref is assigned or updated.
- When you want to run logic **immediately** after the ref is set.
- When you want to assign **multiple elements** to different refs dynamically.
- Useful for **clean-up** or conditional rendering scenarios.

---

### 🔍 Difference from `useRef` or `createRef`:

| Feature               | useRef / createRef       | Callback Ref                  |
|-----------------------|--------------------------|-------------------------------|
| Stored automatically  | ✅ Yes                    | ❌ You handle it manually     |
| Trigger re-renders    | ❌ No                     | ❌ No                         |
| Extra logic on assign | ❌ No                     | ✅ Yes (custom logic possible) |

---

### 🔑 Summary:
> A **callback ref** is a function you pass to the `ref` prop that gives you direct access to the DOM node or component instance, offering more flexibility than `useRef`.

---

## Context API

### 📌 How Does Context API Work? What Does It Solve?

The **Context API** in React provides a way to share values (like state, themes, or user data) between components **without passing props manually at every level**.

---

### 🧠 What Problem Does It Solve?

✅ Solves **"prop drilling"** – where you have to pass props through many nested components that don't need them, just to get data to a deeply nested child.

---

### ✅ How It Works:

1. **Create Context**
```jsx
const ThemeContext = React.createContext();
```

2. **Provide Context Value**
```jsx
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>
```

3. **Consume Context Value**
- Using `useContext` (in functional components):
```jsx
const theme = useContext(ThemeContext);
```

- Using `ThemeContext.Consumer` (in class or functional components):
```jsx
<ThemeContext.Consumer>
  {value => <div>{value}</div>}
</ThemeContext.Consumer>
```

---

### 📦 Use Case Examples:
- App theme (light/dark)
- User authentication state
- Language (i18n)
- Global configuration or settings

---

### 🔑 Summary:
> The **Context API** allows you to share global data across the component tree **without manually passing props**, making your code cleaner, more maintainable, and scalable.

#### Basic Example:
```jsx
const ThemeContext = React.createContext();

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  const theme = useContext(ThemeContext);
  return <div className={theme}>Hello</div>;
}
```

---

## useReducer Hook

### 📌 What does `useReducer` do?

`useReducer` is a React Hook used for **managing complex state logic** in functional components.

It works similarly to a Redux reducer and is ideal when:
- You have **multiple related pieces of state**.
- You need **predictable state transitions** based on actions.

---

### ✅ Syntax:
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

- `reducer`: A function that determines how state should change based on an action.
- `dispatch`: A function used to send actions to the reducer.
- `state`: The current state.

---

### 🧠 Example:
```jsx
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}
```

---

### 🔑 Summary:
> `useReducer` is best for **state with complex logic**, **multiple sub-values**, or when **state changes depend on previous state**. It provides more structure and scalability than `useState`.

---

## useReducer vs useState

### 📌 When to Use `useReducer` vs `useState`?

| Situation                                | useState                         | useReducer                            |
|------------------------------------------|----------------------------------|----------------------------------------|
| Simple state (e.g., form inputs, toggle) | ✅ Best fit                      | ❌ Overkill                            |
| Complex state transitions                | ❌ Hard to manage                | ✅ Easier to organize with actions     |
| State depends on previous state          | ✅ Okay with functional updates | ✅ More structured                     |
| Multiple related state variables         | ❌ Can get messy                 | ✅ Groups logic in one place           |

🧠 **Use `useReducer`** when your state logic is complex, involves many sub-values, or you want better control and organization with actions and state updates.

---

## React Profiler

### 🧪 How Do You Use React Profiler?

The **React Profiler** is a developer tool that helps you **measure and analyze performance** in React applications.

It allows you to **see which components are re-rendering**, how long they take, and why they re-render—helping you optimize your app.

---

### ✅ How to Use React Profiler:

1. **Install React Developer Tools** in Chrome or Firefox.
2. Open the **React tab** in DevTools.
3. Switch to the **"Profiler" tab**.
4. Click the **"Record" button**, then interact with your app.
5. Click **"Stop"** to see:
   - Render time of components
   - Commit duration
   - Why a component re-rendered (if available)

---

### 🧠 What Can You Analyze?

- Which components are rendering frequently
- How long each render takes
- Whether a component was re-rendered unnecessarily
- Effects of memoization (`React.memo`, `useMemo`, etc.)

---

### 🔑 Summary:

> React Profiler helps developers **identify performance bottlenecks** by visualizing **how components render over time**, making it easier to optimize rendering behavior.

---

## Tic Tac Toe - Component Tree & State Management

### 🎮 Tic Tac Toe – Component Tree & State Management Design

Building a Tic Tac Toe game in React involves breaking down the UI into components and deciding **where to hold the state**. React encourages lifting the state to the nearest common ancestor.

---

### 📦 Component Tree Structure

```
<App>
 └── <Game>
      ├── <Board>
      │     ├── <Square />  // (9 times)
      └── <GameInfo />
```

---

### 🧠 State Management Design

| Component     | Responsibility                      | Holds State? |
|---------------|--------------------------------------|--------------|
| `App`         | Root container                       | ❌           |
| `Game`        | Controls overall game logic:<br>- Game history<br>- Current player<br>- Game status | ✅           |
| `Board`       | Displays 3×3 grid using `Square`     | ❌           |
| `Square`      | Displays individual box              | ❌           |
| `GameInfo`    | Displays status & move history       | ❌           |

---

### 🧩 Why is the state kept in `Game`?

- `Game` needs to manage:
  - **Board state** (array of 9 squares)
  - **Current turn** (X or O)
  - **Winner or draw logic**
  - **Move history** (for time-travel feature)

Keeping state in `Game` lets you:
- Share data with both `Board` and `GameInfo`
- Allow undo/redo functionality
- Avoid prop-drilling through intermediate components

---

### ✅ State Example in `Game`
```jsx
const [history, setHistory] = useState([Array(9).fill(null)]);
const [stepNumber, setStepNumber] = useState(0);
const [xIsNext, setXIsNext] = useState(true);
```

---

### 📋 Summary

- **Component Tree:** Organized into `Game`, `Board`, and multiple `Square` components.
- **State Location:** Centralized in the `Game` component to manage board updates and history.
- **Props Flow:** Data and handlers are passed **top-down** from `Game` → `Board` → `Square`.

This design keeps components clean, allows easy state tracking, and enables features like move history and reset functionality.

---

## What is a Dispatcher?

### 📦 What is a Dispatcher?

In React (especially with libraries like Redux or Flux), a **Dispatcher** is a central mechanism used to **send or "dispatch" actions** to update the state of the application.

It acts as a **middleman** between your application and your state logic (like a reducer).

---

### 🧠 In Context of `useReducer` or Redux:

- You **dispatch** an action object (e.g., `{ type: "increment" }`)
- The **dispatcher** sends that action to the **reducer**
- The reducer decides how to update the state based on the action type

---

### ✅ Example with `useReducer`:
```jsx
const [state, dispatch] = useReducer(reducer, initialState);

// Dispatcher in action
dispatch({ type: 'increment' });
```
Here, `dispatch` is the dispatcher. It sends an action to the `reducer`.

---

### 🔁 In Redux:

Redux has a single store and uses a global dispatcher function:
```js
store.dispatch({ type: 'ADD_TODO', payload: 'Study React' });
```

---

### 🔑 Summary:
> A **Dispatcher** is a function that sends **actions** to a reducer or store to **update the state**. It helps separate what happens (the action) from how it affects state (handled in the reducer).

---

## Flux Architecture

### 🔄 What is Flux Architecture?

**Flux** is a design pattern (architecture) used for managing **unidirectional data flow** in React applications. It was introduced by **Facebook** to handle complex state logic more predictably.

---

### 🧠 Core Idea:
Data flows in **one direction**, avoiding the confusion of two-way data binding.

---

### 📦 Key Components of Flux:

| Part         | Role                                                                 |
|--------------|----------------------------------------------------------------------|
| **Actions**  | Plain JavaScript objects that describe "what happened"               |
| **Dispatcher** | Central hub that broadcasts actions to all stores                   |
| **Stores**   | Hold the application state and logic; respond to dispatched actions  |
| **Views**    | React components that render UI based on store state                 |

---

### 🔁 Data Flow in Flux:

```
User Interaction
       ⬇
    Action (e.g., { type: 'ADD_TODO' })
       ⬇
 Dispatcher (sends action to stores)
       ⬇
     Store (updates state)
       ⬇
     View (React re-renders UI)
```

---

### ✅ Benefits of Flux:
- **Predictable state updates**
- **Single source of truth (store)**
- Easier to **debug and test**
- Encourages **separation of concerns**

---

### 🔄 Flux vs Redux:
Redux is a **library inspired by Flux**, but:
- It uses a **single store** instead of multiple.
- It eliminates the need for a dispatcher.
- It uses **pure reducers** to manage state updates.

---

### 🔑 Summary:
> **Flux** is an architecture pattern that ensures a **unidirectional data flow**, making it easier to manage and debug application state in large-scale React apps.

---

## Higher-Order Components (HOCs)

### 🔁 What are Higher-Order Components (HOCs) in React?

A **Higher-Order Component (HOC)** is a **function that takes a component as input and returns a new component** with additional props, logic, or behavior.

HOCs are a pattern for **code reuse** in React.  
They are **not part of the React API**, but a convention based on JavaScript's higher-order functions.

---

### ✅ Syntax:
```jsx
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

---

### 📦 Use Cases:
- Adding authentication checks
- Reusing loading/spinner logic
- Handling errors
- Injecting additional props or behavior

---

### 🧠 Example: `withLogger` HOC

```jsx
// A Higher-Order Component that logs props
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log("Props:", props);
    return <WrappedComponent {...props} />;
  };
}

// Usage
function Hello({ name }) {
  return <h1>Hello, {name}!</h1>;
}

const HelloWithLogger = withLogger(Hello);

// In your App:
<HelloWithLogger name="Purvesh" />
```

🧾 This wraps the `Hello` component and logs the props whenever it's rendered.

---

### 🔑 Summary:
> A **Higher-Order Component (HOC)** is a function that wraps a component to extend its behavior.  
> It allows you to **reuse logic** across multiple components without repeating code.

---

## React Portals

### 🚪 How Do React Portals Work, and When Should They Be Used?

### 📌 What are React Portals?

**React Portals** provide a way to render components **outside the main React DOM tree**  
while still preserving their position in the React component hierarchy.

---

### ✅ Syntax:
```jsx
import ReactDOM from 'react-dom';

ReactDOM.createPortal(child, container)
```

- `child`: The JSX you want to render
- `container`: The DOM node (outside of `#root`) where it should be rendered

---

### 🧠 Use Case Example:

```jsx
import ReactDOM from 'react-dom';

function Modal({ children }) {
  return ReactDOM.createPortal(
    <div className="modal">{children}</div>,
    document.getElementById('modal-root') // separate div from root
  );
}
```

📄 HTML:
```html
<body>
  <div id="root"></div>
  <div id="modal-root"></div> <!-- This is where modal will be rendered -->
</body>
```

---

### 🧩 When Should You Use Portals?

✅ Common scenarios:
- **Modals / Dialogs**
- **Tooltips**
- **Dropdowns**
- **Overlays**  
When you want to **visually "break out" of the parent component**, but still keep the React logic consistent.

---

### 🔑 Summary:
> **React Portals** allow you to render UI into a different part of the DOM (outside the root)  
> while maintaining the component's place in the **React hierarchy** — ideal for modals, tooltips, and overlays.

---

## React Strict Mode

### 🔍 What is React Strict Mode, and How Does It Help Developers?

### 📌 What is React Strict Mode?

**React Strict Mode** is a **development-only tool** that helps you identify potential problems in your React code.

It doesn't render any visible UI. Instead, it activates **additional checks and warnings** for its children.

---

### ✅ How to Use:
```jsx
import React from 'react';

<React.StrictMode>
  <App />
</React.StrictMode>
```

✅ Typically used in `index.js` or `main.jsx`.

---

### 🧠 What Does It Help With?

1. **Identifies Unsafe Lifecycles**  
   Warns about usage of legacy lifecycle methods like `componentWillMount`.

2. **Detects Unexpected Side Effects**  
   Runs components and `useEffect`/`useLayoutEffect` **twice** on purpose (in development) to catch issues.

3. **Warns About Deprecated APIs**  
   Highlights outdated React features so you can update them.

4. **Strict Mode for Concurrent Features**  
   Helps ensure compatibility with upcoming concurrent features in React.

---

### ⚠️ Important Notes:
- It only runs in **development mode**.
- It does **not affect production builds**.
- It renders components **twice** (only in dev) to simulate mounting/unmounting.

---

### 🔑 Summary:
> **React.StrictMode** helps developers write better, safer, and future-proof code by enabling extra checks, warnings, and highlighting unsafe or deprecated patterns — without affecting production behavior.

---

## SSR and CSR

### 🌐 What is SSR and CSR?

### 📌 SSR (Server-Side Rendering)
**Server-Side Rendering** means rendering the HTML of your React components **on the server** and sending a fully-rendered page to the browser.

#### ✅ How it works:
- Server renders the page HTML
- Browser receives the HTML
- React "hydrates" the page to make it interactive

#### ⚙️ Technologies: 
- `Next.js`, `Express + React DOMServer`

#### ✅ Benefits:
- Faster initial page load (good for SEO)
- Content is visible even before JavaScript loads

---

### 📌 CSR (Client-Side Rendering)
**Client-Side Rendering** means the browser downloads a minimal HTML page and then **JavaScript renders everything** on the client (browser) after the app loads.

#### ✅ How it works:
- Server sends a basic HTML shell
- React loads on the browser
- UI is rendered using JavaScript in the browser

#### ⚙️ Technologies:
- `Create React App (CRA)`, `Vite`, `Parcel`

#### ✅ Benefits:
- Faster interactions after initial load
- Better for apps with lots of dynamic content

---

### 🔁 SSR vs CSR Comparison:

| Feature                | SSR                            | CSR                          |
|------------------------|--------------------------------|------------------------------|
| Initial Load Time      | Faster (HTML ready)            | Slower (JS must load first) |
| SEO                    | Better                         | Poor (unless prerendered)   |
| Interactivity Start    | After hydration                | After JS loads               |
| Complexity             | Higher                         | Lower                        |

---

### 🔑 Summary:
> **SSR** renders HTML on the server and is great for SEO & initial load speed.  
> **CSR** renders everything in the browser and is ideal for interactive web apps with fewer SEO needs.
