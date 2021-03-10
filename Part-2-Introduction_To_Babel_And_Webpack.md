# Introduction to WebPack and Babel

# what is a webPack :
webpack is an open-source JavaScript module bundler.` It is a build tool that puts all of our assets like Javascript, images, fonts, and CSS, in a dependency graph. ` It is used to  build and manage our files.
It is made primarily for JavaScript, but it can transform front-end assets such as HTML, CSS, and images too.

## Why should we use it:question:
If we're using many files in our project, **the importing order of the files  is important**. If we switch it,it will cause error and it gets hard to manage them all by ourselves.so if we use a
web pack in this case, it maintains and manages our files for us. It also optimizes and minifies the files.
 
## What it actually Does:question:
webpacks do a lot of work for us.It helps us with some important problems
* When we have got multiple files for our project ( Eg: 3/4 JavaScript files),  we have to bundle them all together. It can be done with minimal efforts from our side using WebPacks.
* Instead of manually managing the order which is error prone , we have a tool that does for us. 
* It takes all the script files and intelligently combines into a bundle and we only have to reference it.
* WebPacks bundle all of our files together and even transform them so that we can write our js code using es6,which isn't supported by all browsers.
but it can be compiled and run in those browsers using this.

## Benefits of using a WebPack:
:point_right: If We're building a complex Front End application with many static assets such as CSS, images, fonts, etc, then Webpack will give us great benefits.

:point_right: A WebPack analyzes connections,bundles and optimizes all our files.

:point_right: It helps us set up a development work flow.

## How Does it work:question:

| It has entry points like app.js . And starts from there|  Makes global transformations before adding it to bundle using loaders like babel.| Adds plugins | we get output (correctly ordered,concatenated output).|
|---------|---------|----------|----------|


# What is Babel:
JavaScript is moving so fast that the browsers are behind and are not able to adapt to all the changes it brings. ` It takes modern Js and compiles it down to a form that could be understood in different environments. `
It is very powerful tool that is built on plugin system.

## What it actually Does:question:
:point_right: It is a tool that allows us to write super advanced Js, that are not yet available to be used inside browsers and babel will take care of it.

:point_right: it will compile the advanced Js features into which our browsers can understand.

## How Does it work:question:

| It parses our modern Js into an Abstract syntax tree or an **AST** | It Rewrites it in a version that can be interpreted by the browser. | It transforms the modern Js. | We can use a new feature of Js before every browser supports it |
|---------|---------|----------|----------|




#  Intro to WebPack and Babel
Webpack lets us use **require()** in our source code to point to local files, like images, and decide how they're processed in your final Javascript bundle,
like replacing the path with a URL pointing to a CDN.

### Simple way to use WebPacks
1. using ` npm ` (node js)
2. open terminal
3. navigate to the folder.
4. ` npm init ` (initialize the project )
it opens a Package.json file for us and it manages all our files in that project
5. ` npm install webpack --save-dev ` (says we don't need it for production)
6. go to package.json and add script ` "build" :"webpack src/js/app.js dist/bundle.js" ` 
(targets the webpack package we downloaded)
7. now adjust the app.js: (give webpack a clue on what it depends on)
add ` import {variables} './dom-loader' ; ` in the top.
8. ` export  dom-loader.js ` in the Js file 
9. ` npm run build `
(WebPack has created a bundle for us)
10. In Index.html we can add our ` <script src = "dist/bundle.js> </script> `

##### It will work properly and we only have 1 import now. WebPack adds them in bundle and manages it for us.


## How to use Babel:

1. Using the CDN
2. we can run Babel by just running
``` 
npx babel script.js 
```
3. Or by configuring it like:
``` 
npm install --save-dev \ @babel/plugin-transform-arrow-functions
```
then to download the package in the node_modules folder:
``` {
  "plugins": ["@babel/plugin-transform-arrow-functions"]
}
```


## Babel Example: 

### what we write  ( Modern JavaScript code):
```
var a = () => {};
var a = (b) => b;

const double = [1,2,3].map((num) => num * 2);
console.log(double); // [2,4,6]

var bob = {
  _name: "Bob",
  _friends: ["Sally", "Tom"],
  printFriends() {
    this._friends.forEach(f =>
      console.log(this._name + " knows " + f));
  }
};
console.log(bob.printFriends());
```
### what is interpreted:

```
var a = function () {};var a = function (b) {
  return b;
};

const double = [1, 2, 3].map(function (num) {
  return num * 2;
});console.log(double); // [2,4,6]

var bob = {
  _name: "Bob",
  _friends: ["Sally", "Tom"],
  printFriends() {
    var _this = this;

    this._friends.forEach(function (f) {
      return console.log(_this._name + " knows " + f);
    });
  }
};
console.log(bob.printFriends());
```
