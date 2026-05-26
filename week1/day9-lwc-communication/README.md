# Day 9 – LWC Component Communication

## Overview

This project demonstrates communication between Lightning Web Components (LWC) using custom events. A child component sends events to a parent component, allowing the parent to update and display data dynamically. The application includes controls for incrementing, decrementing, and multiplying a counter value.

---

## Component Communication

Lightning Web Components support communication through:

### 1. Child to Parent Communication
A child component dispatches a custom event that is handled by the parent component.

Example:

```javascript
this.dispatchEvent(new CustomEvent('add'));
```

The parent listens for the event:

```html
<c-controls onadd={handleIncrement}></c-controls>
```

### 2. Parent to Child Communication
A parent component can communicate with a child component using public properties and methods decorated with `@api`.

Example:

```javascript
@api message;
```

### 3. Unrelated Component Communication
Components that do not share a parent-child relationship can communicate using Lightning Message Service (LMS).

---

## Dashboard Design

The dashboard consists of two main components:

### Numerator Component
- Displays the current counter value.
- Handles increment, decrement, and multiply actions.
- Receives custom events from the Controls component.

### Controls Component
- Provides buttons for user interaction.
- Dispatches custom events:
  - Add
  - Subtract
  - Multiply

### User Interface

```
+---------------------+
|      Numerator      |
|     Count: 10       |
+---------------------+

+---------------------+
|      Controls       |
| Subtract  2  3 Add  |
+---------------------+
```

The layout is simple, responsive, and follows Salesforce Lightning Design System (SLDS) standards.

---

## Data Flow Explanation

### Increment Flow

1. User clicks Add button.
2. Controls component dispatches `add` event.
3. Numerator component receives event.
4. `handleIncrement()` executes.
5. Counter value increases.

### Decrement Flow

1. User clicks Subtract button.
2. Controls component dispatches `subtract` event.
3. Numerator component receives event.
4. `handleDecrement()` executes.
5. Counter value decreases.

### Multiply Flow

1. User clicks multiplication button.
2. Controls component reads factor value.
3. Controls component dispatches `multiply` event with detail data.
4. Numerator component receives event.
5. Counter is multiplied by the selected factor.

Example:

```javascript
new CustomEvent('multiply', {
    detail: factor
});
```

Parent receives:

```javascript
handleMultiply(event) {
    const factor = event.detail;
    this.counter *= factor;
}
```

---

## Aura vs LWC

| Feature | Aura Components | Lightning Web Components |
|----------|----------------|--------------------------|
| Performance | Slower | Faster |
| Standards | Proprietary Framework | Web Standards |
| Learning Curve | Moderate | Easier |
| JavaScript Support | Limited | Modern JavaScript |
| Development Experience | Complex | Simple |
| Reusability | Good | Excellent |
| Rendering Speed | Lower | Higher |

### Advantages of LWC

- Better performance
- Modern JavaScript support
- Lightweight framework
- Faster rendering
- Easier debugging
- Improved maintainability

---

## Reflection

This project provided practical experience with Lightning Web Component communication patterns. I learned how custom events enable child-to-parent communication and how event data can be passed using the `detail` property. I also understood the importance of component reusability, event handling, and clean UI design using Salesforce Lightning Design System.

Key takeaways:

- Creating and dispatching custom events
- Handling events in parent components
- Passing data between components
- Understanding event bubbling
- Building reusable Lightning Web Components
- Comparing Aura Components with Lightning Web Components

This exercise strengthened my understanding of component-based architecture and event-driven development in Salesforce.
