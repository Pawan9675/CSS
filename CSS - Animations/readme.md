

# **CSS Animations: A Complete Guide**

## **1. Transform**
The `transform` property applies a 2D or 3D transformation to an element. You can move, rotate, scale, or skew elements using this property.

### **Usage:**
- **translate(X, Y)**: Moves an element relative to its current position. 
  - **Example**: `transform: translate(50px, 100px);` moves the element 50 pixels to the right and 100 pixels down.
  
- **scale(X, Y)**: Changes the element’s size. 
  - The default scale is `1` (no change); values less than `1` shrink the element, and values greater than `1` enlarge it. 
  - **Example**: `transform: scale(1.5);` enlarges the element to 150% of its original size.

- **rotate(deg)**: Rotates the element by the specified degree value. 
  - Positive values rotate clockwise, while negative values rotate counterclockwise. 
  - **Example**: `transform: rotate(45deg);` rotates the element 45 degrees clockwise.

- **skew(X, Y)**: Skews the element along the X and/or Y axis. 
  - **Example**: `transform: skewX(30deg);` skews the element 30 degrees along the X-axis.

### **Common Transform Functions:**
| Function          | Description                                      |
|-------------------|--------------------------------------------------|
| `translate(X, Y)` | Moves an element relative to its current position. |
| `scale(X, Y)`     | Changes the element’s size; 1 is default, < 1 shrinks, > 1 enlarges. |
| `rotate(deg)`     | Rotates the element; positive for clockwise, negative for counterclockwise. |
| `skew(X, Y)`      | Distorts the element along the X and/or Y axis. |

### **Examples:**
```css
/* Moves the element 100px to the right */
transform: translateX(100px);

/* Scales the element to 150% of its original size */
transform: scale(1.5);

/* Rotates the element by 45 degrees clockwise */
transform: rotate(45deg);

/* Skews the element 20 degrees on the X axis */
transform: skewX(20deg);
```

### **Demo in Code:**
```css
.moving {
    transform: translateX(50px) scale(1.2) rotate(45deg);
}
```

---

## **2. Transitions**
Transitions allow you to smoothly change CSS properties from one state to another. You can control the **duration**, **timing function**, and **delay** of the transition.

### **Usage:**
- **transition-property**: Defines which CSS properties should change smoothly.
- **transition-duration**: How long the transition should take, specified in seconds (`s`) or milliseconds (`ms`).
- **transition-timing-function**: The speed curve of the transition (e.g., `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`).
- **transition-delay**: How long to wait before starting the transition.

### **Common Transition Properties:**
| Property                  | Description                                      |
|---------------------------|--------------------------------------------------|
| `transition-property`     | Specifies which properties will animate.         |
| `transition-duration`     | Specifies how long the transition should take.   |
| `transition-timing-function` | Controls the pace of animation.              |
| `transition-delay`        | Delays the start of the transition.              |

### **Examples:**
```css
/* Transition on background color change over 2 seconds */
transition: background-color 2s ease-in-out;

/* Transition on all properties, 1-second duration */
transition: all 1s ease-in-out;

/* Transition with a 1s delay */
transition: all 1s ease-in-out 1s;
```

### **Demo in Code:**
```css
.moving:hover {
    background-color: red; /* Changes color on hover */
    transform: rotate(180deg); /* Rotates on hover */
    transition: all 1s ease-in-out; /* Smooth transition */
}
```

---

## **3. Keyframes**
The `@keyframes` rule defines the intermediate steps (or frames) of an animation. You can create complex animations by specifying changes at different percentages of the animation duration.

### **Usage:**
- **animation-name**: The name of the keyframes animation.
- **animation-duration**: How long one cycle of the animation takes.
- **animation-timing-function**: Controls the speed curve of the animation.
- **animation-iteration-count**: How many times to repeat the animation (e.g., `infinite`).
- **animation-delay**: Specifies a delay before the animation starts.
- **animation-direction**: Whether the animation should reverse direction after each cycle (`normal`, `reverse`, `alternate`, `alternate-reverse`).

### **Common Keyframe Properties:**
| Property                   | Description                                      |
|----------------------------|--------------------------------------------------|
| `animation-name`           | Links to the `@keyframes` animation.            |
| `animation-duration`       | Specifies how long the animation should last.    |
| `animation-iteration-count`| Specifies how many times the animation should run (`infinite` for endless looping). |
| `animation-timing-function`| Controls the acceleration/deceleration of the animation. |
| `animation-delay`          | Delays the start of the animation.               |
| `animation-direction`      | Can reverse the animation's direction.           |

### **Example:**
```css
@keyframes moveElement {
    0% { transform: translateX(0); }
    50% { transform: translateX(300px); }
    100% { transform: translateX(0); }
}

.moving {
    animation-name: moveElement;
    animation-duration: 3s;
    animation-iteration-count: infinite; /* Loops forever */
    animation-timing-function: ease-in-out; /* Slow start, fast middle, slow end */
}
```

### **Demo in Code:**
```css
@keyframes exampleAnimation {
    0% { transform: scale(1); }
    50% { transform: scale(1.5); }
    100% { transform: scale(1); }
}

.moving {
    animation-name: exampleAnimation;
    animation-duration: 2s;
    animation-iteration-count: infinite;
    animation-timing-function: ease-in-out;
}
```

---

## **4. Combining Transform, Transition, and Keyframes**
You can combine these properties to create more dynamic and interactive animations.

### **Example:**
```css
.moving {
    width: 50px;
    height: 50px;
    background-color: blue;
    border-radius: 50%;
    transition: transform 1s ease, background-color 1s ease; /* Smooth transitions */
    
    /* Applying keyframe animation */
    animation: moveElement 3s infinite ease-in-out;
}

.moving:hover {
    transform: scale(1.5) rotate(180deg); /* Transforms on hover */
    background-color: red; /* Color change on hover */
}
```

### **Explanation:**
- **Hover**: The element enlarges and rotates smoothly when hovered (`scale` + `rotate`).
- **Keyframes**: It moves across the screen, and the animation repeats forever.
- **Transition**: Smooth transition for color and transformation on hover.

---

## **Important Notes:**
- Always define `animation-duration` to see the effect.
- Use `ease-in` or `ease-out` for more natural animations.
- Keep performance in mind; excessive animations can slow down rendering.
- Test animations across different browsers for compatibility.

---
