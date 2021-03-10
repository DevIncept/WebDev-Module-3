# Introduction to ES6 and ES7 Syntax
ES6 is Modern JavaScript. Its abbreviation form is ECMAScript 6 and it was released in 2015 with its full features, but in that time none of browsers could not implement ES6’s all stuffs. That time people used transpilers, it is one kind of library or application, that converts ES6 code to ES5, then the code of ES5 is executed by browsers. For this reason ES6’s adaptability was not improved. But after day-by-day, all browsers implemented it, and then it has become popular. 

## What is ES6:

ES6 is 6th version of ECMAScript and was published in 2015.
 ECMAScript is a general-purpose programming language. It is a JavaScript standard meant to ensure the interoperability of Web pages across different Web browsers. ECMAScript is commonly used for client-side scripting on the World Wide Web.
[Check here](https://en.wikipedia.org/wiki/ECMAScript) to know more about ECMAScript.

**Features of ES6:**
1. Classes
2. constructor() method
3. Arrow functions
4. Variables-let,const,var
5. Promises

For details [click here](https://www.w3schools.com/react/react_es6.asp ).

**Browsers Support:**

1. Chrome............58.......Jan 2017
2. Edge..............14.......Aug 2016 
3. Firefox...........54.......Mar 2017
4. Safari............10.......Jul 2016
5. Opera.............55.......Aug 2018

## What is ES7:
ES7 stands for ECMAScript 7, also named ECMAScript 2016 that was released in 2016. This version gives suitable alternatives to already used functionalities.

**Features of ES7:**

New features of ES7
1.	Exponentiation Operator (**)
2.	Includes
3.	Exponentiation assignment (**=)

**Browsers Support:**

1. Chrome........52......jul 2016
2. Edge..........14.......Aug 2016
3. Firefox.......52......Mar 2017
4. Safari........10.1.....Mar 2017
5. Opera.........39......Aug 2016

  ## Why we should use ES6:
1.	ES6 brings new syntax and new features to make our code modern and readable.
2.	 Write less code and do more.
3.	It introduces us to many great features such as arrow-functions, classes and modules etc.

Also ES6 is modern JavaScript and ES7 has less change than ES6, so users will feel better to use ES6.


<br>
<br>
## How ES6 work with ReactJS:
As we know feaures of ES6 like- Classes, constructor() method, Arrow functions, Variables-let,const,var. And now we will discuss their uses in ReactJS.

**Classes:**

```html
class Sifa {
constructor(y) {
    this.x = y;
  }
}

```
Here we use the key word class and assigned properties in constructor() method.
Now create object using Sifa class

```html
class Sifa {
  constructor(y) {
    this.x = y;
  }
}
Siddiquea = new Sifa("Sefat Siddiquea");
```
Create an object called "Siddiquea" based on the Sifa class. 

The output will be:
```html
Sefat Siddiquea
```
[Check here]( https://www.w3schools.com/react/tryit.asp?filename=tryreact_es6_class) for code, you can change the code as I have written here. 

**Arrow functions:**

```html
hi = () => {
  return "Hi Sifa!!";
}	
```
Here () => this also be written as function()
```html
hi = function() {
  return "Hi Sifa!!";}	
  ```
  We can remove the bracket , can write as
  ```html
hi = () => return "Hi Sifa!!";
```
For these three functions the output will be "Hi Sifa!!" as we know.
```html
Hi Sifa!!
```
**Arrow Function with Parameters:**
```html
hi = (val) => "Hi " + val;
```
Here parameter is the “val” and we can give the parameter variable anything like-x,s,d,fgdf….

[Click for](https://www.w3schools.com/react/react_es6.asp) details. 

## How ES7 work with ReactJS:
We will discuss about ES7’s new features

**Exponentiation Operator(**):**

It’s symbol like **. Exponentiation operator means arithmetic operator (+,-,*, etc.)

Input will be:

```html
console.log(4**2); //4 to the power 2
```
Output will be:

```html
16
```
**Includes:**
Input will be:
```html
var x=[‘a’,’b’,’c’];
console.log(x.includes(‘b’));
```
And output will be:
```html
True
```
Because the elements b, that includes in array x is true.


**Exponentiation Operator(**=):**
```html
 let x = 9;
    x **= 2; // result 81
 ```
This operator (**=) raises the value of a variable to the power of the right operand.
[Check out here](https://github.com/vendethiel/es7-features) about ES7’s features details. 
