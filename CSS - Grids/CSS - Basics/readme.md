# CSS Grid Documentation

## **Overview of CSS Grid**
CSS Grid Layout is a powerful two-dimensional layout system in CSS. It allows for precise control over rows and columns, enabling the creation of responsive and complex web designs. Unlike Flexbox, which is one-dimensional, Grid can manage both horizontal and vertical layouts simultaneously.

---

## **Key Concepts**

### **1. Grid Container**
A **Grid Container** is an element where the `display: grid;` or `display: inline-grid;` property is applied. It establishes a grid context, defining how its child elements (grid items) are laid out.

- **Syntax**:
  ```css
  .container {
      display: grid; /* or inline-grid */
  }
  ```

- **Diagram**:
  ```plaintext
  +-----------------------------------+
  |          Grid Container           |
  | +-----------+ +-----------+ +---+ |
  | | Grid Item | | Grid Item | |...| |
  | +-----------+ +-----------+ +---+ |
  +-----------------------------------+
  ```

### **2. Grid Items**
**Grid Items** are the direct children of the grid container. They can be placed, sized, and aligned within the grid using various properties.

- **Diagram**:
  ```plaintext
  +-------------------------+
  |   Grid Item 1  | Item 2 |
  +-------------------------+
  |         Grid Item 3     |
  +-------------------------+
  ```

---

## **Defining a Grid**

### **3. Grid Tracks**
Grid Tracks are rows and columns in a grid. Use `grid-template-columns` and `grid-template-rows` to define their size.

#### **grid-template-columns**
Defines the width of grid columns.

- **Example**:
  ```css
  .container {
      grid-template-columns: 100px 200px 100px; /* Three columns */
  }
  ```

- **Diagram**:
  ```plaintext
  +-----------+-------------+-----------+
  | Column 1  |  Column 2   | Column 3  |
  +-----------+-------------+-----------+
  ```

#### **grid-template-rows**
Defines the height of grid rows.

- **Example**:
  ```css
  .container {
      grid-template-rows: 100px 50px 150px; /* Three rows */
  }
  ```

- **Diagram**:
  ```plaintext
  +-------------------------+
  |       Row 1 (100px)     |
  +-------------------------+
  |       Row 2 (50px)      |
  +-------------------------+
  |      Row 3 (150px)      |
  +-------------------------+
  ```

---

### **4. Implicit vs Explicit Grid**

- **Explicit Grid**: Rows and columns are explicitly defined using `grid-template-columns` and `grid-template-rows`.

  ```css
  .container {
      grid-template-columns: 1fr 1fr 1fr; /* Three equal columns */
      grid-template-rows: 100px 100px;    /* Two rows */
  }
  ```

- **Implicit Grid**: The browser automatically creates rows or columns for items that don’t fit into the defined grid.

  ```css
  .container {
      grid-template-columns: 1fr 1fr; /* Two columns */
  }
  ```

  Items beyond the defined rows will automatically create new rows.

---

### **5. Grid Gaps**
Defines spacing between rows and columns.

- **Properties**:
  - `row-gap`: Space between rows.
  - `column-gap`: Space between columns.
  - `gap`: Shorthand for both `row-gap` and `column-gap`.

- **Example**:
  ```css
  .container {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      row-gap: 20px;
      column-gap: 15px;
  }
  ```

- **Diagram**:
  ```plaintext
  +--------+   15px   +--------+   15px   +--------+
  |  Item  |          |  Item  |          |  Item  |
  +--------+          +--------+          +--------+
       20px
  +--------+          +--------+          +--------+
  ```

---

### **6. Grid Lines**
Grid lines are the horizontal and vertical lines that divide the grid into cells. They are used to position items with `grid-column` and `grid-row`.

#### **grid-column**
Defines the start and end columns for an item.

- **Example**:
  ```css
  .item {
      grid-column: 1 / 3; /* Start at column 1, span to column 3 */
  }
  ```

#### **grid-row**
Defines the start and end rows for an item.

- **Example**:
  ```css
  .item {
      grid-row: 2 / 4; /* Start at row 2, span to row 4 */
  }
  ```

- **Diagram**:
  ```plaintext
  Grid Layout
  +---+---+---+
  | 1 | 2 | 3 |
  +---+---+---+
  | 4 | 5 | 6 |
  +---+---+---+

  .item (grid-column: 1 / 3)
  +-------+---+
  | Item  |   |
  +-------+---+
  ```

---

### **7. Grid Areas**
Assign names to areas within the grid using `grid-template-areas` and position items by name.

#### Defining Areas:
```css
.container {
    grid-template-areas:
        "header header"
        "sidebar content"
        "footer footer";
}
```

#### Assigning Items:
```css
.header {
    grid-area: header;
}
.sidebar {
    grid-area: sidebar;
}
```

- **Diagram**:
  ```plaintext
  +-------------------+
  |      Header       |
  +-------+-----------+
  | Sidebar | Content |
  +-------+-----------+
  |      Footer       |
  +-------------------+
  ```

---

## **Alignment in Grid**

### **8. justify-content**
Aligns the entire grid along the horizontal (main axis).

- **Values**:
  - `start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`.

---

### **9. align-content**
Aligns the entire grid along the vertical (cross axis).

- **Values**:
  - `start`, `end`, `center`, `space-between`, `space-around`, `space-evenly`.

---

### **10. justify-items and align-items**
- **`justify-items`**: Aligns grid items horizontally inside their cells.
- **`align-items`**: Aligns grid items vertically inside their cells.

---

### **11. Naming Rows and Columns**
You can name grid lines for easier positioning:
```css
.container {
    grid-template-columns: [col-start] 100px [col-middle] 200px [col-end];
}
```

---

### **12. Grid Functions**

- **repeat()**: Repeats columns/rows.
  ```css
  grid-template-columns: repeat(3, 1fr);
  ```

- **minmax()**: Defines minimum and maximum size.
  ```css
  grid-template-columns: minmax(100px, 1fr);
  ```

- **auto-fit / auto-fill**: Automatically adjusts column count.
  ```css
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  ```

---

## **Resources**
- Play CSS Grid game: [CSS Grid Garden](https://cssgridgarden.com/)
- Practice layout: [Grid by Example](https://gridbyexample.com/)

