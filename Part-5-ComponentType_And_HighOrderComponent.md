## What’s React Component?
  - A React Component is one of the core building blocks of React Apps. In other words, we can say that every application you will develop in React will be made up of pieces called components. Components make the task of building UIs much easier.
  - from: https://www.geeksforgeeks.org/reactjs/ 
  - In React we mainly have two types of components: Functional Components and Class Components.
  
<p align="center">
<img src="https://miro.medium.com/max/600/1*3bRc_w8bvE7zbuxISQUukQ.png" width="500px"  ></p>
 
 ### Types of React Components 
 1. **Functional Components**
    - In simple words, Functional components are javascript functions. By writing a javascript function, we can create a functional component in React Apps.Functional components do not require data from other components. Functional components are usually used to display information. They are easy to read, debug, and test.
    - Functions that return JSX. Can do more stuff with React Hooks.
 2. **Class Components**
    - The Class Components are similar to the functional component but has some additional features that makes class component a little more complex than the functional components.Class components are able to do everything a functional component do but more.
    - Classes that can manipulate state, props, and lifecycle methods.
 3. **Pure Components**
    - Pure components are like better functional components. Components that only return a render function are optimal for pure components to shine.Pure components are primarily used to provide optimizations. They are the simplest and fastest components we can write. They do not depend or modify the state of variables outside its scope.
    - Functional components that performs shouldComponentUpdate() automatically. Re-renders only if state or props is different from previous state or props.
 4. **Higher-Order Components**
    - Higher-order components(HOC) is an advanced technique in React for reusing component logic.Take a Component as input and returns the component as output but with extended functionalities.This is a function that returns one or multiple components, depending on the number of elements in the array, also known as HOC.
    - Functions that return one or multiple components, depending on array data.
<br>
<br>

# High Order Components

## What is it :question:

- Components are the primary unit of code reuse in React. 
- A Higher-order Component or **HOC** is an advanced technique in React for reusing component logic.
- They are a pattern that emerges from React’s compositional nature. 
- These functions are pure, that is they are receiving data and returning values according to that data. If the data changes, higher order functions are re-run with different data input.

## Why should we use HOC :question:

 There will be many situations where many components will need a same functionality. In such cases,we should be able to **Reuse** the same code and not **Duplicate** the same.
  For Example: If 10 different components requires a same functionality, We'd instead be repeating the same code over and over again and not duplicating it ,if it weren't for HOC.

## Structure of HOC:

|It is a component. |It takes another component as an argument. |Then, it returns a new component. |The component it returns can render the original component that was passed to it. |
|---------|---------|----------|----------|

## What it Does :question:

- A Higher Order Component takes a component (WrappedComponent) and returns another component inside of it.
- With this technique, whenever we need to reuse a particular component’s logic for something, we can create a HOC out of that component and use it wherever we like.
- It reduces the work of Duplicating the code and promotes Code Reusability.

<br>
<br>
# High Order Components

##### A Higher-order component is a function that takes a component and returns a new component. It can be created using, 
`const EnhancedComponent = higherOrderComponent(WrappedComponent);`

Consider a case where we are required to make a same functionality for more than 1 components in the program, in such cases we can use HOC. In this example , we can create the same for 2 different components called **Hover** and **Click**
1. This is the code for App.js

```
import React, {Component} from 'react'
import Click from './components/counter'
import Hover from './components/hover'

class App extends Components {
	render() {
		return (
			<div className = "App">
			<Click />
			<Hover />
			</div>
			)
		}
	}
	export default App	
  ```
  
  2. Code for Hover.js
  
  ```
  import React, {Component} from 'react'
import UpdatedComponent from './withHOC'

class Hover extends Component {
	render() {
		const { count, incrementCount } = this.props
		return (
			<h1 onMouseOver = {incrementCount}>
			Hovered { count } times
			</h1>
			) 
		  }
	}
	export default UpdatedComponent (Hover) 
  
```

3. code for Click.js

```
import React, {Component} from 'react'
import UpdatedComponent from './withHOC'

class Click extends Component {
	render() {
		const { count, incrementCount } = this.props
		return (
			<button onClick = {incrementCount}>
			Clicked { count } times
			</button>
			) 
		  }
	}
	export default UpdatedComponent (Click) 
  
```
  
 4. And finally, the main code for withcounter.js  where HOC is implemented

```
import React from 'react'

const UpdatedComponent = originalComponent => {
	class NewComponent extends React.Component {
		constructor(props) {
			super(props)
			
			this.state = {
			count:0
			}
		}
		incrementCount = () => {
		this.setState(prevState => {
		return {count: prevState.count + 1}
		})
	}
	render() {
		return (
		<originalComponent count = { this.state.count }
		incrementCount = { this.incerementCount }
		/>
		)
		}
	}
	}
	return NewComponent
}

export default UpdatedComponent 

```


##### HOC is taking care of maintaining the state and incerementing it.
