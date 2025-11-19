# Javascript React Learning Kit 🚀

**Frontend Developer Guide, JavaScript, React, Redux ToolKit, React Testing Library, Node.js, TypeScript, Cypress, DevOps, DSA Problems and Interview Preparations Tasks.**

## Table of Contents
  - [Intro to JavaScript](#intro-to-javascript)
  - [Closure](#closure)
  - [Variable Declaration](#variable-declaration)
  - [Hoisting, Scoping, Execution Context](#hoisting-scoping-execution-context)
  - [Event Loop and Asynchronous Javascript](#event-loop-and-asynchronous-javascript)
  - [Types of Functions](#types-of-functions)
  - [Prototypes & Inheritance](#prototypes--inheritance)
  - [The 'this' keyword](#the-this-keyword)
  - [Callback, Callback Hell](#callback-callback-hell)
  - [Promises & Async Await](#promises--async-await)

## Intro to JavaScript
- JavaScript is a single-threaded and synchronous programming language that primarily runs on the client side in web browsers, but it can also run on the server using environments like Node.js.
- Even though it’s single-threaded, JavaScript efficiently handles concurrent tasks using the event loop, callback queue, and asynchronous APIs such as setTimeout, Promises, and async/await.
- The call stack is where JavaScript executes code line by line in a Last In, First Out (LIFO) manner.
- It can manipulate the DOM (Document Object Model) dynamically to create interactive and responsive user interfaces.
- JavaScript enables event-driven programming, allowing developers to respond to user interactions like clicks, hovers, and keypresses.

## Closure
- In JavaScript, a closure is a function bundled together with its lexical environment. This means an inner function has access to the variables of its outer function even after the outer function has finished executing.
- The inner function remembers and can access the outer function’s variables, allowing data to persist across different execution contexts.

**Example 1:** 
```
function OuterFn () {
  const outeVariable = 250
  console.log("Trigger Outer Function Context 1")
  
  return function ()  {
    console.log("Trigger Inner Function Context 2 and remembers Outer Function Variable", outeVariable)
  }
}
const clouserExample = OuterFn(); // Output : Trigger Outer Function Context 1
clouserExample() // Output: Trigger Inner Function Context 2 and remembers Outer Function Variable' 250
```

**Example 2:** Simple counter increment & decrement, it helps clean and re-usability, modularity, encapsulation, data privacy, etc.
```
const Counter = function () {
  let count = 0;

  return {
    increament: () => {
        count ++;
    },
    decreament : () => {
        count --;
    },
    getCount: () => {
      return count;
    }
  }
}

const myCounter = Counter();
myCounter.increament(); // Adding by 1
myCounter.increament(); // +1 = 2
myCounter.increament(); // 2 +1 = 3;

console.log("After increamenting Steps Executed The Value is :", myCounter.getCount()) // 3;

myCounter.decreament();
myCounter.decreament();

console.log("After decreament Steps Executed The Value is :", myCounter.getCount()) // 1;

```
**Example 3:** What will this code output?

```
  for (var i = 0; i < 3; i++) {
    setTimeout(function() {
    console.log(i);
    }, 1000);
  }
```
It prints 3 three times! Why? By the time the setTimeout callbacks execute, the loop has finished and i is 3. All three
Functions share the same i variable.


**Solutions:**
```
// Use let (block scope)

for (let i =0 ; i< 3; i++) {
  setTimeout( function () {
  console.log(i)
  })
}

// Create a closure with IIFE 

for (var i =0 ; i<3 ; i++) {

  (function (i) {
    setTimeout( function () {
    console.log('check count', i)
    },1)
  })(i)
}
```
**Key Notes:**
- Closures allow functions to access variables from their outer scope
- They enable data privacy and encapsulation
- They’re created automatically when functions are defined
- Understanding closures is crucial for working with callbacks, event handlers, and functional programming

## Variable Declaration
- In JavaScript, variables can be declared using var, let, and const.
- let and const are block-scoped, meaning they are accessible only within the block {} where they are defined.
- var is function-scoped (or globally scoped if declared outside a function) and was commonly used before ES6.
- const is used to declare variables whose values cannot be reassigned.
- let is used to declare variables that can be reassigned later.
- var allows redeclaration and reassignment, which can sometimes lead to unexpected behavior due to hoisting.

```
const flag = true;
if (flag) {
  const age = 20;
  console.log(age); // Output: 20
}
console.log(age); // ReferenceError: age is not defined
```

## Hoisting, Scoping, Execution Context

- ### Hosting
  - Before understanding hoisting, it’s important to know how the JavaScript engine executes code. The execution happens in two phases:
  1. **Memory Creation Phase (Creation Phase)**
    - During this phase, all variable and function declarations are moved to the top of their respective scopes — this behavior is known as hoisting.
    - Variables declared using var are initialized with undefined.
    - let and const declarations are also hoisted but remain uninitialized, staying in the Temporal Dead Zone (TDZ) until the line where they are defined.
    - Function declarations are stored in memory as key–value pairs, where the key is the function name and the value is the entire function definition.
  2. **Code Execution Phase**
    - In this phase, the code is executed line by line inside the call stack, and each statement is pushed and popped as it runs.
  3. **Temporal Dead Zone (TDZ)**
      - The Temporal Dead Zone (TDZ) is the period between the time a variable is hoisted and the time it is initialized (declared in the code).
      - Variables declared using let and const are hoisted to the top of their block scope, but they are not initialized automatically (unlike var, which is initialized with undefined).
      - During this uninitialized period, any attempt to access the variable results in a ReferenceError.
      - The TDZ exists from the start of the block until the line where the variable is actually declared and initialized.

- ### Scoping
  -  In JavaScript, there are three main types of scope:
  -  **Global Scope**: variables declared in the global scope can be accessed anywhere in the program. For example, the window object (in browsers) is globally accessible.
  -  **Function (Local) Scope**: Variables declared inside a function are accessible only within that function. They cannot be accessed outside of it.
  -  **Block Scope**: Variables declared using let or const inside a block {} (e.g., inside loops, if statements) can be accessed only within that block.
  -  **Lexical Scope**: Means that the scope of a variable is determined by its position in the source code, i.e., where it is written (declared), not where it is called from. Inner functions have access to variables defined in their outer (parent) scopes, even if they are executed outside of that scope. This relationship forms a scope chain, which allows nested functions to access variables declared in their parent functions or the global scope. Lexical scope is established at the time of writing (compile phase), not at runtime. Accesing globalVariable is a better example for the scope of chaining or lexical scoping. 
 
 ```
const globalVariable = "Global";

function scopeExample() {
  const localVariable = "Local Value";

  for (let i = 0; i < 3; i++) {
    console.log("Block scope:", i);              // Accessible only inside this block
    console.log("Function scope:", localVariable); // Accessible inside the function
    console.log("Global scope:", globalVariable);  // Accessible anywhere
  }
}

scopeExample();

console.log("Global scope:", globalVariable); // ✅ Accessible
console.log("Function scope:", localVariable); // ❌ ReferenceError
console.log("Block scope:", i);                // ❌ ReferenceError
```
  

## Event Loop and Asynchronous JavaScript
- JavaScript is a single-threaded, non-blocking, and asynchronous language. It achieves concurrency through its event loop mechanism.
- The Event Loop acts as a coordinator between the Call Stack and the Task Queues. It continuously monitors the call stack and, when it becomes empty, it pushes pending tasks from the queues into the call stack for execution. This ensures the application remains responsive and performs non-blocking operations smoothly.
- The event loop primarily works with three main components:
- **Call Stack**: The Call Stack is where JavaScript executes code line by line, following the Last In, First Out (LIFO) principle. Each function call is pushed onto the stack, and once completed, it’s popped off.
- **Microtask Queue**: The Microtask Queue has higher priority and includes tasks like Promises, Mutation Observers, and process.nextTick() (in Node.js). Microtasks are executed immediately after the current operation completes and before any macrotasks.
- **Macrotask Queue**: The Macrotask Queue includes operations such as setTimeout, setInterval, setImmediate (Node.js), and I/O callbacks. Once all microtasks are completed, the event loop picks up macrotasks for execution.
- **Event Loops**: The event loop ensures that asynchronous operations like API calls, timers, and callbacks are handled efficiently, allowing JavaScript to appear concurrent despite being single-threaded.

## Types of Functions

## Prototypes & Inheritance

## The 'this' keyword

## Callback, Callback Hell

## Promises & Async Await
