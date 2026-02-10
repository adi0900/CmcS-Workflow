---
name: responsive-mobile-first
description: >
  Enforces mobile-first responsive design patterns.
  All components start at mobile width and scale up
  using min-width breakpoints. No desktop-first CSS.
version: 1.0
author: Motion_Viz
tags: [responsive, mobile, css, layout]
---

# Mobile-First Responsive Patterns

## Purpose
All generated code must follow mobile-first methodology.
Base styles target mobile (375px). Scale UP with min-width.
INPUT: Any component or page request.
OUTPUT: Code that works on all screen sizes, mobile-first.

## When to Use This Skill
- Every component build (always active)
- Every page build
- Any layout or CSS work

## Rules (Non-Negotiable)
1. Base styles = mobile (375px viewport)
2. Scale UP with min-width breakpoints ONLY
3. NEVER use max-width media queries
4. Touch targets: minimum 44x44px on all interactive elements
5. No horizontal scroll at any breakpoint
6. Images: 100% width on mobile, constrained on desktop
7. Font sizes: reduce 15-20% on mobile vs desktop specs

## Breakpoints
```
sm:  640px    (large phones / small tablets)
md:  768px    (tablets)
lg:  1024px   (small laptops)
xl:  1280px   (desktops)
2xl: 1536px   (large screens)
```

## Tailwind Pattern (Preferred)
Base classes = mobile. Then layer responsive prefixes:

```html
<!-- Padding: 16px mobile → 24px tablet → 32px desktop -->
<div class="px-4 sm:px-6 lg:px-8">

<!-- Grid: 1 col mobile → 2 col tablet → 3 col desktop -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">

<!-- Typography: scales up -->
<h1 class="text-2xl sm:text-3xl lg:text-5xl">

<!-- Visibility: hide on mobile, show on desktop -->
<nav class="hidden lg:flex">

<!-- Full-width on mobile, constrained on desktop -->
<div class="w-full max-w-none lg:max-w-6xl lg:mx-auto">
```

## Layout Rules

### Navigation
- Mobile: Hamburger menu (hidden, toggle on tap)
- lg+: Full horizontal nav bar

### Content Grids
- Mobile: Single column, stacked vertically
- md+: 2-column grid
- lg+: 3 or 4-column grid

### Cards
- Mobile: Full-width, stacked
- md+: Side-by-side in grid
- Images inside cards: 100% width, aspect-ratio locked

### Modals / Drawers
- Mobile: Full-screen overlay (bottom sheet pattern preferred)
- lg+: Centered modal with backdrop

### Tables
- Mobile: Stack rows vertically OR horizontal scroll container
- lg+: Standard table layout

### Hero Sections
- Mobile: Text stacked above image, centered
- lg+: Text left, image right (or vice versa)

### Forms
- Mobile: Full-width inputs, stacked labels
- lg+: Inline labels permitted, max-width on form container

## CSS Pattern (if not using Tailwind)
```css
/* BASE = MOBILE (no media query needed) */
.container {
  padding: 16px;
  display: flex;
  flex-direction: column;
}

/* TABLET AND UP */
@media (min-width: 768px) {
  .container {
    padding: 24px;
    flex-direction: row;
  }
}

/* DESKTOP AND UP */
@media (min-width: 1024px) {
  .container {
    padding: 32px;
    max-width: 1280px;
    margin: 0 auto;
  }
}
```

## Anti-Patterns (Never Do This)
```css
/* BAD: Desktop-first (max-width) */
@media (max-width: 768px) {
  .container { padding: 16px; }
}

/* BAD: Fixed widths */
.card { width: 350px; }

/* BAD: Pixel-based font sizes without responsive scaling */
h1 { font-size: 48px; } /* no responsive variant */
```

## Checklist (AI Self-Verification)
- [ ] No max-width media queries used
- [ ] Tested at 375px (iPhone SE)
- [ ] Tested at 768px (iPad)
- [ ] Tested at 1280px (Desktop)
- [ ] No horizontal scroll at any size
- [ ] All touch targets 44x44px minimum
- [ ] Images have width: 100% on mobile
- [ ] Navigation collapses on mobile
- [ ] Font sizes scale across breakpoints