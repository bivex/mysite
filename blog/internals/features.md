---
title: Electrostatic Features
description: Explore all features of Electrostatic static site generator — lightning fast, markdown-first, and SSR support
keywords: features, ssg, markdown, syntax highlighting
date: 2025-02-21
category: internals
tags: internals, electrostatic, features
readTime: 4 min
---

# Features

Electrostatic packs powerful features while staying minimal and fast.

## Core Features

### ⚡ Lightning Fast
- **100/100 Lighthouse score** — optimized by default
- **Sub-second builds** — even for thousands of pages
- **Zero runtime overhead** — pure HTML output

### 📝 Markdown-First
Write content in Markdown with YAML frontmatter

### 🎨 Syntax Highlighting
Code blocks highlighted with Chroma

### 🔄 SSR Support
- **Serve mode** — live rendering during development
- **Export mode** — generate static HTML for production

### 📄 Custom Templates
HTML templates with placeholder variables

## File Organization

```
mysite/
├── index.md
├── blog/
├── docs/
├── template.html
├── meta.json
├── public/
├── assets/
└── 404.md, 403.md, 500.md
```

## Routing

| File | URL |
|------|-----|
| index.md | / |
| about.md | /about |
| blog/post.md | /blog/post |

---

**Related:**
- [Tech Stack](/blog/internals/stack)
- [Getting Started](/blog/go/getting-started)
