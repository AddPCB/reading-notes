# React intro notes

1. What is React?

React is a JavaScript library that is used to build user interfaces. It was developed by Facebook and is now an open-source project. React allows developers to create reusable components that can be used across different pages or applications. React uses a virtual DOM to efficiently render changes in the user interface.

Example:

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = <h1>Hello World!</h1>;
ReactDOM.render(myElement, document.getElementById("root"));
```

1. What are components?

Components are the building blocks of a React application. They are reusable pieces of code that represent a part of the user interface. Components can be nested within each other to create more complex user interfaces. React components can be either class-based or functional.

Example:

```javascript
import React from "react";

function Button(props) {
  return <button onClick={props.onClick}>{props.label}</button>;
}

export default Button;
```

1. What is the difference between an arrow function and a function declaration?

Arrow functions are a more concise way of writing function declarations. They are often used for callbacks, because they allow for a shorter syntax. Unlike function declarations, arrow functions do not create a new this context, which can be a source of confusion.

Example:

```javascript

// Function declaration
function doSomething(name) {
  // Do something
}

// Arrow function
doSomething = (name) => {
  // Do something
}

// Or make it a one liner!
doSomething = (name) => // Do something small

4. Turning a function declaration into an arrow function:

javascript

function doSomething(name) {
  // Do something
}

doSomething = (name) => {
  // Do something
}
```

1. Difference between a constructor function and a class:

A constructor function is a way of creating objects in JavaScript. It is a special function that gets called when a new object is created. Classes are a newer way of defining objects in JavaScript, and they provide a more concise syntax for creating objects. Classes can be thought of as blueprints for objects.

Example:

```javascript
// Constructor
function Cat(name) {
  this.name = name;
  this.fluffy = true;
}

Cat.prototype.speak = function () {
  console.log(`${this.name} says meow`);
};

const bob = new Cat("Bob");
bob.speak();

// Class
class Cat {
  constructor(name) {
    this.name = name;
    this.fluffy = true;
  }

  speak = () => console.log(`${this.name} says meow`);
}

const bob = new Cat("bob");
bob.speak();
```

1. Basic React Component Structure:

React components can be created as classes or functions. Class-based components need to extend the React.Component class and implement a render method that returns the component's JSX. Functional components are simpler and just need to return the component's JSX.

Example:

```javascript

import React from 'react';

class Something extends React.Component {
  render() {
    return (
      <section>
        <h1>Header for Something</h1>
        <p>Text that is all about Something.<p>
      </section>
    );
  }
}

export default Something;
```
