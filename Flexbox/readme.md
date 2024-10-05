# Flexbox Documentation

### Overview of Flexbox

**Flexbox**, or the **Flexible Box Layout**, is a CSS layout model designed to provide a more efficient way to align and distribute space among items in a container. This model is particularly useful for building responsive designs, allowing for complex layouts without using floats or positioning.

---

### 1. Flex Containers

A **flex container** is an element that uses the `display: flex;` or `display: inline-flex;` property. It establishes a flex formatting context for its children, known as flex items.

**Characteristics of a Flex Container**:
- **Creates a Flex Formatting Context**: All direct children of the flex container become flex items.
- **Defines the Main and Cross Axes**: 
  - **Main Axis**: The direction in which flex items are laid out (row or column).
  - **Cross Axis**: Perpendicular to the main axis.

**Diagram**:
```
Flex Container
+-------------------------------+
| +--------+ +--------+         |
| | Flex   | | Flex   |         |
| | Item 1 | | Item 2 |         |
| +--------+ +--------+         |
+-------------------------------+
```

### 2. Flex Items

A **flex item** is any direct child of a flex container. These items are laid out according to the rules defined by the flex container.

**Characteristics of Flex Items**:
- **Flexible Sizing**: Flex items can grow or shrink based on available space.
- **Order Control**: You can change the visual order of flex items using the `order` property without altering their order in the source HTML.

**Diagram**:
```
+-------------------------------+
| +--------+ +--------+         |
| | Flex   | | Flex   |         |
| | Item 1 | | Item 2 |         |
| +--------+ +--------+         |
+-------------------------------+
```

---


### Main Axis and Cross Axis

In the Flexbox layout model, understanding the **main axis** and **cross axis** is essential for effectively controlling the alignment and distribution of flex items.

#### 1. Main Axis
The **main axis** is the primary direction along which flex items are laid out. It is determined by the `flex-direction` property. Depending on its value, the main axis can be horizontal or vertical.

- **Values of `flex-direction`**:
  - `row`: Main axis is horizontal (left to right).
  - `row-reverse`: Main axis is horizontal (right to left).
  - `column`: Main axis is vertical (top to bottom).
  - `column-reverse`: Main axis is vertical (bottom to top).

**Diagram**:
```
flex-direction: row;
+-----------------------------+
| Main Axis (→)               |
| Flex Item 1 | Flex Item 2   |
+-----------------------------+

flex-direction: column;
+-----------------+
|   Main Axis (↓) |
|   Flex Item 1   |
|   Flex Item 2   |
+-----------------+
```

#### 2. Cross Axis
The **cross axis** is the direction perpendicular to the main axis. It provides a way to align items that run across the main axis.

- For `flex-direction: row`, the cross axis is vertical.
- For `flex-direction: column`, the cross axis is horizontal.

**Diagram**:
```
flex-direction: row;
+-----------------------------+
|                             |
| Cross Axis (↑↓)             |
| Flex Item 1                 |
| Flex Item 2                 |
|                             |
+-----------------------------+

flex-direction: column;
+-----------------+
|                 |
| Cross Axis (←→) |
| Flex Item 1     |
|                 |
| Flex Item 2     |
|                 |
+-----------------+
```

## Flex Container Properties

### 1. display
The **display** property in CSS specifies how an element is displayed on the web page. When used in Flexbox, it defines an element as a flex container, affecting how its direct children (flex items) are arranged.

#### Values of `display` for Flexbox:

1. **display: flex;**
   - Creates a block-level flex container. This means the container takes up the full width available and can contain multiple flex items arranged according to flex properties.

   **Diagram**:
   ```
   +------------------------------------------+
   |          Flex Container                  |
   | +---------+ +---------+ +---------+      |
   | | Flex    | | Flex    | | Flex    |      |
   | | Item 1  | | Item 2  | | Item 3  |      |
   | +---------+ +---------+ +---------+      |
   +------------------------------------------+
   ```

2. **display: inline-flex;**
   - Creates an inline-level flex container. This means the container only takes up as much width as necessary, allowing other elements to sit beside it on the same line.

   **Diagram**:
   ```
   +--------+ +----------------------------+
   | Flex   | | Flex Container             |
   | Item 1 | | +---------+ +---------+    |
   |        | | | Flex    | | Flex    |    |
   |        | | | Item 2  | | Item 3  |    |
   |        | | +---------+ +---------+    |
   +--------+ +----------------------------+
   ```

---

### 2. flex-direction

The **flex-direction** property in Flexbox defines the direction in which the flex items are placed inside the flex container. It determines the main axis (the axis along which the items are aligned) and how items are ordered.

#### Values of `flex-direction`:

1. **row** (default):
   - Flex items are laid out in a row, from left to right (in left-to-right writing modes).
   
   **Diagram**:
   ```
   +------------------------------------------+
   | +---------+ +---------+ +---------+      |
   | | Flex    | | Flex    | | Flex    |      |
   | | Item 1  | | Item 2  | | Item 3  |      |
   | +---------+ +---------+ +---------+      |
   +------------------------------------------+
   Main Axis → (left to right)
   ```

2. **row-reverse**:
   - Flex items are laid out in a row, but in reverse order, from right to left.
   
   **Diagram**:
   ```
   +------------------------------------------+
   |     +---------+ +---------+ +---------+  |
   |     | Flex    | | Flex    | | Flex    |  |
   |     | Item 3  | | Item 2  | | Item 1  |  |
   |     +---------+ +---------+ +---------+  |
   +------------------------------------------+
   Main Axis → (right to left)
   ```

3. **column**:
   - Flex items are laid out in a column, from top to bottom.
   
   **Diagram**:
   ```
   +---------+
   | Flex    |
   | Item 1  |
   +---------+
   | Flex    |
   | Item 2  |
   +---------+
   | Flex    |
   | Item 3  |
   +---------+
   Main Axis ↓ (top to bottom)
   ```

4. **column-reverse**:
   - Flex items are laid out in a column, but in reverse order, from bottom to top.
   
   **Diagram**:
   ```
   +---------+
   | Flex    |
   | Item 3  |
   +---------+
   | Flex    |
   | Item 2  |
   +---------+
   | Flex    |
   | Item 1  |
   +---------+
   Main Axis ↓ (bottom to top)
   ```

---

### 3. flex-wrap

The **flex-wrap** property in Flexbox controls whether the flex items should wrap onto multiple lines when there is not enough space within the flex container. By default, flex items are laid out in a single line, but with **flex-wrap**, they can be arranged in multiple rows or columns.

#### Values of `flex-wrap`:

1. **nowrap** (default):
   - Flex items are forced to stay on a single line, no matter how much space is available.
   
   **Diagram**:
   ```
   +------------------------------------------+
   | +---------+ +---------+ +---------+      |
   | | Flex    | | Flex    | | Flex    |      | 
   | | Item 1  | | Item 2  | | Item 3  |      |  
   | +---------+ +---------+ +---------+      |
   +------------------------------------------+
   ```

2. **wrap**:
   - Flex items will wrap onto multiple lines if there isn't enough space on one line. Items will wrap onto a new line below (in **row** layout) or to the right (in **column** layout).
   
   **Diagram** (for `flex-direction: row`):
   ```
   +------------------------------------------+
   | +---------+ +---------+ +---------+      |
   | | Flex    | | Flex    | | Flex    |      |  (Row 1)
   | | Item 1  | | Item 2  | | Item 3  |      |
   | +---------+ +---------+ +---------+      |
   +------------------------------------------+
   | +---------+ +---------+                  |  (Row 2)
   | | Flex    | | Flex    |                  |
   | | Item 4  | | Item 5  |                  |
   | +---------+ +---------+                  |
   +------------------------------------------+
   ```

3. **wrap-reverse**:
   - Flex items will wrap onto multiple lines, but in reverse order. In **row** layout, the new line of items will appear above the previous line, and in **column** layout, to the left of the previous column.
   
   **Diagram** (for `flex-direction: row`):
   ```
   +------------------------------------------+
   | +---------+ +---------+                  |  (Row 2)
   | | Flex    | | Flex    |                  |
   | | Item 4  | | Item 5  |                  |
   | +---------+ +---------+                  |
   +------------------------------------------+
   | +---------+ +---------+ +---------+      |  (Row 1)
   | | Flex    | | Flex    | | Flex    |      |
   | | Item 1  | | Item 2  | | Item 3  |      |
   | +---------+ +---------+ +---------+      |
   +------------------------------------------+
   ```

---

### 4. justify-content

The **justify-content** property in Flexbox defines how flex items are aligned along the **main axis** (horizontal in a row layout, vertical in a column layout) within a flex container. It controls the distribution of space between and around the flex items.

#### Values of `justify-content`:

1. **flex-start** (default):
   - Items are packed toward the start of the main axis.

   **Diagram**:
   ```
   +------------------------------------------------+
   | +---------+ +---------+ +---------+            |
   | | Flex    | | Flex    | | Flex    |            |
   | | Item 1  | | Item 2  | | Item 3  |            |
   | +---------+ +---------+ +---------+            |
   +------------------------------------------------+
   ```

2. **flex-end**:
   - Items are packed toward the end of the main axis.

   **Diagram**:
   ```
   +----------------------------------------------------+
   |                +---------+ +---------+ +---------+ |
   |                | Flex    | | Flex    | | Flex    | |
   |                | Item 1  | | Item 2  | | Item 3  | |
   |                +---------+ +---------+ +---------+ |
   +----------------------------------------------------+
   ```

3. **center**:
   - Items are centered along the main axis.

   **Diagram**:
   ```
   +---------------------------------------------------------+
   |           +---------+ +---------+ +---------+           |
   |           | Flex    | | Flex    | | Flex    |           |
   |           | Item 1  | | Item 2  | | Item 3  |           |
   |           +---------+ +---------+ +---------+           |
   +---------------------------------------------------------+
   ```

4. **space-between**:
   - Items are evenly distributed, with the first item aligned to the start and the last item aligned to the end, with equal space between them.

   **Diagram**:
   ```
   +-------------------------------------------------------+
   |+---------+           +---------+           +---------+|
   || Flex    |           | Flex    |           | Flex    ||
   || Item 1  |           | Item 2  |           | Item 3  ||
   |+---------+           +---------+           +---------+|
   +-------------------------------------------------------+
   ```

5. **space-around**:
   - Items are evenly distributed with equal space around them. The space between items is larger than the space on the edges.

   **Diagram**:
   ```
   +----------------------------------------------------+
   |   +---------+      +---------+      +---------+    |
   |   | Flex    |      | Flex    |      | Flex    |    |
   |   | Item 1  |      | Item 2  |      | Item 3  |    |
   |   +---------+      +---------+      +---------+    |
   +----------------------------------------------------+
   ```

6. **space-evenly**:
   - Items are distributed with equal space between them and also between the edges and the items.

   **Diagram**:
   ```
   +---------------------------------------------+
   |   +---------+   +---------+   +---------+   |
   |   | Flex    |   | Flex    |   | Flex    |   |
   |   | Item 1  |   | Item 2  |   | Item 3  |   |
   |   +---------+   +---------+   +---------+   |
   +---------------------------------------------+
   ```

---

### 5. align-items
The `align-items` property determines how flex items are aligned along the cross axis (perpendicular to the main axis) within a flex container. The main axis can be horizontal or vertical, depending on the `flex-direction` property.

#### Values of `align-items`:

1. **align-items: flex-start :**
- Flex items are aligned at the **start** of the cross axis (top for rows).


```
+--------------------------------------+
| +--------+  +--------+  +--------+   |
| | Item 1 |  | Item 2 |  | Item 3 |   |
| +--------+  +--------+  +--------+   |
|                                      |
|                                      |
+--------------------------------------+
Main Axis (Row) -> Horizontal
Cross Axis (Column) -> Vertical
```

---

2. **align-items: flex-end:**
- Flex items are aligned at the **end** of the cross axis (bottom for rows).

```
+--------------------------------------+
|                                      |
|                                      |
| +--------+  +--------+  +--------+   |
| | Item 1 |  | Item 2 |  | Item 3 |   |
| +--------+  +--------+  +--------+   |
+--------------------------------------+
Main Axis (Row) -> Horizontal
Cross Axis (Column) -> Vertical
```

---

3. **align-items: center:**
- Flex items are **centered** along the cross axis.

```
+----------------------------------------------+
|                                              |
|      +--------+  +--------+  +--------+      |
|      | Item 1 |  | Item 2 |  | Item 3 |      |
|      +--------+  +--------+  +--------+      |
|                                              |
+----------------------------------------------+
Main Axis (Row) -> Horizontal
Cross Axis (Column) -> Vertical
```

---

4. **align-items: stretch:**
- Flex items stretch to fill the container along the cross axis. If no height is set, they expand to fill the full height of the container.

```
+------------------------------------+
| +--------+  +--------+  +--------+ |
| |        |  |        |  |        | |
| | Item 1 |  | Item 2 |  | Item 3 | |
| |        |  |        |  |        | |
| +--------+  +--------+  +--------+ |
+------------------------------------+
Main Axis (Row) -> Horizontal
Cross Axis (Column) -> Vertical
```

---

5. **align-items: baseline:**
- In `align-items: baseline`, flex items are aligned based on the baseline of their content, typically the bottom of the text inside them. This means items with varying text heights or content will align along the same text baseline.


![](https://media.geeksforgeeks.org/wp-content/uploads/20210329114720/Baselinealignment.PNG)


---

### 6. flex-flow
Shorthand for `flex-direction` and `flex-wrap`.

- **Example**:
```css
.container {
  flex-flow: row wrap; /* Items arranged in a row that can wrap */
}
```

**Diagram**:
```
flex-flow: row wrap;
+---------------------+----------+
| Flex Item 1 | Flex Item 2      |
+---------------------+----------+
| Flex Item 3                    |
+---------------------+----------+
```

---

### Additional Examples

#### 1. `flex-flow: row nowrap;`
- **Example**:
```css
.container {
  flex-flow: row nowrap; /* Items arranged in a row that will not wrap */
}
```
**Diagram**:
```
flex-flow: row nowrap;
+------------------------------------------+
| Flex Item 1 | Flex Item 2 | Flex Item 3  |
+------------------------------------------+
```

---

#### 2. `flex-flow: column wrap;`
- **Example**:
```css
.container {
  flex-flow: column wrap; /* Items arranged in a column that can wrap */
}
```
**Diagram**:
```
flex-flow: column wrap;
+---------------------------+
| Flex Item 1               |
+---------------------------+
| Flex Item 2               |
+---------------------------+
| Flex Item 3 | Flex Item 4 |
+---------------------------+
```

---

### 7. Align Content
The `align-content` property in Flexbox is used to define how the space between flex lines is distributed in a flex container when there are multiple lines of items.

#### Values of `align-content`:

1. **flex-start**:
   - Flex lines are packed toward the **start** of the cross axis (top for horizontal layout).
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: flex-start;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: flex-start;
   +-----------------------------------+
   | +--------+  +--------+            |
   | | Item 1 |  | Item 2 |            |
   | +--------+  +--------+            |
   | +--------+  +--------+            |
   | | Item 3 |  | Item 4 |            |
   | +--------+  +--------+            |
   |                                   |
   |                                   |
   |                                   |
   |                                   |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---

2. **flex-end**:
   - Flex lines are packed toward the **end** of the cross axis (bottom for horizontal layout).
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: flex-end;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: flex-end;
   +-----------------------------------+
   |                                   |
   |                                   |
   |                                   |
   | +--------+  +--------+            |
   | | Item 1 |  | Item 2 |            |
   | +--------+  +--------+            |
   | +--------+  +--------+            |
   | | Item 3 |  | Item 4 |            |
   | +--------+  +--------+            |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---

3. **center**:
   - Flex lines are **centered** in the cross axis.
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: center;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: center;
   +-----------------------------------+
   |                                   |
   |            +--------+             |
   |            | Item 1 |             |
   |            +--------+             |
   |            +--------+             |
   |            | Item 2 |             |
   |            +--------+             |
   |                                   |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---

4. **space-between**:
   - Flex lines are evenly distributed, with the first line at the start and the last line at the end.
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: space-between;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: space-between;
   +-----------------------------------+
   | +--------+                        |
   | | Item 1 |                        |
   | +--------+                        |
   |                                   |
   | +--------+                        |
   | | Item 2 |                        |
   | +--------+                        |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---

5. **space-around**:
   - Flex lines are distributed with equal space around them.
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: space-around;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: space-around;
   +-----------------------------------+
   |                                   |
   |           +--------+              |
   |           | Item 1 |              |
   |           +--------+              |
   |                                   |
   |                                   |
   |           +--------+              |
   |           | Item 2 |              |
   |           +--------+              |
   |                                   |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---

6. **space-evenly**:
   - Flex lines are distributed with equal space between them and at the edges.
   
   **Example**:
   ```css
   .container {
     display: flex;
     flex-wrap: wrap;
     align-content: space-evenly;
   }
   ```

   **ASCII Diagram**:
   ```
   align-content: space-evenly;
   +-----------------------------------+
   |          +--------+               |
   |          | Item 1 |               | 
   |          +--------+               |
   |                                   |
   |          +--------+               |
   |          | Item 2 |               |
   |          +--------+               |
   +-----------------------------------+
   Main Axis: Horizontal
   Cross Axis: Vertical
   ```

---


## Flex Item Properties

### 1. flex-grow

Defines the ability of a flex item to grow relative to the other flex items in the container when there is available space.

- **Values**: A unitless number (default is `0`), where:
  - **0**: The item will not grow.
  - Any positive number: The item will grow relative to others with non-zero values.

**Example**:
```css
.flex-item-1 {
  flex-grow: 1; /* This item will grow */
}
.flex-item-2 {
  flex-grow: 2; /* This item will grow twice as much as flex-item-1 */
}
.flex-item-3 {
  flex-grow: 0; /* This item will not grow */
}
```

### Explanation:
- **Flex Item 1** will take up an equal part of the available space because it has a `flex-grow` value of `1`.
- **Flex Item 2** will take up twice as much space compared to Flex Item 1 because it has a `flex-grow` value of `2`.
- **Flex Item 3** will not grow at all, retaining its original size since its `flex-grow` value is `0`.

---

### 2. flex-shrink
Defines the ability of a flex item to shrink relative to the rest of the items in a flex container when there isn't enough space.

- **Values**: A number (default is 1). A higher number means the item will shrink more compared to others.

**Example**:
```css
.container {
  display: flex;
}

.item1 {
  flex-shrink: 1; /* This item will shrink */
}

.item2 {
  flex-shrink: 2; /* This item will shrink more than item1 */
}

.item3 {
  flex-shrink: 0; /* This item will not shrink */
}
```

---

### 3. flex-basis
Defines the default size of a flex item before any space distribution happens. It can be set to a specific length (like pixels or percentages) or left as `auto`, which allows the item to size itself based on its content.

- **Values**: Any valid CSS length unit, or `auto`.

**Example**:
```css
.container {
  display: flex;
}

.item1 {
  flex-basis: 200px; /* This item will have a base size of 200px */
}

.item2 {
  flex-basis: 50%; /* This item will take 50% of the container's size */
}

.item3 {
  flex-basis: auto; /* This item will size itself based on its content */
}
```
---

### 4. align-self

The `align-self` property in CSS Flexbox is used to specify the alignment of a flex item along the cross axis, overriding the default alignment set by the `align-items` property for that specific item. This property allows for greater flexibility in positioning individual items within a flex container. Overrides the `align-items` value for a specific flex item.


#### Syntax
```css
align-self: <value>;
```

### Possible Values

1. **`auto`**:
   - This value sets the `align-self` property to the default alignment of the flex container, which is determined by the `align-items` property. 
   - If no `align-items` value is set, it defaults to `stretch`.

   **Example**:
   ```css
   .item {
       align-self: auto;
   }
   ```

2. **`flex-start`**:
   - Aligns the flex item at the start of the cross axis. 
   - For a row-based flex container, it means the top of the container; for a column-based flex container, it means the left side.

   **Example**:
   ```css
   .item {
       align-self: flex-start;
   }
   ```

   **Diagram**:
   ```
   +-----------------------+
   | +--------+            |
   | | Item 1 |            | (flex-start)
   | +--------+            |
   |                       |
   |                       |
   |                       |
   +-----------------------+
   ```

3. **`flex-end`**:
   - Aligns the flex item at the end of the cross axis. 
   - For a row-based container, this means the bottom; for a column-based container, it means the right side.

   **Example**:
   ```css
   .item {
       align-self: flex-end;
   }
   ```

   **Diagram**:
   ```
   +-----------------------+
   |                       |
   |                       |
   | +--------+            | (flex-end)
   | | Item 1 |            |
   | +--------+            |
   +-----------------------+
   ```

4. **`center`**:
   - Centers the flex item along the cross axis.

   **Example**:
   ```css
   .item {
       align-self: center;
   }
   ```

   **Diagram**:
   ```
   +-----------------------+
   |                       |
   |      +--------+       | (center)
   |      | Item 1 |       |
   |      +--------+       |
   |                       |
   +-----------------------+
   ```

5. **`baseline`**:
   - Aligns the flex item along the baseline of the text content. If the item doesn't have any text, it behaves like `flex-start`.

   **Example**:
   ```css
   .item {
       align-self: baseline;
   }
   ```

   **Diagram**:
   ```
   +------------------------------+
   |  +--------+                  |   (baseline)
   |  | Item 1 |                  |
   |  +--------+                  |
   |                              |
   |                              |
   |                              |
   +------------------------------+
   ```


6. **`stretch`**:
   - This is the default value if `align-items` is not set to a specific value. The flex item will stretch to fill the container along the cross axis.

   **Example**:
   ```css
   .item {
       align-self: stretch;
   }
   ```

   **Diagram**:
   ```
   +-----------------------+
   | +--------+            |
   | |        |            | (stretch)
   | | Item 1 |            |
   | |        |            |
   | +--------+            |
   +-----------------------+
   ```
---

### 5. `min-width` and `max-width`
These properties define the minimum and maximum width of a flex item, respectively, allowing for responsive design and layout control.

- **`min-width`**: This property sets the minimum width of a flex item. If the content exceeds this width, the item will not shrink below this value. This ensures that important content remains visible.

- **`max-width`**: This property sets the maximum width of a flex item. If the content is less than this width, the item will not grow beyond this value, allowing for better control over layout in various screen sizes.

**Example**:
```css
.item {
    min-width: 100px; /* Minimum width of 100 pixels */
    max-width: 300px; /* Maximum width of 300 pixels */
}
```

**Use Cases**:
- Setting `min-width` is particularly useful when you want to ensure that a flex item maintains its readability or usability regardless of the screen size.
- `max-width` is helpful in preventing items from becoming excessively wide on larger screens, which can improve the overall aesthetic and usability of the layout.

---


### Learn Flexbox with an Interactive Game

If you'd like to practice and solidify your understanding of Flexbox concepts, try out **[Flexbox Froggy](https://flexboxfroggy.com/)** – a fun and interactive game to learn Flexbox by helping Froggy and his friends!


