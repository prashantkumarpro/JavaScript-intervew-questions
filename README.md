# **JavaScript-intervew-questions**

** Let's start:**\

## ** Q1: Can you explain the difference between `var`, `let`, and `const` in JavaScript?**

###**Answer:**
- **`var`** is function-scoped, meaning it is accessible throughout the function where it's declared. It can also be re-declared and re-assigned, but it leads to issues like **hoisting** and **unexpected behaviors** due to its scope.
- **`let`** is block-scoped, so it's only accessible within the block where it is declared (e.g., within an `if` statement or loop). You can re-assign `let`, but not re-declare it within the same scope.
- In JavaScript, `var` can be **re-declared** within the same scope, which means you can declare the same variable multiple times without getting an error. Here's an example:

```
var name = "Prashant";
var name = "Kumar";  // re-declaring 'name'
console.log(name);    // Output: "Kumar"
```

In this case, `var` allows you to declare the `name` variable twice in the same scope without throwing an error, and it simply overwrites the previous value.

This is one of the issues with `var`, as it can lead to unintended behavior, especially in larger codebases, which is why `let` and `const` (block-scoped) are preferred for better control.

- **`const`** is also block-scoped like `let`, but it **cannot be re-assigned** after its initial assignment. However, if the `const` holds an object or array, you can still modify the contents of that object or array.

## ** Q2: Can you explain hoisting in JavaScript, specifically in the context of var, let, and const?**
---
**Answer:** Sure! Let's break down **hoisting** in JavaScript and how it works with `var`, `let`, and `const`.


### **What is Hoisting?**

**Hoisting** is a JavaScript mechanism where variable and function declarations are moved (or "hoisted") to the top of their scope before code execution. This means that you can use variables and functions before they appear in the code, but the behavior varies depending on how they are declared.

In hoisting:
- Variable **declarations** (but not assignments) are hoisted.
- Function **declarations** (entire functions) are hoisted.

However, variables declared with `var`, `let`, and `const` behave differently when hoisted.

---

### **Hoisting with `var`**

- When you declare a variable with `var`, **the declaration is hoisted** to the top of the function or global scope, but it is initialized with `undefined` until the assignment is encountered.
- This is why you can reference `var` variables before they are initialized without getting an error.

#### Example:
```javascript
console.log(x);  // Output: undefined
var x = 5;
console.log(x);  // Output: 5
```

**Explanation:**
- The `var` declaration is hoisted, but its value is set to `undefined` until the assignment `x = 5` is executed. So, when `console.log(x)` is called before the assignment, it logs `undefined`.

---

### **Hoisting with `let`**

- Variables declared with `let` are also hoisted, but they are **not initialized**. They remain in the **Temporal Dead Zone (TDZ)** from the start of the block until they are initialized.
- Accessing the variable before initialization results in a **ReferenceError**.

#### Example:
```javascript
console.log(y);  // ReferenceError: Cannot access 'y' before initialization
let y = 10;
console.log(y);  // Output: 10
```

**Explanation:**
- The `let` declaration is hoisted, but because the variable is in the TDZ, accessing it before the initialization causes a `ReferenceError`.

---

### **Hoisting with `const`**

- Variables declared with `const` behave similarly to `let`. They are hoisted but remain in the **Temporal Dead Zone** until they are initialized.
- Accessing a `const` variable before initialization results in a **ReferenceError**.
- Additionally, once initialized, `const` variables cannot be reassigned.

#### Example:
```javascript
console.log(z);  // ReferenceError: Cannot access 'z' before initialization
const z = 15;
console.log(z);  // Output: 15
```

**Explanation:**
- Just like with `let`, the `const` declaration is hoisted, but trying to access `z` before it’s initialized results in a `ReferenceError`.

---

### **Comparison of `var`, `let`, and `const` Hoisting**

| Variable Type | Hoisted | Initial Value Before Assignment | TDZ (Temporal Dead Zone) | Can Be Reassigned? |
|---------------|---------|---------------------------------|--------------------------|--------------------|
| `var`         | Yes     | `undefined`                     | No                       | Yes                |
| `let`         | Yes     | Not initialized (TDZ)            | Yes                      | Yes                |
| `const`       | Yes     | Not initialized (TDZ)            | Yes                      | No                 |

---

### **Summary:**
- **`var`** is hoisted and initialized with `undefined`. You can reference it before assignment, but it will give `undefined` until the actual assignment.
- **`let`** and **`const`** are hoisted but are not initialized. They are in the **temporal dead zone** (TDZ) and accessing them before the initialization line throws a `ReferenceError`. `const` also cannot be reassigned once initialized.

---

### Example Code (to understand all together):

```javascript
console.log(a);  // undefined (var is hoisted and initialized to undefined)
var a = 5;

console.log(b);  // ReferenceError: Cannot access 'b' before initialization
let b = 10;

console.log(c);  // ReferenceError: Cannot access 'c' before initialization
const c = 15;
```

In the above code:
- `var a` is hoisted and initialized as `undefined` before its assignment.
- `let b` and `const c` are hoisted but are not initialized until the point where their declarations appear in the code, so trying to access them before that results in a `ReferenceError`.

---
## **Q3: What are the differences between var, let, and const in terms of scope, hoisting, and reassignment?**

### Answer:

1. **Scope:**
   - `var` is **function-scoped**. This means that a `var` variable is accessible throughout the function or globally if declared outside any function.
   - `let` and `const` are **block-scoped**, meaning they are only accessible within the block `{}` in which they are defined (such as inside loops, `if` statements, or functions).

2. **Hoisting:**
   - Variables declared with `var` are **hoisted** to the top of their scope and initialized with `undefined`. This is why you can reference a `var` variable before its declaration without getting an error, though its value will be `undefined` until it's assigned.
   - `let` and `const` are also **hoisted**, but they are **not initialized**. Accessing them before their declaration will result in a **ReferenceError** because they are in the **Temporal Dead Zone (TDZ)** until the point where they are initialized.

3. **Reassignment:**
   - `var` and `let` can be **reassigned** after their declaration.
   - `const` cannot be reassigned after its initial assignment. However, if a `const` is used with an **object** or **array**, the properties or elements of the object/array can still be **modified**, but you cannot reassign the entire object/array itself.

---

### Example to Demonstrate the Differences:

```javascript
function example() {
    // Scope
    if (true) {
        var x = 1;      // function-scoped
        let y = 2;      // block-scoped
        const z = 3;    // block-scoped
    }
    console.log(x); // 1
    console.log(y); // ReferenceError: y is not defined
    console.log(z); // ReferenceError: z is not defined
}
example();

// Hoisting
console.log(a);  // undefined
var a = 10;

console.log(b);  // ReferenceError: Cannot access 'b' before initialization
let b = 20;

console.log(c);  // ReferenceError: Cannot access 'c' before initialization
const c = 30;
```

## **Q4: What are the different data types in JavaScript?**
  
**Answer**
In JavaScript, there are two main categories of data types: **primitive** and **non-primitive** (or reference types).

### 1. **Primitive Data Types**:
   These are the basic data types that are **immutable**, meaning their values cannot be altered (changed) directly.
   - **Number**: Represents both integer and floating-point numbers. Example: `42`, `3.14`
   - **String**: Represents text or sequences of characters. Example: `"Hello"`, `'World'`
   - **Boolean**: Represents a logical entity with two values: `true` or `false`.
   - **Undefined**: A variable that has been declared but not assigned a value yet.
   - **Null**: Represents the intentional absence of any value.
   - **BigInt**: Used for very large integers that exceed the safe integer limit. Example: `123n`
   - **Symbol**: Used to create unique and immutable values, often used as object keys.

### Example with Primitive Types (Immutable):
_Primitive data types like `number`, `string`, `boolean`, `null`, `undefined`, `symbol`, and `bigInt` are immutable. Here's an example:_

```javascript
let greeting = "Hello";
greeting[0] = "J";  // Trying to change the first letter
console.log(greeting);  // Output: "Hello"
```

Even though we tried to change the first letter of the string `"Hello"`, it didn't change because **strings are immutable**. Instead, if we want a new string, we have to create a completely new one:

```javascript
let newGreeting = greeting.replace("H", "J");
console.log(newGreeting);  // Output: "Jello"
```

Here, the string wasn't modified in place. Instead, a new string `"Jello"` was created, and the original `"Hello"` remained unchanged.

In JavaScript, the term **immutable** means that once a value is created, it **cannot be changed** or modified directly. If you try to alter (change) an immutable value, a new value is created instead, while the original remains unchanged.

### 2. **Non-Primitive Data Types** (Reference Types):
   These are mutable and more complex data structures.
   - **Object**: A collection of key-value pairs. Example: `{ name: "Prashant", age: 25 }`
   - **Array**: A special kind of object used to store ordered lists of values. Example: `[1, 2, 3]`
   - **Function**: A block of code that can be executed when called.
   - **Date**: Represents date and time. Example: `new Date()`.

### Key Point:
- Primitive types are **passed by value**, while non-primitive types (objects, arrays) are **passed by reference**.

---

### Example with Non-Primitive Types (Mutable):
Non-primitive types like **objects** and **arrays** are mutable, meaning they can be modified:

```javascript
let person = { name: "Prashant", age: 25 };
person.age = 26;  // Changing the age property
console.log(person);  // Output: { name: "Prashant", age: 26 }
```

In this case, the `person` object was directly modified.

---

In summary, **immutable** values cannot be changed after they are created, while **mutable** values (like objects) can be modified.

**Let me explain the concepts of **pass by value** and **pass by reference** in JavaScript.**

### 1. **Pass by Value**:
When a variable holding a **primitive data type** (like `number`, `string`, `boolean`, etc.) is passed to a function or assigned to another variable, **only the value** is passed or copied. Changes made to this copied value **do not affect the original variable**.

**Example**:

```javascript
let a = 10;
let b = a;  // 'b' is a copy of 'a'
b = 20;     // Changing 'b' won't affect 'a'

console.log(a);  // Output: 10
console.log(b);  // Output: 20
```

In this example, `b` gets a **copy** of `a`'s value. When `b` is changed, it does **not** affect the original value of `a`, because they are stored separately in memory.

### 2. **Pass by Reference**:
When a variable holding a **non-primitive data type** (like objects or arrays) is passed to a function or assigned to another variable, a **reference** (or memory address) to the original data is passed. This means that **both variables point to the same object in memory**. Any changes made to the new variable will also affect the original variable.

**Example**:

```javascript
let obj1 = { name: "Prashant" };
let obj2 = obj1;  // 'obj2' holds a reference to the same object as 'obj1'
obj2.name = "Kumar";  // Changing 'obj2' affects 'obj1'

console.log(obj1.name);  // Output: "Kumar"
console.log(obj2.name);  // Output: "Kumar"
```

Here, `obj2` holds a reference to the same object in memory as `obj1`. When you change `obj2.name`, it also changes `obj1.name`, because they both point to the same object.

### Key Differences:
- **Pass by value** copies the actual value. Changes to one copy do not affect the other.
- **Pass by reference** passes the memory address. Changes to the reference affect the original object or array.

## **Q5. What is the difference between == (Equality Check) and === (Strict Equality Check) in JavaScript?
###**Answer:** In JavaScript, == checks the equality of values, but === checks the equality of both the values and the type of the value. For example:

```javascript
5 == "5";      // true
5 === "5";   // false
```
### **Q6. What is type coercion in JavaScript?**

**Type coercion** in JavaScript is the process where the JavaScript engine automatically or implicitly converts one data type to another in order to perform operations or comparisons. This happens when different types of values (e.g., strings and numbers) are used together.

There are two types of type coercion:

1. **Implicit Coercion**: This occurs automatically during operations. JavaScript attempts to convert data types to make them compatible with the operation being performed.
   - Example:  
     ```javascript
     console.log(5 + "10"); // "510" (number 5 is coerced to a string, and the result is string concatenation)
     console.log(5 == "5"); // true (the string "5" is coerced to a number before comparison)
     ```

2. **Explicit Coercion**: This happens when the developer intentionally converts a value from one type to another using functions like `Number()`, `String()`, or `Boolean()`.
   - Example:  
     ```javascript
     console.log(Number("10"));  // 10 (string is explicitly converted to a number)
     console.log(String(123));   // "123" (number is explicitly converted to a string)
     ```

#### Why is it important?
Type coercion allows for flexibility in JavaScript, but it can also lead to unexpected results if you're not aware of how it works. For example:
```javascript
console.log(true + 2); // 3 (true is coerced to 1)
console.log(false + "test"); // "falsetest" (false is coerced to a string)
```

## **Q7. What are JavaScript data types? Can you explain the difference between null and undefined?**
###**Answer:** 
**Data types** in JavaScript are a way to categorize data based on the kind of values they hold. JavaScript has two main categories of data types:

1. **Primitive Data Types**: These are immutable, meaning their values cannot be changed.
   - `Number`
   - `String`
   - `Boolean`
   - `Undefined`
   - `Null`
   - `Symbol`
   - `BigInt`

2. **Non-Primitive (Reference) Data Types**: These are mutable, meaning their values can be changed.
   - `Object`
   - `Array`
   - `Function`
   - `Date`, etc.

**Null** vs **Undefined**:
- `null`: Represents the **intentional absence of any value**. It is used when a variable should be empty or have no value.
  - Type: **Object** (This is a known bug in JavaScript but has been left as is for historical reasons).
  
- `undefined`: Indicates that a variable has been **declared but not yet assigned a value**. It is the default value for uninitialized variables.
  - Type: **undefined**

Example:
```javascript
let x;            // x is declared but not assigned a value, so it's undefined
let y = null;     // y is explicitly assigned the value of null, indicating no value
```

## **Q8.How do you convert a variable from one data type to another in JavaScript? Can you provide examples for converting between string, number, and boolean types?**
###**Answer:** 
### Converting Data Types in JavaScript

1. **Number to String**:
   - You can convert a number to a string using:
     - `String()`
     - `toString()` method
     - Template literals (using backticks)
     - Concatenation with an empty string
   - **Examples**:
     ```javascript
     let num = 5;
     let str1 = String(num); // "5"
     let str2 = num.toString(); // "5"
     let str3 = `${num}`; // "5"
     let str4 = num + ''; // "5"
     ```

2. **String to Number**:
   - You can convert a string to a number using:
     - `Number()`
     - `parseInt()` for integers
     - `parseFloat()` for floating-point numbers
   - **Examples**:
     ```javascript
     let str = "5";
     let num1 = Number(str); // 5
     let num2 = parseInt(str); // 5
     let num3 = parseFloat("5.5"); // 5.5
     ```

3. **String to Boolean**:
   - While JavaScript does not have a direct method for converting strings to booleans, you can evaluate the truthiness of a string:
     - An empty string (`""`) is falsy, while a non-empty string (like `"true"`) is truthy.
   - **Example**:
     ```javascript
     let str = "true";
     let bool = Boolean(str); // true
     let emptyStr = "";
     let boolEmpty = Boolean(emptyStr); // false
     ```
### **Note:**
In JavaScript, values are considered **truthy** or **falsy** based on their behavior in a boolean context (like conditions in an `if` statement). Here's a breakdown:

### Falsy Values
These values evaluate to `false` when coerced to a boolean:
1. **`false`** - The boolean value false.
2. **`0`** - The number zero.
3. **`-0`** - The negative zero.
4. **`""`** or **`''`** - An empty string.
5. **`null`** - Represents the absence of a value.
6. **`undefined`** - Indicates that a variable has not been assigned a value.
7. **`NaN`** - Stands for "Not-a-Number", a special value that indicates an invalid number.

### Truthy Values
These values evaluate to `true` when coerced to a boolean:
- Any non-zero number (e.g., `1`, `-1`, `3.14`)
- Any non-empty string (e.g., `"hello"`, `"false"`, `"0"`)
- Any object (including arrays and functions)
- Any array (e.g., `[]`, `[1, 2, 3]`)
- The special value `Infinity` and `-Infinity`

### Examples
Here’s a quick demonstration of how these values behave in conditions:

```javascript
// Falsy values
if (false) console.log('This won’t run.');
if (0) console.log('This won’t run.');
if ("") console.log('This won’t run.');
if (null) console.log('This won’t run.');
if (undefined) console.log('This won’t run.');
if (NaN) console.log('This won’t run.');

// Truthy values
if (1) console.log('This will run.');
if (-1) console.log('This will run.');
if ("hello") console.log('This will run.');
if ([]) console.log('This will run.');
if ({}) console.log('This will run.');
```
## **Q9.How do you convert a variable from one data type to another in JavaScript? Can you provide examples for converting between string, number, and boolean types?**
###**Answer:** 
**Functions in JavaScript** are blocks of reusable code that help make our code more modular and maintainable. There are different ways to define functions:

1. **Function Declaration**:
    ```javascript
    function sumOfTwoNumbers(a, b) {
        return a + b;
    }

    // Function is invoked here
    sumOfTwoNumbers(5, 8); // Output: 13
    ```
    - **Explanation**: This is the most common way to define a function. It’s hoisted, meaning it can be called before its declaration in the code.

2. **Function Expression**:
    ```javascript
    let test = function () {
        console.log('I am a function');
    };

    test(); // Output: I am a function
    ```
    - **Explanation**: In this form, a function is assigned to a variable. It’s not hoisted, so it can only be called after the assignment.

3. **Arrow Function** (introduced in ES6):
    ```javascript
    let testArrowFun = () => {
        console.log('I am a function');
    };

    testArrowFun(); // Output: I am a function
    ```
    - **Explanation**: This is a shorter syntax for function expressions. It’s great for simple functions and has some differences with regular functions, such as not having its own `this`.

## **Q10. What is the difference between function declarations and function expressions in JavaScript? Can you explain how hoisting affects both?**
###**Answer:** 

**Function Declarations**:
- **Hoisting**: Function declarations are fully hoisted in JavaScript. This means the entire function is moved to the top of its scope during the compilation phase. As a result, you can call a function declared this way before it's defined in the code.
    ```javascript
    sayHello(); // Works even though the function is declared later

    function sayHello() {
        console.log('Hello!');
    }
    ```

**Function Expressions**:
- **Hoisting**: Function expressions, unlike declarations, are **not** hoisted. This means the function is only available after the expression is assigned. If you try to call the function before its assignment, you’ll get an error.
    ```javascript
    sayHello(); // Error: sayHello is not a function

    let sayHello = function () {
        console.log('Hello!');
    };
    ```

### Key Difference:
- **Function declarations** are hoisted entirely (including their code block), so you can invoke them before they are declared.
- **Function expressions** are not hoisted because they are treated like any other variable assignment. The variable itself is hoisted, but its value (the function) is not.

## **Q11. What is the purpose of closures in JavaScript? Can you explain with an example?**:  



