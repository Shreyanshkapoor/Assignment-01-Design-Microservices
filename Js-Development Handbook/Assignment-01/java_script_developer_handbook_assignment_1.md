# Assignment-01
# The JavaScript Developer’s Handbook (ES6+)


# Part 1 — The Core Engine (ES6+ Fundamentals)

## Scope & Declaration: var vs let vs const

### Why modern code defaults to `const`
In modern development (especially React), we default to `const` because variables should **not change unless absolutely necessary**. This prevents accidental bugs.

### Bad Way (Old Practice)
```javascript
var count = 10;
if (true) {
  var count = 20; // accidentally overwrites outer variable
}
console.log(count); // 20 (unexpected behavior)
```

### Pro Way (Modern ES6+)
```javascript
let count = 10;
if (true) {
  let count = 20; // separate block scope
}
console.log(count); // 10 (safe)
```

### const Example
```javascript
const API_URL = "https://api.example.com";
// cannot be reassigned -> safer code
```

### Hoisting (Simple Explanation)
Hoisting means JavaScript moves declarations to the top during execution.
- `var` → hoisted and initialized as `undefined`
- `let/const` → hoisted but not initialized (Temporal Dead Zone)

---

## Modern Functions: Traditional vs Arrow Functions

### Bad Way (Traditional Function)
```javascript
function add(a, b) {
  return a + b;
}
```

### Pro Way (Arrow Function)
```javascript
const add = (a, b) => a + b; // implicit return
```

Arrow functions:
- shorter syntax
- automatic return (when single expression)
- lexical `this` (important in React)

---

## Array Mastery — map, filter, reduce

### When to Use
- `map()` → transform data
- `filter()` → select data
- `reduce()` → combine data into single value

### Bad Way (for loop)
```javascript
let doubled = [];
for (let i = 0; i < arr.length; i++) {
  doubled.push(arr[i] * 2);
}
```

### Pro Way (map)
```javascript
const doubled = arr.map(num => num * 2);
```

### filter Example
```javascript
const adults = users.filter(user => user.age >= 18);
```

### reduce Example
```javascript
const total = prices.reduce((sum, price) => sum + price, 0);
```

---

## Objects & Destructuring

### Bad Way
```javascript
const name = user.name;
const age = user.age;
```

### Pro Way
```javascript
const { name, age } = user;
```

### Spread Operator
```javascript
const newUser = { ...user, active: true };
```

### Rest Operator
```javascript
const { id, ...rest } = user;
```

---

# Part 2 — The Interface (DOM Manipulation & Storage)

## Selection & Modification

### getElementById
```javascript
const title = document.getElementById("title");
title.textContent = "Welcome";
```

### querySelector (recommended)
```javascript
const btn = document.querySelector(".btn");
btn.style.background = "blue";
```

`querySelector` works like CSS selectors → more flexible.

---

## Event Handling

```javascript
button.addEventListener("click", () => {
  alert("Button clicked");
});
```

Lifecycle of event:
1. User action occurs
2. Browser detects event
3. Listener executes callback function

---

## Event Bubbling & Delegation

**Analogy:** Imagine a child shouting in a house. The voice travels room → hallway → house. Events travel the same way from child element to parent.

Delegation Example:
```javascript
document.querySelector("ul").addEventListener("click", e => {
  if (e.target.tagName === "LI") {
    console.log("Item clicked");
  }
});
```

This saves performance when many elements exist.

---

## Local Storage (Persistence)

### Save data
```javascript
localStorage.setItem("theme", "dark");
```

### Retrieve data
```javascript
const theme = localStorage.getItem("theme");
```

### Storing Objects
```javascript
localStorage.setItem("user", JSON.stringify(user));
const data = JSON.parse(localStorage.getItem("user"));
```

`JSON.stringify()` → converts object to string
`JSON.parse()` → converts string back to object

---

# Part 3 — The Data Flow (Asynchronous JavaScript)

## Event Loop (Simple Explanation)
JavaScript runs one task at a time. Long tasks (API calls) are sent to Web APIs, and when completed, the **event loop** pushes the result back into the execution queue so the browser never freezes.

---

## Callback Hell (Old Way)
```javascript
login(user, function(){
  getProfile(function(){
    getPosts(function(){
      // nested chaos
    });
  });
});
```

Promises solved this nesting problem.

---

## Async/Await Fetch Tutorial

Reusable Fetch Function:
```javascript
async function fetchData(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) throw new Error("Network error");
    return await response.json();
  } catch (error) {
    console.error(error);
    return null;
  }
}

fetchData("https://jsonplaceholder.typicode.com/posts")
  .then(data => console.log(data));
```

---

## Error Handling (Graceful UI)

If API fails and errors are not handled → app crashes or shows blank screen.

Better UX:
```javascript
const data = await fetchData(url);
if (!data) {
  document.querySelector("#status").textContent = "Server temporarily unavailable. Try again later.";
}
```

This ensures the user always sees feedback instead of broken UI.

---



