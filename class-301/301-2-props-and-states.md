# React States and Props Notes

## What is state?

State is an object that holds data that a component can access and modify. It is used to keep track of the internal state of a component and to update the UI based on changes in that state.

Example:

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

## What are props?

Props, short for properties, are a way to pass data from a parent component to a child component. They are read-only and cannot be modified by the child component. Props are defined as attributes on a JSX element and accessed through the props object in the child component.

Example:

```jsx
function Parent() {
  const name = "Alice";
  return <Child name={name} />;
}

function Child(props) {
  return <p>Hello, {props.name}!</p>;
}
```

## Sending stuff from props to a child component

To pass data as props to a child component, we can define attributes on the child component in the parent component's JSX.

Example:

```jsx
function Parent() {
  const message = "Hello World!";
  return <Child message={message} />;
}

function Child(props) {
  return <p>{props.message}</p>;
}
```

## Accessing a variable in the props from the child component

To access props in a child component, we use the props object that is passed as an argument to the component function.

Example:

```jsx
function Child(props) {
  return <p>{props.message}</p>;
}
```

## Information flows from parent components to child components

Information flows in one direction: from parent components to child components. Child components cannot pass data back up to their parent components, but they can trigger events that their parent components can listen for.
What is Bootstrap?

Bootstrap is a popular CSS framework that provides pre-made UI components and styles for building responsive web pages. It is a set of CSS classes and JavaScript plugins that simplify the process of creating a responsive web design.

Example:

```jsx
import React from "react";
import { Button } from "react-bootstrap";

function App() {
  return (
    <div>
      <Button variant="primary">Click me!</Button>
    </div>
  );
}
```

## What are different things that I can customize using something like Bootstrap or Tailwind?

Using a CSS framework like Bootstrap or Tailwind, you can customize many different aspects of your website's appearance, including typography, colors, layout, forms, buttons, and more. These frameworks provide pre-built CSS classes that can be easily applied to your HTML elements to achieve a desired look and feel.

Example:

```html
<button class="btn btn-primary">Click me!</button>
```

## How does Bootstrap use classes for customization?

Bootstrap uses CSS classes to apply pre-built styles and components to HTML elements. These classes can be added directly to HTML elements, or they can be used in conjunction with JavaScript plugins to add interactive behavior to your website.

Example:

```html
<button class="btn btn-primary">Click me!</button>
```
