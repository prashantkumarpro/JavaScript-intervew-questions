**# JavaScript-intervew-questions**

** Let's start:**

**### Q1: Can you explain the difference between `var`, `let`, and `const` in JavaScript?**

**Answer:**
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
- 
**### Q2: What are the different data types in JavaScript?**
  
**Answer**
  Your answer is mostly correct, but there's room for improvement and clarification. Here's a refined version with more detail:

---


In JavaScript, there are two main categories of data types: **primitive** and **non-primitive** (or reference types).

### 1. **Primitive Data Types**:
   These are the basic data types that are immutable, meaning their values cannot be altered.
   - **Number**: Represents both integer and floating-point numbers. Example: `42`, `3.14`
   - **String**: Represents text or sequences of characters. Example: `"Hello"`, `'World'`
   - **Boolean**: Represents a logical entity with two values: `true` or `false`.
   - **Undefined**: A variable that has been declared but not assigned a value yet.
   - **Null**: Represents the intentional absence of any value.
   - **BigInt**: Used for very large integers that exceed the safe integer limit. Example: `123n`
   - **Symbol**: Used to create unique and immutable values, often used as object keys.

### 2. **Non-Primitive Data Types** (Reference Types):
   These are mutable and more complex data structures.
   - **Object**: A collection of key-value pairs. Example: `{ name: "Prashant", age: 25 }`
   - **Array**: A special kind of object used to store ordered lists of values. Example: `[1, 2, 3]`
   - **Function**: A block of code that can be executed when called.
   - **Date**: Represents date and time. Example: `new Date()`.

### Key Point:
- Primitive types are **passed by value**, while non-primitive types (objects, arrays) are **passed by reference**.

---
In JavaScript, the term **immutable** means that once a value is created, it **cannot be changed** or modified directly. If you try to alter an immutable value, a new value is created instead, while the original remains unchanged.

### Example with Primitive Types (Immutable):
Primitive data types like `number`, `string`, `boolean`, `null`, `undefined`, `symbol`, and `bigInt` are immutable. Here's an example:

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

This concept is important for working with objects and arrays in JavaScript, as modifying one reference affects all references to the same object.

Let me know if you need more examples or clarification!
