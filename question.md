# Frontend Interview Questions

A practical collection of common and intermediate frontend interview questions with clear, concise answers.  
Covers the core topics most companies ask about: HTML, CSS, JavaScript, React, browser behavior, performance, and accessibility.

Feel free to fork, expand, or use this as a study guide.

## Table of Contents
- [HTML](#html)
- [CSS](#css)
- [JavaScript](#javascript)
- [React](#react)
- [Browser & Performance](#browser--performance)
- [Accessibility](#accessibility)

---

## HTML

### 1. What is the purpose of `<!DOCTYPE html>`?
It tells the browser to render the page in standards mode. Without it, many browsers fall into quirks mode, which can cause inconsistent box model and layout behavior.

### 2. What are semantic HTML elements and why do they matter?
Semantic elements (`<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<button>`, `<form>`, etc.) describe the meaning of the content rather than just its appearance. They improve accessibility (screen readers), SEO, and code maintainability.

### 3. What’s the difference between `<button>` and a clickable `<div>`?
A native `<button>` is keyboard-accessible by default, has built-in focus styles, and works with form submission. A `<div>` requires extra ARIA attributes and JavaScript to become accessible.

### 4. How do you make a form accessible?
- Associate every input with a `<label>` (using `for`/`id` or by nesting).
- Use appropriate `type` attributes.
- Provide clear error messages.
- Use `<fieldset>` + `<legend>` for groups of related controls.

---

## CSS

### 1. Explain the CSS box model.
Every element is a rectangular box consisting of:
- **Content**
- **Padding**
- **Border**
- **Margin**

With the default `box-sizing: content-box`, `width`/`height` only apply to the content. With `box-sizing: border-box` (recommended), they include padding and border.

### 2. How does CSS specificity work?
Specificity is calculated as a tuple of (inline styles, IDs, classes/attributes/pseudo-classes, elements/pseudo-elements). Higher specificity wins. In case of a tie, the later rule in the stylesheet wins. `!important` overrides normal specificity.

### 3. When would you use Flexbox vs CSS Grid?
- **Flexbox**: One-dimensional layouts (rows or columns), alignment, distribution of space.
- **Grid**: Two-dimensional layouts (rows *and* columns simultaneously), complex page or component structures.

### 4. What creates a new stacking context?
Common triggers: `position` + `z-index` (not auto), `opacity` < 1, `transform`, `filter`, `will-change`, `isolation: isolate`, and flex/grid items with `z-index`.

### 5. How do you center a div both horizontally and vertically?
Common modern approaches:
- Flexbox: `display: flex; align-items: center; justify-content: center;`
- Grid: `display: grid; place-items: center;`

---

## JavaScript

### 1. What’s the difference between `var`, `let`, and `const`?
- `var`: Function-scoped, hoisted (initialized as `undefined`), can be redeclared.
- `let` / `const`: Block-scoped, not hoisted in the same way (temporal dead zone), cannot be redeclared in the same scope. `const` cannot be reassigned (but objects/arrays it holds can be mutated).

### 2. Explain closures.
A closure is a function that retains access to its lexical scope even after the outer function has finished executing. Common uses: data privacy, function factories, event handlers, and module patterns.

### 3. How does the JavaScript event loop work?
Call stack → Web APIs / Node APIs → Task queues (macrotasks) and microtask queue.  
After the call stack is empty, the event loop processes all microtasks (Promises, queueMicrotask), then one macrotask (setTimeout, setInterval, I/O), then repeats. Rendering can happen between macrotasks.

### 4. What’s the difference between `==` and `===`?
`==` performs type coercion before comparison. `===` is strict equality (no coercion). Prefer `===` in almost all cases.

### 5. Explain `this` in JavaScript.
`this` is determined by how a function is called:
- Method call → the object
- Simple function call → `undefined` (strict mode) or global object
- Arrow functions → lexical `this` from the enclosing scope
- `call`/`apply`/`bind` → explicit value
- Constructor → the new object

### 6. What are Promises and how do `async/await` relate to them?
A Promise represents a future value (pending → fulfilled or rejected). `async/await` is syntactic sugar over Promises that lets you write asynchronous code in a more synchronous style. `await` only works inside `async` functions and pauses execution until the Promise settles.

---

## React

### 1. What is the Virtual DOM and how does React use it?
React maintains a lightweight in-memory representation of the UI (Virtual DOM). On state changes it creates a new Virtual DOM tree, diffs it against the previous one (reconciliation), and applies only the minimal real DOM updates.

### 2. Why are keys important in lists?
Keys help React identify which items have changed, been added, or removed. Stable, unique keys (ideally IDs) prevent unnecessary remounts and bugs with component state. Avoid using array indexes as keys when the list can reorder or filter.

### 3. What’s the difference between `useState` and `useReducer`?
- `useState`: Simple state updates (primitives or simple objects).
- `useReducer`: More complex state logic, multiple related values, or when the next state depends on the previous one in a structured way. Often preferred for larger components or shared state logic.

### 4. Rules of Hooks — why can’t they be called conditionally?
Hooks must be called in the same order on every render so React can correctly associate state and effects with the component. Conditional or looped calls break that guarantee and lead to bugs.

### 5. What does `useEffect` do and what are common pitfalls?
`useEffect` runs side effects after render. The dependency array controls when it re-runs. Common pitfalls: missing dependencies, infinite loops, and not cleaning up subscriptions/timers.

---

## Browser & Performance

### 1. What are Core Web Vitals?
Google’s key user-experience metrics:
- **LCP** (Largest Contentful Paint) — loading performance
- **INP** (Interaction to Next Paint) — interactivity
- **CLS** (Cumulative Layout Shift) — visual stability

### 2. What is the critical rendering path?
The sequence the browser follows to turn HTML, CSS, and JavaScript into pixels: HTML parsing → DOM, CSS parsing → CSSOM, combining into Render Tree, Layout, Paint, and Composite.

### 3. How can you improve frontend performance?
- Code splitting and lazy loading
- Image optimization (modern formats, proper sizing, lazy loading)
- Minimizing main-thread work
- Caching strategies
- Reducing layout thrashing and unnecessary re-renders
- Using a CDN

---

## Accessibility

### 1. Why is accessibility important?
It ensures people with disabilities can use your application. It also improves SEO, keyboard usability, and overall code quality. Legal requirements (WCAG) apply in many regions.

### 2. Key practices for accessible frontend code
- Use semantic HTML first.
- Ensure sufficient color contrast.
- Make everything keyboard-operable.
- Provide text alternatives for images.
- Manage focus properly (especially in modals and SPAs).
- Use ARIA only when native HTML isn’t sufficient.

---

## Contributing
Feel free to open issues or pull requests to add more questions, improve answers, or add code examples.

## License
MIT