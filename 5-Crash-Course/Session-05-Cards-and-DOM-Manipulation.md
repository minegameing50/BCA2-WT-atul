# Session 5: "Meet the Team" — Faculty Cards + DOM Manipulation

**BCA Semester II | Mandsaur University | Web Technology (25BCA060)**

> **Session 5 of 15** | ⏱️ Duration: 2 hours  
> **Labs Covered:** Lab 14 (Bootstrap shopping page), Lab 7 (Div/Span layout), Lab 20 (JS dynamic styling)  
> **JavaScript Style:** ES5 — `var`, `function() {}`, string concatenation with `+`  

---

## 🎯 What We'll Build Today

Today we're adding a brand-new **"Our Faculty & Staff"** section to our class website. Think of it like creating digital visiting cards for your professors — each card shows their photo, name, designation, and a "Read More" button that reveals hidden details.

**By the end of this session, you'll have:**

- ✅ A responsive grid of 6 faculty cards (looks great on mobile AND desktop)
- ✅ "Read More / Read Less" toggle on each card (JavaScript DOM manipulation!)
- ✅ A live counter: "Expanded: 0 of 6"
- ✅ A "Show All / Hide All" button that controls all cards at once

**What the section looks like:**

```
┌─────────────────────────────────────────────────────────┐
│             👨‍🏫 Our Faculty & Staff                       │
│             Expanded: 0 of 6   [Show All]               │
│                                                         │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │  [photo] │  │  [photo] │  │  [photo] │              │
│  │ Dr.Rajesh│  │ Prof.Sunita│ │ Dr.Amit  │              │
│  │ HOD Prof │  │ Assoc Prof│  │ Asst Prof│              │
│  │[Read More]│ │[Read More]│  │[Read More]│             │
│  └──────────┘  └──────────┘  └──────────┘              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │  [photo] │  │  [photo] │  │  [photo] │              │
│  │ Prof.Neha│  │Shri Vikram│  │Prof.Kavita│             │
│  │ Asst Prof│  │ Lab Asst  │  │ Asst Prof│              │
│  │[Read More]│ │[Read More]│  │[Read More]│             │
│  └──────────┘  └──────────┘  └──────────┘              │
└─────────────────────────────────────────────────────────┘
```

---

## 📌 New HTML Tags & Concepts

These are the new HTML elements and attributes you'll learn today. Watch for 📌 callouts when they first appear in the code!

| Tag / Attribute | What It Does | Analogy |
|----------------|--------------|---------|
| `<div>` (deep dive) | Generic block container — groups elements together | 📦 A cardboard box — no special meaning, just holds things together |
| `<span>` | Generic inline container — marks a small piece of text | 🖍️ A highlighter pen — marks text within a line without creating a new line |
| `<h4>`, `<h5>` | Sub-subheadings (smaller than `<h3>`) | Chapter → Section → Sub-section → Paragraph heading |
| `class` attribute | Assigns one or more category labels to an element | "BCA" is a class — many students belong to the BCA class |
| `id` attribute | Assigns a unique identifier to an element | A roll number — only ONE student has roll number 25BCA001 |
| `data-*` attributes | Custom data stored on an HTML element | Your own private notes written on the back of an element |
| `style` attribute | Inline CSS applied directly to one element | A sticky note with styling instructions attached to one element |
| `onclick` attribute | Runs JavaScript when the element is clicked | A doorbell — press it, and something happens inside |

---

## 📖 Bootstrap Cards — Deep Dive

### What Is a Card?

A **Bootstrap Card** is a flexible, styled container for content. Think of it like a **visiting card** (business card) — it has a defined structure with specific areas for different types of information.

In the real world, you've seen cards everywhere:
- 📱 Instagram posts (image + caption + actions)
- 🛒 Amazon product listings (image + name + price + button)
- 👤 LinkedIn profiles (photo + name + title)

Bootstrap gives you ready-made CSS classes to build these card layouts instantly!

### Card Anatomy

Every Bootstrap card has these parts: an outer `card` wrapper, an optional image (`card-img-top`), a `card-body` for content, `card-title` for the heading, `card-text` for paragraphs, and optional `card-header`/`card-footer`.

### Key Card Classes

| Class | Purpose | Example |
|-------|---------|---------|
| `card` | The outer container | `<div class="card">` |
| `card-img-top` | Image at top of card | `<img class="card-img-top">` |
| `card-body` | Main content wrapper | `<div class="card-body">` |
| `card-title` | Card heading | `<h5 class="card-title">` |
| `card-text` | Card paragraph | `<p class="card-text">` |
| `card-header` | Header section | `<div class="card-header">` |
| `card-footer` | Footer section | `<div class="card-footer">` |

### Making Cards Look Professional

Bootstrap provides utility classes that make your cards look polished without writing any CSS:

| Class | What It Does | Visual Effect |
|-------|-------------|---------------|
| `h-100` | Sets height to 100% | All cards in a row become equal height |
| `shadow-sm` | Adds a small box shadow | Card appears slightly "lifted" off the page |
| `border-0` | Removes the border | Clean, modern look |
| `rounded` | Rounds the corners | Softer, friendlier appearance |
| `text-truncate` | Cuts long text with "..." | Prevents text overflow in fixed-width cards |

### Card Grid Layout

To display multiple cards in a responsive grid, we use Bootstrap's **row-cols** system:

```html
<div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 g-4">
```

Translation:
- `row-cols-1` → 1 card per row on **mobile** (extra small screens)
- `row-cols-sm-2` → 2 cards per row on **tablets** (≥576px)
- `row-cols-lg-3` → 3 cards per row on **laptops** (≥992px)
- `g-4` → **gap** of 1.5rem between cards (gutters)

> 💡 **Why not `col-12 col-sm-6 col-lg-4`?** Both approaches work! `row-cols-*` is newer and cleaner — you set columns on the parent `<div class="row">` instead of each child `<div class="col">`. The individual column approach (`col-12 col-sm-6 col-lg-4 col-xl-3`) gives you more per-card control.

### Badges

Badges are small labels used to highlight information — perfect for showing designations:

```html
<span class="badge bg-primary">HOD</span>
<span class="badge bg-success">Professor</span>
<span class="badge bg-warning text-dark">Lab Assistant</span>
```

| Badge Class | Color | Use For |
|-------------|-------|---------|
| `badge bg-primary` | Blue | HOD, Head of Department |
| `badge bg-success` | Green | Professor, Senior roles |
| `badge bg-info` | Cyan | Associate Professor |
| `badge bg-warning text-dark` | Yellow | Lab Assistant, Support Staff |
| `badge bg-secondary` | Grey | General labels |

---

## 📖 JavaScript DOM Manipulation

### What Is the DOM?

**DOM** stands for **Document Object Model**. It's the browser's internal representation of your HTML page as a tree of objects.

Think of it this way:

> 🏠 **Analogy:** Your HTML file is like a **blueprint** of a house. When the browser reads the HTML, it **builds the house** (the DOM). JavaScript can then walk through the house, open doors, move furniture, and repaint walls — all **without rewriting the blueprint**.

When you use `document.getElementById("details-1")`, JavaScript walks through this tree to find the element with `id="details-1"`.

### `document.getElementById()` — Finding Elements

This is the most fundamental DOM method. It finds **one** element by its unique `id`.

```javascript
// Find the element with id="details-1"
var details = document.getElementById("details-1");
```

> 🏠 **Analogy:** Imagine a huge apartment building. Every flat has a unique number (like 101, 202, 303). `getElementById` is like telling the security guard: "Take me to flat 303." He knows exactly where it is because flat numbers are unique.

**Rules:**
- The `id` must be **unique** on the page — no two elements should share the same `id`
- Returns `null` if no element with that `id` is found
- Case-sensitive: `"Details-1"` ≠ `"details-1"`

### `.textContent` vs `.innerHTML` — Changing Content

Once you've found an element, you can change what's inside it:

**`.textContent`** — Changes the **text** only (safe):

```javascript
var heading = document.getElementById("sectionTitle");
heading.textContent = "Our Amazing Faculty";
// Result: <h2 id="sectionTitle">Our Amazing Faculty</h2>
```

**`.innerHTML`** — Changes the **HTML** content (powerful but risky):

```javascript
var info = document.getElementById("details-1");
info.innerHTML = "<strong>Research:</strong> AI, Machine Learning";
// Result: <div id="details-1"><strong>Research:</strong> AI, Machine Learning</div>
```

> ⚠️ **Security Warning (XSS):** Never put user-typed text directly into `.innerHTML`! Bad people could inject harmful code. If a user types `<script>stealPasswords()</script>` and you put it into `.innerHTML`, that code **will run**. Always use `.textContent` for user-supplied data.

| Property | Changes | Safe for user input? | When to use |
|----------|---------|---------------------|-------------|
| `.textContent` | Plain text only | ✅ Yes | Changing labels, counters, messages |
| `.innerHTML` | Full HTML content | ❌ No — XSS risk | Adding formatted content you control |

### `.style.display` — Showing and Hiding Elements

You can hide or show any element by changing its `display` CSS property through JavaScript:

```javascript
var details = document.getElementById("details-1");

// Hide the element
details.style.display = "none";

// Show the element
details.style.display = "block";
```

> 🏠 **Analogy:** Think of `display: none` as pulling a **curtain** over a section of a room. The furniture (content) is still there — you just can't see it. When you set `display: block`, you open the curtain and everything is visible again.

### Functions with Parameters

In Session 4, we wrote simple functions. Now we'll write **functions that accept input values** (parameters):

```javascript
// Without parameter — works for only ONE thing
function toggleCard1() {
    var details = document.getElementById("details-1");
    // ... toggle logic for card 1 only
}

// With parameter — works for ANY card!
function toggleReadMore(id) {
    var details = document.getElementById("details-" + id);
    // ... toggle logic for card 1, 2, 3, 4, 5, or 6!
}
```

> 🏠 **Analogy:** A function without parameters is like a TV remote with **only one button** — it can only control one TV. A function WITH parameters is like a **universal remote** — you tell it which device to control: `pressButton("TV")`, `pressButton("AC")`, `pressButton("Fan")`.

### String Concatenation — Building Text Dynamically

In ES5, we join strings together using the `+` operator:

```javascript
var count = 3;
var total = 6;
var message = "Expanded: " + count + " of " + total;
// Result: "Expanded: 3 of 6"
```

```javascript
var id = 2;
var elementId = "details-" + id;
// Result: "details-2"
```

> 💡 **The Pattern:** Every interactive feature follows this flow:
> ```
> User Clicks → Function Runs → DOM Changes → User Sees Update
> ```
> The user clicks "Read More" → `toggleReadMore(1)` runs → `details-1` becomes visible → user sees the hidden text appear.

### `class` vs `id` — Know the Difference!

This is one of the most confusing things for beginners, so let's make it crystal clear:

| | `class` | `id` |
|---|---------|------|
| **Uniqueness** | Multiple elements can share the same class | Only ONE element can have a given id |
| **Analogy** | A category label: "BCA students" — many people | A roll number: "25BCA001" — one person |
| **Syntax in HTML** | `class="card-title"` | `id="details-1"` |
| **Syntax in CSS** | `.card-title { }` (dot) | `#details-1 { }` (hash) |
| **JS selector** | `getElementsByClassName()` | `getElementById()` |
| **Multiple values?** | Yes: `class="card h-100 shadow-sm"` | No: one id per element |
| **Use for** | Styling groups of similar elements | Targeting ONE specific element |

---

## 🔨 Let's Build! — Step by Step

### Where Does This Go?

This new section goes **after the About section** and **before the closing `</body>` tag** in your `index.html`. The new JavaScript goes inside the existing `<script>` tag, **after your Session 4 code**.

```
index.html (current structure):
├── <nav> .............. Navbar (Session 1)
├── <section> .......... Hero Carousel (Session 2)
├── <section> .......... About Department (Session 3)
├── <section> .......... 👈 NEW! Faculty Cards (Session 5)
├── <script> ........... Session 4 JS + NEW Session 5 JS
└── </body>
```

---

### Step 1: Add the Faculty Section Shell

Add this right after the closing `</section>` of the About section:

```html
<!-- ============================================
     FACULTY & STAFF SECTION (Session 5)
     Labs: 14 (Card Grid), 7 (Div/Span), 20 (JS Styling)
     ============================================ -->
```

📌 **`<section>` reminder:** We use `<section>` for each major content block. It tells the browser (and screen readers): "This is a distinct part of the page."

```html
<section id="faculty" class="py-5 bg-light">
```

📌 **`id="faculty"`** — This gives the section a **unique identifier**. We can now:
1. Link to it from the navbar: `<a href="#faculty">`
2. Find it with JavaScript: `document.getElementById("faculty")`
3. Style it in CSS: `#faculty { }`

📌 **`class="py-5 bg-light"`** — Two Bootstrap utility classes:
- `py-5` = **padding** on the **y-axis** (top and bottom), size 5 (3rem)
- `bg-light` = light grey **background** color — visually separates this section from the one above

---

### Step 2: Add the Container and Heading

Inside the section, add:

```html
<section id="faculty" class="py-5 bg-light">
    <div class="container">
        <h2 class="text-center mb-2">👨‍🏫 Our Faculty & Staff</h2>
        <p class="text-center text-muted mb-4">The people who guide your BCA journey at Mandsaur University</p>
```

📌 **`<div class="container">`** — Deep Dive on `<div>`:

> A `<div>` is the most common HTML element. It's a **generic container** — it has no special meaning on its own. Think of it as a **cardboard box**: you can put anything inside it, label it with classes and ids, and style it however you want.
>
> `<div class="container">` means: "Here's a box, and I want Bootstrap to center it on the page with proper side margins."
>
> **Why not use `<section>` for everything?** Because `<section>` means "a thematic grouping of content." A `<div>` is just "a box to hold stuff." Use `<section>` for meaningful sections, and `<div>` for layout/grouping purposes.

---

### Step 3: Add the Counter and Toggle Button

Below the subtitle paragraph, add:

```html
        <!-- Counter and Toggle Controls -->
        <div class="text-center mb-4">
            <span id="expandedCounter" class="me-3 fw-bold">Expanded: 0 of 6</span>
            <button id="toggleAllBtn" class="btn btn-outline-secondary btn-sm" onclick="toggleAll()">
                Show All
            </button>
        </div>
```

📌 **`<span>` — First appearance!**

> A `<span>` is like a `<div>`'s little sibling — it's also a generic container, but **inline** instead of block.
>
> - `<div>` = 📦 A cardboard **box** — takes up a full line (block-level)
> - `<span>` = 🖍️ A **highlighter pen** — marks text within a line without breaking to a new line
>
> Here, we use `<span id="expandedCounter">` so the counter text sits **on the same line** as the button. If we used `<div>`, the button would drop to the next line.

📌 **`id="expandedCounter"`** — We give this span a unique id because JavaScript needs to find it and update the text ("Expanded: 0 of 6" → "Expanded: 3 of 6") whenever a card is expanded.

📌 **`onclick="toggleAll()"`** — When this button is clicked, the browser runs the JavaScript function `toggleAll()`. We'll write that function in Step 6.

---

### Step 4: Create the Card Grid Row

Now add the row that will hold all 6 cards:

```html
        <!-- Faculty Card Grid -->
        <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 g-4">
```

This creates a responsive grid:
- 📱 **Mobile** (< 576px): 1 card per row — easy to read on small screens
- 📱 **Tablet** (≥ 576px): 2 cards per row — uses the wider space
- 💻 **Laptop** (≥ 992px): 3 cards per row — nice grid layout

The `g-4` adds consistent **gutters** (gaps) between cards.

---

### Step 5: Add the 6 Faculty Cards

Now add each card inside the row. Here are all 6 cards — type each one carefully!

**Card 1 — Dr. Rajesh Sharma (HOD)**

```html
            <!-- Card 1: Dr. Rajesh Sharma -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=1" class="card-img-top" alt="Dr. Rajesh Sharma">
                    <div class="card-body">
                        <h5 class="card-title">Dr. Rajesh Sharma</h5>
                        <p class="card-text">
                            <span class="badge bg-primary">HOD</span>
                            <span class="badge bg-success">Professor</span>
                        </p>
                        <p class="card-text text-muted">Department of Computer Applications</p>
                        <div id="details-1" style="display: none;">
                            <p class="card-text"><strong>Research:</strong> Artificial Intelligence, Machine Learning</p>
                            <p class="card-text"><strong>Qualification:</strong> Ph.D. (Computer Science), M.Tech</p>
                        </div>
                        <button id="btn-1" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(1)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

📌 **`<h5 class="card-title">`** — Heading level 5. We use `<h5>` inside cards because `<h2>` is used for the section title and `<h3>`/`<h4>` might be used for sub-sections. Heading levels should go in order — don't jump from `<h2>` straight to `<h6>`!

📌 **`<span class="badge bg-primary">HOD</span>`** — Here's our `<span>` in action! The badge is an **inline** element — both badges sit side by side on the same line. Bootstrap's `badge` class makes it look like a small colored pill.

📌 **`data-*` concept with `id="details-1"` and `id="btn-1"`** — We use numbered ids so JavaScript can target each card individually. The number acts like a **data attribute** — it tells our function which card to control. (We'll learn actual `data-*` attributes in a later session, but the concept is the same: attaching custom information to elements.)

📌 **`style="display: none;"`** — This **inline style** hides the details `<div>` when the page first loads. JavaScript will change this to `display: block` when "Read More" is clicked.

📌 **`onclick="toggleReadMore(1)"`** — When clicked, calls our function with `1` as the argument. The function uses this number to find `details-1` and `btn-1`.

**Card 2 — Prof. Sunita Verma**

```html
            <!-- Card 2: Prof. Sunita Verma -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=2" class="card-img-top" alt="Prof. Sunita Verma">
                    <div class="card-body">
                        <h5 class="card-title">Prof. Sunita Verma</h5>
                        <p class="card-text">
                            <span class="badge bg-info text-dark">Associate Professor</span>
                        </p>
                        <p class="card-text text-muted">Department of Computer Applications</p>
                        <div id="details-2" style="display: none;">
                            <p class="card-text"><strong>Research:</strong> Web Technologies, Cloud Computing</p>
                            <p class="card-text"><strong>Qualification:</strong> M.Tech (IT), NET Qualified</p>
                        </div>
                        <button id="btn-2" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(2)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

**Card 3 — Dr. Amit Patel**

```html
            <!-- Card 3: Dr. Amit Patel -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=3" class="card-img-top" alt="Dr. Amit Patel">
                    <div class="card-body">
                        <h5 class="card-title">Dr. Amit Patel</h5>
                        <p class="card-text">
                            <span class="badge bg-success">Assistant Professor</span>
                        </p>
                        <p class="card-text text-muted">Department of Computer Applications</p>
                        <div id="details-3" style="display: none;">
                            <p class="card-text"><strong>Research:</strong> Data Science, Python Programming</p>
                            <p class="card-text"><strong>Qualification:</strong> Ph.D. (Data Science), MCA</p>
                        </div>
                        <button id="btn-3" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(3)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

**Card 4 — Prof. Neha Gupta**

```html
            <!-- Card 4: Prof. Neha Gupta -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=4" class="card-img-top" alt="Prof. Neha Gupta">
                    <div class="card-body">
                        <h5 class="card-title">Prof. Neha Gupta</h5>
                        <p class="card-text">
                            <span class="badge bg-success">Assistant Professor</span>
                        </p>
                        <p class="card-text text-muted">Department of Computer Applications</p>
                        <div id="details-4" style="display: none;">
                            <p class="card-text"><strong>Research:</strong> Database Systems, SQL Optimization</p>
                            <p class="card-text"><strong>Qualification:</strong> M.Tech (CSE), NET Qualified</p>
                        </div>
                        <button id="btn-4" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(4)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

**Card 5 — Shri Vikram Singh (Lab Assistant)**

```html
            <!-- Card 5: Shri Vikram Singh -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=5" class="card-img-top" alt="Shri Vikram Singh">
                    <div class="card-body">
                        <h5 class="card-title">Shri Vikram Singh</h5>
                        <p class="card-text">
                            <span class="badge bg-warning text-dark">Lab Assistant</span>
                        </p>
                        <p class="card-text text-muted">Computer Lab, BCA Department</p>
                        <div id="details-5" style="display: none;">
                            <p class="card-text"><strong>Skills:</strong> Hardware Maintenance, Networking, Troubleshooting</p>
                            <p class="card-text"><strong>Qualification:</strong> Diploma in Computer Engineering</p>
                        </div>
                        <button id="btn-5" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(5)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

**Card 6 — Prof. Kavita Joshi**

```html
            <!-- Card 6: Prof. Kavita Joshi -->
            <div class="col">
                <div class="card h-100 shadow-sm">
                    <img src="https://picsum.photos/300/200?random=6" class="card-img-top" alt="Prof. Kavita Joshi">
                    <div class="card-body">
                        <h5 class="card-title">Prof. Kavita Joshi</h5>
                        <p class="card-text">
                            <span class="badge bg-success">Assistant Professor</span>
                        </p>
                        <p class="card-text text-muted">Department of Computer Applications</p>
                        <div id="details-6" style="display: none;">
                            <p class="card-text"><strong>Research:</strong> Cyber Security, Ethical Hacking</p>
                            <p class="card-text"><strong>Qualification:</strong> M.Tech (Cyber Security), CEH Certified</p>
                        </div>
                        <button id="btn-6" class="btn btn-outline-primary btn-sm" onclick="toggleReadMore(6)">Read More ▼</button>
                    </div>
                </div>
            </div>
```

**Close the row, container, and section:**

```html
        </div>
        <!-- End of card grid row -->
    </div>
    <!-- End of container -->
</section>
<!-- End of Faculty Section -->
```

---

### Step 6: Add the JavaScript

Add this JavaScript inside your existing `<script>` tag, **after your Session 4 code** (the click counter etc.):

```javascript
// ============================================
// FACULTY CARDS — Read More Toggle (Session 5)
// Labs: 14, 7, 20
// ============================================

// Variables to track how many cards are expanded
var expandedCount = 0;
var totalCards = 6;

// -----------------------------------------
// Function: toggleReadMore(id)
// Purpose: Show or hide details for ONE card
// Parameter: id — the card number (1 to 6)
// Pattern: Click → Function → DOM Change → User Sees Update
// -----------------------------------------
function toggleReadMore(id) {
    // Step 1: Find the hidden details div and the button
    var details = document.getElementById("details-" + id);
    var btn = document.getElementById("btn-" + id);

    // Step 2: Check current state and toggle
    if (details.style.display === "none") {
        // Currently hidden → show it
        details.style.display = "block";
        btn.textContent = "Read Less ▲";
        expandedCount = expandedCount + 1;
    } else {
        // Currently visible → hide it
        details.style.display = "none";
        btn.textContent = "Read More ▼";
        expandedCount = expandedCount - 1;
    }

    // Step 3: Update the counter text
    document.getElementById("expandedCounter").textContent = "Expanded: " + expandedCount + " of " + totalCards;
}

// -----------------------------------------
// Function: toggleAll()
// Purpose: Show ALL or Hide ALL card details at once
// Uses a for loop to go through every card (1 to 6)
// -----------------------------------------
function toggleAll() {
    // Decide: should we show all or hide all?
    // If not all are expanded, show all. Otherwise, hide all.
    var showAll = expandedCount < totalCards;

    // Loop through each card
    for (var i = 1; i <= totalCards; i++) {
        var details = document.getElementById("details-" + i);
        var btn = document.getElementById("btn-" + i);

        if (showAll) {
            details.style.display = "block";
            btn.textContent = "Read Less ▲";
        } else {
            details.style.display = "none";
            btn.textContent = "Read More ▼";
        }
    }

    // Update the counter
    expandedCount = showAll ? totalCards : 0;
    document.getElementById("expandedCounter").textContent = "Expanded: " + expandedCount + " of " + totalCards;

    // Update the button text
    document.getElementById("toggleAllBtn").textContent = showAll ? "Hide All" : "Show All";
}
```

📌 **New JS Concept: `for` loop** — We use `for (var i = 1; i <= totalCards; i++)` to repeat the same action for cards 1 through 6. Think of it like a teacher taking attendance: "Roll number 1? Roll number 2? Roll number 3? ..." — the same question, different student each time.

📌 **New JS Concept: Ternary operator** — `showAll ? totalCards : 0` is a shorthand for:
```javascript
if (showAll) {
    expandedCount = totalCards;
} else {
    expandedCount = 0;
}
```
Read it as: "If `showAll` is true, use `totalCards`; otherwise, use `0`."

---

## ✅ Checkpoint

Before moving on, verify that everything works:

| # | Check | Expected Result |
|---|-------|----------------|
| 1 | Page loads without errors | Open browser console (F12 → Console tab) — no red errors |
| 2 | Faculty section is visible | You see 6 cards below the About section |
| 3 | Responsive layout | Resize browser: 1 column on mobile, 2 on tablet, 3 on desktop |
| 4 | Click "Read More" on any card | Hidden text appears, button changes to "Read Less ▲" |
| 5 | Click "Read Less" | Hidden text disappears, button changes back to "Read More ▼" |
| 6 | Counter updates | "Expanded: 0 of 6" changes as you click Read More buttons |
| 7 | "Show All" button | All 6 cards expand, counter shows "Expanded: 6 of 6", button says "Hide All" |
| 8 | "Hide All" button | All 6 cards collapse, counter shows "Expanded: 0 of 6", button says "Show All" |
| 9 | Cards have shadows | Each card has a subtle shadow (from `shadow-sm` class) |
| 10 | Badges are colored | HOD = blue, Professor = green, Lab Assistant = yellow |

---

## 🔍 Quick Reference

### Bootstrap Classes Used Today

| Class | What It Does |
|-------|-------------|
| `card`, `card-img-top`, `card-body`, `card-title`, `card-text` | Card structure components |
| `h-100` | Equal-height cards in a row |
| `shadow-sm` | Subtle box shadow (lifted look) |
| `badge`, `bg-primary`, `bg-success`, `bg-info`, `bg-warning` | Colored label badges |
| `text-dark`, `text-muted`, `text-truncate` | Text color and overflow control |
| `row-cols-1`, `row-cols-sm-2`, `row-cols-lg-3` | Responsive grid column counts |
| `g-4` | Grid gutters (gap between cards) |
| `py-5`, `mb-2`, `mb-4`, `me-3` | Padding and margin spacing |
| `fw-bold` | Bold font weight |
| `btn-outline-primary`, `btn-outline-secondary`, `btn-sm` | Outlined and small buttons |
| `bg-light` | Light grey background |

### JavaScript Concepts Used Today

| Concept | Syntax | Purpose |
|---------|--------|---------|
| Get element by ID | `document.getElementById("id")` | Find one element on the page |
| Change text | `.textContent = "new text"` | Update text content safely |
| Change HTML | `.innerHTML = "<b>html</b>"` | Update HTML content (use carefully!) |
| Show element | `.style.display = "block"` | Make a hidden element visible |
| Hide element | `.style.display = "none"` | Hide an element |
| Function with parameter | `function name(param) { }` | Reusable function that accepts input |
| String concatenation | `"text" + variable + "text"` | Build strings dynamically |
| For loop | `for (var i = 1; i <= n; i++)` | Repeat an action multiple times |
| Ternary operator | `condition ? valueA : valueB` | Shorthand if/else for values |
| If/else | `if (cond) { } else { }` | Make decisions in code |

---

## 📝 Key Takeaways

1. **Bootstrap Cards** are flexible content containers with a defined structure (`card` → `card-body` → `card-title` + `card-text`). They're everywhere on the modern web — learn them well!

2. **`<div>` is a box, `<span>` is a highlighter.** `<div>` creates block-level groupings (takes full width); `<span>` wraps inline content (stays in the flow of text). Neither has any semantic meaning — they're just containers.

3. **`class` is a category, `id` is a roll number.** Many elements can share a class, but only one element should have a given id. Use `id` when JavaScript needs to find a specific element.

4. **DOM Manipulation is the heart of interactive web pages.** The pattern is always: **Find an element** → **Change something** → **User sees the update**. Today we used `getElementById` to find, `.style.display` and `.textContent` to change.

5. **Functions with parameters are like universal remotes.** Instead of writing 6 separate functions for 6 cards, we wrote ONE function that accepts a card number. This is the DRY principle: **Don't Repeat Yourself**.

6. **`.textContent` is safe, `.innerHTML` is powerful but dangerous.** Always use `.textContent` for plain text updates. Only use `.innerHTML` when you need to insert HTML that YOU wrote (never user input!).

7. **The counter pattern** (tracking state in a variable, updating the display) — remember this! You'll use it again and again: shopping carts, form progress bars, quiz scores, notification badges.

---

## 🏋️ Practice Challenges

Try these on your own to reinforce what you learned:

### Challenge 1: Add a 7th Card (⭐ Easy)

Add a guest lecturer card:
- **Name:** Dr. Priya Mehta
- **Designation:** Guest Lecturer
- **Department:** Department of Computer Applications
- **Research:** Internet of Things (IoT), Embedded Systems
- **Qualification:** Ph.D. (Electronics), B.Tech

**Hints:**
- Copy Card 6 and change the content
- Use `random=7` for the image
- Update `id="details-7"`, `id="btn-7"`, and `onclick="toggleReadMore(7)"`
- **Don't forget** to change `var totalCards = 6;` to `var totalCards = 7;` in JavaScript!

### Challenge 2: Color-Coded Card Borders (⭐⭐ Medium)

Give each card a colored left border based on designation:
- **HOD** → `border-start border-primary border-4`
- **Professor / Associate Professor** → `border-start border-success border-4`
- **Assistant Professor** → `border-start border-info border-4`
- **Lab Assistant** → `border-start border-warning border-4`

**Example:** Change the card `<div>` from:
```html
<div class="card h-100 shadow-sm">
```
to:
```html
<div class="card h-100 shadow-sm border-start border-primary border-4">
```

### Challenge 3: Search/Filter Faculty (⭐⭐⭐ Hard)

Add a search input above the cards that filters faculty by name as you type:

```html
<input type="text" id="facultySearch" class="form-control mb-3" placeholder="Search faculty by name..." onkeyup="filterFaculty()">
```

Then write the JavaScript:

```javascript
function filterFaculty() {
    var searchText = document.getElementById("facultySearch").value;
    searchText = searchText.toLowerCase();

    // Get all card titles and check if they match
    for (var i = 1; i <= totalCards; i++) {
        var card = document.getElementById("btn-" + i).parentElement.parentElement;
        var name = card.querySelector(".card-title").textContent.toLowerCase();

        if (name.indexOf(searchText) !== -1) {
            card.parentElement.style.display = "block";
        } else {
            card.parentElement.style.display = "none";
        }
    }
}
```

> 💡 **New concepts in this challenge:** `.value` (gets input text), `.toLowerCase()` (converts to lowercase for case-insensitive matching), `.indexOf()` (searches within a string — returns -1 if not found), `.parentElement` (goes up one level in the DOM tree), `.querySelector()` (finds the first element matching a CSS selector inside a parent).

---

## 🔗 Labs Covered in This Session

| Lab # | Experiment Description | How We Covered It |
|-------|----------------------|-------------------|
| **Lab 14** | Bootstrap shopping/product page with card grid layout | ✅ Built a 6-card responsive grid with `row-cols-*`, `card`, `shadow-sm`, `h-100`, badges — same techniques used for product/shopping pages |
| **Lab 7** | Div and Span layout | ✅ Extensive use of `<div>` for card structure, containers, and grouping; `<span>` for inline badges and counter text. Deep-dive explanations of both. |
| **Lab 20** | JavaScript dynamic bold/italic/underline styling | ✅ Used `style.display` to dynamically change element visibility; button text changes dynamically via `.textContent`. Same DOM manipulation approach applies to bold/italic/underline toggling. |

---

## ⏭️ Next Session Preview

### Session 6: Class Timetable + Loops & Arrays

In the next session, we'll build a **Class Timetable** section using Bootstrap tables. You'll learn:

- 📖 **Bootstrap Tables** — `table`, `table-striped`, `table-hover`, `table-bordered`, responsive wrappers
- 📖 **HTML `<table>` elements** — `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`
- 📖 **JavaScript Arrays** — storing lists of data: `var days = ["Mon", "Tue", "Wed", "Thu", "Fri"];`
- 📖 **JavaScript Loops** — `for` loops to build table rows dynamically from data
- 📖 **`classList.add()` / `classList.remove()`** — a better way to change styling than `style.display`
- 📖 **`Date` object** — highlight today's row in the timetable automatically!

> 💡 **Fun preview:** Instead of typing 30+ table rows by hand, you'll learn to **generate the entire timetable from a JavaScript array** — that's the power of programming!

**Labs covered next time:** Lab 5 (Class timetable table) ✅, Lab 6 (University table layout) ✅

---

*Session 5 of 15 — Crash Course: Bootstrap + JavaScript — BCA Semester II, Mandsaur University, 2025-26*
