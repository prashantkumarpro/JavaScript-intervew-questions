# JavaScript-intervew-questions

 Let's start:

### Interviewer: Can you explain the difference between `var`, `let`, and `const` in JavaScript?
Answer:
- **`var`** is function-scoped, meaning it is accessible throughout the function where it's declared. It can also be re-declared and re-assigned, but it leads to issues like **hoisting** and **unexpected behaviors** due to its scope.
- **`let`** is block-scoped, so it's only accessible within the block where it is declared (e.g., within an `if` statement or loop). You can re-assign `let`, but not re-declare it within the same scope.
- **`const`** is also block-scoped like `let`, but it **cannot be re-assigned** after its initial assignment. However, if the `const` holds an object or array, you can still modify the contents of that object or array.
