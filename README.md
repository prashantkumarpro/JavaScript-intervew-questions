**# JavaScript-intervew-questions**

** Let's start:**

**## Q1: Can you explain the difference between `var`, `let`, and `const` in JavaScript?**

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

**## Q2: Can you explain hoisting in JavaScript, specifically in the context of var, let, and const?**

**Answer:** Sure! Let's break down **hoisting** in JavaScript and how it works with `var`, `let`, and `const`.
---

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

 
**## Q: What are the different data types in JavaScript?**
  
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


