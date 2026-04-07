# Session 6 — Data in Tables: Class Timetable + Loops & Arrays

**Labs Covered:** Lab 5 (Class timetable) • Lab 6 (University table layout)

> **Where we are:** Our website has a navbar, hero carousel, about section with info cards,  
> JavaScript foundations (alert, prompt, show/hide, click counter), and faculty cards with  
> Read More toggle. Today we add a **Class Timetable** — and learn how to make JavaScript  
> repeat things automatically!

---

## 🎯 What We'll Build Today

By the end of this session, our website will have:

1. A **"Class Timetable"** section with a full weekly schedule (Mon–Sat, 5 periods)
2. A **Bootstrap-styled responsive table** — striped, bordered, and hoverable
3. **JavaScript that highlights today's row** automatically (no manual work!)
4. A **"Today's Classes" summary box** below the table, built dynamically from a JS array

**New skills you'll learn:**
- HTML tables (a whole family of new tags!)
- Bootstrap table classes
- JavaScript arrays (storing lists of data)
- JavaScript `for` loops (repeating actions)
- The `Date` object, `querySelector`, and `classList`

---

## 📌 New HTML Tags — The Table Family

Tables are how we display **rows and columns of data** — like a spreadsheet, a register,
or... a timetable! HTML gives us a whole family of tags to build tables properly.

> Think of an HTML table like the **attendance register** your teacher uses.
> The register has a title, column headings (Roll No, Name, Date columns),
> and rows of data (one per student). HTML tables work the exact same way!

---

### 📌 `<table>` — The Table Container

```html
<table>
  <!-- All rows and cells go inside here -->
</table>
```

Creates a table — everything (headers, rows, cells) lives inside this tag.

> **Analogy:** `<table>` is like the **register book itself**. Without the book,
> you can't write any rows or columns!

---

### 📌 `<caption>` — Table Title (Accessibility)

```html
<table>
  <caption>BCA Semester II — Weekly Class Timetable</caption>
</table>
```

Adds a title/description to the table. Screen readers announce this first, so visually
impaired users know what data the table contains.

> **Think of it as:** The title on the cover of the attendance register — "BCA Section A, Roll List 2025-26".

---

### 📌 `<thead>` and `<tbody>` — Header vs Body Sections

```html
<table>
  <thead>
    <!-- Header row(s) — column labels -->
  </thead>
  <tbody>
    <!-- Data rows — actual content -->
  </tbody>
</table>
```

`<thead>` groups the **header rows** (column labels). `<tbody>` groups the **data rows**.

> **Analogy:** In the attendance register, the first row with "Roll No", "Name", "Mon", "Tue"
> is `<thead>`. All rows below with actual student data — that's `<tbody>`.

---

### 📌 `<tr>` — Table Row

```html
<tr>
  <td>Monday</td>
  <td>Web Technology</td>
</tr>
```

Creates **one horizontal row**. In our timetable, each `<tr>` = one day of the week.

> **Analogy:** Each row is like **one line in the register** — one student's entire record.

---

### 📌 `<th>` and `<td>` — Header Cell vs Data Cell

```html
<tr>
  <th>Day</th>       <!-- Header cell: bold and centered -->
  <td>Monday</td>    <!-- Data cell: normal content -->
</tr>
```

`<th>` creates a **header cell** (bold, centered) — used for column/row labels.
`<td>` creates a **regular data cell** — where actual information goes.

> **Analogy:** `<th>` = the column titles ("Roll No", "Name"). `<td>` = the actual
> data in each box (the student's name, their mark).

---

### 📌 `scope` Attribute — Accessibility Helper

```html
<th scope="col">Period 1</th>   <!-- This header labels a column -->
<th scope="row">Monday</th>     <!-- This header labels a row -->
```

**What it does:** Tells screen readers whether a header cell applies to its **column** or
its **row**. Critical for accessibility!

---

### 📌 `colspan` — Merge Cells Horizontally

```html
<tr>
  <td colspan="3">Lunch Break (1:15 PM – 2:00 PM)</td>
</tr>
```

**What it does:** Makes one cell span across **multiple columns**. The number tells how many
columns to merge.

> **Analogy:** When you draw a long line across three columns in your notebook and write
> "Lunch Break" — that's `colspan`.

---

### 📌 `rowspan` — Merge Cells Vertically

```html
<td rowspan="2">Lab (WT)</td>
```

**What it does:** Makes one cell span across **multiple rows** vertically. Useful when the
same subject continues for two periods.

> **Analogy:** Writing "Lab" once and drawing a bracket across two time slots.

---

### Quick Summary — The Table Family

| Tag | Purpose | Goes Inside |
|-----|---------|-------------|
| `<table>` | The table itself | Section/div |
| `<caption>` | Table title | `<table>` |
| `<thead>` | Header section | `<table>` |
| `<tbody>` | Body section | `<table>` |
| `<tr>` | One row | `<thead>` or `<tbody>` |
| `<th>` | Header cell | `<tr>` |
| `<td>` | Data cell | `<tr>` |

---

## 📖 Bootstrap Table Classes

Bootstrap makes tables look professional with just a few CSS classes. No custom CSS needed!

### Base Class — `table`

```html
<table class="table">
```

Every Bootstrap table starts with the `table` class. It adds nice padding, borders on rows,
and proper text alignment.

### `table-striped` — Zebra Pattern

```html
<table class="table table-striped">
```

Alternating light/dark rows — like a zebra! Makes it easier to read across long rows.

> **Why?** Imagine reading a timetable with 6 columns and no color difference —
> your eyes would jump to the wrong row constantly. Stripes fix that.

### `table-bordered` — All Borders

Adds borders around **every cell**, not just between rows.

### `table-hover` — Highlight on Mouse

Row highlights when you move your mouse over it. Great for interactive tables!

### `table-sm` — Compact Size

Reduces cell padding by half. Useful when you have lots of data in a small space.

### `table-responsive` — Scroll on Mobile

```html
<div class="table-responsive">
  <table class="table">...</table>
</div>
```

> ⚠️ **Important:** `table-responsive` goes on a **wrapper `<div>`**, not on the `<table>`
> itself! On phones, the table gets a horizontal scrollbar instead of breaking the layout.

### Row/Cell Color Variants

```html
<tr class="table-warning">...</tr>    <!-- Yellow highlight -->
<tr class="table-success">...</tr>    <!-- Green highlight -->
<tr class="table-primary">...</tr>    <!-- Blue highlight -->
<tr class="table-danger">...</tr>     <!-- Red highlight -->
```

We'll use `table-warning` to highlight today's row!

---

### Bootstrap Alert Classes

```html
<div class="alert alert-info" role="alert">
  This is an informational message.
</div>
```

`alert` is the **base class** for Bootstrap's alert component — colored notification boxes.
Add a variant class to set the color:

| Class | Color | Used For |
|-------|-------|----------|
| `alert-info` | Blue | General information |
| `alert-success` | Green | Positive messages |
| `alert-warning` | Yellow | Caution messages |
| `alert-danger` | Red | Error messages |

> **Analogy:** Alerts are like the **notice board** in your college hallway. The board
> background color tells you the type: blue for information, green for good news,
> red for urgent warnings.

### `role="alert"` — Accessibility Attribute

```html
<div class="alert alert-info" role="alert">
```

The `role="alert"` attribute tells screen readers to **announce this content immediately**
when it appears or changes — like an important PA system announcement. Always add it to
Bootstrap alert boxes!

---

## 📖 JavaScript: Arrays

### What Is an Array?

An **array** is a list of values stored in one variable.

> **Analogy:** Think of an array as a **train with numbered coaches**.
> Coach 0 has "Mathematics", Coach 1 has "English", Coach 2 has "Web Technology".
> The coaches are numbered starting from **zero** (not one!).

```
  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │   Math   │  │ English  │  │  Web Tech │  │   DSA    │
  │ Index: 0 │  │ Index: 1 │  │ Index: 2  │  │ Index: 3 │
  └──────────┘  └──────────┘  └──────────┘  └──────────┘
       ↑              ↑             ↑              ↑
    arr[0]         arr[1]        arr[2]         arr[3]
```

### Creating an Array

```javascript
var subjects = ["Mathematics", "English", "Web Technology", "Data Structures"];
var marks = [85, 72, 91, 68];
var mixed = ["Hello", 42, true];   // Arrays can mix types (but usually don't)
```

### Accessing Elements (Index Starts at 0!)

```javascript
var days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

days[0]   // → "Monday"     (first item)
days[1]   // → "Tuesday"    (second item)
days[5]   // → "Saturday"   (last item, because 6 items → index 0 to 5)
days[6]   // → undefined    (nothing at index 6!)
```

> ⚠️ **Common mistake:** Students write `days[1]` expecting "Monday" (the first day).
> Remember — arrays start counting from **0**, not 1! `days[0]` is the first item.

### Array Length

```javascript
days.length   // → 6 (there are 6 items in the array)
```

The last item is always at index `days.length - 1`. Here: `days[6 - 1]` = `days[5]` = "Saturday".

### Adding Items

```javascript
days.push("Sunday");      // Adds "Sunday" at the end
days.length               // → 7 now
```

> **Analogy:** `push` is like attaching a new coach at the end of the train.

### Arrays of Arrays (2D Arrays)

You can put arrays inside arrays — like a **table of data**:

```javascript
var timetable = [
    ["Web Technology", "Mathematics", "Data Structures", "English", "Lab (WT)"],
    ["Mathematics", "Web Technology", "English", "Data Structures", "Lab (DS)"]
];

timetable[0]       // → The entire Monday array
timetable[0][0]    // → "Web Technology" (Monday, Period 1)
timetable[1][2]    // → "English" (Tuesday, Period 3)
```

> **Analogy:** A 2D array is like a **spreadsheet**. First index = row, second index = column.

---

## 📖 JavaScript: The `for` Loop

### Why Do We Need Loops?

Imagine printing 6 subjects one by one:

```javascript
document.write(subjects[0] + "<br>");
document.write(subjects[1] + "<br>");
document.write(subjects[2] + "<br>");
document.write(subjects[3] + "<br>");
// ... what if there are 100 items?!
```

That's **tedious and repetitive**. Loops do this automatically!

### The `for` Loop — Syntax

```javascript
for (var i = 0; i < 6; i++) {
    // This code runs 6 times (i = 0, 1, 2, 3, 4, 5)
}
```

> **Analogy:** A `for` loop is like a **watchman doing his night rounds**.
>
> 1. **Start:** "Begin at Gate 0" → `var i = 0`
> 2. **Check:** "Have I passed the last gate?" → `i < 6`
> 3. **Do the work:** Check the gate, write in the logbook → `{ ... }`
> 4. **Move to next:** "Go to the next gate" → `i++`
> 5. **Repeat** steps 2-4 until the condition is false

### Step-by-Step Trace

Let's trace `for (var i = 0; i < 3; i++) { console.log(i); }`:

```
Step 1: i = 0  → Is 0 < 3? YES → console.log(0) → i becomes 1
Step 2: i = 1  → Is 1 < 3? YES → console.log(1) → i becomes 2
Step 3: i = 2  → Is 2 < 3? YES → console.log(2) → i becomes 3
Step 4: i = 3  → Is 3 < 3? NO  → STOP! Loop ends.
```

Output: `0`, `1`, `2` (three times, as expected).

### Looping Through an Array

This is the **most common use** of a for loop — go through each item in an array:

```javascript
var subjects = ["Math", "English", "Web Tech", "DSA"];

for (var i = 0; i < subjects.length; i++) {
    console.log("Period " + (i + 1) + ": " + subjects[i]);
}
```

Output:
```
Period 1: Math
Period 2: English
Period 3: Web Tech
Period 4: DSA
```

> **Why `i < subjects.length` instead of `i < 4`?** Because if you add more subjects later,
> the loop automatically adjusts. **Never hard-code the array length!**

---

## 📖 Date Object + querySelector + classList

### `new Date()` — Getting Today's Information

```javascript
var today = new Date();         // Current date and time
var dayNumber = today.getDay(); // 0 = Sunday, 1 = Monday, ..., 6 = Saturday
var hours = today.getHours();   // 0–23
```

> **Why does Sunday = 0?** It's an American convention in JavaScript.
> Our timetable is Mon–Sat, so we'll use `dayNumber` 1 through 6.

### `querySelector` — Finding Elements by CSS Selector

More powerful than `getElementById` — it uses **CSS selectors**:

```javascript
document.querySelector("#timetable");           // By ID
document.querySelector(".table");               // By class (first match)
document.querySelectorAll(".table tbody tr");   // ALL matching elements (returns a list)
```

> **Analogy:** `getElementById` is like knowing someone's Aadhaar number — you go directly.
> `querySelector` is like describing someone — "the person in the blue shirt sitting in row 3".

### `classList` — Adding/Removing CSS Classes

Instead of changing styles directly, we add or remove **classes**:

```javascript
var row = document.querySelector("#timetableBody tr");
row.classList.add("table-warning");      // Add yellow highlight
row.classList.remove("table-warning");   // Remove highlight
row.classList.toggle("table-warning");   // Add if missing, remove if present
```

> **Why classes instead of inline styles?** Bootstrap already defines beautiful
> styles for `table-warning`. We just "turn them on"!

---

## 🔨 Let's Build! — Step by Step

### Step 1: Add the Timetable Section (HTML Structure)

Add this **after the faculty cards section** and **before the closing `</main>` tag** in
your `index.html`:

```html
<!-- ============================================ -->
<!--         SECTION: CLASS TIMETABLE             -->
<!-- ============================================ -->
<section id="timetable" class="py-5 bg-light">
  <div class="container">
    <h2 class="text-center mb-2">📅 Class Timetable</h2>
    <p class="text-center text-muted mb-4">BCA Semester II — Weekly Schedule</p>

    <!-- Today's Summary (filled by JavaScript) -->
    <div id="todaySummary" class="alert alert-info text-center mb-4" role="alert">
      Loading today's schedule...
    </div>

    <!-- Responsive wrapper for mobile scrolling -->
    <div class="table-responsive">
      <table class="table table-striped table-bordered table-hover">
        <caption class="caption-top text-center">
          BCA Batch 2025-26 — Semester II Timetable (Room 301, CS Block)
        </caption>

        <thead class="table-dark">
          <tr>
            <th scope="col">Day / Time</th>
            <th scope="col">9:00–10:00</th>
            <th scope="col">10:00–11:00</th>
            <th scope="col">11:15–12:15</th>
            <th scope="col">12:15–1:15</th>
            <th scope="col">2:00–3:00</th>
          </tr>
        </thead>

        <tbody id="timetableBody">
          <tr>
            <th scope="row">Monday</th>
            <td>Web Technology</td>
            <td>Mathematics</td>
            <td>Data Structures</td>
            <td>English</td>
            <td>Lab (WT)</td>
          </tr>
          <tr>
            <th scope="row">Tuesday</th>
            <td>Mathematics</td>
            <td>Web Technology</td>
            <td>English</td>
            <td>Data Structures</td>
            <td>Lab (DS)</td>
          </tr>
          <tr>
            <th scope="row">Wednesday</th>
            <td>English</td>
            <td>Web Technology</td>
            <td>Mathematics</td>
            <td>Data Structures</td>
            <td>Library</td>
          </tr>
          <tr>
            <th scope="row">Thursday</th>
            <td>Web Technology</td>
            <td>Data Structures</td>
            <td>English</td>
            <td>Mathematics</td>
            <td>Lab (WT)</td>
          </tr>
          <tr>
            <th scope="row">Friday</th>
            <td>Mathematics</td>
            <td>English</td>
            <td>Web Technology</td>
            <td>Data Structures</td>
            <td>Lab (DS)</td>
          </tr>
          <tr>
            <th scope="row">Saturday</th>
            <td colspan="4" class="text-center">Lab — Practical Sessions (Full Day)</td>
            <td>—</td>
          </tr>
        </tbody>

      </table>
    </div><!-- /table-responsive -->

    <!-- Highlight Subject Button -->
    <div class="text-center mt-3">
      <button class="btn btn-outline-success" id="btnHighlightWT" onclick="highlightSubject()">
        🔍 Highlight "Web Technology" Classes
      </button>
    </div>

  </div><!-- /container -->
</section>
```

**What we used:**
- `bg-light` → light gray background to separate from the section above
- `table-responsive` div → horizontal scroll on phones
- `table table-striped table-bordered table-hover` → professional look
- `thead class="table-dark"` → dark header row
- `scope="col"` and `scope="row"` → accessibility
- `colspan="4"` → Saturday's lab spans 4 period columns
- `caption-top` → shows the caption above the table (Bootstrap class)
- `alert alert-info` → Bootstrap alert box in blue (informational notification)
- `role="alert"` → accessibility: screen readers announce content immediately
- `btn btn-outline-success` → green outline button

> 📌 **First Time Seeing `alert` and `alert-info`?** `alert` is Bootstrap's notification box component — a colored box for messages. `alert-info` makes it blue. We use it for the "Today's Classes" summary. Other variants: `alert-success` (green), `alert-warning` (yellow), `alert-danger` (red).

> 📌 **First Time Seeing `role="alert"`?** This accessibility attribute tells screen readers to announce the content immediately when it changes — like a PA system announcement. Always add it to Bootstrap alert boxes!

> 📌 **First Time Seeing `btn-outline-success`?** It follows the same `btn-outline-*` pattern as `btn-outline-primary` (Session 4) and `btn-outline-secondary` (Session 5), but in green.

---

### Step 2: Add the JavaScript (Highlight Today + Summary)

Add this inside your `<script>` tag at the bottom of `index.html`, **after the existing
JavaScript code from previous sessions**:

```javascript
// ============================================
// TIMETABLE — Highlight Today + Summary
// ============================================

// --- Arrays: Our timetable data ---
var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

var timetableData = [
    // Index 0 = Sunday (not used — no classes on Sunday)
    [],
    // Index 1 = Monday
    ["Web Technology", "Mathematics", "Data Structures", "English", "Lab (WT)"],
    // Index 2 = Tuesday
    ["Mathematics", "Web Technology", "English", "Data Structures", "Lab (DS)"],
    // Index 3 = Wednesday
    ["English", "Web Technology", "Mathematics", "Data Structures", "Library"],
    // Index 4 = Thursday
    ["Web Technology", "Data Structures", "English", "Mathematics", "Lab (WT)"],
    // Index 5 = Friday
    ["Mathematics", "English", "Web Technology", "Data Structures", "Lab (DS)"],
    // Index 6 = Saturday
    ["Lab", "Lab", "Lab", "Lab", "—"]
];

var timeSlots = ["9:00–10:00", "10:00–11:00", "11:15–12:15", "12:15–1:15", "2:00–3:00"];

// --- Date Object: What day is it today? ---
var today = new Date();
var dayNumber = today.getDay();   // 0 = Sunday, 1 = Monday, ..., 6 = Saturday

// --- querySelector: Find all rows in the timetable body ---
var rows = document.querySelectorAll("#timetableBody tr");

// --- classList: Highlight today's row ---
if (dayNumber >= 1 && dayNumber <= 6) {
    // dayNumber 1 = Monday = rows[0], dayNumber 2 = Tuesday = rows[1], etc.
    rows[dayNumber - 1].classList.add("table-warning");
}

// --- For Loop: Build today's summary ---
var summaryBox = document.getElementById("todaySummary");

if (dayNumber === 0) {
    // Sunday — no classes!
    summaryBox.textContent = "🎉 It's Sunday — no classes today! Enjoy your day off.";
    summaryBox.className = "alert alert-success text-center mb-4";
} else {
    var todayClasses = timetableData[dayNumber];
    var dayName = days[dayNumber];

    // Build the summary string using a for loop
    var summary = "📚 " + dayName + "'s Classes: ";
    for (var i = 0; i < todayClasses.length; i++) {
        summary = summary + todayClasses[i];
        if (i < todayClasses.length - 1) {
            summary = summary + " → ";
        }
    }

    summaryBox.textContent = summary;
    summaryBox.className = "alert alert-info text-center mb-4";
}

// --- Bonus: Highlight all "Web Technology" cells ---
function highlightSubject() {
    var allCells = document.querySelectorAll("#timetableBody td");
    for (var i = 0; i < allCells.length; i++) {
        if (allCells[i].textContent === "Web Technology") {
            allCells[i].classList.toggle("table-success");
        }
    }
}
```

> 📌 **First Time Seeing `alert-success`?** Just like `alert-info` is blue, `alert-success` makes the alert box green — used here to show the happy "Sunday — no classes!" message.

---

### Step 3: Understanding the Code — Walk-Through

Assuming today is **Wednesday** (`dayNumber = 3`):

1. `timetableData[3]` → `["English", "Web Technology", "Mathematics", "Data Structures", "Library"]`
2. `rows[dayNumber - 1]` = `rows[2]` → Wednesday's `<tr>` → gets `table-warning` class (yellow)
3. The `for` loop builds the summary string piece by piece:

```
i=0: "📚 Wednesday's Classes: English"
i=1: "📚 Wednesday's Classes: English → Web Technology"
i=2: "📚 Wednesday's Classes: English → Web Technology → Mathematics"
i=3: "... → Mathematics → Data Structures"
i=4: "... → Data Structures → Library"    ← final result shown in the alert box
```

---

## ✅ Checkpoint — Verify Your Work

Open `index.html` in your browser and check:

| # | Check | Expected Result |
|---|-------|-----------------|
| 1 | Table is visible | 6 rows (Mon–Sat), 6 columns (Day + 5 periods) |
| 2 | Striped rows | Alternating white/gray background |
| 3 | Borders visible | Lines around every cell |
| 4 | Hover effect | Row highlights when you move your mouse over it |
| 5 | Resize browser to phone width | Table scrolls horizontally (no layout break) |
| 6 | Today's row is yellow | The row matching today's weekday has a yellow background |
| 7 | Summary box shows today's classes | Blue info box above the table lists all periods |
| 8 | Sunday test | Change `var dayNumber = 0;` temporarily — should show "Enjoy your day off" |
| 9 | Highlight button works | Click "Highlight Web Technology" — those cells turn green |
| 10 | Saturday row | "Lab — Practical Sessions" spans 4 columns |

> **Debugging tip:** Press F12 → Console tab. If something is wrong, JavaScript errors
> will appear here in red. Common mistakes:
> - Forgetting to add `id="timetableBody"` to the `<tbody>` tag
> - Misspelling `querySelectorAll` (capital A, double l)
> - Putting the `<script>` tag before the HTML (JavaScript runs before the table exists!)

---

## 🔍 Quick Reference

### HTML Table Tags

| Tag | Purpose | Example |
|-----|---------|---------|
| `<table>` | Table container | `<table class="table">` |
| `<caption>` | Table title | `<caption>BCA Timetable</caption>` |
| `<thead>` | Header section | Groups `<th>` cells |
| `<tbody>` | Body section | Groups data `<tr>` rows |
| `<tr>` | Table row | One horizontal row |
| `<th>` | Header cell | Bold, centered |
| `<td>` | Data cell | Normal content |
| `colspan="n"` | Merge n columns | `<td colspan="3">Break</td>` |
| `rowspan="n"` | Merge n rows | `<td rowspan="2">Lab</td>` |
| `scope="col"` | Column header | Accessibility |
| `scope="row"` | Row header | Accessibility |

### Bootstrap Table Classes

| Class | Effect |
|-------|--------|
| `table` | Base table styling |
| `table-striped` | Alternating row colors |
| `table-bordered` | Borders on all cells |
| `table-hover` | Highlight row on hover |
| `table-sm` | Compact padding |
| `table-responsive` | Horizontal scroll (on wrapper div!) |
| `table-dark` | Dark background |
| `table-warning` | Yellow row/cell |
| `table-success` | Green row/cell |
| `table-danger` | Red row/cell |
| `table-primary` | Blue row/cell |
| `caption-top` | Caption above table |
| `alert` | Base alert (notification box) component |
| `alert-info` | Blue information alert |
| `alert-success` | Green success alert |
| `table-secondary` | Gray row/cell |
| `btn-outline-success` | Green outline button |

### Bootstrap Classes (from Previous Sessions)

| Class | Effect |
|-------|--------|
| `container` | Fixed-width centered wrapper (from Session 1) |
| `py-5` | Padding top + bottom — 3rem (from Session 2) |
| `btn` | Base button styling (from Session 2) |
| `mt-3` | Margin top — 1rem (from Session 2) |
| `bg-light` | Light gray background (from Session 3) |
| `text-center` | Center-align text (from Session 3) |
| `text-muted` | Gray subdued text (from Session 3) |
| `mb-2` | Margin bottom — 0.5rem (from Session 3) |
| `mb-4` | Margin bottom — 1.5rem (from Session 3) |

### JavaScript — Arrays & Loops

| Concept | Syntax | Example |
|---------|--------|---------|
| Create array | `var arr = [a, b, c];` | `var days = ["Mon", "Tue"];` |
| Access item | `arr[index]` | `days[0]` → `"Mon"` |
| Array length | `arr.length` | `days.length` → `2` |
| Add item | `arr.push(item)` | `days.push("Wed")` |
| For loop | `for (var i=0; i<n; i++)` | Loop through array |
| Get today | `new Date().getDay()` | 0=Sun … 6=Sat |
| Find element | `document.querySelector(sel)` | CSS selector |
| Find all | `document.querySelectorAll(sel)` | Returns list |
| Add class | `el.classList.add("cls")` | Highlight |
| Remove class | `el.classList.remove("cls")` | Un-highlight |
| Toggle class | `el.classList.toggle("cls")` | Switch on/off |

### HTML Tags (from Previous Sessions)

| Tag | Purpose | Example |
|-----|---------|---------|
| `<section>` | Thematic content group (from Session 2) | `<section id="timetable">` |
| `<div>` | Generic container (from Session 1) | `<div class="container">` |
| `<h2>` | Second-level heading (from Session 3) | `<h2>Class Timetable</h2>` |
| `<p>` | Paragraph of text (from Session 2) | `<p class="lead">...</p>` |
| `<button>` | Clickable button (from Session 4) | `<button class="btn">` |
| `<br>` | Line break (from Session 1) | Used in `document.write()` output |

### HTML Attributes

| Attribute | Used On | What It Does |
|-----------|---------|--------------|
| `role="alert"` | Alert `<div>` | Screen readers announce content immediately |
| `id` | Any element | Unique identifier for JS/CSS targeting (from Session 1) |
| `class` | Any element | Applies CSS/Bootstrap styles (from Session 1) |
| `onclick` | `<button>` | Runs JavaScript function when clicked (from Session 4) |

---

## 📝 Key Takeaways

1. **HTML tables** use `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`.
   Always use `<thead>` + `<tbody>` for structure and accessibility.
2. **Bootstrap table classes** (`table-striped`, `table-bordered`, `table-hover`,
   `table-responsive`) → professional tables with zero custom CSS.
3. **Arrays** store ordered lists. Index starts at **0**, not 1.
4. **For loops** repeat code: `for (var i = 0; i < arr.length; i++) { }`.
5. **`new Date().getDay()`** → today's day (0–6). Makes pages dynamic!
6. **`querySelector`** finds elements by CSS selector — more flexible than `getElementById`.
7. **`classList.add/remove/toggle`** → change appearance by switching CSS classes.
8. **`colspan` and `scope`** → better table structure and accessibility.

---

## 🏋️ Practice Challenges

### Challenge 1: Break Row (Easy)
Add a "Lunch Break" row between morning and afternoon periods:

```html
<tr class="table-secondary">
  <th scope="row" colspan="6" class="text-center">🍽️ Lunch Break (1:15 PM – 2:00 PM)</th>
</tr>
```

> 📌 **First Time Seeing `table-secondary`?** Another Bootstrap table color variant — gray background. Like `table-warning` (yellow) and `table-success` (green), but neutral gray. Perfect for break rows that shouldn't draw attention.

> ⚠️ After adding the break row, your JavaScript row indexing changes! You'll need to
> adjust the highlight logic since the break row shifts row indices.

### Challenge 2: Highlight Subject Button (Medium)
The button is already in the code! But try extending it:
- Add a second button for "Data Structures" (highlight in blue using `table-primary`)
- Add a "Clear All Highlights" button that removes all color classes

### Challenge 3: Sortable Columns (Advanced)
Make the table sortable by clicking column headers:

```javascript
// Hint: When a <th> is clicked...
// 1. Read all rows into an array
// 2. Sort the array based on the clicked column's text
// 3. Re-append the sorted rows to <tbody>
```

This is advanced — try it only if you finish the other challenges!

### Challenge 4: Period Counter (Medium)
Add a paragraph below the table that says:
"Web Technology appears **X** times this week."

Use a `for` loop inside a `for` loop (nested loop) to count through `timetableData`:

```javascript
var count = 0;
for (var day = 1; day <= 6; day++) {
    for (var period = 0; period < timetableData[day].length; period++) {
        if (timetableData[day][period] === "Web Technology") {
            count = count + 1;
        }
    }
}
```

---

## 🔗 Labs Covered

| Lab | Title | Status |
|-----|-------|--------|
| **Lab 5** | Design a web page to display class timetable | ✅ Done! |
| **Lab 6** | Create a university/department table layout | ✅ Done! |

---

## ⏭️ Next Session Preview

**Session 7 — Image Gallery + Modal Lightbox:** A responsive photo grid where clicking
a photo opens it in a full-screen modal (lightbox). New tags: `<figure>`, `<figcaption>`,
Bootstrap Modal component.

> **Prep:** Find 6–8 photos of your campus, classroom, or college events.
> Save them in `website/images/` — we'll use them next session!

---

*Session 6 of 15 — Crash Course: Bootstrap + JavaScript — BCA Semester II, Mandsaur University, 2025-26*
