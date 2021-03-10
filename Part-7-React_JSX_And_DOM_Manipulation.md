# Introduction to JSX :computer:

JSX stands for Javascript XML. It is a syntax extension to Javascript. It allows us to write HTML element in React in a very easy and efficient way to describe what the UI should look like.

## Using JSX

JSX looks like a regular HTML in most cases.

```
import React from 'react';

class Example extends React.Component {
   render() {
      return (
         <div>
           <h2> Hey there !! </h2>
           <p> Welcome to our website </p>
           <button> Know More!! </button>
         </div>
      );
   }
}
export default Example;

```

JSX is just like HTML, a template language but it has full power of Javascript. For Example: In HTML we cannot bind event to any element directly, i.e. , we'll have to select any element in Javascript and then add event listener to that element. 

####  To add event listener to a button element in HTML :

``` 
document.getElementsByTagName("button").addEventListener("click",() => {
   console.log("HIII");
  })
```

But, in JSX events can be directly attached to elements.

####  To add event listener to a button element in JSX :

```

 <button onClick={ () => { console.log("HIII} }> Click </button>
 
```

## Why to use JSX in React? :information_desk_person:

  JSX makes it easy to write HTML elements in React and place them in the DOM without using createElement(). 


#### Consider the example given below:

This is a simple example in which I've just created a div element which contains a h1 element.

### Code 1 - With JSX :thumbsup:
  
  ```
  
  import React from "react"

      class Example extends React.Component{

         render(){
            return (
               <div className="box">
                <h1 className="heading">Hello World!!</h1>
               </div>
            );
         }
         
} 

export default Example;

```

The above code can be achieved without using JSX. 

### Code 2 - Without JSX :thumbsdown:

```

import React from "react"

class Example extends React.Component{
   
 render(){
  return (
   React.createElement('div', { className : "box"}, React.createElement('h1', { className : "heading"}, "Hello World!!")) 
  )
 }

} 

export default Example;

```
##### Code 1 and Code 2 will give the same result.

You can clearly see how difficult it is to create even a simple h1 element without JSX ( i.e., using createElement() ). That's why JSX is used to create elements in React.

## Some more Advantages of JSX : :snowflake:

Apart from making the syntax easier, following are some more pros of using JSX :

1. JSX is fast as it performs optimization while compiling code to JavaScript.
2. JSX is also type-safe and most of the errors can be caught during compilation.
 
## Naming Convention in JSX :book:

Since JSX is closer to JavaScript than to HTML, React uses camelCase property naming convention.

For example, class becomes className in JSX, and tabindex becomes tabIndex.

## Rules of using JSX :pencil:  

##### 1. If we need to return more than one element from render() function then we must wrap it in one parent container. 

 Example : In the example given :point_down: h1 and p is wrapped in one div container.

```
import React from 'react';

class App extends React.Component {
   render() {
      return (
         <div>
            <h1>Welcome!! </h1>
            <p>How are you!!!</p>
         </div>
      );
   }
}
export default App;

```

##### 2. We can use Javascript expressions inside JSX. We just have to wrap it with curly brackets {}.

 Example : In the example given :point_down: count is an javascript expression and so to use it in JSX we must wrap it in {}.


```
import React from 'react';

class App extends React.Component {
   render() {
       let count = "HELLO WORLD";
      return (
         <div>
            <h1> {count}</h1>
         </div>
      );
   }
}
export default App;

```

##### 3. We can use inline style with JSX in React. To use inline style in JSX we need to create an object containing all the styles that has to be applied on an element and then we can embed that to the element in curly brackets just like a javascript expression.

 Example : In the example given :point_down: inlineStyle is an object containing all the styles.


```
import React from 'react';

class App extends React.Component {
   render() {
      let inlineStyle = {
         color : "#db3b61",
         fontSize : "25 px"
      }
      return (
         <div>
            <h2 style = {inlineStyle}> Welcome  </h2>
         </div>
      );
   }
}
export default App;
```

##### 4. In JSX, comments has to be wrapped within curly brackets {}.

 Example : In the example given :point_down: both single and multi line comments has been shown.

```
import React from 'react';

class App extends React.Component {
   render() {
      return (
         <div>
            <h1>Introduction to Web Development</h1>
            <p> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.  </p>
            
            {// Single Line Comment...}
            {/*Multi Line Comment...*/}
         </div>
      );
   }
}
export default App;
```
<br>
<br>

# How React actually performs the DOM Manipulation :pencil:

DOM stands for Document Object Model. DOM is a tree structured, in-memory representation of HTML. DOM Manipulation is a method by which the content of a web page is dynamically altered.

Javascript is usually used for performing DOM manipulation by using methods like getElementByTagName or getElementById, but there is a problem in using Javascript for manipulating DOM.

## Why React is preferred for DOM Manipulation over other Javascript frameworks?

DOM Manipulation is the most essential thing for making a web page dynamic and more interactive. So, it is very important that the process of DOM manipulation must be quick so that the web page is user friendly. But in Javascript the process of DOM Manipualtion is very slow and hence, it also make the loading of web page slow. 

**For Example :** We have a to-do list app and we want to update the first item of the list. In this we do not need to update the entire list but most of the javascript frameworks will update the entire list just to update the first item. This results in making the loading of the web page slow. 

**To solve this problem, React uses something called the Virtual DOM.**


## What is Virtual DOM ? :beginner:

Virtual DOM is just a copy of real HTML DOM. The manipulation of virtual DOM is much more faster than the real DOM. So, the changes that needs to be done in real DOM, React does it to the virtual DOM and then update the real DOM according to that. This process is known as  **Reconciliation**. 

Before updating the real DOM, React creates a copy of Virtual DOM and compare it with the updated Virtual DOM. Then React figures out which elements have been changed. Once React knows which elements is changed, it updates only those elements in the Real DOM. 

## Rules followed by React in updating DOM

React follows **Diffing Algorithm**  for DOM Manipulation. Diffing Algorithm means comparing two trees before updating. Hence, React compares the copy of Virtual DOM before updating with the Virtual DOM after updating, and then make the necessary changes to the DOM. React uses diffing algorithm with somes rules for manipulating the DOM. These rules are given below with the necessary codes for explaination:

#### 1. If the root element is different, then React will update the entire tree.
  Example :  In the below codes, the root element is different **div** and **span** so React will update the entire tree.
  
 ```
   <span> 
   <h1> Hello </h2>
   </span>
 ```
     

``` 
  <div>
   <h1> Hello </h1>
  </div>
 ```

#### 2. It the elements are same, then React will compare the attributes of both the elements and change only the attribute if necessary.
 Example :  In the below codes, elements are same so React only alters the attributes.
  
 ```
   <div id="div1" />
 ```
     

``` 
  <div id="div2" />
```


## How React compares Child Elements?

Let us consider two lists.

**List 1**

```
<ul>
   <li> Item 1 </li>
   <li> Item 2 </li>
</ul>
```

**List 2**

```
<ul>
   <li> Item 1 </li>
   <li> Item 2 </li>
   <li> Item 3 </li>
</ul>
```
  
In list 2, a new item has been added to the end of the list. React iterates over the list and compares each chid and creates a new **li** element where there is a difference. A problem arises when a new item is added to the start of the list.

**List 1**

```
<ul>
   <li> Item 1 </li>
   <li> Item 2 </li>
</ul>
```

**List 2**

```
<ul>
   <li> Item 3 </li>
   <li> Item 1 </li>
   <li> Item 2 </li>
</ul>
```
 
In this, React compares the first elements and finds that there is a difference ans so creates a new element. The same happens to the next elements as well. So, in this case React is updating the entire list unknowingly. This makes the process of loading web page very slow.

**To overcome this problem, React supports an attribute, Key.**

### Comparison using Key Attributes :thumbsup:

If the attribute key is added to the list element, React compares the values in key of the first tree, and matches it to the key value in the second tree.

Example :

**List 1**

```
<ul>
   <li key="0"> Item 1 </li>
   <li key="1"> Item 2 </li>
</ul>
```

**List 2**

```
<ul>
   <li key="2"> Item 3 </li>
   <li key="0"> Item 1 </li>
   <li key="1"> Item 2 </li>
</ul>
```

Now, using key attribute's value React will know that a new child element with key="2" has been added to the list. Hence, it’ll not update the entire list again. This will improve the speed of DOM Manipulation.

Hence, React makes the process of DOM Manipulation quick and makes the web page more user friendly.
