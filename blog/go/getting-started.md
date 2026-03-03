---
title: Getting Started with Electrostatic
description: Learn how to set up your first static site with Electrostatic in minutes
keywords: electrostatic, tutorial, getting started, ssg
date: 2025-02-21
category: go
tags: tutorial, go, ssg
readTime: 5 min
---

# Getting Started with Electrostatic

Electrostatic is a minimal static site generator written in Go. It converts Markdown files into HTML, perfect for blogs, documentation, and landing pages.

## Installation

First, clone the repository:

```bash
git clone https://github.com/laranatech/electrostatic
cd electrostatic
```

## Creating Your First Site

Initialize a new project:

```bash
go run . -m init -r ./mysite
```

This creates a basic structure with:
- `index.md` — your homepage
- `template.html` — HTML template
- `meta.json` — metadata configuration
- `public/` — static assets (CSS, JS)
- `assets/` — images and media

## Development Mode

Start the SSR server for live development:

```bash
go run . -m serve -r ./mysite
```

Now visit `http://localhost:3030`. Any changes to `.md` files are reflected immediately on refresh.

## Building for Production

Export static HTML files:

```bash
go run . -m export -r ./mysite -d ./dist
```

The `dist/` folder contains your complete site, ready to deploy to any web server.

## Writing Content

Create new markdown files with frontmatter:

```yaml
---
title: My Article
description: Article description
keywords: tag1, tag2
date: 2025-02-21
category: go
tags: tutorial, go
---

# Content here

Markdown content...
```

## Customization

Edit `template.html` to change the layout and `public/style.css` for styling.

Happy writing!

---

**Related:**
- [Go vs JavaScript for Static Site Generators](/blog/go/go-vs-js)
- [Why Static Sites Are Making a Comeback](/blog/devops/why-static-sites)
