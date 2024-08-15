# Javascript Revision Notes

- [Javascript Revision Notes](#javascript-revision-notes)
  - [Basics - Part 1](#basics---part-1)
    - [1. Variables](#1-variables)
    - [2. Data Types](#2-data-types)
    - [3. Type Conversion and Operations](#3-type-conversion-and-operations)
    - [4. Strings](#4-strings)
    - [5. Numbers and Math](#5-numbers-and-math)
    - [6. Dates](#6-dates)
  - [Basics - Part 2](#basics---part-2)
    - [1. Arrays](#1-arrays)
    - [2. Objects](#2-objects)
  - [Basics - Part 3](#basics---part-3)
    - [1. Functions](#1-functions)
    - [2. Scopes in Functions](#2-scopes-in-functions)
    - [3. Arrow Functions](#3-arrow-functions)
    - [4. Immediately Invoked Function Expressions (IIFE)](#4-immediately-invoked-function-expressions-iife)
  - [How JS Works](#how-js-works)
  - [Call Stack](#call-stack)
  - [Loops and Iteration](#loops-and-iteration)
    - [ES6 Array Methods](#es6-array-methods)
  - [Additional Resources](#additional-resources)

## Basics - Part 1

### 1. Variables

In JavaScript, variables can be declared using `const`, `let`, or `var`.

```jsx
const accountId = 144553; // Declaring a constant
let accountEmail = "tushar@google.com"; // Declaring a variable (new way)
var accountPassword = "12345"; // Declaring a variable (old way)
let accountState;
console.log(accountState); // Output: undefined
```

Without strict mode:

```jsx
num = 5; // The variable "num" is created if it didn't exist
```

### 2. Data Types

JavaScript has eight basic data types.

#### Primitive Data Types

Primitive data types are the most basic data types in JavaScript.

##### i. Number

The `number` type is used for both integer and floating-point values.

```jsx
let n = 123;
n = 12.345;
```

Special numeric values include `Infinity`, `-Infinity`, and `NaN`.

Number capacity: \(2^{53} - 1\)

##### ii. BigInt

`BigInt` is used for integers of arbitrary length.

```jsx
// The "n" at the end indicates a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

##### iii. String

A `string` represents textual data.

```jsx
let str = "Hello";
let str2 = "Single quotes are ok too";
let phrase = `can embed another ${str}`;
```

Backticks (``) allow embedding variables and expressions into a string:

```jsx
let name = "John";

// Embed a variable
alert(`Hello, ${name}!`); // Hello, John!

// Embed an expression
alert(`The result is ${1 + 2}`); // The result is 3
```

##### iv. Boolean

The `boolean` type has only two values: `true` and `false`.

##### v. Null

`null` represents “nothing”, “empty” or “value unknown”.

```jsx
let age = null;
```

##### vi. Undefined

`undefined` means a value is not assigned. If a variable is declared but not assigned, its value is `undefined`:

```jsx
let age;
alert(age); // Shows "undefined"
```

##### vii. Symbol

The `symbol` type is used to create unique identifiers for objects.

##### viii. Object

Objects are a non-primitive data type used for storing collections of data and more complex entities.

#### Non-Primitive Data Types

Non-primitive data types can hold multiple values and are mutable.

##### i. Arrays

Arrays are used to store multiple values in a single variable.

```jsx
const heros = ["Ironman", "Thor", "Loki"];
```

##### ii. Objects

Objects store key-value pairs and are used to represent real-world entities.

```jsx
let myObj = {
  name: "Tushar",
  age: 22,
};
```

##### iii. Functions

Functions are blocks of code designed to perform a particular task.

```jsx
const myFunction = function () {
  console.log("Hello world");
};
```

#### The `typeof` Operator

The `typeof` operator returns the type of the operand.

```jsx
typeof undefined; // "undefined"
typeof 0; // "number"
typeof 10n; // "bigint"
typeof true; // "boolean"
typeof "foo"; // "string"
typeof Symbol("id"); // "symbol"
typeof Math; // "object"  (1)
typeof null; // "object"  (2)
typeof alert; // "function"  (3)
typeof heros; // "object"
typeof myObj; // "object"
typeof myFunction; // "function"
```

---

Notes:

1. `typeof Math` returns `"object"` because `Math` is a built-in object.
2. `typeof null` returns `"object"` due to a legacy bug in JavaScript.
3. `typeof alert` and `typeof myFunction` return `"function"` because functions are objects in JavaScript.

### 3. Type Conversion and Operations

#### i. Converting to Number

You can convert a string or boolean to a number using the `Number()` function.

```jsx
let score = "tushar";
console.log(typeof score); // "string"
console.log(typeof Number(score)); // "number"

let valueInNumber = Number(score);
console.log(valueInNumber); // NaN (because "tushar" cannot be converted to a number)
```

Examples:

- `"33"` → `33`
- `"33abc"` → `NaN`
- `true` → `1`, `false` → `0`

##### ii. Converting to Boolean

You can convert other types to a boolean using the `Boolean()` function.

```jsx
let isLoggedIn = "tushar";
let booleanIsLoggedIn = Boolean(isLoggedIn);
console.log(booleanIsLoggedIn); // true
```

Examples:

- `1` → `true`, `0` → `false`
- `""` (empty string) → `false`
- `"tushar"` → `true`

##### iii. Converting to String

You can convert numbers or other types to a string using the `String()` function.

```jsx
let someNumber = 33;
let stringNumber = String(someNumber);
console.log(stringNumber); // "33"
console.log(typeof stringNumber); // "string"
```

#### Operations

JavaScript supports various arithmetic and string operations.

##### i. Basic Arithmetic Operations

```jsx
let value = 3;
let negValue = -value;
console.log(negValue); // -3

console.log(2 + 2); // 4
console.log(2 - 2); // 0
console.log(2 * 2); // 4
console.log(2 ** 3); // 8 (exponentiation)
console.log(2 / 3); // 0.6666666666666666
console.log(2 % 3); // 2 (remainder)
```

##### ii. String Concatenation

```jsx
let str1 = "hello";
let str2 = " tushar";

let str3 = str1 + str2;
console.log(str3); // "hello tushar"
```

##### iii. Type Coercion in Operations

JavaScript automatically converts data types in certain operations.

```jsx
console.log("1" + 2); // "12"
console.log(1 + "2"); // "12"
console.log("1" + 2 + 2); // "122"
console.log(1 + 2 + "2"); // "32"
```

##### iv. Unary Plus (`+`) Operator

The unary plus (`+`) operator converts its operand to a number.

```jsx
console.log(+true); // 1
console.log(+""); // 0
```

##### v. Multiple Assignments

You can assign values to multiple variables at once.

```jsx
let num1, num2, num3;
num1 = num2 = num3 = 2 + 2;
console.log(num1, num2, num3); // 4 4 4
```

##### vi. Increment Operator

The increment operator (`++`) increases the value of a variable by one.

```jsx
let gameCounter = 100;
++gameCounter;
console.log(gameCounter); // 101
```

---

### 4. Strings

String can also be created `String` constructor:

```jsx
const gameName = new String("tushar-ta-com");

// Accessing individual characters
console.log(gameName[0]); // "h"

// Accessing properties and methods
console.log(gameName.__proto__); // String prototype
console.log(gameName.length); // 13
console.log(gameName.toUpperCase()); // "TUSHAR-TA-COM"
console.log(gameName.charAt(2)); // "s"
console.log(gameName.indexOf("s")); // 2
```

#### String Methods

JavaScript provides several methods to manipulate strings:

```jsx
// Extracting a substring
const newString = gameName.substring(0, 4);
console.log(newString); // "tush"

// Slicing a string (can use negative indices)
const anotherString = gameName.slice(-8, 4);
console.log(anotherString); // ""

// Trimming whitespace
const newStringOne = "   tushar    ";
console.log(newStringOne.trim()); // "tushar"

// Replacing parts of a string
const url = "https://tushar.com/tushar%20agrawal";
console.log(url.replace("%20", "-")); // "https://tushar.com/tushar-agrawal"

// Checking for substring inclusion
console.log(url.includes("sundar")); // false

// Splitting a string into an array
console.log(gameName.split("-")); // ["tushar", "ta", "com"]
```

---

### 5. Numbers and Math

```jsx
const score = 400;
console.log(score);

const balance = new Number(100);
console.log(balance.toString().length); // 3
console.log(balance.toFixed(1)); // "100.0"
```

#### Number Methods

```jsx
const otherNumber = 123.8966;
console.log(otherNumber.toPrecision(4)); // "123.9"

const hundreds = 1000000;
console.log(hundreds.toLocaleString("en-IN")); // "10,00,000"
```

#### Random Numbers

```jsx
console.log(Math.random()); // Random number between 0 and 1
console.log(Math.floor(Math.random() * 10) + 1); // Random number between 1 and 10

const min = 10;
const max = 20;
console.log(Math.floor(Math.random() * (max - min + 1)) + min); // Random number between 10 and 20
```

---

### 6. Dates

```jsx
let myDate = new Date();
console.log(myDate.toString()); // Current date and time as a string
console.log(myDate.toDateString()); // Current date as a string (e.g., "Wed Jan 23 2023")
console.log(myDate.toLocaleString()); // Locale-specific date and time string
console.log(typeof myDate); // "object"

// Creating specific dates
let myCreatedDate = new Date("01-14-2023");
console.log(myCreatedDate.toLocaleString()); // "14/01/2023, 00:00:00"
```

#### Timestamps

You can get the current timestamp or convert dates to timestamps:

```jsx
let myTimeStamp = Date.now();
console.log(myTimeStamp); // Current timestamp in milliseconds

console.log(myCreatedDate.getTime()); // Timestamp for the created date

// Current timestamp in seconds
console.log(Math.floor(Date.now() / 1000));
```

#### Date Methods

```jsx
let newDate = new Date();
console.log(newDate.getMonth() + 1); // Current month (1-12)
console.log(newDate.getDay()); // Day of the week (0-6, where 0 is Sunday)

// Getting the weekday as a string
console.log(newDate.toLocaleString("default", { weekday: "long" })); // E.g., "Wednesday"
```

---

## Basics - Part 2

### 1. Arrays

```javascript
const myArr = [0, 1, 2, 3, 4, 5];
const myHeors = ["shaktiman", "naagraj"];

const myArr2 = new Array(1, 2, 3, 4); // Creates an array with elements 1, 2, 3, 4
```

#### Array Methods

- **Push and Pop:** Add or remove elements from the end of the array.

```javascript
myArr.push(6); // Adds 6 to the end of the array
myArr.pop(); // Removes the last element
```

- **Unshift and Shift:** Add or remove elements from the beginning of the array.

```javascript
myArr.unshift(9); // Adds 9 to the beginning
myArr.shift(); // Removes the first element
```

- **Includes and IndexOf:** Check for the presence of an element or find its index.

```javascript
console.log(myArr.includes(9)); // Checks if 9 is in the array
console.log(myArr.indexOf(3)); // Returns the index of 3
```

- **Join:** Convert an array into a string.

```javascript
const newArr = myArr.join(); // Joins elements with a comma
console.log(newArr); // "0,1,2,3,4,5"
```

#### Shallow Copy and Deep Copy

- A shallow copy of an object is a copy whose properties share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you may also cause the other object to change too.

- A deep copy of an object is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you can be assured you're not causing the other object to change too.

#### Slice and Splice

- **Slice:** Returns a shallow copy of a portion of an array.

```javascript
const myn1 = myArr.slice(1, 3); // Returns elements from index 1 to 2
console.log(myn1); // [1, 2]
```

- **Splice:** Modifies the array by removing or replacing elements.

```javascript
const myn2 = myArr.splice(1, 3); // Removes 3 elements starting from index 1
console.log(myn2); // [1, 2, 3]
```

#### Combining Arrays

- **Concat:** Combine two arrays.

```javascript
const marvel_heros = ["thor", "Ironman", "spiderman"];
const dc_heros = ["superman", "flash", "batman"];

const allHeros = marvel_heros.concat(dc_heros);
console.log(allHeros); // ["thor", "Ironman", "spiderman", "superman", "flash", "batman"]
```

- **Spread Operator:** Another way to combine arrays.

```javascript
const all_new_heros = [...marvel_heros, ...dc_heros];
console.log(all_new_heros); // Same as allHeros
```

#### Other Useful Methods

- **Flat:** Flattens nested arrays.

```javascript
const another_array = [1, 2, 3, [4, 5, 6], 7, [6, 7, [4, 5]]];
const real_another_array = another_array.flat(Infinity);
console.log(real_another_array); // [1, 2, 3, 4, 5, 6, 7, 6, 7, 4, 5]
```

- **Array.isArray:** Checks if a value is an array.

```javascript
console.log(Array.isArray("tushar")); // false
```

- **Array.from:** Creates an array from an iterable.

```javascript
console.log(Array.from("tushar")); // ["H", "i", "t", "e", "s", "h"]
```

- **Array.of:** Creates an array from arguments.

```javascript
let score1 = 100,
  score2 = 200,
  score3 = 300;
console.log(Array.of(score1, score2, score3)); // [100, 200, 300]
```

---

### 2. Objects

```javascript
const mySym = Symbol("key1");

const JsUser = {
  name: "tushar",
  "full name": "tushar agrawal",
  [mySym]: "mykey1",
  age: 18,
  location: "Jaipur",
  email: "tushar@google.com",
  isLoggedIn: false,
  lastLoginDays: ["Monday", "Saturday"],
};
```

#### Accessing Object Properties

- Using dot notation and bracket notation:

```javascript
console.log(JsUser.email); // "tushar@google.com"
console.log(JsUser["full name"]); // "tushar agrawal"
console.log(JsUser[mySym]); // "mykey1"
```

#### Modifying Objects

- **Object.freeze:** Prevents modification to the object.

```javascript
JsUser.email = "tushar@chatgpt.com";
Object.freeze(JsUser);
JsUser.email = "tushar@microsoft.com"; // Will not change due to freeze
console.log(JsUser.email); // "tushar@chatgpt.com"
```

#### Methods in Objects

- **Adding methods:**

```javascript
JsUser.greeting = function () {
  console.log("Hello JS user");
};
JsUser.greetingTwo = function () {
  console.log(`Hello JS user, ${this.name}`);
};

console.log(JsUser.greeting()); // "Hello JS user"
console.log(JsUser.greetingTwo()); // "Hello JS user, tushar"
```

#### Working with Multiple Objects

- **Merging Objects:**

```javascript
const obj1 = { 1: "a", 2: "b" };
const obj2 = { 3: "a", 4: "b" };

const obj3 = { ...obj1, ...obj2 }; // Merging obj1 and obj2
console.log(obj3); // {1: "a", 2: "b", 3: "a", 4: "b"}
```

#### Object Utilities

- **Keys, Values, Entries:**

```javascript
console.log(Object.keys(JsUser)); // ["name", "full name", "age", "location", "email", "isLoggedIn", "lastLoginDays"]
console.log(Object.values(JsUser)); // ["tushar", "tushar agrawal", 18, "Jaipur", "tushar@chatgpt.com", false, ["Monday", "Saturday"]]
console.log(Object.entries(JsUser)); // [["name", "tushar"], ["full name", "tushar agrawal"], ...]
```

- **Destructuring:**

```javascript
const course = {
  coursename: "js in hindi",
  price: "999",
  courseInstructor: "tushar",
};

const { courseInstructor: instructor } = course;
console.log(instructor); // "tushar"
```

---

## Basics - Part 3

### 1. Functions

```javascript
function sayMyName() {
  console.log("T");
  console.log("U");
  console.log("S");
  console.log("H");
  console.log("A");
  console.log("R");
}

sayMyName();
```

#### Function with Parameters

```javascript
function addTwoNumbers(number1, number2) {
  return number1 + number2;
}

const result = addTwoNumbers(3, 5);
console.log("Result: ", result); // Result: 8
```

#### Default Parameters

- Default values can be assigned to parameters in case no argument is passed.

```javascript
function loginUserMessage(username = "sam") {
  if (!username) {
    console.log("Please enter a username");
    return;
  }
  return `${username} just logged in`;
}

console.log(loginUserMessage("tushar")); // tushar just logged in
console.log(loginUserMessage()); // sam just logged in
```

#### Rest Parameters

- Rest parameters allow functions to accept an indefinite number of arguments as an array.

```javascript
function calculateCartPrice(val1, val2, ...num1) {
  return num1;
}

console.log(calculateCartPrice(200, 400, 500, 2000)); // [500, 2000]
```

#### Function as Object Methods

- Functions can be defined as methods within objects.

```javascript
const user = {
  username: "tushar",
  price: 199,

  welcomeMessage: function () {
    console.log(`${this.username}, welcome to the website`);
  },
};

user.welcomeMessage(); // tushar, welcome to the website
```

---

### 2. Scopes in Functions

- Variables declared within a function are in the function's local scope, while those declared outside are in the global scope.

```javascript
function one() {
  const username = "tushar";

  function two() {
    const website = "youtube";
    console.log(username); // Accessible due to closure
  }

  two();
}

one();

// console.log(username); // Error: username is not defined
```

#### `let` vs `var`

#### Scoping Rules

- **`var`: Function Scope**

  Variables declared with `var` are scoped to the immediate function body they are declared in. If declared outside a function, they are globally scoped.

- **`let`: Block Scope**

  Variables declared with `let` are scoped to the immediate enclosing block, denoted by `{ }`. This means they are only accessible within the block they are defined in.

```javascript
function run() {
  var foo = "Foo";
  let bar = "Bar";

  console.log(foo, bar); // Foo Bar

  {
    var moo = "Mooo";
    let baz = "Bazz";
    console.log(moo, baz); // Mooo Bazz
  }

  console.log(moo); // Mooo
  console.log(baz); // ReferenceError
}

run();
```

- In the above code, `moo` is accessible outside the block because it is declared with `var`, which is function-scoped.
- `baz`, declared with `let`, is block-scoped, and hence trying to access it outside the block results in a `ReferenceError`.

#### Why `let` Was Introduced

- **Function Scope Confusion:**
  The primary reason `let` was introduced is that function scope can be confusing and is a common source of bugs in JavaScript.

```javascript
var funcs = [];
for (var i = 0; i < 3; i++) {
  funcs[i] = function () {
    console.log("My value: " + i);
  };
}
for (var j = 0; j < 3; j++) {
  funcs[j]();
}
```

- **Output:**

  - `My value: 3`
  - `My value: 3`
  - `My value: 3`

- **Explanation:**
  Here, all the functions in the `funcs` array log `3` because `var` is function-scoped, so the loop variable `i` is shared across all iterations. When the functions are called, they all reference the same `i` value, which is `3` after the loop ends.

- **Solution with `let`:**
  By using `let`, each iteration has its own block-scoped `i`.

#### Hoisting

- **`var` Hoisting:**
  Variables declared with `var` are hoisted to the top of their scope and are initialized as `undefined`. This means they can be accessed before the declaration, but their value will be `undefined`.

```javascript
function checkHoisting() {
  console.log(foo); // undefined
  var foo = "Foo";
  console.log(foo); // Foo
}

checkHoisting();
```

- **`let` Hoisting:**
  Variables declared with `let` are also hoisted, but they are not initialized. Accessing them before their declaration results in a `ReferenceError`. This behavior is known as being in the "temporal dead zone" (TDZ).

```javascript
function checkHoisting() {
  console.log(foo); // ReferenceError
  let foo = "Foo";
  console.log(foo); // Foo
}

checkHoisting();
```

#### Creating Global Object Property

- **`var` Creates Global Properties:**
  When `var` is used at the top level, it creates a property on the global object (`window` in browsers).

- **`let` Does Not Create Global Properties:**
  `let` does not create a property on the global object, even when used at the top level.

```javascript
var foo = "Foo"; // Globally scoped
let bar = "Bar"; // Globally scoped but not part of the global object

console.log(window.foo); // Foo
console.log(window.bar); // undefined
```

#### Redeclaration

- **`var` Allows Redeclaration:**
  In strict mode, `var` allows you to redeclare the same variable within the same scope.

- **`let` Does Not Allow Redeclaration:**
  `let` raises a `SyntaxError` if you try to redeclare the same variable in the same scope.

```javascript
"use strict";
var foo = "foo1";
var foo = "foo2"; // No problem, 'foo1' is replaced with 'foo2'.

let bar = "bar1";
let bar = "bar2"; // SyntaxError: Identifier 'bar' has already been declared
```

#### Closure Intro

Closure is a feature where an inner function has access to variables from its outer (enclosing) function even after the outer function has finished executing. This happens because, when a function is created, it retains a reference to its lexical environment, which includes the scope in which the function was declared.

```javascript
function outerFunction() {
  let outerVariable = "I am from the outer function";

  function innerFunction() {
    console.log(outerVariable); // Accessing the outer function's variable
  }

  return innerFunction;
}

const myClosure = outerFunction(); // outerFunction runs and returns innerFunction
myClosure(); // "I am from the outer function"
```

Explanation:

`outerFunction` declares a variable `outerVariable` and an `innerFunction`.
`innerFunction` is returned by `outerFunction` and stored in `myClosure`.
Even though `outerFunction` has finished executing, `myClosure` (which is `innerFunction`) still has access to `outerVariable` because of the closure.

---

### 3. Arrow Functions

- In regular functions, `this` refers to the object that is calling the function.

```js
const user = {
  name: "tushar",
  greet: function () {
    console.log(this.name); // 'this' refers to the 'user' object
  },
};

user.greet(); // Output: "tushar"
user.name = "sam";
user.greet(); // output: "sam"
```

- Arrow functions provide a shorter syntax and do not have their own `this`.
- Instead, they inherit `this` from the surrounding lexical context (where the arrow function is defined).

```js
const user = {
  name: "tushar",
  greet: () => {
    console.log(this.name); // 'this' refers to the outer context, not the 'user' object
  },
};

user.greet(); // Output: undefined
```

```javascript
const chai = () => {
  console.log(this); // output : {}, because it takes outer context instead of chai() context
};

chai();
```

---

### 4. Immediately Invoked Function Expressions (IIFE)

- IIFE are functions that are executed immediately after they are defined.

```javascript
(function chai() {
  console.log("DB CONNECTED");
})();

((name) => {
  console.log(`DB CONNECTED TWO ${name}`);
})("tushar");
```

Why IIFE ?

- An IIFE immediately executes and does not leave a trace behind in the global scope.
- Variables and functions inside an IIFE are scoped to the function itself, avoiding conflicts with other variables or functions in the global scope.

- `Global Scope Protection:` IIFE helps prevent variable name collisions by not polluting the global namespace.
- `Data Privacy:` Variables inside an IIFE are not accessible outside, which helps in keeping data private.
- `Immediate Execution:` IIFE is useful for code that needs to run immediately without having to be invoked later.

---

## How JS Works

## Call Stack

## Loops and Iteration

1. **`for...of` Loop**:

   - Iterates over iterable objects like arrays or strings. (not object)
   - Example:

     ```javascript
     const arr = [1, 2, 3, 4, 5];
     for (const num of arr) {
       console.log(num); // 1, 2, 3, 4, 5
     }

     const greetings = "Hello world!";
     for (const greet of greetings) {
       console.log(`Each char is ${greet}`);
     }
     ```

2. **`for...in` Loop**:

   - Iterates over the keys (property names) of an object. (also works for array)
   - Example:

     ```javascript
     const myObject = {
       js: "javascript",
       cpp: "C++",
       rb: "ruby",
       swift: "swift by apple",
     };

     for (const key in myObject) {
       console.log(`${key} shortcut is for ${myObject[key]}`);
     }
     ```

3. **`forEach` Method**:

   - Executes a provided function once for each array element.
   - Example:

     ```javascript
     const coding = ["js", "ruby", "java", "python", "cpp"];
     coding.forEach((item) => {
       console.log(item);
     });

     const myCoding = [
       { languageName: "javascript", languageFileName: "js" },
       { languageName: "java", languageFileName: "java" },
       { languageName: "python", languageFileName: "py" },
     ];

     myCoding.forEach((item) => {
       console.log(item.languageName); // output: javascript, java, python
     });
     ```

   ### Maps

   - `Map` is a collection of keyed data items, like an object. However, a `Map` allows keys of any type.
   - Example:

     ```javascript
     const map = new Map();
     map.set("IN", "India");
     map.set("USA", "United States of America");
     map.set("Fr", "France");

     for (const [key, value] of map) {
       console.log(key, ":-", value);
     }
     ```

### ES6 Array Methods

1. **`filter` Method**:

   - Creates a new array with all elements that pass the test implemented by the provided function.

   ```js
   const myNums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
   const newNums = myNums.filter((num) => {
     return num > 4;
   }); // output: [5,6,7....]
   ```

   ```javascript
   const books = [
     {
       title: "Book One",
       genre: "Fiction",
       publish: 1981,
       edition: 2004,
     },
     {
       title: "Book Two",
       genre: "Non-Fiction",
       publish: 1992,
       edition: 2008,
     },
     {
       title: "Book Three",
       genre: "History",
       publish: 1999,
       edition: 2007,
     },
     {
       title: "Book Four",
       genre: "Non-Fiction",
       publish: 1989,
       edition: 2010,
     },
     {
       title: "Book Five",
       genre: "Science",
       publish: 2009,
       edition: 2014,
     },
     {
       title: "Book Six",
       genre: "Fiction",
       publish: 1987,
       edition: 2010,
     },
     {
       title: "Book Seven",
       genre: "History",
       publish: 1986,
       edition: 1996,
     },
     {
       title: "Book Eight",
       genre: "Science",
       publish: 2011,
       edition: 2016,
     },
     {
       title: "Book Nine",
       genre: "Non-Fiction",
       publish: 1981,
       edition: 1989,
     },
   ];

   let userBooks = books.filter((bk) => bk.genre === "History");
   userBooks = books.filter(
     (bk) => bk.publish >= 1995 && bk.genre === "History"
   );

   console.log(userBooks);
   ```

2. **`map` Method**:

   - Creates a new array populated with the results of calling a provided function on every element in the calling array.

   ```js
   const myNumers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
   const newNums = myNumers.map((num) => {
     return num + 10;
   }); // [11, 12, 13,...]
   ```

   ```javascript
   const myNumbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

   const newNums = myNumbers
     .map((num) => num * 10)
     .map((num) => num + 1)
     .filter((num) => num >= 40);

   console.log(newNums); // [41, 51, 61, 71, 81, 91, 101]
   ```

3. **`reduce` method**:

   - The `reduce` method in JavaScript is used to accumulate a single output value from an array. It applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

   ```js
   const myNums = [1, 2, 3];
   const myTotal = myNums.reduce((acc, curr) => acc + curr, 0);
   console.log(myTotal); // Output: 6
   ```

   - **Explanation**:

     - **Accumulator (`acc`)**: This is the accumulated value previously returned in the last invocation of the callback or the initial value if provided.
     - **Current Value (`curr`)**: The current element being processed in the array.
     - **Initial Value (`0`)**: The initial value to start the accumulation. This will `acc` value in first iteration.

   - **Process**:
     - First iteration: `acc = 0`, `curr = 1` → `acc + curr = 1`
     - Second iteration: `acc = 1`, `curr = 2` → `acc + curr = 3`
     - Third iteration: `acc = 3`, `curr = 3` → `acc + curr = 6`
     - The final result is `6`.

   #### Example with an Array of Objects

   ```javascript
   const shoppingCart = [
     { itemName: "js course", price: 2999 },
     { itemName: "py course", price: 999 },
     { itemName: "mobile dev course", price: 5999 },
     { itemName: "data science course", price: 12999 },
   ];

   const priceToPay = shoppingCart.reduce((acc, item) => acc + item.price, 0);

   console.log(priceToPay); // Output: 22996
   ```

## Additional Resources

- JS Lectures Hindi [Chai aur Code YT](https://youtube.com/playlist?list=PLu71SKxNbfoBuX3f4EOACle2y-tRC5Q37&si=6ICoBvqycEJzGJ67)
- Type Conversion [ECMAScript Language Specification](https://tc39.es/ecma262/multipage/abstract-operations.html#sec-type-conversion).
- The typeof operator [ECMAScript Language Specification](https://262.ecma-international.org/5.1/#sec-11.4.3).
- let vs var [Stackoverflow](https://stackoverflow.com/questions/762011/what-is-the-difference-between-let-and-var)

---
