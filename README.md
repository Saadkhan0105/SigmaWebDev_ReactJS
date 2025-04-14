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

## 3.useRef:

- useRef is a React Hook that allows you to create a mutable reference to a DOM element or a variable that persists between renders without causing re-renders.

###  When to Use useRef?
- ✅ Accessing DOM elements (like input fields)
- ✅ Storing values that don’t trigger re-renders
- ✅ Keeping track of previous values

```
import { useRef } from "react";

function InputFocus() {
  const inputRef = useRef(null);

  const handleClick = () => {
    inputRef.current.focus(); // Focus the input field
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Type something..." />
      <button onClick={handleClick}>Focus Input</button>
    </div>
  );
}

export default InputFocus;
```

## Limitatios of using useRef: 

- You can mutate the ref.current property. Unlike state, it is mutable. However, if it holds an object that is used for rendering (for example, a piece of your state), then you shouldn’t mutate that object.
- When you change the ref.current property, React does not re-render your component. React is not aware of when you change it because a ref is a plain JavaScript object.
- Do not write or read ref.current during rendering, except for initialization. This makes your component’s behavior unpredictable.
- In Strict Mode, React will call your component function twice in order to help you find accidental impurities. This is development-only behavior and does not affect production. Each ref object will be created twice, but one of the versions will be discarded. If your component function is pure (as it should be), this should not affect the behavior.


## Handling Events:

- Handling events in React is similar to handling events in regular JavaScript, but with some differences:
 1. Events are written in camelCase (onClick instead of onclick).
 2. Instead of strings, event handlers are passed as functions.

```
import { useState } from "react";

function ClickCounter() {
  const [count, setCount] = useState(0);

  // Event handler function
  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div className="p-4 text-center">
      <p className="text-xl">Count: {count}</p>
      <button 
        className="mt-2 px-4 py-2 bg-blue-500 text-white rounded-lg"
        onClick={handleClick}
      >
        Click Me
      </button>
    </div>
  );
}

export default ClickCounter;
```

## 4. useContext:

- The useContext hook in React is used to access the value of a context directly inside a functional component, without having to wrap your component in a Consumer component.

## When to use useContext:

- Use it when you want to share data globally (like theme, user authentication, language preferences, etc.) across components, without prop-drilling (passing props through every intermediate component).

## Basic Syntax:
```
const value = useContext(MyContext);
```