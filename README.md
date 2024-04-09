<a id="readme-top"></a>

<div align="center">
    <img src="pictures/js_logo.png" alt="Logo" width="80" height="70">
  <h3 align="center">JavaScript learning</h3>

  <p align="center">
    Review knowledge of JavaScript!
    <br />
    <a href="https://www.w3schools.com/js/default.asp"><strong>Explore the docs »</strong></a>
    
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#variables">Variables</a>
      <ul>
        <li><a href="#var">var</a></li>
        <li><a href="#let">let</a></li>
        <li><a href="#const">const</a></li>
      </ul>
    </li>
    <li>
      <a href="#data-types">Data Types</a>
      <ul>
        <li><a href="#primitive-data-types">Primitive Data Types</a></li>
        <li><a href="#non-primitive-data-types">Non-Primitive Data Types</a></li>
      </ul>
    </li>
    <li><a href="#functions">Functions</a>
        <ul>
        <li><a href="#function-declaration">Function Declaration</a></li>
        <li><a href="#function-expression">Function Expression</a></li>
        <li><a href="#arrow-functions">Arrow Functions</a></li>
      </ul>
    </li>
    <li><a href="#dom-manipulation">DOM Manipulation</a></li>
    <li><a href="#events">Events</a></li>
    <li><a href="#arrays-and-array-methods">Arrays and Array Methods</a></li>
    <li><a href="#es6-features">ES6+ Features</a></li>
    <li><a href="#asynchronous-javascript">Asynchronous JavaScript</a></li>
    <li><a href="#modules">Modules</a></li>
    <li><a href="#json">JSON</a></li>
  </ol>
</details>


# Variables
## var:
* var was the original way to declare variables in JavaScript and is still widely used.
* Variables declared with var are function-scoped or globally scoped, meaning they are accessible throughout the entire function or globally if declared outside any function.
* var variables are hoisted to the top of their function or global scope, but their initialization remains in place.
* They can be re-declared and updated within their scope.
* They can be declared without being initialized, in which case they have the value undefined.
* Example:
```js
var x = 5;
function example() {
    console.log(x); // undefined
    var x = 10;
    console.log(x); // 10
}
example();
console.log(x); // 5
```
## let
* let was introduced in ES6 (ECMAScript 2015) to address some of the issues associated with var.
* Variables declared with let are block-scoped, meaning they are only accessible within the block they are declared in, such as if statements, loops, or function blocks.
* let variables are not hoisted until their declaration, resulting in a "temporal dead zone" if accessed before declaration.
* They can be re-assigned within their scope but cannot be re-declared in the same scope.
* They can be declared without being initialized, in which case they have the value undefined.
* Example:
```js
let x = 5;
if (true) {
    console.log(x); // ReferenceError: Cannot access 'x' before initialization
    let x = 10;
    console.log(x); // 10
}
console.log(x); // 5
```
## const:
* const also introduced in ES6, is used to declare constants, whose value cannot be re-assigned.
* Variables declared with const are block-scoped.
* const variables must be initialized at the time of declaration and cannot be left uninitialized.
* They are not hoisted until their declaration and also reside in the "temporal dead zone" if accessed before declaration.
* The value of a const variable cannot be changed once it's assigned, but for objects and arrays, the properties or elements can be mutated.
* Example:
```js
const x = 5;
if (true) {
    console.log(x); 
    // ReferenceError: Cannot access 'x' before initialization
    const x = 10;
    console.log(x); // 10
}
console.log(x); // 5
```

In summary, while var, let, and const are all used for variable declaration in JavaScript, let and const provide more predictable behavior and better scoping rules compared to var. const is preferred when you want to declare variables that should not be re-assigned, while let is used when you need to re-assign variables. Understanding the differences between them is crucial for writing clean and maintainable JavaScript code.

# Data Types

## Primitive Data Types:
Primitive data types are immutable data types that hold a single value and do not have methods. They are directly assigned to memory and accessed by their value. JavaScript has six primitive data types:

### String:

* Represents textual data.
* Enclosed in single quotes ('') or double quotes ("").
* Example: "Hello, world!".
### Number:

* Represents numeric data.
* Includes integers, floating-point numbers, and special numeric values like Infinity and NaN (Not-a-Number).
* Example: 42, 3.14, Infinity.
### Boolean:

* Represents a logical value indicating true or false.
* Example: true, false.
### Undefined:

* Represents a variable that has been declared but not assigned a value.
* It is also a primitive data type, but unlike the others, it is often considered a type with only one value (undefined).
* Example: let x; console.log(x); // Output: undefined.
### Null:

* Represents the intentional absence of any object value.
* It is often used to indicate a deliberate non-value or a null value.
* Example: let y = null;.
### Symbol:

* Represents a unique and immutable value used to identify object properties.
* Symbols are guaranteed to be unique, which makes them useful for defining object properties where you want to ensure no name clashes occur.
* Example: const symbol = Symbol('description');.
## Non-Primitive Data Types:
Non-primitive data types are mutable data types that are used to store collections of data and more complex entities. They are not directly accessed, but rather accessed by reference. JavaScript has two non-primitive data types:

### Object:

* Represents a collection of key-value pairs (properties).
* Objects are reference types, meaning they are stored and accessed by reference rather than by value.
* Example: { name: 'John', age: 30 }.
### Array:

* Represents a list-like collection of elements.
* Arrays are special kinds of objects with numerically indexed elements.
* They are often used to store multiple values in a single variable.
* Example: [1, 2, 3, 4, 5].
<p>In summary, primitive data types in JavaScript include String, Number, Boolean, Undefined, Null, and Symbol, while Object and Array are non-primitive data types. Understanding the distinction between primitive and non-primitive data types is essential for effectively working with data in JavaScript.</p>

# Functions
## Function Declaration:
```js
function greet(name) {
    return "Hello, " + name + "!";
}
```

* Function declarations start with the function keyword, followed by the name of the function.
* They can take parameters (in this case, name).
* The body of the function is enclosed in curly braces {}.
* They are hoisted, meaning you can call them before they are defined in the code.

## Function Expression:

```js
var greet = function(name) {
    return "Hello, " + name + "!";
};
```

* Function expressions define a function as part of a larger expression, typically by assigning it to a variable.
* They are not hoisted, so you cannot call them before the expression is defined.

## Arrow Functions:

```js
const greet = (name) => {
    return "Hello, " + name + "!";
};
```

* Arrow functions provide a more concise syntax for defining functions.
* They use the => syntax (sometimes called the "fat arrow").
* If the function body consists of only one expression, you can omit the curly braces {} and the return keyword, and the result of the expression will be automatically returned.
* They do not have their own this keyword; instead, they inherit the this value from the surrounding code.
<p>Here's a breakdown of the differences between these function types:</p>

* <b>Hoisting:</b> Function declarations are hoisted, while function expressions are not. This means you can call function declarations before they are defined in the code. 
* <b>Syntax:</b> Function declarations and expressions have slightly different syntax, with function expressions typically assigned to a variable. 
* <b>Arrow Functions:</b> Arrow functions provide a concise syntax for defining functions, especially for simple, one-line functions. They also have lexical scoping for the this keyword, which can be advantageous in certain situations.

# DOM Manipulation
DOM Manipulation refers to the process of accessing, modifying, or updating elements within the Document Object Model (DOM) of a web page using JavaScript. The DOM is a programming interface for web documents and represents the structure of an HTML document as a tree of nodes, where each node corresponds to an element, attribute, or piece of text in the document.

Here are the main aspects of DOM manipulation:

### Accessing Elements:
JavaScript allows you to access elements within the DOM using various methods such as `document.getElementById()`, `document.getElementsByClassName()`, `document.querySelector()`, and `document.querySelectorAll()`.

Example:

```js
// Get an element by its ID
const element = document.getElementById('myElement');

// Get elements by class name
const elements = document.getElementsByClassName('myClass');

// Get the first element that matches a CSS selector
const element = document.querySelector('.mySelector');

// Get all elements that match a CSS selector
const elements = document.querySelectorAll('.mySelector');
```

### Modifying Elements:
Once you've accessed an element, you can modify its attributes, properties, or content using JavaScript.

Example:
```js
// Modify element content
element.innerHTML = 'New content';

// Modify element attributes
element.setAttribute('id', 'newId');

// Modify element styles
element.style.color = 'red';
```

### Creating and Appending Elements:
You can create new elements dynamically with JavaScript and append them to the DOM.

Example:

```js
// Create a new element
const newElement = document.createElement('div');
newElement.textContent = 'New Element';

// Append the new element to an existing element
parentElement.appendChild(newElement);
```

### Removing Elements:
You can remove elements from the DOM using methods like removeChild().

Example:

```js 
// Remove an element
parentElement.removeChild(childElement);
```
### Event Handling:
You can add event listeners to elements to handle user interactions such as clicks, mouse movements, key presses, etc.

Example:

```js
// Add an event listener
element.addEventListener('click', function() {
    // Handle click event
});
```
DOM manipulation is a fundamental aspect of client-side web development, and mastering it allows you to create dynamic and interactive web applications. However, it's important to use DOM manipulation judiciously to ensure good performance and maintainability of your code.

# Events
Events in web development refer to actions or occurrences that happen in the browser. These can be triggered by the user, the browser, or by other elements in the webpage. JavaScript provides a way to listen for these events and execute code in response. Here's an overview of events in web development:

### Types of Events:
Events in JavaScript can be categorized into various types based on their source or trigger. Some common types include:

* Mouse Events: Actions performed with the mouse, such as clicks, hovering, dragging, etc. (e.g., `click`, `mouseover`, `mouseout`).
* Keyboard Events: Actions performed with the keyboard, such as key presses, key releases, etc. (e.g., `keydown`, `keyup`).
* Form Events: Events related to form elements, such as submitting a form, changing input values, etc. (e.g., `submit`, `change`).
* Document and Window Events: Events related to the document or window, such as loading, resizing, scrolling, etc. (e.g., `load`, `resize`, `scroll`).
* Focus Events: Events related to focus changes on elements, such as focusing on an input field, blurring out, etc. (e.g., `focus`, `blur`).
* Custom Events: Events that you can create and dispatch manually in your code.
### Event Handlers:
Event handlers are functions that are executed when a particular event occurs. In JavaScript, you can attach event handlers to DOM elements using the `addEventListener()` method or by assigning event handler properties directly.

Example using `addEventListener()`:

```js
const button = document.getElementById('myButton');
button.addEventListener('click', function() {
    console.log('Button clicked!');
});
```
Example using event handler properties:

```js
const button = document.getElementById('myButton');
button.onclick = function() {
    console.log('Button clicked!');
};
```
### Event Object:
When an event occurs, JavaScript creates an event object containing information about the event. This object is passed as an argument to the event handler function and contains properties and methods that provide details about the event, such as the target element, event type, mouse coordinates, etc.

Example:
```js
const button = document.getElementById('myButton');
button.addEventListener('click', function(event) {
    console.log('Button clicked!');
    console.log('Target element:', event.target);
    console.log('Mouse coordinates:', event.clientX, event.clientY);
});
```
### Event Propagation:
Events in the DOM propagate or bubble up from the target element to its ancestors. This means that if an event occurs on a child element, it will also trigger event handlers on its parent elements, unless propagation is stopped using the stopPropagation() method.

Example:
```js
document.getElementById('parent').addEventListener('click', function() {
    console.log('Parent clicked!');
});

document.getElementById('child').addEventListener('click', function(event) {
    console.log('Child clicked!');
    event.stopPropagation(); // Stop event propagation
});
```
Understanding events and how to handle them is crucial for creating interactive and dynamic web applications. Event-driven programming is a core concept in web development, and mastering events allows you to build responsive and engaging user interfaces.

# Arrays and Array Methods
Arrays are a fundamental data structure in JavaScript used to store multiple values in a single variable. They are ordered collections of elements, where each element has an index. JavaScript provides a variety of built-in methods for working with arrays, allowing you to manipulate, iterate over, and perform operations on array elements. Here's an overview of arrays and some common array methods:

### Creating Arrays:
You can create an array in JavaScript using array literal notation (`[]`) or the `Array` constructor.

Example:
```js
const fruits = ['apple', 'banana', 'orange'];
const numbers = new Array(1, 2, 3, 4, 5);
```
### Accessing Elements:
You can access elements in an array using square bracket notation (`[]`) with the index of the element.

Example:
```js
console.log(fruits[0]); // Output: 'apple'
```
### Array Methods:
JavaScript provides several built-in methods for manipulating arrays. Here are some common ones:

* `push()`: Adds one or more elements to the end of an array and returns the new length of the array.
* `pop()`: Removes the last element from an array and returns that element.
* `shift()`: Removes the first element from an array and returns that element.
* `unshift()`: Adds one or more elements to the beginning of an array and returns the new length of the array.
* `concat()`: Combines two or more arrays and returns a new array.
* `slice()`: Returns a shallow copy of a portion of an array into a new array object.
* `splice()`: Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.
* `indexOf()`: Returns the first index at which a given element can be found in the array, or -1 if it is not present.
* `includes()`: Determines whether an array includes a certain element, returning true or false as appropriate.
* `forEach()`: Executes a provided function once for each array element.
* `map()`: Creates a new array with the results of calling a provided function on every element in the calling array.
* `filter()`: Creates a new array with all elements that pass the test implemented by the provided function.
* `reduce()`: Executes a reducer function on each element of the array, resulting in a single output value.
* `sort()`: Sorts the elements of an array in place and returns the sorted array.
* `reverse()`: Reverses the elements of an array in place.
* `join()`: Joins all elements of an array into a string.
* `toString()`: Returns a string representing the specified array and its elements.
### Iterating Over Arrays:
You can iterate over arrays using loops such as `for`, `for...of`, or array methods like `forEach()`, `map()`, `filter()`, etc.

Example using `forEach()`:
```js
fruits.forEach(function(fruit) {
    console.log(fruit);
});
```
Arrays and array methods are essential tools for working with collections of data in JavaScript, and understanding how to use them effectively is key to writing clean and efficient code.

# ES6+ Features
ES6, also known as ECMAScript 2015, introduced many new features and improvements to the JavaScript language. Since then, subsequent versions of ECMAScript have brought even more enhancements. Here's an overview of some ES6+ features that have become widely adopted and are commonly used in modern JavaScript development:

## Arrow Functions:
Arrow functions provide a concise syntax for writing anonymous functions, with implicit returns and lexical this binding.

Example:

```js
// ES5
function add(x, y) {
    return x + y;
}

// ES6
const add = (x, y) => x + y;
```
## let and const:
let and const provide block-scoped variable declarations, replacing var. let allows re-assignment, while const creates variables with immutable values.

Example:

```js
let count = 10;
count = 20; // Valid

const PI = 3.14;
PI = 3.14159; // Invalid
```

## The Spread (...) Operator
The ... operator expands an iterable (like an array) into more elements:

Example

```js
const q1 = ["Jan", "Feb", "Mar"];
const q2 = ["Apr", "May", "Jun"];
const q3 = ["Jul", "Aug", "Sep"];
const q4 = ["Oct", "Nov", "May"];

const year = [...q1, ...q2, ...q3, ...q4];
```
The ... operator can be used to expand an iterable into more arguments for function calls:

Example
```js
const numbers = [23,55,21,87,56];
let maxValue = Math.max(...numbers);
```
## The For/Of Loop
The JavaScript `for/of` statement loops through the values of an iterable objects.

`for/of` lets you loop over data structures that are iterable such as Arrays, Strings, Maps, NodeLists, and more.

The `for/of` loop has the following syntax:
```js
for (variable of iterable) {
  // code block to be executed
}
```
* _variable_ - For every iteration the value of the next property is assigned to the variable. Variable can be declared with `const`, `let`, or `var`.

* _iterable_ - An object that has iterable properties.

### Looping over an Array
Example
```js
const cars = ["BMW", "Volvo", "Mini"];
let text = "";

for (let x of cars) {
  text += x + " ";
}
```
### Looping over a String
Example
```js
let language = "JavaScript";
let text = "";

for (let x of language) {
    text += x + " ";
}
```

## JavaScript Maps
Being able to use an Object as a key is an important Map feature.

Example
```js
const fruits = new Map([
["apples", 500],
["bananas", 300],
["oranges", 200]
]);
```

## JavaScript Sets
Example
```js
// Create a Set
const letters = new Set();

// Add some values to the Set
letters.add("a");
letters.add("b");
letters.add("c");
```

## JavaScript Classes
JavaScript Classes are templates for JavaScript Objects.

Use the keyword `class` to create a class.

Always add a method named `constructor()`:

Syntax
```js
class ClassName {
  constructor() { ... }
}
```
Example
```js
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}
//The example above creates a class named "Car".
//The class has two initial properties: "name" and "year".
```

* A JavaScript class is **not** an object.

* It is a **template** for JavaScript objects.

## Using a Class
When you have a class, you can use the class to create objects:

Example
```js
const myCar1 = new Car("Ford", 2014);
const myCar2 = new Car("Audi", 2019);
```

## JavaScript Promises
A Promise is a JavaScript object that links "Producing Code" and "Consuming Code".

"Producing Code" can take some time and "Consuming Code" must wait for the result.

Promise Syntax
```js
const myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise).
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
```
Example Using a Promise
```js
const myPromise = new Promise(function(myResolve, myReject) {
  setTimeout(function() { myResolve("I love You !!"); }, 3000);
});

myPromise.then(function(value) {
  document.getElementById("demo").innerHTML = value;
});

```

## The Symbol Type
A JavaScript Symbol is a primitive data type just like Number, String, or Boolean.

It represents a unique "hidden" identifier that no other code can accidentally access.

For instance, if different coders want to add a person.id property to a person object belonging to a third-party code, they could mix each others values.

Using Symbol() to create a unique identifiers, solves this problem:

Example
```js
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

let id = Symbol('id');
person[id] = 140353;
// Now person[id] = 140353
// but person.id is still undefined
```
```
Note
Symbols are always unique.

If you create two symbols with the same description they will have different values:

Symbol("id") == Symbol("id"); // false
```

## Default Parameter Values
ES6 allows function parameters to have default values.

Example
```js
function myFunction(x, y = 10) {
  // y is 10 if not passed or undefined
  return x + y;
}
myFunction(5); // will return 15
```
## Function Rest Parameter
The rest parameter (...) allows a function to treat an indefinite number of arguments as an array:

Example
```js
function sum(...args) {
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
}

let x = sum(4, 9, 16, 25, 29, 100, 66, 77);
```
## String methods
### String.includes()
The `includes()` method returns `true` if a string contains a specified value, otherwise `false`:

Example
```js
let text = "Hello world, welcome to the universe.";
text.includes("world")    // Returns true
```
### String.startsWith()
The `startsWith()` method returns `true` if a string begins with a specified value, otherwise `false`:

Example
```js
let text = "Hello world, welcome to the universe.";

text.startsWith("Hello")   // Returns true
```
### String.endsWith()
The `endsWith()` method returns `true` if a string ends with a specified value, otherwise `false`:

Example
```js
var text = "John Doe";
text.endsWith("Doe")    // Returns true
```
## Array methods
### Array.from()
The `Array.from()` method returns an Array object from any object with a length property or any iterable object.

Example
Create an Array from a String:
```js
Array.from("ABCDEFG")   // Returns [A,B,C,D,E,F,G]
```
### Array keys()
The `keys()` method returns an Array Iterator object with the keys of an array.

Example
Create an Array Iterator object, containing the keys of the array:
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
const keys = fruits.keys();

let text = "";
for (let x of keys) {
  text += x + "<br>";
}
```
### Array find()
The `find()` method returns the value of the first array element that passes a test function.

This example finds (returns the value of ) the first element that is larger than 18:

Example
```js
const numbers = [4, 9, 16, 25, 29];
let first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
Note that the function takes 3 arguments:

* The item value
* The item index
* The array itself
### Array findIndex()
The `findIndex()` method returns the index of the first array element that passes a test function.

This example finds the index of the first element that is larger than 18:

Example
```js
const numbers = [4, 9, 16, 25, 29];
let first = numbers.findIndex(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
Note that the function takes 3 arguments:

* The item value
* The item index
* The array itself
## New Math Methods
ES6 added the following methods to the Math object:

* `Math.trunc()`
* `Math.sign()`
* `Math.cbrt()`
* `Math.log2()`
* `Math.log10()`
### The Math.trunc() Method
`Math.trunc(x)` returns the integer part of x:

Example
```js
Math.trunc(4.9);    // returns 4
Math.trunc(4.7);    // returns 4
Math.trunc(4.4);    // returns 4
Math.trunc(4.2);    // returns 4
Math.trunc(-4.2);    // returns -4
```
### The Math.sign() Method
`Math.sign(x)` returns if x is negative, null or positive:

Example
```js
Math.sign(-4);    // returns -1
Math.sign(0);    // returns 0
Math.sign(4);    // returns 1
```
### The Math.cbrt() Method
`Math.cbrt(x)` returns the cube root of x:

Example
```js
Math.cbrt(8);    // returns 2
Math.cbrt(64);    // returns 4
Math.cbrt(125);    // returns 5
```
### The Math.log2() Method
`Math.log2(x)` returns the base 2 logarithm of x:

Example
```js
Math.log2(2);    // returns 1
```
### The Math.log10() Method
`Math.log10(x)` returns the base 10 logarithm of x:

Example
```js
Math.log10(10);    // returns 1
```
## New Number Properties
ES6 added the following properties to the Number object:

* `EPSILON`
* `MIN_SAFE_INTEGER`
* `MAX_SAFE_INTEGER`

### EPSILON Example
```js
let x = Number.EPSILON;
```
### MIN_SAFE_INTEGER Example
```js
let x = Number.MIN_SAFE_INTEGER;
```
### MAX_SAFE_INTEGER Example
```js
let x = Number.MAX_SAFE_INTEGER;
```

## New Number Methods
ES6 added 2 new methods to the Number object:

* `Number.isInteger()`
* `Number.isSafeInteger()`

### The Number.isInteger() Method
The `Number.isInteger()` method returns true if the argument is an integer.

Example
```js
Number.isInteger(10);        // returns true
Number.isInteger(10.5);      // returns false
```
### The Number.isSafeInteger() Method
A safe integer is an integer that can be exactly represented as a double precision number.

The `Number.isSafeInteger()` method returns true if the argument is a safe integer.

Example
```js
Number.isSafeInteger(10);    // returns true
Number.isSafeInteger(12345678901234567890);  // returns false
```
Safe integers are all integers from -(253 - 1) to +(253 - 1).

This is safe: 9007199254740991. This is not safe: 9007199254740992.
## New Global Methods
ES6 added 2 new global number methods:

* `isFinite()`
* `isNaN()`
### The isFinite() Method
The global `isFinite()` method returns `false` if the argument is `Infinity` or `NaN`.

Otherwise it returns `true`:

Example
```js
isFinite(10/0);       // returns false
isFinite(10/1);       // returns true
```
### The isNaN() Method
The global `isNaN()` method returns `true` if the argument is `NaN`. Otherwise it returns `false`:

Example
```js
isNaN("Hello");       // returns true
```
## Object entries()
Example
Create an Array Iterator, and then iterate over the key/value pairs:
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
const f = fruits.entries();

for (let x of f) {
  document.getElementById("demo").innerHTML += x;
}
```
The `entries()` method returns an Array Iterator object with key/value pairs:
```
[0, "Banana"]
[1, "Orange"]
[2, "Apple"]
[3, "Mango"]
```
The `entries()` method does not change the original array
## Modules:
ES6 modules allow organizing code into separate files, making it easier to manage dependencies and reuse code.

Example:

```js
// Exporting module
export function greet(name) {
    return `Hello, ${name}!`;
}

// Importing module
import { greet } from './utils.js';
```
These are just some of the key features introduced in ES6 and later versions of ECMAScript. Embracing these features can greatly enhance productivity and maintainability when writing JavaScript code.

# Asynchronous JavaScript
Asynchronous JavaScript is a programming paradigm that allows you to execute code non-sequentially, meaning that certain operations can be initiated without waiting for their completion before moving on to the next task. This is particularly useful for handling tasks such as network requests, file I/O, timers, and other operations that may take some time to complete.

Here are some common techniques and concepts associated with asynchronous JavaScript:

### Callbacks:
Callbacks are functions passed as arguments to other functions, which are then invoked once an asynchronous operation is completed. Callbacks have been a traditional way to handle asynchronous code in JavaScript.

Example:

```js
function fetchData(callback) {
    setTimeout(() => {
        const data = 'Some data';
        callback(data);
    }, 1000);
}

fetchData((data) => {
    console.log(data);
});
```
### Promises:
Promises provide a cleaner and more structured way to work with asynchronous code compared to callbacks. A promise represents the eventual completion or failure of an asynchronous operation and allows chaining of asynchronous operations using .then() and .catch() methods.

Example:

```js
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const data = 'Some data';
            resolve(data);
        }, 1000);
    });
}

fetchData()
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.error(error);
    });
```
### Async/Await:
Async functions and the await keyword provide a more elegant way to write asynchronous code, making it look more like synchronous code. Async functions return a promise, and the await keyword can be used to wait for the resolution of a promise inside an async function.

Example:

```js
async function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const data = 'Some data';
            resolve(data);
        }, 1000);
    });
}

async function fetchDataAndProcess() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}

fetchDataAndProcess();
```
### Event Loop:
JavaScript has a single-threaded event loop model, meaning that all code is executed in a single thread. Asynchronous operations such as timers, network requests, and I/O operations are offloaded to the browser or Node.js runtime environment, and their completion is handled by the event loop.

##
**Asynchronous JavaScript** is essential for building responsive and efficient web applications, especially when dealing with tasks that involve waiting for external resources or performing time-consuming operations. Promises and async/await have become the preferred techniques for handling asynchronous code due to their cleaner syntax and better error handling compared to callbacks. Understanding these concepts is crucial for effective JavaScript development.

# Modules
Modules in JavaScript are a way to organize code into separate files or modules, making it easier to manage dependencies, reuse code, and maintain a clean codebase. Before the introduction of native module support in JavaScript, developers often used various module patterns such as the Revealing Module Pattern or AMD (Asynchronous Module Definition). However, with the advent of ECMAScript 6 (ES6), also known as ES2015, JavaScript gained built-in support for modules.

JavaScript modules use the `import` and `export` keywords to define dependencies and expose functionality between different modules. Here's an overview of how modules work in JavaScript:

## Exporting from a Module:
To make functionality available from a module to other parts of the application, you use the export keyword followed by the keyword default or the name of the function, variable, or class you want to export.

Example:

```js
// export a single function
export function add(a, b) {
    return a + b;
}

// export a single variable
export const PI = 3.14;

// export a class
export class Person {
    constructor(name) {
        this.name = name;
    }
}

// default export
const data = [1, 2, 3];
export default data;
```
## Importing from a Module:
To use functionality exported from another module, you use the import keyword followed by the module path and the names of the functions, variables, or classes you want to import. You can also use the default keyword for default exports.

Example:

```js
// import named exports
import { add, PI, Person } from './math.js';

// use the imported functions, variables, or classes
console.log(add(2, 3)); // Output: 5
console.log(PI); // Output: 3.14
const person = new Person('John');

// import default export
import data from './data.js';
console.log(data); // Output: [1, 2, 3]
```
## Module Types:
JavaScript supports two types of modules:

* **ES6 Modules:** These are native JavaScript modules that are supported in modern browsers and Node.js. They use `import` and `export` syntax.
* **CommonJS Modules:** These are used in Node.js and follow the `require()` and `module.exports` syntax. While Node.js supports both types of modules, ES6 modules are generally preferred for new projects.
## Browser Support:
While modern browsers have good support for ES6 modules, older browsers may require transpilation using tools like Babel to convert ES6 modules into a format that they understand.
##
Modules play a crucial role in modern JavaScript development, helping to organize code, manage dependencies, and improve code maintainability. They facilitate better code reuse and make it easier to work on large-scale applications with multiple developers.

# JSON
**JSON**, short for JavaScript Object Notation, is a lightweight data interchange format that is easy for humans to read and write and easy for machines to parse and generate. In JavaScript, JSON is commonly used for data exchange between a client and a server, storing configuration settings, and serializing JavaScript objects into a string format for storage or transmission.

JSON Syntax:

* JSON data is written as key-value pairs.
* Keys are always strings, enclosed in double quotes.
* Values can be strings, numbers, arrays, objects, booleans, or null.
* Data is separated by commas.
* Objects are enclosed in curly braces {}, and arrays are enclosed in square brackets `[]`.
Example of JSON Data:

```js
{
  "name": "John",
  "age": 30,
  "isStudent": false,
  "favorites": ["pizza", "movies", "coding"],
  "address": {
    "street": "123 Main St",
    "city": "New York"
  },
  "isActive": true,
  "birthDate": null
}
```
In JavaScript, you can work with JSON using built-in methods provided by the `JSON` object:

### `JSON.stringify()`: Converts a JavaScript object into a JSON string.

Example:

```js
const person = {
    name: 'John',
    age: 30,
    isStudent: false
};

const jsonString = JSON.stringify(person);
console.log(jsonString);
```
### `JSON.parse()`: Parses a JSON string and returns a JavaScript object.

Example:

```js
const jsonString = '{"name":"John","age":30,"isStudent":false}';
const person = JSON.parse(jsonString);
console.log(person);
```
These methods allow you to serialize JavaScript objects into JSON strings and deserialize JSON strings into JavaScript objects, facilitating data exchange between different systems and platforms. JSON is widely used in web development due to its simplicity, versatility, and compatibility with various programming languages and systems.

<p align="right">(<a href="#readme-top">back to top</a>)</p>




# Refferences

* [W3Schools](https://www.w3schools.com/js/default.asp)