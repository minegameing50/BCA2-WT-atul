# Session 2: "Making an Impression" — Hero Section + Image Carousel

| Detail | Info |
|--------|------|
| **Session** | 2 of 15 |
| **Topic** | Hero Section + Bootstrap Image Carousel |
| **Labs Covered** | Lab 16 (Image Slider), Lab 27 (Carousel with Navigation) |
| **Duration** | 2-hour practical lab |
| **Previous** | [Session 1 — Project Setup + Responsive Navbar](Session-01-Setup-and-Navbar.md) |
| **Next** | [Session 3 — About Section + Grid System](Session-03-About-Section-and-Grid.md) |
| **Bootstrap** | 5.3.2 via CDN |
| **JavaScript** | Just `console.log()` — a tiny taste! |

---

## 🎯 What We'll Build Today

Today, we're building the **hero section** of our BCA Class Website — the very first thing visitors see when they open the page.

> **Real-world analogy:** Think about the front gate of Mandsaur University. When someone visits the campus for the first time, what's the first thing they see? The grand entrance, the name board, maybe a welcome banner. The hero section is exactly that — the **front gate of your website**. It's the first impression, and it needs to look impressive.

Here's what we'll add:

- 🖼️ A **full-width image carousel** (slideshow) that automatically cycles through 3 beautiful images
- 📝 **Overlay text** on each slide — welcoming visitors to BCA Batch 2025-26
- ◀️▶️ **Navigation arrows** and **indicator dots** to manually browse slides
- 🔘 A **Call-to-Action (CTA) button** — "Explore Our Class →" — that invites visitors to scroll down
- 🧠 A **tiny introduction to JavaScript** — just one line in the console!

By the end of this session, your page will go from a plain navbar with a paragraph to a **stunning, professional-looking landing page** that auto-plays a slideshow with text and buttons.

**Before (Session 1):**
```
[====== Navbar ======]
This is our BCA Class Website...
```

**After (Session 2):**
```
[======= Navbar =======]
[                         ]
[   🖼️ Beautiful Image    ]
[   "Welcome to BCA..."   ]
[   [Explore Our Class →] ]
[                         ]
[  ● ○ ○    ◄  ►         ]
```

---

## 📌 New HTML & CSS Tags

Here are the **new** HTML tags and attributes you'll meet for the first time in this session. If a tag appeared in Session 1, we won't re-explain it — just use it!

| Tag / Attribute | What It Does | First Time? |
|----------------|--------------|:-----------:|
| `<section>` | Groups related content (like a chapter in a book) | ✅ NEW |
| `<h1>` | Main heading — the biggest, most important title | ✅ NEW |
| `<h2>` | Sub-heading — second level title | ✅ NEW |
| `<p>` | Paragraph — a block of text | ✅ NEW |
| `<img>` | Displays an image (with `src`, `alt`, `width`, `height`) | ✅ NEW |
| `<a>` (as button) | A link styled as a button using Bootstrap classes | ✅ NEW (as button) |
| `<script>` | Embeds JavaScript code in the page | ✅ NEW |
| `<div>` | Generic container for grouping elements | Session 1 |
| `<ul>`, `<li>` | Unordered list and list items | Session 1 |
| `<nav>` | Navigation bar container | Session 1 |
| `<span>` | Inline container for text | Session 1 |

> 💡 **Remember from Session 1:** We already learned `<div>`, `<ul>`, `<li>`, `<nav>`, `<span>`, `<button>`, `<a>` (as link), and `<input>`. We won't explain those again — refer to Session 1 if you need a refresher!

---

## 📌 First Time Seeing `<section>`?

```html
<section id="home">
    ...content goes here...
</section>
```

Think of `<section>` as a **chapter in a textbook**. Your entire website is the book, and each major part (Hero, About, Faculty, Contact) is a chapter. The `<section>` tag tells the browser: *"This is one distinct part of the page."*

**Why not just use `<div>`?** You *could*, but `<section>` is **semantic** — it carries meaning. It tells search engines and screen readers that this is a meaningful group of content, not just a random box. Think of it like labeling a folder "Exam Papers" vs. just putting papers in a plain folder.

The `id="home"` attribute gives this section a **unique name** so our navbar link `href="#home"` can jump directly here (like a bookmark in a book).

---

## 📌 First Time Seeing `<h1>` and `<h2>`?

```html
<h1>Welcome to BCA Batch 2025-26</h1>
<h2>Department of Computer Applications</h2>
```

HTML has **six heading levels**: `<h1>` (biggest, most important) through `<h6>` (smallest). Think of them like the hierarchy on a university noticeboard:

| Heading | Analogy | Example |
|---------|---------|---------|
| `<h1>` | University name on the main gate | "Mandsaur University" |
| `<h2>` | Department name on the building | "Department of Computer Applications" |
| `<h3>` | Section within department | "BCA Program" |
| `<h4>` | Subsection | "Semester II Subjects" |
| `<h5>` | Specific detail | "Web Technology" |
| `<h6>` | Fine print | "Lab Schedule" |

**Rule of thumb:** Use only ONE `<h1>` per page (it's like the page title), and use `<h2>`, `<h3>`, etc. for sub-sections — just like headings in a Word document.

---

## 📌 First Time Seeing `<p>`?

```html
<p>Building the future, one website at a time.</p>
```

The `<p>` tag creates a **paragraph** — a block of text with automatic spacing above and below it. Think of it like pressing Enter twice in a Word document to start a new paragraph. Browsers automatically add some margin above and below `<p>` elements so they don't stick together.

> **Note:** If you just write text without `<p>`, it will appear on the page, but it won't have proper paragraph spacing and won't be semantically correct.

---

## 📌 First Time Seeing `<img>`?

```html
<img src="https://picsum.photos/1200/500?random=1"
     alt="BCA Students in computer lab"
     width="1200"
     height="500"
     class="d-block w-100">
```

The `<img>` tag puts an image on the page. It's a **self-closing tag** — no `</img>` needed! Let's understand each attribute:

| Attribute | What It Does | Analogy |
|-----------|-------------|---------|
| `src` | The image URL or file path | Like the address of a photo studio |
| `alt` | Text description if image can't load | Like a caption under a painting |
| `width` | Width in pixels | How wide the photo frame is |
| `height` | Height in pixels | How tall the photo frame is |

**Why `alt` matters:** If the image fails to load (slow internet!), the `alt` text appears instead. Also, screen readers for visually impaired students read the `alt` text aloud. **Always include `alt`!**

**About `https://picsum.photos/`:** This is a free service that gives us beautiful placeholder images. The numbers (1200/500) specify width × height. The `?random=1` gives us a different image each time. Later, you can replace these with real BCA class photos!

---

## 📌 First Time Seeing `<a>` Used as a Button?

```html
<a href="#about" class="btn btn-lg btn-light">Explore Our Class →</a>
```

Wait — isn't `<a>` a link? Yes! But with Bootstrap's `btn` classes, we can make it *look and feel* like a button. Think of it this way:

- `<a>` is like a **direction sign** — it points somewhere
- `<button>` is like a **switch** — it triggers an action

When we want something that **looks like a button but goes to a section on the page**, using `<a>` with `btn` classes is perfect. The `href="#about"` makes it scroll to the About section (which we'll build in Session 3).

---

## 📌 First Time Seeing `<script>`?

```html
<script>
    console.log("BCA Class Website loaded!");
</script>
```

The `<script>` tag is where JavaScript lives inside an HTML page. Think of it as a **smart notice board** — while HTML is the static structure and CSS is the decoration, the `<script>` tag lets you add behavior and logic.

**Where to place it?** Always at the **end of the `<body>`**, just before `</body>`. Why? Because the browser reads your page from top to bottom — if JavaScript runs before the HTML loads, it might try to modify elements that don't exist yet! It's like trying to arrange furniture in a room that hasn't been built yet.

---

## 📖 Bootstrap Carousel — How It Works

### What Is a Carousel?

A carousel (also called a **slider** or **slideshow**) is a component that cycles through images or content, one at a time, with smooth slide transitions.

> **Analogy:** Imagine a **photo album on a table**. You flip through pages one at a time — you can go forward, go backward, or just let someone flip the pages for you automatically. That's exactly what a Bootstrap carousel does on a webpage!

You've seen carousels everywhere — on Amazon (product images), on news websites (featured stories), and on college websites (campus photos). Now you'll build one!

### Carousel Structure

A Bootstrap carousel has a specific hierarchy — like a Russian nesting doll (Matryoshka). Each part fits inside the other:

```
carousel (the outer shell)
├── carousel-indicators (the dots at the bottom: ● ○ ○)
├── carousel-inner (the container holding all slides)
│   ├── carousel-item (Slide 1) ← one of these is "active"
│   │   ├── img (the slide image)
│   │   └── carousel-caption (text overlay on the slide)
│   ├── carousel-item (Slide 2)
│   │   ├── img
│   │   └── carousel-caption
│   └── carousel-item (Slide 3)
│       ├── img
│       └── carousel-caption
├── carousel-control-prev (← left arrow button)
└── carousel-control-next (→ right arrow button)
```

### Understanding Each Part

**1. The Carousel Container:**
```html
<div id="heroCarousel" class="carousel slide" data-bs-ride="carousel">
```
- `id="heroCarousel"` — a unique name so controls can target this specific carousel
- `class="carousel"` — tells Bootstrap "this is a carousel component"
- `class="slide"` — adds the smooth sliding animation
- `data-bs-ride="carousel"` — makes it auto-play (like setting a photo slideshow to automatic)

**2. Indicators (the dots):**
```html
<div class="carousel-indicators">
    <button data-bs-target="#heroCarousel" data-bs-slide-to="0" class="active"></button>
    <button data-bs-target="#heroCarousel" data-bs-slide-to="1"></button>
    <button data-bs-target="#heroCarousel" data-bs-slide-to="2"></button>
</div>
```
- These are the small dots at the bottom (● ○ ○)
- `data-bs-target` points to which carousel they control (by id)
- `data-bs-slide-to="0"` means "jump to slide number 0" (computers count from 0!)
- `class="active"` marks which dot is currently highlighted

**3. Slides (carousel-inner + carousel-item):**
```html
<div class="carousel-inner">
    <div class="carousel-item active">
        <img src="..." class="d-block w-100" alt="...">
    </div>
    <div class="carousel-item">
        <img src="..." class="d-block w-100" alt="...">
    </div>
</div>
```
- `carousel-inner` wraps ALL the slides together
- Each `carousel-item` is ONE slide
- **Exactly one item must have `class="active"`** — this is the slide shown first
- `d-block` makes the image a block element (takes full width)
- `w-100` makes the image 100% width of its container

> 🤔 **Why does one item need "active"?** Think of it like a PowerPoint presentation — when you open it, one slide is already showing. The `active` class tells Bootstrap which slide to show first.

**4. Captions (text overlay):**
```html
<div class="carousel-caption d-none d-md-block">
    <h1>Welcome to BCA Batch 2025-26</h1>
    <p>Department of Computer Applications, Mandsaur University</p>
</div>
```
- `carousel-caption` positions text over the image
- `d-none d-md-block` means: hide captions on small phones (they'd overlap badly), show them on medium screens and above
- You can put any HTML inside the caption — headings, paragraphs, buttons!

**5. Controls (arrows):**
```html
<button class="carousel-control-prev" data-bs-target="#heroCarousel" data-bs-slide="prev">
    <span class="carousel-control-prev-icon"></span>
    <span class="visually-hidden">Previous</span>
</button>
```
- `carousel-control-prev` / `carousel-control-next` — the left and right arrow buttons
- `data-bs-slide="prev"` / `data-bs-slide="next"` — the direction to go
- `visually-hidden` — text for screen readers (not visible on screen, but accessible)

### Auto-Play and Interval

By default, `data-bs-ride="carousel"` makes the carousel start sliding automatically. You can control the speed:

```html
<!-- Change slide every 3 seconds (3000 milliseconds) -->
<div class="carousel slide" data-bs-ride="carousel" data-bs-interval="3000">

<!-- Change a specific slide's display time -->
<div class="carousel-item" data-bs-interval="5000">
```

- Default interval: **5000ms** (5 seconds)
- Set `data-bs-interval="false"` on the carousel to disable auto-play
- Or simply remove `data-bs-ride="carousel"` to disable auto-play entirely

---

## 📖 Bootstrap Hero Section Pattern

A **hero section** is a large, prominent section at the top of a webpage — usually with a big image, bold text, and a call-to-action button. Think of movie posters — big image, title, "Coming Soon" text, and a "Buy Tickets" button. That's a hero section!

Bootstrap doesn't have a specific "hero" component, but we create one using a combination of utilities:

### Key Bootstrap Classes for Hero Sections

**Padding Utilities (spacing):**
| Class | What It Does |
|-------|-------------|
| `py-5` | Adds vertical padding (top + bottom), level 5 (3rem) |
| `px-3` | Adds horizontal padding (left + right), level 3 |
| `pt-5` | Padding top only |
| `pb-3` | Padding bottom only |

> **Analogy:** Padding is like the gap between the frame and the photo inside it. More padding = more breathing room around your content.

**Text Utilities:**
| Class | What It Does |
|-------|-------------|
| `display-4` | Very large heading (bigger than regular `<h1>`) |
| `lead` | Slightly larger, lighter paragraph text |
| `text-center` | Centers the text horizontally |
| `text-white` | Makes text white (great on dark backgrounds/images) |
| `fw-bold` | Makes text bold |

**Button Classes:**
| Class | What It Does |
|-------|-------------|
| `btn` | Base button class (required on all Bootstrap buttons) |
| `btn-primary` | Blue filled button |
| `btn-light` | Light/white filled button |
| `btn-outline-light` | White bordered button (transparent fill) |
| `btn-lg` | Makes the button larger |

**Image Classes:**
| Class | What It Does |
|-------|-------------|
| `img-fluid` | Makes image responsive (scales with container) |
| `w-100` | Image fills 100% width of parent |
| `d-block` | Display as block element (needed for carousel images) |

### Overlaying Text on a Carousel

In our design, we'll use the carousel itself as the hero background. The carousel captions serve as the hero text. This is a common and elegant pattern — the images create visual interest while the text communicates the message.

We'll also add a semi-transparent dark overlay (using inline styles) to ensure text is readable on any image:

```html
<div class="carousel-caption">
    <h1 class="display-4 fw-bold">Welcome to BCA</h1>
    <p class="lead">Department of Computer Applications</p>
    <a href="#about" class="btn btn-lg btn-light">Explore Our Class →</a>
</div>
```

---

## 📖 Brief JavaScript Introduction

### What Is JavaScript?

> **Analogy:** If HTML is the **skeleton** of a building (the structure — walls, floors, doors), and CSS is the **paint and decoration** (colors, curtains, tiles), then JavaScript is the **electricity and plumbing** — it makes things *work*. Lights turn on, doors open automatically, the elevator moves. JavaScript brings your webpage to life!

JavaScript (often shortened to **JS**) is a programming language that runs **inside the browser**. While HTML and CSS create a static, lifeless page, JavaScript makes it interactive — forms can validate input, buttons can show/hide content, images can slide, and data can be saved.

### Where Does JavaScript Go?

JavaScript code lives inside a `<script>` tag, placed at the **very end of the `<body>`**, just before `</body>`:

```html
<body>
    <!-- All your HTML content first -->
    <nav>...</nav>
    <section>...</section>

    <!-- JavaScript comes LAST -->
    <script>
        // Your JavaScript code here
    </script>
</body>
```

**Why at the end?** The browser reads the page top-to-bottom. If JavaScript runs before the page content loads, it might try to interact with elements that don't exist yet — like trying to turn on a fan in a room that hasn't been built!

### Your First Line of JavaScript

Today, we'll write just ONE line of JavaScript:

```javascript
console.log("BCA Class Website loaded!");
```

This line **prints a message to the browser's console** — a hidden developer tool where you can see messages from your code. It doesn't appear on the webpage itself; it's like a backstage monitor that only the developer can see.

### How to See the Console

1. Open your webpage in Google Chrome
2. Press **F12** (or right-click → "Inspect")
3. Click the **Console** tab at the top
4. You should see: `BCA Class Website loaded!`

This is how developers **debug** (find and fix problems in) their code. We'll use `console.log()` a LOT in future sessions!

> 🚀 **Don't worry!** We're just scratching the surface of JavaScript today. In **Session 4**, we'll dive deep into variables, functions, alerts, and making things appear/disappear. For now, just know that JavaScript exists and lives in `<script>` tags.

---

## 🔨 Let's Build! (Step-by-Step)

We'll take the code from Session 1 and add our hero section with the carousel. Follow each step carefully!

### Step 1: Start with Your Session 1 Code

Open the `index.html` file you created in Session 1. It should have a responsive navbar. Here's what it looks like (if yours is slightly different, that's okay — the navbar structure should be similar):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BCA Batch 2025-26 — Our Class Website</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">BCA 2025-26</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item"><a class="nav-link active" href="#home">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                    <li class="nav-item"><a class="nav-link" href="#faculty">Faculty</a></li>
                    <li class="nav-item"><a class="nav-link" href="#timetable">Timetable</a></li>
                    <li class="nav-item"><a class="nav-link" href="#gallery">Gallery</a></li>
                    <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" data-bs-toggle="dropdown">More</a>
                        <ul class="dropdown-menu dropdown-menu-end">
                            <li><a class="dropdown-item" href="#faq">FAQ</a></li>
                            <li><a class="dropdown-item" href="#login">Login</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Placeholder content from Session 1 -->
    <div class="container mt-5 pt-5">
        <p>Welcome to BCA Batch 2025-26 Class Website. Content coming soon...</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

### Step 2: Remove the Placeholder Content

Find and **delete** these lines:

```html
    <!-- Placeholder content from Session 1 -->
    <div class="container mt-5 pt-5">
        <p>Welcome to BCA Batch 2025-26 Class Website. Content coming soon...</p>
    </div>
```

We're replacing this with our hero section!

### Step 3: Add the Hero Section with Carousel Container

Right after the closing `</nav>` tag, add the hero `<section>` with the carousel container. The `style="padding-top: 56px;"` ensures the hero isn't hidden behind the fixed navbar (the navbar is approximately 56px tall):

```html
    <!-- ===================== -->
    <!-- HERO SECTION          -->
    <!-- ===================== -->
    <section id="home" style="padding-top: 56px;">
        <div id="heroCarousel" class="carousel slide" data-bs-ride="carousel">

            <!-- We'll add indicators, slides, and controls in the next steps -->

        </div>
    </section>
```

> 📝 **Why `padding-top: 56px;`?** Because our navbar has `fixed-top`, it floats above the page. Without this padding, the top part of our carousel would be hidden behind the navbar — like a painting hung too high behind a shelf!

### Step 4: Add Carousel Indicators (the Dots)

Inside the `heroCarousel` div, add the indicator dots. These let users click to jump to a specific slide:

```html
            <!-- Carousel Indicators (dots) -->
            <div class="carousel-indicators">
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="1" aria-label="Slide 2"></button>
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>
```

Notice:
- Three buttons for three slides
- `data-bs-slide-to="0"` — slides are numbered starting from 0 (like arrays in programming!)
- The first button has `class="active"` — it's highlighted by default
- `aria-label` helps screen readers announce "Slide 1", "Slide 2", etc.

### Step 5: Add Carousel Slides with Images

Below the indicators, add the `carousel-inner` with three slides:

```html
            <!-- Carousel Slides -->
            <div class="carousel-inner">

                <!-- Slide 1 (active — this shows first) -->
                <div class="carousel-item active">
                    <img src="https://picsum.photos/1200/500?random=1"
                         class="d-block w-100"
                         alt="BCA campus and students"
                         width="1200" height="500">
                </div>

                <!-- Slide 2 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=2"
                         class="d-block w-100"
                         alt="Students coding in computer lab"
                         width="1200" height="500">
                </div>

                <!-- Slide 3 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=3"
                         class="d-block w-100"
                         alt="Mandsaur University building"
                         width="1200" height="500">
                </div>

            </div>
```

> 💡 **Tip:** The `?random=1`, `?random=2`, `?random=3` at the end of each URL ensures we get **different** placeholder images. Later, you can replace these URLs with actual photos of your class!

### Step 6: Add Carousel Controls (Prev/Next Arrows)

After the `carousel-inner` closing div, add the navigation arrows:

```html
            <!-- Carousel Controls (arrows) -->
            <button class="carousel-control-prev" type="button" data-bs-target="#heroCarousel" data-bs-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#heroCarousel" data-bs-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Next</span>
            </button>
```

These create the `‹` and `›` arrow buttons on the left and right edges of the carousel.

- `aria-hidden="true"` on the icon means screen readers skip the icon itself
- `visually-hidden` text gives screen readers something meaningful to read ("Previous", "Next")

### Step 7: Add Carousel Captions with Overlay Text

Now let's go back to each `carousel-item` and add captions. Update each slide to include a `carousel-caption` div:

**Update Slide 1:**
```html
                <!-- Slide 1 (active — this shows first) -->
                <div class="carousel-item active">
                    <img src="https://picsum.photos/1200/500?random=1"
                         class="d-block w-100"
                         alt="BCA campus and students"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">Welcome to BCA Batch 2025-26</h1>
                        <p class="lead">Department of Computer Applications, Mandsaur University</p>
                    </div>
                </div>
```

**Update Slide 2:**
```html
                <!-- Slide 2 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=2"
                         class="d-block w-100"
                         alt="Students coding in computer lab"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">Learn. Code. Create.</h1>
                        <p class="lead">Building the future, one website at a time</p>
                    </div>
                </div>
```

**Update Slide 3:**
```html
                <!-- Slide 3 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=3"
                         class="d-block w-100"
                         alt="Mandsaur University building"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">15 Sessions. 1 Website. Unlimited Skills.</h1>
                        <p class="lead">Your crash course journey starts here</p>
                    </div>
                </div>
```

### Step 8: Add the CTA Button to the First Slide

Let's add the "Explore Our Class →" button to the **first slide's caption** so it's the first thing visitors see. Update the first slide's caption:

```html
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">Welcome to BCA Batch 2025-26</h1>
                        <p class="lead">Department of Computer Applications, Mandsaur University</p>
                        <a href="#about" class="btn btn-lg btn-light mt-3">Explore Our Class →</a>
                    </div>
```

The `mt-3` class adds a little margin above the button so it doesn't touch the paragraph text.

### Step 9: Add a Small JavaScript Line

Just before the Bootstrap JS `<script>` tag (at the bottom of `<body>`), add our first JavaScript:

```html
    <!-- Our first JavaScript! -->
    <script>
        console.log("BCA Class Website loaded!");
    </script>
```

After saving, open DevTools (F12 → Console tab) — you should see the message printed there!

### ✨ Complete Updated Code

Here is the **full `index.html`** with everything from Session 1 (navbar) + Session 2 (hero carousel + JS):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BCA Batch 2025-26 — Our Class Website</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

    <!-- ===================== -->
    <!-- NAVBAR (from Session 1) -->
    <!-- ===================== -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">BCA 2025-26</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item"><a class="nav-link active" href="#home">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                    <li class="nav-item"><a class="nav-link" href="#faculty">Faculty</a></li>
                    <li class="nav-item"><a class="nav-link" href="#timetable">Timetable</a></li>
                    <li class="nav-item"><a class="nav-link" href="#gallery">Gallery</a></li>
                    <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" data-bs-toggle="dropdown">More</a>
                        <ul class="dropdown-menu dropdown-menu-end">
                            <li><a class="dropdown-item" href="#faq">FAQ</a></li>
                            <li><a class="dropdown-item" href="#login">Login</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- ===================== -->
    <!-- HERO SECTION (Session 2) -->
    <!-- ===================== -->
    <section id="home" style="padding-top: 56px;">
        <div id="heroCarousel" class="carousel slide" data-bs-ride="carousel">

            <!-- Carousel Indicators (dots) -->
            <div class="carousel-indicators">
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="1" aria-label="Slide 2"></button>
                <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>

            <!-- Carousel Slides -->
            <div class="carousel-inner">

                <!-- Slide 1 (active — shows first) -->
                <div class="carousel-item active">
                    <img src="https://picsum.photos/1200/500?random=1"
                         class="d-block w-100"
                         alt="BCA campus and students"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">Welcome to BCA Batch 2025-26</h1>
                        <p class="lead">Department of Computer Applications, Mandsaur University</p>
                        <a href="#about" class="btn btn-lg btn-light mt-3">Explore Our Class →</a>
                    </div>
                </div>

                <!-- Slide 2 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=2"
                         class="d-block w-100"
                         alt="Students coding in computer lab"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">Learn. Code. Create.</h1>
                        <p class="lead">Building the future, one website at a time</p>
                    </div>
                </div>

                <!-- Slide 3 -->
                <div class="carousel-item">
                    <img src="https://picsum.photos/1200/500?random=3"
                         class="d-block w-100"
                         alt="Mandsaur University building"
                         width="1200" height="500">
                    <div class="carousel-caption d-none d-md-block">
                        <h1 class="display-4 fw-bold">15 Sessions. 1 Website. Unlimited Skills.</h1>
                        <p class="lead">Your crash course journey starts here</p>
                    </div>
                </div>

            </div>

            <!-- Carousel Controls (arrows) -->
            <button class="carousel-control-prev" type="button" data-bs-target="#heroCarousel" data-bs-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#heroCarousel" data-bs-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Next</span>
            </button>

        </div>
    </section>

    <!-- ===================== -->
    <!-- SCRIPTS               -->
    <!-- ===================== -->

    <!-- Our first JavaScript! -->
    <script>
        console.log("BCA Class Website loaded!");
    </script>

    <!-- Bootstrap JS (keep this last) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

> 💾 **Save the file (Ctrl+S) and refresh your browser (F5).** You should see the carousel auto-playing with three slides, captions, and navigation arrows!

---

## ✅ Checkpoint — Does Your Page Work?

Test each of these before moving on:

### Desktop (laptop/PC screen):

- [ ] The carousel takes up the full width of the browser window
- [ ] Three slides auto-play every 5 seconds
- [ ] Each slide has a different placeholder image
- [ ] Overlay text (headings and paragraphs) is visible on each slide
- [ ] The "Explore Our Class →" button appears on the first slide
- [ ] Left (‹) and right (›) arrow buttons work when clicked
- [ ] The three indicator dots at the bottom are visible and clickable
- [ ] The active indicator dot changes as slides change
- [ ] The navbar is still visible on top and doesn't overlap the carousel content
- [ ] Open DevTools (F12 → Console) and verify `BCA Class Website loaded!` appears

### Mobile (resize browser to narrow width, or use DevTools device mode):

- [ ] The carousel still works and slides fit the screen width
- [ ] Images scale down proportionally (no horizontal scrollbar)
- [ ] Captions are hidden on very small screens (this is intentional — `d-none d-md-block`)
- [ ] Arrow controls are still clickable
- [ ] The hamburger menu in the navbar still works

> ⚠️ **Image Loading:** Since we're using `picsum.photos` (an online service), images need internet. If images don't load, check your Wi-Fi! The placeholder images will be different each time you refresh — that's normal.

---

## 🔍 HTML & CSS Quick Reference — Session 2

All the **new** tags, attributes, and Bootstrap classes introduced in this session:

### New HTML Tags

| Tag | Purpose | Example |
|-----|---------|---------|
| `<section>` | Semantic grouping of related content | `<section id="home">...</section>` |
| `<h1>` | Main heading (largest) | `<h1>Welcome</h1>` |
| `<h2>` | Sub-heading (second largest) | `<h2>About Us</h2>` |
| `<p>` | Paragraph of text | `<p>Some text here.</p>` |
| `<img>` | Embeds an image | `<img src="photo.jpg" alt="Photo">` |
| `<script>` | Embeds JavaScript code | `<script>console.log("Hi");</script>` |

### New HTML Attributes

| Attribute | Used On | Purpose |
|-----------|---------|---------|
| `src` | `<img>` | Path/URL of the image file |
| `alt` | `<img>` | Text description of the image |
| `width` | `<img>` | Width of the image in pixels |
| `height` | `<img>` | Height of the image in pixels |
| `data-bs-ride` | Carousel div | Enables auto-play (`"carousel"`) |
| `data-bs-slide-to` | Indicator buttons | Jump to specific slide number |
| `data-bs-slide` | Control buttons | Go to `"prev"` or `"next"` slide |
| `data-bs-target` | Indicators/controls | Which carousel to control (by `#id`) |
| `aria-label` | Buttons | Accessibility label for screen readers |
| `aria-hidden` | Icons | Hides decorative elements from screen readers |
| `aria-current` | Active indicator | Marks the current item for accessibility |

### New Bootstrap Classes

| Class | What It Does |
|-------|-------------|
| `carousel` | Makes a div into a Bootstrap carousel |
| `slide` | Adds sliding animation to the carousel |
| `carousel-indicators` | Container for the dot indicators |
| `carousel-inner` | Container for all carousel slides |
| `carousel-item` | One individual slide |
| `carousel-caption` | Text overlay on a slide |
| `carousel-control-prev` | Left arrow button |
| `carousel-control-next` | Right arrow button |
| `carousel-control-prev-icon` | Left arrow icon (‹) |
| `carousel-control-next-icon` | Right arrow icon (›) |
| `d-block` | Sets display to block |
| `d-none` | Hides element (display: none) |
| `d-md-block` | Shows element on medium screens and above |
| `w-100` | Width: 100% of parent |
| `display-4` | Extra-large heading text |
| `lead` | Larger, lighter paragraph text |
| `fw-bold` | Font weight: bold |
| `text-center` | Center-align text |
| `text-white` | White text color |
| `btn` | Base Bootstrap button class |
| `btn-light` | Light/white button style |
| `btn-lg` | Large button size |
| `mt-3` | Margin-top level 3 (1rem) |
| `visually-hidden` | Hidden from view but readable by screen readers |
| `active` | Marks the currently shown slide/indicator |

### JavaScript (Just One!)

| Code | What It Does |
|------|-------------|
| `console.log("text")` | Prints a message to the browser's Developer Console |

---

## 📝 Key Takeaways

1. **The hero section is your website's first impression** — make it count! A carousel with overlay text creates a professional, engaging landing page.

2. **Bootstrap's carousel has a strict structure** — `carousel` → `carousel-inner` → `carousel-item`. Exactly ONE item must have the `active` class. Miss any of these, and the carousel won't work.

3. **`data-bs-*` attributes are Bootstrap's magic** — they let Bootstrap's JavaScript know what to do without you writing a single line of JS. `data-bs-ride="carousel"` auto-plays it, `data-bs-slide-to="0"` jumps to a slide, `data-bs-slide="prev"` goes backward.

4. **Semantic HTML matters** — using `<section>` instead of `<div>`, writing meaningful `alt` text for images, and using `visually-hidden` for accessibility are professional habits that separate good developers from great ones.

5. **JavaScript lives in `<script>` tags at the bottom of `<body>`** — and `console.log()` is your best debugging friend. We'll explore much more JavaScript starting in Session 4!

6. **The `fixed-top` navbar needs padding compensation** — always add `padding-top` to the first element after a fixed navbar, or your content will hide behind it. This is a common mistake even experienced developers make!

---

## 🏋️ Practice Challenges

Done early? Try these on your own:

### Challenge 1: Disable Auto-Play ⭐ (Easy)
Remove the `data-bs-ride="carousel"` attribute from the carousel container. Refresh the page. Does the carousel still slide on its own? (It shouldn't!) Now you'll need to use the arrows or dots to navigate. Add it back when done.

### Challenge 2: Add a 4th Slide ⭐⭐ (Medium)
Add a fourth slide to the carousel with:
- A different placeholder image: `https://picsum.photos/1200/500?random=4`
- Caption: **"Code Today. Lead Tomorrow."** / *"BCA — Where ideas become reality"*
- Don't forget to add a 4th indicator button with `data-bs-slide-to="3"`!

### Challenge 3: Change Button Style ⭐⭐ (Medium)
Change the CTA button from `btn-light` (solid white) to `btn-outline-light` (white border, transparent background). Compare how they look. Which one do you prefer? Try `btn-warning` and `btn-success` too!

### Challenge 4: Slow Down the Carousel ⭐ (Easy)
Add `data-bs-interval="8000"` to the carousel container to make each slide stay for 8 seconds instead of the default 5 seconds. Can you make just the second slide stay for 10 seconds while others remain at 5?

### Challenge 5: Add `console.log` Messages ⭐ (Easy)
Add more `console.log()` lines in the `<script>` tag:
```javascript
console.log("BCA Class Website loaded!");
console.log("Session 2: Hero Section + Carousel");
console.log("Built by: [Your Name]");
```
Open the Console (F12) and see all three messages!

---

## 🔗 Labs Covered in This Session

| Lab | Experiment | Status |
|-----|-----------|--------|
| **Lab 16** | Create a Bootstrap image slider with captions | ✅ Covered — Carousel with 3 slides and captions |
| **Lab 27** | Create a Bootstrap carousel with previous/next navigation | ✅ Covered — Full carousel with arrows, indicators, and auto-play |

> 🎓 When your examiner asks about image sliders or carousel navigation, you can confidently demonstrate this hero section!

---

## ⏭️ Coming Up Next — Session 3

### Session 3: "Who We Are" — About Section + Grid System

In the next session, we'll build the **About Department** section right below the hero. You'll learn:

- 🏗️ **Bootstrap Grid System** — the most powerful layout tool (rows and columns)
- 📦 **Cards** — beautiful content boxes for organizing information
- 📝 **Lists and paragraphs** — writing structured content about the BCA department
- 📐 **Responsive breakpoints** — how to make 3 columns on desktop become 1 column on mobile

> **Analogy preview:** The grid system is like a **tiffin box with compartments** — you decide how many compartments each row has, and what goes in each one. On a big plate (desktop), you have 3 compartments side by side. On a small plate (mobile), they stack on top of each other.

See you in Session 3! 🚀

---

*Session 2 of 15 — Crash Course: Bootstrap + JavaScript — BCA Semester II, Mandsaur University, 2025-26*
