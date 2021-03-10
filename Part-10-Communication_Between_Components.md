# ReactJS Components Inner Communication.

<p align="center">
<img src="https://miro.medium.com/max/2000/1*k-06JYgpyNdd9ApmOANTzw.jpeg" width="500px"  ></p>

## There are a total of 3 cases of communication between components:

1. **Case 1: Parent to Child communication**
   - **Using Props:**
   - Props provide one-way communication from a parent to a child. Any changes in the values of an attribute/argument in the prop will directly reflect in the child.
   - **Using the Instance method:**
   - Child instance can be created in Parent by using ref. In the above example we have created a reference for child component and saved in foo.
Using the reference of the child component, we can call any method of child from the parent.



2. **Case 2: Child to Parent communication**
   - Data from a child can be passed to the parent using a callback. This can be achieved by using the following steps.
   - 1. Create a callback method in parent and pass it to the child using props.
   - 2. Child can call this method using “this.props.[yourCallbackName]” form child and pass data as argument.
   
   
   
3. **Case 3: Communication between Sibling / Any components**
   - React support one-way data flow. In order to send data from sibling 1 to sibling 2, you have to send data to parent and then from parent to sibling 2. This approach is a little complicated and difficult to maintain.
   
   
   
   
   
- Reference:https://medium.com/@sumeet.ru/component-communication-in-react-without-redux-5006b7a6009d
<br>
<br>

# Communication Between Other Components
According to [**Wikipedia**](https://en.wikipedia.org/wiki/React_(web_framework))
> _**ReactJS is an open source, front-end, JavaScript-library, not a development framework in JavaScript. It is maintained by facebook and individual developers and companies. It’s mainly used for single-page or mobile application development.**_ 

## Components:

Components are independent and reusable code. Their proposals are same as JavaScript functions but they work separately. In ReactJs they return html function via a render function. 
There are two types of components- Class components and Functional components.

**Functional Components:**

It is a way to write components that only contain render method and just a simple JavaScript function, don’t have own state.
```html
function Welcome(props) {  
  return <h1>Welcome {props.name}</h1>;  
}  
```
This example says that we have called function named  ***Welcome***  and this function has a valid React component, ***props***(properties) that contains object argument data .If we run the code and inside ***{props.name}*** we can put anything, e.g.  Sifa, it will show “Welcome Sifa”. 

**Class Components:**

Class components are more complex than functional components. Because here you will have to create render function. The advantage of this component is more and more, you can pass data from one class to another class, and can manage local state. Class component is also defined by stateful component.
```html
class Welcome extends React.Component {
  render() {
    return (
      <div>Welcome Sifa.</div>  
    );  
  }  
  }
  ```
To know more about [Components and Props](https://reactjs.org/docs/components-and-props.html)

## Strategies for communicating between React components:

We will discuss here about 8 strategies which all connected with each other. 

**1. Props:**

Props are the root of transferring data between components. Without props React is nothing. So we should be gather knowledge about props. As I mentioned it before in functional components.

**2. Instance Methods:**

By using instance method we can communicate child component by parent using ***refs***
 
**3. Callback functions:**

Callback functions work to send data from parent component to child component by props.

**4. Child to Parent:**

To send data from child to parent, we have to use props and this function is called from parent component to child component.
![image](https://www.javascriptstuff.com/static/child-to-parent-a34180d7d83bb61f4f1fab6eecc620a6-8aa1a.png)

**5. Parent to Child:**

This is the easiest communication; we can pass props down to child components.
![image](https://cdn-media-1.freecodecamp.org/images/zdcDnVK0Okw3GBfFb8vzE3Ofi0uKUpD5KRRN)

Here EventEmitter is one of the most popular library in observer pattern.

**6. Observer Pattern:**

Parent to child, child to parent or child to child relationship is required to use this strategy.
This pattern is used for software design in which an object can send messages to multiple other objects.
![image](https://miro.medium.com/max/700/1*7mdN2oN6S_43LC8MPmswzA.png)

**7. Event Bubbling:**

This is the process of that JavaScript looks for the DOM element at which event happened.  It is divided into 3 phases: capturing phase, targeting phase, and bubbling phase.

**8. Context:**

Context send data to an entire subtree as- child of a child, child of a child of a child, so on.

## Communication of Components:

![image](https://cdn-images-1.medium.com/max/1600/1*A8ds6m4es9z3ZRWwbb2NXQ.png)

Mainly communication between components means:
1. Parent → Child: properties, methods
2. Child → Parent: events, callbacks
3. Child → Child: via parent, domain store, UI store, or global event bus.
