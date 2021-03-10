#  Introduction to Functional Components and Class Components

Components are the building blocks of any React app. Components allow us split the UI into independent and reusable pieces.

*A component is combination of*

1.  Template using HTML

2.  User Interactivity using JS

3.  Applying Styles using CSS

A typical React app will have many components like header component, navbar component, footer component and content component. Conceptually a component is a JavaScript class or function that accepts inputs which are properties(props) and returns a React element that describes how a section of the User Interface should appear. A component can be created as Function Component or Class Component.

![Image](https://i.ytimg.com/vi/_sApRiMqLVg/maxresdefault.jpg)

## Functional Components
Functional components are some of the more common components that will come across while working in React. These are simply JavaScript functions. We can create a functional component to React by writing a JavaScript function. These functions may or may not receive data as parameters. In the functional Components, the return value is the JSX code to render to the DOM tree.

**Functional components**  lack a significant amount of features as compared to  **class-based components**. The gap is made up with the help of a special ReactJS concept called  **“hooks”**. Hooks are special functions that allow ReactJS features to be used in  **functional components**.

![Image](https://cms-assets.tutsplus.com/uploads/users/1795/posts/29541/image/Stateful-vs-Stateless-Component-Tutorial-Component-with-state.jpg)


Functional components do not have access to lifecycle functions like class-based components do since lifecycle functions need to be defined within the boundaries of a class. If lifecycle functions need to be used with functional components, a special React hook called useEffect() needs to be used. It is worth noting that **useEffect()** isn’t an exact duplicate of the lifecycle functions – it works and behaves in a slightly different manner.
-   There is no render method used in functional components.
-   These are mainly responsible for UI and are typically presentational only (For example, a Button component).
-   Functional components can accept and use props.
-   Functional components should be favored if you do not need to make use of React state.

## Class Components

**class-based components** are the bread and butter of most modern web apps built in ReactJS. These components are simple classes (made up of multiple functions that add functionality to the application). All **class-based components** are child classes for the Component class of ReactJS.

**Class-based components** have access to the lifecycle functions like **componentWillMount()**, **componentDidMount()**, **componentWillReceiveProps()**, **componentWillUpdate()**, **shouldComponentUpdate()**,**render()** and **componentWillUnmount()**;. These lifecycle functions are called at different stages of the lifecycle and are used for a variety of purposes like changing the state or doing some work (like fetching data from an external API). They are also referred to as **lifecycle hooks**.

![Image](https://cms-assets.tutsplus.com/uploads/users/1795/posts/29541/image/Stateful-vs-Stateless-Component-Tutorial-Class-Component.jpg)


-   Class components make use of ES6 class and extend the  `Component`  class in React.
-   Sometimes called “smart” or “stateful” components as they tend to implement logic and state.
-   React lifecycle methods can be used inside class components (for example,  `componentDidMount`).
-   You pass props down to class components and access them with  `this.props`

<br>
<br>
### 1. Functional Components
### 2. Class Components

## Functional Components 

Functional Component is just like a simple javascript function which accepts an argument as props and return React element.

```
function Example(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

Earlier Functional Components was also called as stateless components as there was no way to set state of the component in functional component. But, this changed with the React 16.8 Hooks update. We can now use state and other React features without writing a class. 

**NOTE: We'll see an example of a counter (where we'll need to use state) with both class and functional component in the code section. So, do check out the code section for better understanding.**

### Pros of using Functional Components

1. Easy to read.

2. You can do things with less code.


## Class Components

Class component is just like javascript classes containing multiple functions to add different functionality to the application. You need to extend class component from React.Component and you must include a render function in class components which return the JSX which needs to be rendered on the web page. There is a constructor function in class component which accepts **props** as argument. State of the component is also set in this constructor function as shown below in the code.

```
class Example extends React.Component {
   
  constructor(props){
     super(props);
     this.state = {
       message : "Welcome"
       }
  }

  render() {
     return
     ( 
        <div>
           <h2> Hello World!! </h2>;
           <h1> {this.state.message} </h1>;
        </div>   
     );     
  }
}
```

## Differences in Class Component and Functional Component
<table>
  <td> <h1> Functional Components </h1 >    </td>
  <td> <h1> Class Components </h1 >     </td>
  <tr> 
    <td>It is just a plain JavaScript function as it accepts props as an argument and returns a React element. </td>
    <td> It requires you to extend from React.Component. You must create a render function which return the JSX which needs to be rendered on the web page. .</td>
  </tr>
  <tr> 
    <td> It doesn't contain any render method.</td>
    <td> It must contain the render() method.</td>
  </tr>
  <tr> 
    <td> You can use state in functional component with React Hooks (example :- useState, useEffect etc.). </td>
    <td>State is defined in the constructor method in class component. </td>
  </tr>
  <tr>
    <td> You cannot use React lifecycle methods in functional components.</td>
    <td> You can use React lifecycle methods in functional components.</td>
  </tr>
</table>
