# Passing Functions As Props

## How a child can component update the state of a parent component

In React, data flows down from a parent component to a child component through props.
However, when a child component needs to update the state of a parent component, it can do so by passing a function down to the child component through props.
The child component can then call this function to update the state of the parent component.
This allows for two-way communication between components and enables the child component to change the state of the parent component.

Example:

````kotlin

class Parent extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      count: 0
    }
  }

  updateCount = (newCount) => this.setState({ count: newCount });

  render(){
    return(
      <Child updateCount={this.updateCount}>
    )
  }
}

class Child extends React.Component {
  constructor(props){
    super(props);
    this.state={
      newCount: 0
    }
  }

  updateChildCount = () => {
    const { updateCount } = this.props;
    const { newCount } = this.state;
    updateCount(newCount);
  }

  render(){
    return(
      <>
        <form onSubmit={this.updateChildCount}>
          <label>Enter a new count:</label>
          <input onChange={(e) => this.setState({ newCount: e.target.value })} />
        </form>
      </>
    )
  }
}
``

In the example above, the Parent component passes down its updateCount function to the Child component through props.
The Child component then calls this function with the new count entered in the input field.
This updates the count state in the Parent component, and the new count is displayed in the Parent component.

# How a parent component sends a function into a child component?

In React, a parent component can send a function into a child component through props.
To do this, the parent component defines a function and passes it down to the child component as a prop.
The child component can then use this function to perform some action, such as updating the state of the parent component.

Example:

```kotlin

class Parent extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      message: 'Hello, World!'
    }
  }

  showMessage = () => {
    console.log(this.state.message);
  }

  render(){
    return(
      <Child showMessage={this.showMessage}>
    )
  }
}

class Child extends React.Component {
  render(){
    const { showMessage } = this.props;
    return(
      <>
        <button onClick={showMessage}>Click me!</button>
      </>
    )
  }
}
````

In the example above, the Parent component defines a function called showMessage, which logs the message stored in the Parent component's state to the console.
The Parent component passes this function down to the Child component through props.
The Child component then renders a button with an onClick handler that calls the showMessage function when clicked.
When the button is clicked, the showMessage function defined in the Parent component is executed, and the message is logged to the console.

## Using React-Bootstrap to determine if a modal is open or closed

In React-Bootstrap, you can use the show prop to determine whether a modal is open or closed.
If the show prop is set to true, the modal is open.
If the show prop is set to false, the modal is closed.

Example:

```javascript
import { Modal, Button } from "react-bootstrap";

class MyModal extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      showModal: false,
    };
  }

  handleClose = () => {
    this.setState({ showModal: false });
  };

  handleShow = () => {
    this.setState({ showModal: true });
  };

  render() {
    const { showModal } = this.state;
    return (
      <>
        <Button onClick={this.handleShow}>Open Modal</Button>
        <Modal show={showModal} onHide={this.handleClose}>
          <Modal.Header closeButton>
            <Modal.Title>Modal Title</Modal.Title>
          </Modal.Header>
          <Modal.Body>Modal content goes here</Modal.Body>
          <Modal.Footer>
            <Button variant="secondary" onClick={this.handleClose}>
              Close
            </Button>
          </Modal.Footer>
        </Modal>
      </>
    );
  }
}
```

In the example above, a modal is created using the Modal component from React-Bootstrap.
The show prop is set to the value of the showModal state variable, which determines whether the modal is open or closed.
The handleShow and handleClose functions are defined to update the showModal state variable.
When the Open Modal button is clicked, the handleShow function is called, which sets the showModal state variable to true, causing the modal to open.
When the Close button is clicked, the handleClose function is called, which sets the showModal state variable to false, causing the modal to close.

## Allowing the child component to update the state in the parent component

### Step 1

Send a function into the child component that updates the state in the parent component

````javascript

class Parent extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      name: 'bob'
    }
  }

  updateName = (newName) => this.setState({ name: newName });

  render(){
    return(
      <Child updateName={this.updateName}>
    )
  }
}
``

In the example above, the Parent component defines a function called updateName that updates the name state in the Parent component.
The Parent component passes this function down to the Child component through props using the prop name updateName.

### Step 2

Invoke that function from the props in the child component

```javascript

class Child extends React.Component {
  constructor(props){
    super(props);
    this.state={
      newName:''
    }
  }

  updateChildName = () => {
    const { updateName } = this.props;
    const { newName } = this.state;
    updateName(newName);
  }

  render(){
    return(
      <>
        <form onSubmit={this.updateChildName}>
          <label>What is your new name?</label>
          <input onChange={(e) => this.setState({ newName: e.target.value })} />
        </form>
      </>
    )
  }
}
````

In the example above, the Child component defines a function called updateChildName that is called when the form is submitted.
This function first retrieves the updateName function from the props and the new name from the state.
It then calls the updateName function with the new name as an argument.
This updates the name state in the Parent component, and the new name is displayed in the Parent component.

### Step 3

The invoked function from the child component will update the name in the parent component and tada! Your child component has essentially changed the state of your parent component

Here are three examples of how to implement this pattern in React:

#### Example 1

```javascript
class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  updateCount = (newCount) => {
    this.setState({ count: newCount });
  };

  render() {
    return <Child updateCount={this.updateCount} />;
  }
}

class Child extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      newCount: 0,
    };
  }

  handleInputChange = (event) => {
    this.setState({ newCount: event.target.value });
  };

  handleSubmit = (event) => {
    event.preventDefault();
    this.props.updateCount(this.state.newCount);
  };

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Enter a new count:
          <input type="number" value={this.state.newCount} onChange={this.handleInputChange} />
        </label>
        <button type="submit">Update Count</button>
      </form>
    );
  }
}
```

#### Example 2

```javascript
class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "",
    };
  }

  updateText = (newText) => {
    this.setState({ text: newText });
  };

  render() {
    return (
      <div>
        <Child updateText={this.updateText} />
        <p>Current Text: {this.state.text}</p>
      </div>
    );
  }
}

class Child extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      newText: "",
    };
  }

  handleInputChange = (event) => {
    this.setState({ newText: event.target.value });
  };

  handleSubmit = (event) => {
    event.preventDefault();
    this.props.updateText(this.state.newText);
  };

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Enter new text:
          <input type="text" value={this.state.newText} onChange={this.handleInputChange} />
        </label>
        <button type="submit">Update Text</button>
      </form>
    );
  }
}
```

#### Example 3

```javascript
class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      items: [],
    };
  }

  addItem = (newItem) => {
    this.setState({ items: [...this.state.items, newItem] });
  };

  render() {
    return (
      <div>
        <Child addItem={this.addItem} />
        <ul>
          {this.state.items.map((item) => (
            <li key={item}>{item}</li>
          ))}
        </ul>
      </div>
    );
  }
}

class Child extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      newItem: "",
    };
  }

  handleInputChange = (event) => {
    this.setState({ newItem: event.target.value });
  };

  handleSubmit = (event) => {
    event.preventDefault();
    this.props.addItem(this.state.newItem);
    this.setState({ newItem: "" });
  };

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Add item:
          <input type="text" value={this.state.newItem} onChange={this.handleInputChange} />
        </label>
        <button type="submit">Add</button>
      </form>
    );
  }
}
```

In these examples, the parent components pass down a function through props to the child components.
The child components then call this function with new data to update the state of the parent components.
This pattern enables communication and collaboration between components and is a fundamental concept in React.
