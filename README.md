# SigmaWebDev_ReactJS

## Why React?
- We can use **states**, which means that once we update the state variable, it changes across the page.
- We can split our app into **multiple components** and reuse those components.
- React uses a **virtual DOM** to efficiently update the UI, which is better than updating content using direct DOM Manipulation.
- **Debugging and maintenance** are easy.

## Features
- Component-based architecture
- State management with React hooks
- Responsive design with Tailwind CSS
- API integration using Axios
- Routing with React Router


# React Components, Props, and JSX

React components are the **building blocks** of a React application. They help break down the UI into **reusable**, **independent**, and **manageable** pieces.

---

## Components in React

### 1. Functional Components (Stateless Components)
- Simple JavaScript functions that return JSX.
- **Do not** have their own state (before React Hooks), but now they can use `useState`, `useEffect`, etc.

```jsx
function Greeting() {
  return <h1>Hello, Saad!</h1>;
}

export default Greeting;
```

---

### 2. Class Components (Stateful Components)
- ES6 classes that extend `React.Component`.
- Can have their own state and lifecycle methods (`componentDidMount`, `componentDidUpdate`, etc.).

```jsx
import React, { Component } from 'react';

class Counter extends Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>Count: {this.state.count}</h1>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```

---

## Props in React

- **Props (short for Properties)** are used to pass data from a parent component to a child component.
- They are **read-only** and **cannot be modified** inside the child component.

```jsx
function UserProfile({ name, age }) {
  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
    </div>
  );
}

function App() {
  return <UserProfile name="Saad Khan" age={28} />;
}
```

---

## JSX in React

- **JSX (JavaScript XML)** is a syntax extension that allows writing HTML-like code inside JavaScript.
- It makes the code more readable and expressive.

### Features of JSX
1. **Looks like HTML** but is transpiled to JavaScript.
2. **Allows embedding expressions using `{}`**.
3. **Must have a single parent element**.
4. **Attributes are written in camelCase (e.g., `className` instead of `class`)**.

```jsx
const element = <h1>Hello, {name}!</h1>;
```

### JSX vs JavaScript

JSX:
```jsx
const heading = <h1>Hello, React!</h1>;
```
JavaScript (without JSX):
```jsx
const heading = React.createElement('h1', null, 'Hello, React!');
```

---

### Hooks

- React hooks are special functions in React that allow you to manage state and lifecycle features in functional components, which were traditionally only available in class components.
- Hooks simplify the code and make it easier to manage complex logic and side effects in React components.

## Types of Hooks are:

## 1. useState:
- The React useState Hook allows us to track state in a function component.
- useState is a React Hook that lets you add a state variable to your component.

```
import { useState } from "react";

  function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>The count is {count}</div>
      <button onClick={()=>setCount(count+1)}>Update Count</button>
    </>
  )
}
```

## 2. useEffect:
-useEffect is a React Hook that allows you to perform side effects in function components. It runs after the component renders and can be used for tasks like:

- ✅ Fetching data from an API
- ✅ Updating the DOM
- ✅ Setting up event listeners
- ✅ Managing timers or intervals
- Call useEffect at the top level of your component to declare an Effect:
```
function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`Count updated: ${count}`);
  }, [count]); // Runs when 'count' changes

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```