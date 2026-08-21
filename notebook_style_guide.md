# Digital Notebook Style Guide

This document defines the strict UI, UX, and code design guidelines for generating digital lecture notes. All future topic files must adhere to these specifications to maintain a cohesive, high-quality, and visually stunning notebook theme.

---

## 1. Visual Theme (The Physical Notebook)

Each page must simulate a real student binder/notebook.

### Colors & Palette
*   **Paper Background:** `#FAF6EE` (warm, cream-colored paper).
*   **Lined Paper Pattern:** A subtle horizontal grid using CSS `linear-gradient` to look like ruled notebook lines.
*   **Notebook Margin Line:** A vertical red margin line (`#E53E3E` or `#FC8181`) positioned 3rem to 4rem from the left edge.
*   **Pen Ink Colors:**
    *   **Primary Ink (Blue):** `#1A365D` (Tailwind `text-slate-900` or custom deep ink blue) for body text and code.
    *   **Highlight/Correction Ink (Red):** `#9B2C2C` (Tailwind `text-red-800` or custom deep ink red) for headers, critical terms, and active states.
    *   **Pencil/Annotation Ink (Gray/Graphite):** `#4A5568` for secondary captions or subtle hints.
*   **Spiral Binder Rings:** Drawn with CSS gradients/borders on the far-left margin, overlapping the paper edge to simulate a ring-bound notebook.

---

## 2. Typography & Fonts

To support readability while preserving the handwritten theme, we use two Google Fonts loaded via CDN:
1.  **Handwritten Font:** `'Kalam', cursive` or `'Caveat', cursive` (gives an authentic pen-written look).
2.  **Readable Font:** `'Inter', sans-serif` or `'Outfit', sans-serif` (for easy reading of dense code or descriptions).

### Font Toggle Feature
*   Every page must feature a sticky font-toggle button in the upper-right corner.
*   **Implementation:** Toggling a class (e.g., `font-sans-mode`) on the `<body>` element.
*   **Transition:** Apply a smooth transition on font properties so the toggle feels fluid.

---

## 3. Structure & Navigation

*   **Left-hand Margin (Binder Area):** Width of `4rem` to `5rem` containing the spiral rings. The main content is padded to the right of this margin.
*   **Header / Notebook Title:** Designed like a handwritten header at the top of a page (e.g., Topic Name, Date, Class).
*   **Tabbed Navigation:** Tab headers styled like sticky index dividers (tabs) sticking out from the side or organized neatly at the top of the sheet.
    *   *Tab 1:* **Definitions & Concepts** (cheat sheets, core terms).
    *   *Tab 2:* **Step-by-Step Examples** (dry runs, algorithm walks).
    *   *Tab 3:* **Complexity Analysis** (tables, performance).
    *   *Tab 4:* **Interactive Visualizations** (HTML5 canvases).

---

## 4. Canvas Drawing Rules (The Diagrams)

All data structures, trees, or graphs must be drawn programmatically using HTML5 `<canvas>` and vanilla ES6+ JS. **No SVG or Mermaid.js.**

### Aesthetics for Drawings
*   **Background:** Transparent or a solid, paper-like off-white (`#FCFBF9`).
*   **Line Styles:** Nodes and connections should look hand-drawn. Use slightly rounded lines, or style them with solid deep ink colors (`#1A365D` or `#9B2C2C`).
*   **Node Fills:** Soft, pastel, or cream-colored fills (`#EBF8FF` for neutral, `#FEEBC8` for active/highlighted).
*   **Animations:** Canvas animations (like path drawing or node shifting) should run smoothly.
*   **Responsiveness:**
    *   Include a `resize` listener or calculate bounds dynamically.
    *   Scale the canvas context for high-DPI screens using `devicePixelRatio` to prevent blurry text/lines.

---

## 5. Granular Step-by-Step Layout

For algorithms (e.g., Insertion, Deletion, Rotations):
*   Do **NOT** use a video player style (Next/Prev buttons) unless requested.
*   Instead, display the steps sequentially down the page (a vertical timeline).
*   Each step block contains:
    1.  **Action Title** (e.g., *Action: Balance Left-Left Heavy Tree*)
    2.  **Detailed Sub-steps** (e.g., *Step 1.1: Identify the pivot node...*)
    3.  **Dedicated Canvas**: A unique `<canvas>` element drawn immediately below or next to the sub-steps showing the exact state *at that specific frame/step*.

---

## 6. HTML Template Structure (Single File)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Topic Name - Digital Notebook</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts CDN -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Inter:wght@400;500;600;700&family=Kalam:wght@400;700&display=swap" rel="stylesheet">
  
  <style>
    /* Lined Paper Base Pattern */
    .notebook-paper {
      background-color: #FAF6EE;
      background-image: linear-gradient(#D9D4C7 1px, transparent 1px);
      background-size: 100% 2rem;
      position: relative;
    }
    
    /* Margin line */
    .notebook-margin {
      border-left: 2px solid #FC8181;
    }
    
    /* Font definitions */
    .handwritten {
      font-family: 'Kalam', 'Caveat', cursive;
    }
    
    .readable-sans {
      font-family: 'Inter', sans-serif;
    }
    
    /* Smooth transition when toggling fonts */
    body {
      transition: font-family 0.2s ease-in-out;
    }
  </style>
</head>
<body class="handwritten text-slate-900">
  <!-- Interactive elements, canvas rendering script, and tab toggle script -->
</body>
</html>
```
