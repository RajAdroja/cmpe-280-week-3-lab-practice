# CMPE 280 Week 3 Lab

This README outlines the three activities for the week 3 lab practice.

---

## Activity A — Flexbox Navigation (Student Handout)

### 🎯 Goal

Build a simple, responsive, and accessible navigation bar:

- Logo on the left, links on the right
- Items vertically centered
- Keyboard accessible (Tab moves focus, visible focus ring)
- Wrap or stack neatly on small screens

### ⏱ Timebox

8–10 minutes (pair programming encouraged)

### 🧭 Steps

#### 1) index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Flexbox Nav</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <a href="#main" class="skip">Skip to content</a>
    <header>
      <nav aria-label="Primary">
        <div class="logo">
          <a href="/" class="brand">SJSU</a>
        </div>
        <ul class="links">
          <li><a href="#home" aria-current="page">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a class="btn" href="#contact">Contact</a></li>
        </ul>
      </nav>
    </header>
    <main id="main">
      <h1>Welcome</h1>
      <p>Content…</p>
    </main>
  </body>
</html>
```

#### 2) style.css

```css
:root {
  --blue: #0033a0;
  --gold: #ffcc00;
}
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  font-family: system-ui, Arial, sans-serif;
  line-height: 1.5;
}
a {
  color: inherit;
  text-decoration: none;
}
a:focus {
  outline: 3px solid var(--gold);
  outline-offset: 2px;
}

.skip {
  position: absolute;
  left: -9999px;
  top: auto;
}
.skip:focus {
  left: 1rem;
  top: 1rem;
  background: var(--gold);
  color: #000;
  padding: 0.4rem 0.6rem;
  border-radius: 6px;
}

header {
  border-bottom: 3px solid var(--gold);
}
nav {
  display: flex;
  justify-content: space-between; /* logo left, links right */
  align-items: center; /* vertical centering */
  gap: 1rem;
  padding: 0.75rem 1rem;
  max-width: 1100px;
  margin: 0 auto;
}
.logo .brand {
  font-weight: 700;
  color: var(--blue);
  font-size: 1.25rem;
}

.links {
  display: flex;
  gap: 1rem;
  list-style: none;
  margin: 0;
  padding: 0;
}
.links a {
  padding: 0.4rem 0.6rem;
  border-radius: 6px;
}
.links a:hover,
.links a:focus {
  background: rgba(0, 0, 0, 0.06);
}

.btn {
  background: var(--blue);
  color: #fff;
  border-radius: 8px;
  padding: 0.45rem 0.8rem;
}
.btn:hover,
.btn:focus {
  background: #001f60;
}

/* Small screens: stack neatly */
@media (max-width: 520px) {
  nav {
    flex-direction: column;
    align-items: stretch;
    gap: 0.5rem;
  }
  .links {
    justify-content: center;
    flex-wrap: wrap;
  }
}
```

### ✅ Success Criteria

- Logo left, links right at ≥520px
- Items vertically centered
- Tab/Shift+Tab cycles through links with a visible focus ring
- On small screens, nav wraps or stacks without overlap

### 🩺 Troubleshooting

- Links won’t move right → ensure nav has `display:flex` + `justify-content: space-between`
- Items not centered → add `align-items: center` to nav
- Odd spacing → remove list defaults on .links (`list-style:none; margin:0; padding:0`)
- No wrap → add `flex-wrap: wrap` or a `@media` rule with `flex-direction: column`
- No focus ring → add `a:focus` styles

### 🌱 Stretch Goals

- Add active state for current page
- Include an SVG icon with the logo
- Make Contact a call‑to‑action button (done)
- Add a Skip to content link (done)

---

## Activity B — CSS Grid (Student Handout)

### 🎯 Goal

Build a two‑column page with a 200px sidebar, flexible main area, and a footer spanning full width using CSS Grid.

### ⏱ Timebox

12–15 minutes (pairs or solo).

### 🧭 Steps

#### 1) index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Grid Layout (Starter)</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="layout">
      <aside>
        <h2>Sidebar</h2>
        <ul>
          <li><a href="#">Overview</a></li>
          <li><a href="#">Settings</a></li>
          <li><a href="#">Billing</a></li>
        </ul>
      </aside>
      <main>
        <h1>Main Content</h1>
        <p>...</p>
      </main>
      <footer>Footer</footer>
    </div>
  </body>
</html>
```

#### 2) style.css

```css
.layout {
  /* TODO:
    1) Make this a grid container
    2) Define areas: 'sidebar main' and 'footer footer'
    3) Columns: 200px for sidebar, rest flexible
    4) Rows: 1fr for content, auto for footer
  */
}
aside,
main,
footer {
  padding: 1rem;
}
```

### ✅ Success Criteria

- Sidebar is fixed at 200px
- Main expands with free space
- Footer spans across both columns
- ≤768px stacks vertically

### 🩺 Troubleshooting

- Footer not spanning → ensure footer has `grid-area: footer` and template has `'footer footer'`
- Overlap → check that area names in CSS match the template string

### 🌱 Stretch Goals

- Add a header row
- Collapse sidebar below 768px (stack order header → main → sidebar → footer)

---

## Activity C — Responsive Profile (Student Handout)

### 🎯 Goal

Make the profile mobile‑first, then add breakpoints: 1 column → 2 columns (≥768px) → 3 columns (≥1024px).

### ⏱ Timebox

15 minutes.

### 🧭 Steps

#### 1) index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Responsive Profile (Starter)</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <main class="profile">
      <img class="avatar" src="jane.jpg" alt="Portrait of Jane Doe" />
      <section class="about">
        <h2>About</h2>
        <p>Web UI Student at SJSU</p>
      </section>
      <aside class="contact">
        <h2>Contact</h2>
        <p><a href="mailto:jane@example.com">jane@example.com</a></p>
      </aside>
    </main>
  </body>
</html>
```

#### 2) style.css

```css
.profile {
  /* TODO:
    1) Make a single-column mobile default
    2) At ≥768px, switch to 2 columns (image left, text right)
    3) At ≥1024px, switch to 3 columns (image, about, contact)
  */
}
.avatar {
  width: 160px;
  height: 160px;
  object-fit: cover;
  border-radius: 50%;
}
```

### ✅ Success Criteria

- 1 column mobile
- 2 columns at ≥768px (image left, text right)
- 3 columns at ≥1024px (image, about, contact)
- No overlap; readable text

### 🩺 Troubleshooting

- Grid not changing → check `@media (min-width: …)` syntax
- Squished content → consider increasing min widths or adjusting column fractions

### 🌱 Stretch Goals

- Add a skills card as a third column on desktop
- Make avatar scale down gracefully
