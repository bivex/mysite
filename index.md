---
title: Electrostatic | Blazing Fast Static Sites
description: Minimalist static site generator with SSR support. Build, deploy, scale.
keywords: static site generator, ssg, go, markdown, fast, minimal
---

## ⚡ Electrostatic

**Build instant websites with Markdown & Go**

Minimalist static site generator with SSR support.

---

## Why Electrostatic?

### 🚀 Lightning Fast
**100/100 Lighthouse score** out of the box. No JavaScript bloat, no hydration, just pure HTML.

### 📝 Write in Markdown
Focus on content, not code. Use frontmatter for metadata, let the engine handle the rest.

### 🔄 SSR Support
Develop with live rendering — every request regenerates the page. Export to static for production.

---

## Features {#features}

- **Syntax Highlighting** — Code blocks with Chroma lexer in Monokai theme
- **Custom Templates** — HTML templates with `%title%`, `%CONTENT%` placeholders
- **Static Assets** — CSS, JS, images served from `/assets/` and `/public/`
- **Error Pages** — Built-in 404, 403, 500 templates
- **Article Index** — Auto-generated `/articles` page with all content
- **Minimal Dependencies** — Only Go standard library + markdown parser

---

## Get Started {#getting-started}

```bash
# Clone the repo
git clone https://github.com/laranatech/electrostatic

# Initialize a new site
go run . -m init -r ./mysite

# Serve with SSR
go run . -m serve -r ./mysite

# Export to static files
go run . -m export -r ./mysite -d ./dist
```

---

## Tech Stack {#stack}

- **Go** — Backend and server
- **gomarkdown/markdown** — Markdown to HTML
- **alecthomas/chroma** — Syntax highlighting
- **Zero JS** — No build tools, no npm, no bundlers

---

*Powered by [Electrostatic](https://github.com/laranatech/electrostatic)*
