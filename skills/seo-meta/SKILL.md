---
name: seo-meta-generation
description: >
  Auto-generates SEO meta tags, Open Graph data,
  structured data (JSON-LD), and sitemap entries
  for every page created.
version: 1.0
author: Motion_Viz
tags: [seo, meta, og, structured-data]
---

# SEO Meta Generation

## Purpose
Ensure every page ships with complete SEO metadata.
INPUT: Page content and purpose.
OUTPUT: Meta tags, OG tags, Twitter cards, JSON-LD, canonical URL.

## When to Use This Skill
- Every page deployment (always active)
- When creating new routes or pages
- When deploying to production

## Rules (Non-Negotiable)
1. Title tag: 50-60 characters, primary keyword at front
2. Meta description: 150-160 characters, include a CTA verb
3. OG image: Must be specified (1200x630px recommended)
4. Canonical URL: Always set (prevents duplicate content)
5. JSON-LD: At minimum Organization or WebPage schema
6. Heading hierarchy: Exactly one H1, H2s follow logically
7. All images must have descriptive alt text (not "image1.png")

## Required Output for Every Page

### Head Tags
```html
<title>[Primary Keyword] - [Brand] | [Value Prop]</title>
<meta name="description" content="[Action-oriented description, 150-160 chars]">
<meta name="robots" content="index, follow">
<link rel="canonical" href="[full-canonical-url]">
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Open Graph
```html
<meta property="og:title" content="[Same as title or shorter]">
<meta property="og:description" content="[Same as meta description]">
<meta property="og:image" content="[1200x630 image URL]">
<meta property="og:url" content="[canonical URL]">
<meta property="og:type" content="website">
<meta property="og:site_name" content="[Brand Name]">
```

### Twitter Card
```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[title]">
<meta name="twitter:description" content="[description]">
<meta name="twitter:image" content="[image URL]">
<meta name="twitter:site" content="@[handle]">
```

### JSON-LD (minimum)
```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "[Page Title]",
  "description": "[Meta Description]",
  "url": "[Canonical URL]",
  "publisher": {
    "@type": "Organization",
    "name": "[Brand Name]",
    "url": "[Homepage URL]"
  }
}
```

### For Service/Product Pages, Add:
```json
{
  "@type": "Service",
  "name": "[Service Name]",
  "description": "[Service Description]",
  "provider": {
    "@type": "Organization",
    "name": "[Brand Name]"
  }
}
```

## Checklist (AI Self-Verification)
- [ ] Title tag under 60 characters
- [ ] Meta description under 160 characters
- [ ] OG image specified with correct dimensions
- [ ] Canonical URL set and correct
- [ ] JSON-LD is valid JSON (no trailing commas)
- [ ] Exactly one H1 on page
- [ ] All images have descriptive alt text
- [ ] Twitter card tags present
- [ ] No duplicate meta tags
- [ ] Robots tag allows indexing