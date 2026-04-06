# Session 3: "Tell Your Story" — About Section + Grid System

**BCA Semester II | Web Technology (25BCA060) | Mandsaur University**

| Detail            | Info                                                       |
|-------------------|------------------------------------------------------------|
| **Session**       | 3 of 15                                                    |
| **Labs Covered**  | Lab 1 (Department webpage with paragraphs & lists), Lab 25 (Bootstrap layout with navbar, header, 3-column) |
| **Time**          | 2-hour practical lab                                       |
| **Prerequisites** | Session 2 complete (Navbar + Hero with Carousel)           |
| **Previous**      | [Session 2 — Hero Section + Image Carousel](Session-02-Hero-and-Carousel.md) |
| **Next**          | [Session 4 — JavaScript Foundations](Session-04-JavaScript-Foundations.md) |

> **No JavaScript in this session.** Today is pure Bootstrap layout mastery — the most important skill in the entire course.

---

## 🎯 What We'll Build Today

We're adding an **"About Our Department"** section below the hero carousel. By the end of this session your page will have:

1. A **section heading** — "About BCA Department"
2. A **2-column responsive layout** — text on the left, image on the right (stacks on mobile)
3. **3 info cards** in a row — Vision, Mission, Values (stacks on mobile)

```
┌──────────────────────────────────────────────┐
│              NAVBAR (from Session 1)          │
├──────────────────────────────────────────────┤
│         HERO CAROUSEL (from Session 2)       │
├──────────────────────────────────────────────┤
│          ★ ABOUT BCA DEPARTMENT ★            │
│                                              │
│  ┌──────────────┐  ┌──────────────┐          │
│  │  Department   │  │              │          │
│  │  Description  │  │  📷 Image    │          │
│  │  + Highlights │  │              │          │
│  └──────────────┘  └──────────────┘          │
│                                              │
│  ┌──────┐  ┌──────┐  ┌──────┐               │
│  │ 🎯   │  │ 🚀   │  │ 💡   │               │
│  │Vision│  │Mission│  │Values│               │
│  └──────┘  └──────┘  └──────┘               │
└──────────────────────────────────────────────┘
```

---

## 📌 New HTML Tags You'll Learn

Every time you see a **📌 "First Time Seeing This?"** callout, it means that tag is being introduced for the first time in this crash course.

| Tag              | Purpose                          | Example                                   |
|------------------|----------------------------------|-------------------------------------------|
| `<section>`      | Semantic container for a page section | `<section id="about">...</section>`   |
| `<article>`      | Self-contained content block     | `<article>...</article>`                  |
| `<h2>`           | Second-level heading             | `<h2>About BCA Department</h2>`           |
| `<h3>`           | Third-level heading              | `<h3>Our Vision</h3>`                     |
| `<strong>`       | Bold with semantic importance    | `<strong>120+ students</strong>`           |
| `<em>`           | Italic with emphasis             | `<em>excellence in technology</em>`       |
| `<br>`           | Line break (use sparingly!)      | `Line one<br>Line two`                    |
| `<ul>`           | Unordered (bullet) list          | `<ul><li>Item</li></ul>`                  |
| `<ol>`           | Ordered (numbered) list          | `<ol><li>First</li></ol>`                 |
| `<li>`           | List item (inside `<ul>` or `<ol>`) | `<li>BCA Program</li>`               |
| `<figure>`       | Image with optional caption      | `<figure><img ...></figure>`              |
| `<figcaption>`   | Caption for a `<figure>`         | `<figcaption>Campus</figcaption>`         |

---

## 📖 Bootstrap Grid System — The Big Concept

> **This is the single most important concept in Bootstrap.** If you understand the grid, you understand 80% of Bootstrap layout. Take your time with this section.

### The 12-Column Mental Model

**Analogy — The Chessboard:**

Imagine a chessboard, but instead of 8 columns it has **12 columns**. Every row on your webpage is divided into 12 invisible columns. You decide how many columns each piece of content takes up.

- Want two equal halves? Each piece gets **6 columns** (6 + 6 = 12).
- Want a sidebar + main area? Sidebar gets **4 columns**, main gets **8 columns** (4 + 8 = 12).
- Want three equal cards? Each gets **4 columns** (4 + 4 + 4 = 12).
- Want four equal boxes? Each gets **3 columns** (3 + 3 + 3 + 3 = 12).

The total must **always add up to 12** (or less — extra space stays empty).

```
The 12-Column Grid:
|  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  9 | 10 | 11 | 12 |

Two equal columns (6 + 6):
|←────── col-6 ──────→|←────── col-6 ──────→|

Sidebar + Main (4 + 8):
|←── col-4 ──→|←──────────── col-8 ────────────→|

Three equal columns (4 + 4 + 4):
|←── col-4 ──→|←── col-4 ──→|←── col-4 ──→|

Four equal columns (3 + 3 + 3 + 3):
|← col-3 →|← col-3 →|← col-3 →|← col-3 →|
```

**Analogy — Splitting a Roti:**

Think of each row as a big round roti. You can cut it into 12 equal slices. When you say `col-6`, you're giving that content 6 slices (half the roti). When you say `col-4`, you're giving it 4 slices (one-third). The roti always has exactly 12 slices — no more, no less.

---

### The Three Sacred Rules: Container → Row → Col

Bootstrap's grid follows a strict hierarchy. **You must always follow this order:**

```
<div class="container">          ← 1. The outer wrapper (sets max-width, centers content)
    <div class="row">            ← 2. A horizontal group (enables the 12-column system)
        <div class="col-6">     ← 3. A column (takes up space in the row)
            Content here
        </div>
        <div class="col-6">
            More content
        </div>
    </div>
</div>
```

| Level       | Class          | What It Does                                          |
|-------------|----------------|-------------------------------------------------------|
| **Container** | `container`  | Centers content, adds side padding, sets max-width    |
| **Row**       | `row`        | Creates a horizontal group, enables the grid          |
| **Column**    | `col-*`      | Defines how wide each piece is (out of 12)            |

**Think of it like a bookshelf:**
- **Container** = the bookshelf itself (fixed width, centered against the wall)
- **Row** = one shelf on the bookshelf (horizontal)
- **Columns** = books placed side by side on that shelf (each taking up some space)

> ⚠️ **Never put a `col` directly inside a `container` without a `row`.** Never put a `row` outside a `container`. Always follow: Container → Row → Col.

---

### Responsive Breakpoints — The Magic of Mobile-First

Bootstrap is **mobile-first**. This means everything is designed for small screens by default, and you add classes to change behavior on larger screens.

**The 6 Breakpoints:**

| Breakpoint | Class Prefix | Screen Width | Common Devices         |
|------------|-------------|--------------|------------------------|
| Extra small | (none)     | < 576px      | Small phones (portrait) |
| Small       | `sm`       | ≥ 576px      | Large phones (landscape) |
| Medium      | `md`       | ≥ 768px      | Tablets                 |
| Large       | `lg`       | ≥ 992px      | Laptops                 |
| Extra large | `xl`       | ≥ 1200px     | Desktops                |
| XXL         | `xxl`      | ≥ 1400px     | Large monitors          |

**How to read column classes:**

| Class      | Meaning                                             |
|------------|-----------------------------------------------------|
| `col-12`   | Full width on ALL screen sizes (default behavior)   |
| `col-md-6` | 6 columns (half width) on **medium screens and up** |
| `col-lg-4` | 4 columns (one-third) on **large screens and up**   |
| `col-sm-6 col-lg-3` | Half on small+, quarter on large+          |

**The key insight:** On screens *smaller* than the breakpoint, the column becomes full width (12 columns). On screens *at or above* the breakpoint, it becomes the size you specified.

### Responsive Behavior — Visual Diagram

Here's how our About section will behave at different screen sizes:

```
Desktop (≥992px) — lg breakpoint:
┌────────────────────────────────────────────┐
│  ┌──── col-lg-6 ────┐ ┌──── col-lg-6 ────┐│
│  │                   │ │                   ││
│  │   Text content    │ │   Image           ││
│  │   (description,   │ │   (placeholder)   ││
│  │    highlights)    │ │                   ││
│  │                   │ │                   ││
│  └───────────────────┘ └───────────────────┘│
└────────────────────────────────────────────┘

Tablet (≥768px, <992px) — md breakpoint:
┌────────────────────────────────────────────┐
│  ┌──── col-md-6 ────┐ ┌──── col-md-6 ────┐│
│  │  Text content     │ │  Image            ││
│  │  (narrower)       │ │  (smaller)        ││
│  └───────────────────┘ └───────────────────┘│
└────────────────────────────────────────────┘

Mobile (<768px) — columns stack vertically:
┌────────────────────────────────────────────┐
│  ┌──────────── col-12 ───────────────┐     │
│  │  Text content (full width)        │     │
│  └───────────────────────────────────┘     │
│  ┌──────────── col-12 ───────────────┐     │
│  │  Image (full width, below text)   │     │
│  └───────────────────────────────────┘     │
└────────────────────────────────────────────┘
```

**How did we achieve this?** By writing:

```html
<div class="col-md-6">Text</div>
<div class="col-md-6">Image</div>
```

- On screens **≥ 768px** (md and up): each column is 6 out of 12 → side by side.
- On screens **< 768px**: columns automatically become full width (12 out of 12) → stacked.

We didn't write any CSS. We didn't write any JavaScript. **Just one class name.**

---

### Common Grid Patterns

Here are layouts you'll use again and again:

```
Pattern 1: Two equal columns
<div class="row">
    <div class="col-md-6">Left</div>
    <div class="col-md-6">Right</div>
</div>

Pattern 2: Three equal columns
<div class="row">
    <div class="col-md-4">One</div>
    <div class="col-md-4">Two</div>
    <div class="col-md-4">Three</div>
</div>

Pattern 3: Four equal columns
<div class="row">
    <div class="col-md-6 col-lg-3">A</div>
    <div class="col-md-6 col-lg-3">B</div>
    <div class="col-md-6 col-lg-3">C</div>
    <div class="col-md-6 col-lg-3">D</div>
</div>
(On medium: 2 per row. On large: 4 per row. On small: 1 per row.)

Pattern 4: Sidebar + Main content
<div class="row">
    <div class="col-lg-4">Sidebar</div>
    <div class="col-lg-8">Main content</div>
</div>
```

---

### Gutters — Space Between Columns

By default, Bootstrap adds some space (gutter) between columns. You can control this with gutter classes on the **row**:

| Class  | What It Does                               |
|--------|--------------------------------------------|
| `g-0`  | No gutter (columns touch each other)       |
| `g-3`  | Medium gutter on all sides                 |
| `g-4`  | Standard gutter (most common)              |
| `gx-2` | Horizontal gutter only (left-right space)  |
| `gy-3` | Vertical gutter only (top-bottom space)    |

```html
<div class="row g-4">
    <div class="col-md-4">Card 1</div>
    <div class="col-md-4">Card 2</div>
    <div class="col-md-4">Card 3</div>
</div>
```

---

## 📖 Bootstrap Spacing & Text Utilities

### Spacing Utilities — Margin & Padding

Instead of writing CSS like `margin-top: 3rem`, Bootstrap gives you shorthand classes:

**Format:** `{property}{side}-{size}`

| Property | Letter |
|----------|--------|
| Margin   | `m`    |
| Padding  | `p`    |

| Side     | Letter | Meaning          |
|----------|--------|------------------|
| Top      | `t`    | Top only         |
| Bottom   | `b`    | Bottom only      |
| Start    | `s`    | Left (in LTR)   |
| End      | `e`    | Right (in LTR)   |
| X-axis   | `x`    | Left + Right     |
| Y-axis   | `y`    | Top + Bottom     |
| All      | (none) | All 4 sides      |

| Size | Value      |
|------|------------|
| `0`  | 0          |
| `1`  | 0.25rem    |
| `2`  | 0.5rem     |
| `3`  | 1rem       |
| `4`  | 1.5rem     |
| `5`  | 3rem       |

**Examples:**

| Class   | What It Does                      |
|---------|-----------------------------------|
| `mt-5`  | Margin-top: 3rem (large space)    |
| `mb-3`  | Margin-bottom: 1rem               |
| `p-4`   | Padding: 1.5rem on all sides      |
| `py-5`  | Padding top + bottom: 3rem        |
| `px-3`  | Padding left + right: 1rem        |
| `ms-2`  | Margin-start (left): 0.5rem       |

**Analogy — A Gift Box:** Margin is the space *outside* the gift box (distance from other boxes). Padding is the space *inside* the box (distance from the box edge to the gift). `mt-5` means "leave a big gap above this box." `p-4` means "add cushioning inside the box."

---

### Text Utilities

| Class         | What It Does                        |
|---------------|-------------------------------------|
| `text-center` | Centers text horizontally           |
| `text-start`  | Aligns text to the left (default)   |
| `text-end`    | Aligns text to the right            |
| `text-muted`  | Makes text light gray (de-emphasized) |
| `fw-bold`     | Makes text bold (font-weight: bold) |
| `fw-light`    | Makes text light                    |
| `fs-4`        | Sets font size (1=largest, 6=smallest) |
| `fs-5`        | Slightly smaller font size          |
| `lead`        | Makes a paragraph stand out (larger, lighter) |
| `lh-lg`       | Increases line height for readability |

---

## 📖 Bootstrap Cards

A **card** is one of Bootstrap's most versatile components. Think of it as a rectangular box with optional header, body, image, and footer — like a playing card that can hold any content.

**Basic card structure:**

```html
<div class="card">
    <div class="card-body">
        <h5 class="card-title">Title</h5>
        <p class="card-text">Some content goes here.</p>
    </div>
</div>
```

**Card with centered content (what we'll use for info cards):**

```html
<div class="card h-100 text-center">
    <div class="card-body">
        <div class="fs-1 mb-3">🎯</div>
        <h5 class="card-title">Our Vision</h5>
        <p class="card-text">To be a leading department...</p>
    </div>
</div>
```

| Class        | What It Does                                    |
|--------------|-------------------------------------------------|
| `card`       | The card container (adds border, rounded corners) |
| `card-body`  | Adds padding inside the card                     |
| `card-title` | Styles the card heading                          |
| `card-text`  | Styles the card paragraph                        |
| `h-100`      | Makes the card full height (equal-height cards in a row) |

---

## 🔨 Let's Build! — Step by Step

Open the `index.html` file you've been building since Session 1. We'll add the About section **after** the hero carousel and **before** the closing `</body>` tag.

---

### Step 1: Add a `<section>` for About

> 📌 **First Time Seeing This? — `<section>`**
>
> The `<section>` tag is a **semantic HTML5 element** that represents a thematic grouping of content. Think of it like a chapter in a book — each major part of your webpage gets its own `<section>`. It tells the browser (and screen readers) "this is one distinct part of the page."
>
> Unlike `<div>` which means nothing ("just a box"), `<section>` says "this content belongs together as a group."

Add this right after your hero carousel's closing `</div>`:

```html
<!-- ============================================ -->
<!-- ABOUT SECTION                                -->
<!-- ============================================ -->
<section id="about" class="py-5">
    <div class="container">
        <!-- Content will go here -->
    </div>
</section>
```

- `id="about"` — so the navbar link `href="#about"` scrolls here.
- `class="py-5"` — padding on top and bottom (3rem each) to give the section breathing room.
- `class="container"` — centers the content and sets a max-width.

---

### Step 2: Add the Section Heading

> 📌 **First Time Seeing This? — `<h2>`**
>
> You've used `<h1>` for the page title (in the hero). `<h2>` is a **second-level heading** — like a chapter title. HTML has 6 heading levels: `<h1>` (most important) through `<h6>` (least important). Use them in order — don't skip from `<h1>` to `<h4>`. This helps screen readers and search engines understand your page structure.

```html
<section id="about" class="py-5">
    <div class="container">
        <h2 class="text-center fw-bold mb-4">About BCA Department</h2>
        <p class="text-center text-muted mb-5">Shaping the future of technology, one student at a time.</p>
    </div>
</section>
```

- `text-center` — centers the heading.
- `fw-bold` — makes it bold.
- `mb-4` — margin-bottom of 1.5rem (space between heading and content below).
- `text-muted` — the subtitle is a lighter gray color, making it visually secondary.
- `mb-5` — larger margin-bottom to separate the subtitle from the content below.

---

### Step 3: Create the 2-Column Layout (Text + Image)

Now we use the grid! Add a `row` inside the container, with two `col-md-6` columns:

```html
<div class="row align-items-center g-4">
    <!-- Left Column: Department Description -->
    <div class="col-md-6">
        <!-- Text content goes here (Step 3a) -->
    </div>

    <!-- Right Column: Image -->
    <div class="col-md-6">
        <!-- Image goes here (Step 3b) -->
    </div>
</div>
```

- `row` — activates the 12-column grid system.
- `align-items-center` — vertically centers both columns (so if the text is shorter than the image, they align nicely in the middle).
- `g-4` — adds standard gutter (space) between the two columns.
- `col-md-6` — each column takes 6 out of 12 columns on medium screens and larger. On mobile (< 768px), each becomes full width and stacks vertically.

---

### Step 3a: Left Column — Department Description

> 📌 **First Time Seeing This? — `<strong>`**
>
> `<strong>` makes text **bold** AND tells the browser "this text is important." Compare with `<b>` which is just visual bold with no meaning. Use `<strong>` when the boldness conveys importance (like key facts). Use `<b>` when you just want the look (rare).

> 📌 **First Time Seeing This? — `<em>`**
>
> `<em>` makes text *italic* AND tells the browser "this text has emphasis." Compare with `<i>` which is just visual italic. Think of `<em>` as how you'd stress a word when reading aloud: "We are *committed* to excellence." Screen readers actually change their tone of voice for `<em>` text!

> 📌 **First Time Seeing This? — `<ul>`, `<ol>`, `<li>`**
>
> `<ul>` creates a **bullet list** (unordered). `<ol>` creates a **numbered list** (ordered). `<li>` is each **list item** inside either type of list. Think of a grocery list — if the order doesn't matter (buy milk, eggs, bread in any order), use `<ul>`. If the order matters (step 1, step 2, step 3 of a recipe), use `<ol>`.

```html
<!-- Left Column: Department Description -->
<div class="col-md-6">
    <h3 class="fw-bold mb-3">Welcome to BCA @ Mandsaur University</h3>
    <p class="lead lh-lg">
        The Department of Computer Applications is dedicated to nurturing
        the next generation of <em>technology leaders</em>. Since our
        establishment, we have been committed to providing
        <strong>quality education</strong> that blends theoretical
        knowledge with hands-on practical skills.
    </p>
    <p class="text-muted">
        Our curriculum is designed to meet industry demands, and our
        students consistently excel in academics, projects, and placements.
    </p>

    <ul class="list-unstyled mt-4">
        <li class="mb-2">🏫 <strong>Established:</strong> Part of Mandsaur University's growing tech family</li>
        <li class="mb-2">👨‍🎓 <strong>Students:</strong> 120+ bright minds across all years</li>
        <li class="mb-2">👩‍🏫 <strong>Faculty:</strong> 15+ experienced and dedicated educators</li>
        <li class="mb-2">💼 <strong>Focus:</strong> Web Development, Programming, Databases & more</li>
    </ul>
</div>
```

> 📌 **First Time Seeing This? — `<h3>`**
>
> `<h3>` is a **third-level heading**. We used `<h2>` for the section title ("About BCA Department") and now `<h3>` for a sub-section ("Welcome to BCA..."). This hierarchy helps structure your content — like a textbook has chapters (h2) and sub-topics (h3).

New Bootstrap classes used:
- `lead` — makes the paragraph slightly larger and lighter, creating a "introductory" look.
- `lh-lg` — increases line-height for better readability.
- `list-unstyled` — removes the default bullet points from the `<ul>`.
- `mb-2` — small bottom margin on each list item.

---

### Step 3b: Right Column — Image with Caption

> 📌 **First Time Seeing This? — `<figure>` and `<figcaption>`**
>
> `<figure>` wraps an image (or diagram, code snippet, etc.) that is referenced from the main text. `<figcaption>` provides a caption for it. Think of it like a photo in a newspaper — the photo is the `<figure>` and the text below saying "Students at the annual fest" is the `<figcaption>`.

```html
<!-- Right Column: Image -->
<div class="col-md-6 text-center">
    <figure>
        <img src="https://placehold.co/600x400/0d6efd/white?text=BCA+Department"
             alt="BCA Department at Mandsaur University"
             class="img-fluid rounded shadow">
        <figcaption class="text-muted mt-2">
            <small>BCA Department — Mandsaur University Campus</small>
        </figcaption>
    </figure>
</div>
```

New Bootstrap classes used:
- `img-fluid` — makes the image responsive (scales down on small screens, never exceeds its container).
- `rounded` — adds slightly rounded corners to the image.
- `shadow` — adds a subtle drop shadow for a professional look.

> 💡 **Placeholder Image:** We're using `placehold.co` — a free service that generates placeholder images. Later you can replace this URL with a real photo of your campus. The format is: `https://placehold.co/WIDTHxHEIGHT/BGCOLOR/TEXTCOLOR?text=YOUR+TEXT`

---

### Step 4: Add the 3 Info Cards (Vision, Mission, Values)

Now let's add three cards below the 2-column layout but still inside the same `<section>`. We'll use another `row` with three `col-md-4` columns:

> 📌 **First Time Seeing This? — `<article>`**
>
> The `<article>` tag represents a **self-contained piece of content** that could stand on its own — like a blog post, a news story, or in our case, an info card. Each card has its own heading, text, and meaning. If you pulled one card out and put it on a different page, it would still make sense. That's the test for `<article>`.

```html
<!-- Info Cards Row -->
<div class="row g-4 mt-4">

    <!-- Card 1: Vision -->
    <div class="col-md-4">
        <article class="card h-100 text-center border-0 shadow-sm">
            <div class="card-body p-4">
                <div class="fs-1 mb-3">🎯</div>
                <h3 class="card-title fw-bold">Our Vision</h3>
                <p class="card-text text-muted">
                    To be a nationally recognized department that produces
                    innovative and industry-ready IT professionals who
                    contribute to India's digital transformation.
                </p>
            </div>
        </article>
    </div>

    <!-- Card 2: Mission -->
    <div class="col-md-4">
        <article class="card h-100 text-center border-0 shadow-sm">
            <div class="card-body p-4">
                <div class="fs-1 mb-3">🚀</div>
                <h3 class="card-title fw-bold">Our Mission</h3>
                <p class="card-text text-muted">
                    To deliver high-quality education through modern
                    curriculum, practical labs, industry exposure, and
                    a supportive learning environment for every student.
                </p>
            </div>
        </article>
    </div>

    <!-- Card 3: Values -->
    <div class="col-md-4">
        <article class="card h-100 text-center border-0 shadow-sm">
            <div class="card-body p-4">
                <div class="fs-1 mb-3">💡</div>
                <h3 class="card-title fw-bold">Our Values</h3>
                <p class="card-text text-muted">
                    Innovation, integrity, teamwork, and a commitment
                    to continuous learning. We believe every student has
                    the potential to excel in the tech world.
                </p>
            </div>
        </article>
    </div>

</div><!-- /Info Cards Row -->
```

**Why `col-md-4`?** → 4 + 4 + 4 = 12 columns. Three equal cards on medium screens and larger. On mobile (< 768px), each card takes full width and stacks vertically.

**Why `h-100`?** → Forces all cards to be the same height within the row. Without this, if one card has more text, it would be taller than the others — `h-100` prevents that.

**Why `border-0 shadow-sm`?** → Removes the default card border and adds a subtle shadow instead — a cleaner, more modern look.

---

### Step 5: Complete About Section Code

Here is the complete `<section>` — copy this and add it after your hero carousel:

```html
<!-- ============================================ -->
<!-- ABOUT SECTION                                -->
<!-- ============================================ -->
<section id="about" class="py-5">
    <div class="container">

        <!-- Section Heading -->
        <h2 class="text-center fw-bold mb-4">About BCA Department</h2>
        <p class="text-center text-muted mb-5">
            Shaping the future of technology, one student at a time.
        </p>

        <!-- Two-Column Layout: Text + Image -->
        <div class="row align-items-center g-4">

            <!-- Left Column: Description -->
            <div class="col-md-6">
                <h3 class="fw-bold mb-3">Welcome to BCA @ Mandsaur University</h3>
                <p class="lead lh-lg">
                    The Department of Computer Applications is dedicated to
                    nurturing the next generation of <em>technology leaders</em>.
                    Since our establishment, we have been committed to providing
                    <strong>quality education</strong> that blends theoretical
                    knowledge with hands-on practical skills.
                </p>
                <p class="text-muted">
                    Our curriculum is designed to meet industry demands, and our
                    students consistently excel in academics, projects, and
                    placements.
                </p>
                <ul class="list-unstyled mt-4">
                    <li class="mb-2">🏫 <strong>Established:</strong> Part of Mandsaur University's growing tech family</li>
                    <li class="mb-2">👨‍🎓 <strong>Students:</strong> 120+ bright minds across all years</li>
                    <li class="mb-2">👩‍🏫 <strong>Faculty:</strong> 15+ experienced and dedicated educators</li>
                    <li class="mb-2">💼 <strong>Focus:</strong> Web Development, Programming, Databases & more</li>
                </ul>
            </div>

            <!-- Right Column: Image -->
            <div class="col-md-6 text-center">
                <figure>
                    <img src="https://placehold.co/600x400/0d6efd/white?text=BCA+Department"
                         alt="BCA Department at Mandsaur University"
                         class="img-fluid rounded shadow">
                    <figcaption class="text-muted mt-2">
                        <small>BCA Department — Mandsaur University Campus</small>
                    </figcaption>
                </figure>
            </div>

        </div><!-- /Two-Column Row -->

        <!-- Info Cards: Vision, Mission, Values -->
        <div class="row g-4 mt-4">

            <!-- Card 1: Vision -->
            <div class="col-md-4">
                <article class="card h-100 text-center border-0 shadow-sm">
                    <div class="card-body p-4">
                        <div class="fs-1 mb-3">🎯</div>
                        <h3 class="card-title fw-bold">Our Vision</h3>
                        <p class="card-text text-muted">
                            To be a nationally recognized department that produces
                            innovative and industry-ready IT professionals who
                            contribute to India's digital transformation.
                        </p>
                    </div>
                </article>
            </div>

            <!-- Card 2: Mission -->
            <div class="col-md-4">
                <article class="card h-100 text-center border-0 shadow-sm">
                    <div class="card-body p-4">
                        <div class="fs-1 mb-3">🚀</div>
                        <h3 class="card-title fw-bold">Our Mission</h3>
                        <p class="card-text text-muted">
                            To deliver high-quality education through modern
                            curriculum, practical labs, industry exposure, and
                            a supportive learning environment for every student.
                        </p>
                    </div>
                </article>
            </div>

            <!-- Card 3: Values -->
            <div class="col-md-4">
                <article class="card h-100 text-center border-0 shadow-sm">
                    <div class="card-body p-4">
                        <div class="fs-1 mb-3">💡</div>
                        <h3 class="card-title fw-bold">Our Values</h3>
                        <p class="card-text text-muted">
                            Innovation, integrity, teamwork, and a commitment
                            to continuous learning. We believe every student has
                            the potential to excel in the tech world.
                        </p>
                    </div>
                </article>
            </div>

        </div><!-- /Info Cards Row -->

    </div><!-- /container -->
</section>
```

---

### Full Cumulative Code — `index.html`

Here is your **complete** `index.html` after Sessions 1, 2, and 3. This includes the navbar, hero carousel, and the new About section:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BCA Batch 2025-26 — Our Class Website</title>

    <!-- Bootstrap 5.3.2 CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
          rel="stylesheet">
</head>
<body>

    <!-- ============================================ -->
    <!-- NAVBAR (Session 1)                           -->
    <!-- ============================================ -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark sticky-top">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">🎓 BCA 2025-26</a>
            <button class="navbar-toggler" type="button"
                    data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#about">About</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#faculty">Faculty</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#gallery">Gallery</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#contact">Contact</a>
                    </li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#"
                           role="button" data-bs-toggle="dropdown">
                            More
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#timetable">Timetable</a></li>
                            <li><a class="dropdown-item" href="#faq">FAQ</a></li>
                            <li><hr class="dropdown-divider"></li>
                            <li><a class="dropdown-item" href="#login">Login</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- ============================================ -->
    <!-- HERO SECTION WITH CAROUSEL (Session 2)       -->
    <!-- ============================================ -->
    <section id="hero">
        <div id="heroCarousel" class="carousel slide" data-bs-ride="carousel">

            <!-- Indicators -->
            <div class="carousel-indicators">
                <button type="button" data-bs-target="#heroCarousel"
                        data-bs-slide-to="0" class="active"></button>
                <button type="button" data-bs-target="#heroCarousel"
                        data-bs-slide-to="1"></button>
                <button type="button" data-bs-target="#heroCarousel"
                        data-bs-slide-to="2"></button>
            </div>

            <!-- Slides -->
            <div class="carousel-inner">

                <!-- Slide 1 -->
                <div class="carousel-item active">
                    <img src="https://placehold.co/1400x500/0d6efd/white?text=Welcome+to+BCA+2025-26"
                         class="d-block w-100" alt="Welcome to BCA">
                    <div class="carousel-caption">
                        <h1>Welcome to BCA 2025-26</h1>
                        <p>Your journey in technology starts here.</p>
                    </div>
                </div>

                <!-- Slide 2 -->
                <div class="carousel-item">
                    <img src="https://placehold.co/1400x500/198754/white?text=Learn+%7C+Build+%7C+Grow"
                         class="d-block w-100" alt="Learn Build Grow">
                    <div class="carousel-caption">
                        <h1>Learn · Build · Grow</h1>
                        <p>Hands-on labs, real-world projects, and endless possibilities.</p>
                    </div>
                </div>

                <!-- Slide 3 -->
                <div class="carousel-item">
                    <img src="https://placehold.co/1400x500/6f42c1/white?text=Mandsaur+University"
                         class="d-block w-100" alt="Mandsaur University">
                    <div class="carousel-caption">
                        <h1>Mandsaur University</h1>
                        <p>Shaping future-ready IT professionals since day one.</p>
                    </div>
                </div>

            </div><!-- /carousel-inner -->

            <!-- Controls -->
            <button class="carousel-control-prev" type="button"
                    data-bs-target="#heroCarousel" data-bs-slide="prev">
                <span class="carousel-control-prev-icon"></span>
                <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button"
                    data-bs-target="#heroCarousel" data-bs-slide="next">
                <span class="carousel-control-next-icon"></span>
                <span class="visually-hidden">Next</span>
            </button>

        </div><!-- /heroCarousel -->
    </section>

    <!-- ============================================ -->
    <!-- ABOUT SECTION (Session 3) ★ NEW ★            -->
    <!-- ============================================ -->
    <section id="about" class="py-5">
        <div class="container">

            <!-- Section Heading -->
            <h2 class="text-center fw-bold mb-4">About BCA Department</h2>
            <p class="text-center text-muted mb-5">
                Shaping the future of technology, one student at a time.
            </p>

            <!-- Two-Column Layout: Text + Image -->
            <div class="row align-items-center g-4">

                <!-- Left Column: Description -->
                <div class="col-md-6">
                    <h3 class="fw-bold mb-3">Welcome to BCA @ Mandsaur University</h3>
                    <p class="lead lh-lg">
                        The Department of Computer Applications is dedicated to
                        nurturing the next generation of <em>technology leaders</em>.
                        Since our establishment, we have been committed to providing
                        <strong>quality education</strong> that blends theoretical
                        knowledge with hands-on practical skills.
                    </p>
                    <p class="text-muted">
                        Our curriculum is designed to meet industry demands, and our
                        students consistently excel in academics, projects, and
                        placements.
                    </p>
                    <ul class="list-unstyled mt-4">
                        <li class="mb-2">🏫 <strong>Established:</strong> Part of Mandsaur University's growing tech family</li>
                        <li class="mb-2">👨‍🎓 <strong>Students:</strong> 120+ bright minds across all years</li>
                        <li class="mb-2">👩‍🏫 <strong>Faculty:</strong> 15+ experienced and dedicated educators</li>
                        <li class="mb-2">💼 <strong>Focus:</strong> Web Development, Programming, Databases & more</li>
                    </ul>
                </div>

                <!-- Right Column: Image -->
                <div class="col-md-6 text-center">
                    <figure>
                        <img src="https://placehold.co/600x400/0d6efd/white?text=BCA+Department"
                             alt="BCA Department at Mandsaur University"
                             class="img-fluid rounded shadow">
                        <figcaption class="text-muted mt-2">
                            <small>BCA Department — Mandsaur University Campus</small>
                        </figcaption>
                    </figure>
                </div>

            </div><!-- /Two-Column Row -->

            <!-- Info Cards: Vision, Mission, Values -->
            <div class="row g-4 mt-4">

                <!-- Card 1: Vision -->
                <div class="col-md-4">
                    <article class="card h-100 text-center border-0 shadow-sm">
                        <div class="card-body p-4">
                            <div class="fs-1 mb-3">🎯</div>
                            <h3 class="card-title fw-bold">Our Vision</h3>
                            <p class="card-text text-muted">
                                To be a nationally recognized department that produces
                                innovative and industry-ready IT professionals who
                                contribute to India's digital transformation.
                            </p>
                        </div>
                    </article>
                </div>

                <!-- Card 2: Mission -->
                <div class="col-md-4">
                    <article class="card h-100 text-center border-0 shadow-sm">
                        <div class="card-body p-4">
                            <div class="fs-1 mb-3">🚀</div>
                            <h3 class="card-title fw-bold">Our Mission</h3>
                            <p class="card-text text-muted">
                                To deliver high-quality education through modern
                                curriculum, practical labs, industry exposure, and
                                a supportive learning environment for every student.
                            </p>
                        </div>
                    </article>
                </div>

                <!-- Card 3: Values -->
                <div class="col-md-4">
                    <article class="card h-100 text-center border-0 shadow-sm">
                        <div class="card-body p-4">
                            <div class="fs-1 mb-3">💡</div>
                            <h3 class="card-title fw-bold">Our Values</h3>
                            <p class="card-text text-muted">
                                Innovation, integrity, teamwork, and a commitment
                                to continuous learning. We believe every student has
                                the potential to excel in the tech world.
                            </p>
                        </div>
                    </article>
                </div>

            </div><!-- /Info Cards Row -->

        </div><!-- /container -->
    </section>

    <!-- Bootstrap 5.3.2 JS Bundle -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

---

## ✅ Checkpoint — Does Your Page Match?

Open `index.html` in Chrome and verify:

**Desktop (make your browser window wide):**
- [ ] Section heading "About BCA Department" is centered below the hero
- [ ] Two columns side by side — text on the left, image on the right
- [ ] Image has rounded corners and a shadow
- [ ] Three cards (Vision, Mission, Values) are in one row below the text
- [ ] All three cards have equal height

**Mobile (press F12 → click the phone icon → choose iPhone SE):**
- [ ] Text and image stack vertically (text first, image below)
- [ ] All three cards stack vertically (one per row)
- [ ] Everything is readable and nothing overflows the screen

**Navbar link test:**
- [ ] Click "About" in the navbar → page scrolls to the About section

> 🐛 **Something broken?** Check these common mistakes:
> - Missing `row` class on the parent div (columns won't go side by side)
> - Columns don't add up to 12 (content may wrap unexpectedly)
> - `col-md-6` typo (e.g., `col-m-6` won't work — Bootstrap doesn't have `m` prefix)
> - Missing `container` class (content stretches edge to edge)
> - Forgot to close a `<div>` tag (count your opening and closing tags!)

---

## 🔍 HTML & CSS Quick Reference

All new tags, attributes, and Bootstrap classes introduced in this session:

| # | Tag / Class          | Type        | What It Does                                            |
|---|----------------------|-------------|--------------------------------------------------------|
| 1 | `<section>`          | HTML tag    | Semantic container for a thematic page section          |
| 2 | `<article>`          | HTML tag    | Self-contained content (could stand alone)              |
| 3 | `<h2>`               | HTML tag    | Second-level heading (section title)                    |
| 4 | `<h3>`               | HTML tag    | Third-level heading (sub-section title)                 |
| 5 | `<strong>`           | HTML tag    | Bold text with semantic importance                      |
| 6 | `<em>`               | HTML tag    | Italic text with semantic emphasis                      |
| 7 | `<br>`               | HTML tag    | Line break — forces text to next line (use sparingly)   |
| 8 | `<ul>`               | HTML tag    | Unordered (bullet) list                                 |
| 9 | `<ol>`               | HTML tag    | Ordered (numbered) list                                 |
| 10| `<li>`               | HTML tag    | List item (inside `<ul>` or `<ol>`)                     |
| 11| `<figure>`           | HTML tag    | Wraps an image with optional caption                    |
| 12| `<figcaption>`       | HTML tag    | Caption text for a `<figure>`                           |
| 13| `container`          | Bootstrap   | Centers content, sets max-width, adds side padding      |
| 14| `row`                | Bootstrap   | Creates a horizontal group — enables 12-column grid     |
| 15| `col-md-6`           | Bootstrap   | 6/12 columns (half width) on medium screens and up      |
| 16| `col-md-4`           | Bootstrap   | 4/12 columns (one-third) on medium screens and up       |
| 17| `g-4`                | Bootstrap   | Gutter (space between columns) — standard size          |
| 18| `py-5`               | Bootstrap   | Padding on Y-axis (top + bottom) — 3rem                 |
| 19| `mt-4`, `mb-3`       | Bootstrap   | Margin-top / margin-bottom                              |
| 20| `text-center`        | Bootstrap   | Centers text horizontally                               |
| 21| `text-muted`         | Bootstrap   | Light gray text (de-emphasized)                         |
| 22| `fw-bold`            | Bootstrap   | Bold font weight                                        |
| 23| `fs-1`               | Bootstrap   | Font size level 1 (largest)                             |
| 24| `lead`               | Bootstrap   | Larger, lighter paragraph text (intro style)            |
| 25| `lh-lg`              | Bootstrap   | Increased line-height for readability                   |
| 26| `list-unstyled`      | Bootstrap   | Removes bullet points from `<ul>`                       |
| 27| `img-fluid`          | Bootstrap   | Responsive image (scales to container)                  |
| 28| `rounded`            | Bootstrap   | Adds rounded corners                                    |
| 29| `shadow` / `shadow-sm`| Bootstrap  | Adds drop shadow (regular / small)                      |
| 30| `card`, `card-body`  | Bootstrap   | Card component and its padded inner area                |
| 31| `card-title`, `card-text` | Bootstrap | Card heading and paragraph styles                   |
| 32| `h-100`              | Bootstrap   | Full height (equalizes card heights in a row)           |
| 33| `border-0`           | Bootstrap   | Removes default border                                  |
| 34| `align-items-center` | Bootstrap   | Vertically centers items in a flex row                  |
| 35| `p-4`                | Bootstrap   | Padding on all sides — 1.5rem                           |

---

## 📝 Key Takeaways

1. **The grid is always 12 columns.** Every row is divided into 12 invisible columns. Your content pieces share those 12 columns (6+6, 4+4+4, 3+3+3+3, etc.).

2. **Always follow Container → Row → Col.** Never put a `col` directly inside a `container`. Never put a `row` outside a `container`. This three-level hierarchy is non-negotiable.

3. **Bootstrap is mobile-first.** `col-md-6` means "be 6 columns on medium and up, be full width on anything smaller." You design for mobile by default and add breakpoint classes for larger screens.

4. **Use semantic HTML tags.** `<section>` for page sections, `<article>` for self-contained content, `<strong>` for important text (not just `<b>`), `<em>` for emphasis (not just `<i>`). These help accessibility and SEO.

5. **Spacing utilities save you from writing CSS.** `mt-5`, `py-3`, `mb-4` — memorize the format `{m|p}{t|b|s|e|x|y}-{0-5}` and you'll rarely need custom margin/padding CSS.

6. **Cards + Grid = powerful layouts.** A `row` of `col-md-4` divs containing `card` components is one of the most common patterns in modern web design. You'll use this pattern in almost every website you build.

---

## 🏋️ Practice Challenges

Try these on your own to strengthen your grid skills:

### Challenge 1: Add a 4th Card — "Our Achievements" 🏆

Add a fourth card to the info cards row. You'll need to change the column class from `col-md-4` to `col-md-6 col-lg-3` so all four cards fit in one row on large screens and pair up (2 per row) on medium screens.

```html
<!-- Hint: Change ALL four cards to this column class -->
<div class="col-md-6 col-lg-3">
    <article class="card h-100 text-center border-0 shadow-sm">
        <div class="card-body p-4">
            <div class="fs-1 mb-3">🏆</div>
            <h3 class="card-title fw-bold">Our Achievements</h3>
            <p class="card-text text-muted">
                University rank holders, hackathon winners, and students
                placed at top IT companies across India.
            </p>
        </div>
    </article>
</div>
```

### Challenge 2: Change the About Layout to 4 + 8

Instead of the current 6 + 6 (equal split), try a **sidebar + main** layout:
- Left column: change `col-md-6` to `col-md-4` (narrow sidebar with highlights only)
- Right column: change `col-md-6` to `col-md-8` (wider area with text + image)

See how the balance of the page changes. Experiment with `col-lg-3` + `col-lg-9` too.

### Challenge 3: Add a Background Color

Add `bg-light` to the `<section>` tag to give the About section a light gray background:

```html
<section id="about" class="py-5 bg-light">
```

Try other colors too: `bg-white`, `bg-dark text-white`, `bg-primary text-white`. Notice how `bg-dark` requires `text-white` to keep the text readable.

---

## 🔗 Labs Covered in This Session

| Lab # | Experiment Description                           | Status | How It's Covered                                        |
|-------|--------------------------------------------------|--------|---------------------------------------------------------|
| 1     | Department webpage with paragraphs and lists     | ✅     | About section uses `<p>`, `<ul>`, `<li>`, `<strong>`, `<em>` |
| 25    | Bootstrap layout with navbar, header, 3-column   | ✅     | Grid system with `container`, `row`, `col-md-*`, 3 cards in a row |

**Running total: Labs 1, 2, 15, 16, 25, 27, 28 covered (7 of 30)**

---

## ⏭️ Next Session: JavaScript Foundations

In **Session 4**, we leave Bootstrap layout behind for a session and dive into **JavaScript** — the programming language of the web!

You'll learn:
- Variables, data types, and operators
- `alert()`, `prompt()`, and `console.log()`
- Functions — writing reusable blocks of code
- Show/hide elements on the page (your first DOM manipulation!)

> **Bring your thinking cap — it's coding time!** 🧠💻

---

*Session 3 of 15 — Crash Course: Bootstrap + JavaScript — BCA Semester II, Mandsaur University, 2025-26*
