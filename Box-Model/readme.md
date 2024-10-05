# CSS Box Model

In CSS, the **box model** represents the structure and layout of elements on a webpage. Every element on a web page is essentially a rectangular box, and the box model defines the space taken up by the element, which includes its:

1. **Content**: The actual content inside the box (like text, images, etc.).
2. **Padding**: Space between the content and the border.
3. **Border**: The border surrounding the padding.
4. **Margin**: Space outside the border, which separates the element from other elements.

## CSS Box Model (Diagram)

```
+--------------------------------------------+
|                  Margin                    |
|  +--------------------------------------+  |
|  |               Border                 |  |
|  |  +--------------------------------+  |  |
|  |  |            Padding             |  |  |
|  |  |  +--------------------------+  |  |  |
|  |  |  |         Content          |  |  |  |
|  |  |  +--------------------------+  |  |  |
|  |  +--------------------------------+  |  |
|  +--------------------------------------+  |
+--------------------------------------------+
```


### Two Types of Box Models:

#### 1. **Content Box** (Default):
In this model, the width and height you set for an element apply only to the content. Padding, border, and margin are added outside the content box.

- **Example:**
  ```css
  .example-content-box {
      width: 200px;
      padding: 20px;
      border: 10px solid;
      margin: 15px;
  }
  ```
  Here, the actual space taken by the element will be:
  - Total width = 200px (content) + 20px (padding) + 10px (border) = 240px
  - Similarly, the height will increase if padding and borders are applied.

#### 2. **Border Box**:
In this model, the width and height you set include the content, padding, and border. So, the element’s total width and height stay consistent, and padding and border are subtracted from the content size.

- **Example:**
  ```css
  .example-border-box {
      width: 200px;
      padding: 20px;
      border: 10px solid;
      margin: 15px;
      box-sizing: border-box;
  }
  ```
  Here, the total width remains 200px, and the padding and border are contained within this space. The content shrinks to accommodate the padding and border.

#### `box-sizing` Property:
The `box-sizing` property in CSS determines whether the element uses the content box model or the border box model.
- `box-sizing: content-box;` (default)
- `box-sizing: border-box;`

Using `border-box` is generally more predictable and easier to control layouts.


### Why Use `box-sizing: inherit` Instead of `* { box-sizing: border-box; }`

**Old Method:**
```css
* {
  box-sizing: border-box;
}
```
- Applies `border-box` to **all elements** globally, including components or libraries that expect `content-box`.
- If you use a component that relies on `content-box`, you’ll need to manually reset each internal element like `<header>` to `content-box`, which can get messy.

**Better Method:**
```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```
- By using `inherit`, all elements follow the parent’s box-sizing.
- It allows components to easily switch back to `content-box` without affecting nested elements. For example:
  
  ```css
  .component {
    box-sizing: content-box;
  }
  ```

- Now, everything inside `.component` also inherits `content-box`, making it easier to manage without unexpected behavior.


