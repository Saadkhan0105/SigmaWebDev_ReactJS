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


# React Components

React components are the **building blocks** of a React application. They help break down the UI into **reusable**, **independent**, and **manageable** pieces.

---

## Types of Components in React

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

### 3. Pure Components
- **Class-based components** that prevent unnecessary re-renders.
- Improves performance by **reducing unnecessary DOM updates**.

```jsx
import React, { PureComponent } from 'react';

class PureComp extends PureComponent {
  render() {
    console.log("Pure Component Rendered");
    return <h1>Pure Component Example</h1>;
  }
}

export default PureComp;
```

---

### 4. Higher-Order Components (HOC)
- A pattern where a function **takes a component as input** and **returns a new component** with added functionality.
- Used for **code reuse**, **conditional rendering**, and **authentication**.

```jsx
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log("Logging Props:", props);
    return <WrappedComponent {...props} />;
  };
}
```

---

### 5. Controlled & Uncontrolled Components

#### **Controlled Components:**
- React **controls the value** through `useState` or `this.state`.
- Input values update via **onChange handlers**.

```jsx
function ControlledInput() {
  const [name, setName] = React.useState("");

  return (
    <input type="text" value={name} onChange={(e) => setName(e.target.value)} />
  );
}
```

#### **Uncontrolled Components:**
- React **does not control** the form input values. Instead, it accesses them via `ref`.

```jsx
import React, { useRef } from "react";

function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    alert(inputRef.current.value);
  };

  return (
    <>
      <input type="text" ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

---

### 6. Presentational vs Container Components

#### **Presentational Components:**
- Only responsible for **UI rendering**.
- **Do not** have state or logic.

```jsx
function UserCard({ name }) {
  return <h2>User: {name}</h2>;
}
```

#### **Container Components:**
- Handle **logic, state, and data fetching**.
- Pass data to presentational components.

```jsx
import React, { useState } from "react";
import UserCard from "./UserCard";

function UserContainer() {
  const [user, setUser] = useState("Saad Khan");

  return <UserCard name={user} />;
}
```

---

### 7. Lazy Loaded Components (React.lazy & Suspense)
- **Loads components dynamically** when needed to improve performance.

```jsx
import React, { Suspense, lazy } from "react";

const LazyComponent = lazy(() => import("./HeavyComponent"));

function App() {
  return (
    <Suspense fallback={<h2>Loading...</h2>}>
      <LazyComponent />
    </Suspense>
  );
}
```

---


