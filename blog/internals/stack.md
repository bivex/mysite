---
title: Tech Stack
description: Under the hood of Electrostatic — technologies and architecture
keywords: stack, architecture, go, dependencies
date: 2025-02-21
category: internals
tags: internals, go, architecture
readTime: 10 min
---

# Tech Stack

Electrostatic is built with simplicity and performance in mind.

## Core Technology

### Go (Golang)

The entire application is written in Go, chosen for:

- **Performance** — compiles to native machine code
- **Single binary** — no runtime dependencies
- **Cross-platform** — runs everywhere
- **Concurrency** — efficient parallel processing
- **Stability** — Go's compatibility promise

### Version

```go
go 1.25.1
```

## Dependencies

Electrostatic uses minimal external dependencies:

### gomarkdown/markdown

```go
import "github.com/gomarkdown/markdown"
```

- **Purpose**: Markdown to HTML conversion
- **Size**: Lightweight markdown parser
- **Extensions**: AutoHeadingIDs, NoEmptyLineBeforeBlock
- **HTML Renderer**: HrefTargetBlank, LazyLoadImages

### alecthomas/chroma

```go
import "github.com/alecthomas/chroma/v2"
```

- **Purpose**: Syntax highlighting for code blocks
- **Languages**: 100+ programming languages
- **Theme**: Monokai (customizable)
- **Features**: Line numbers, CSS classes

## Architecture

### Package Structure

```
electrostatic/
├── main.go           # CLI entry point
├── content/          # Project template initialization
├── export/           # Static site export
├── mdparcer/         # Markdown + code highlighting
├── pages/            # Page processing & routing
│   ├── types.go      # Data structures
│   ├── parse.go      # Frontmatter parsing
│   ├── scanner.go    # File system scanning
│   ├── paths.go      # URL routing
│   ├── meta.go       # Metadata handling
│   ├── template.go   # Template rendering
│   └── serve.go      # HTTP handlers
├── sitemap/          # XML sitemap (TODO)
└── static/           # Static file serving
```

### Data Flow

#### SSR Mode (Development)

```
HTTP Request
    ↓
ScanAllFilepaths() → find .md files
    ↓
ReadPageFile() → read content
    ↓
ParsePageInfo() → extract frontmatter
    ↓
NewMetaMap() → build metadata
    ↓
ReadTemplateFile() → load template
    ↓
FormatTemplate() → replace placeholders
    ↓
MdToHTML() → markdown → HTML
    ↓
RenderCode() → syntax highlight
    ↓
HTTP Response
```

#### Export Mode (Production)

```
For each .md file:
    [Same as SSR]
    ↓
Write .html to dist/
```

### Frontmatter Parsing

YAML frontmatter extracted with custom parser:

```go
---
key: value
---

Content
```

Supports:
- Colons in values (`key: value: with: colons`)
- Multiple keys per line
- Fallback to defaults if missing

### Template System

Simple string-based templating:

```go
strings.Replace(template, "%title%", page.Meta["title"], 1)
```

No complex template engine — just fast string operations.

### Routing

Filesystem-based routing:

```
content/index.md        → /
content/about.md         → /about
content/blog/post.md    → /blog/post
content/blog/index.md   → /blog
```

### HTTP Handlers

Go's `http.HandleFunc`:

```go
http.HandleFunc("/", func(w, r *http.Request) {
    // Route matching
    // Page rendering
})

http.HandleFunc("/articles", func(w, r *http.Request) {
    // Article list
})
```

### Static Files

`http.FileServer` for static assets:

```go
http.Handle("/assets/", http.StripPrefix("/assets/",
    http.FileServer(http.Dir(root + "/assets"))))
```

## Performance

### Benchmarks

Building 1000 pages:

```
Time:    ~50ms
Memory:  ~20MB
Binary:  ~10MB
```

### Optimization Strategies

1. **No template engine** — string replacement is faster
2. **Single pass parsing** — read file once
3. **Lazy rendering** — only when requested (SSR)
4. **Native code** — Go compiler optimizations

## Security

### Headers

Security headers added by server wrapper:

```http
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Cross-Origin-Opener-Policy: same-origin
Strict-Transport-Security: max-age=31536000
Content-Security-Policy: default-src 'self'; ...
```

### No User Input

- No database queries
- No form processing
- No user authentication
- No server-side scripting

Markdown files are trusted content — reduced attack surface.

## Deployment

### Binary Size

```
Electrostatic: ~10MB
Hugo:           ~50MB
Next.js:        node_modules/ ~500MB
```

### Deployment Options

Since output is static HTML:

- **GitHub Pages**
- **Netlify**
- **Vercel**
- **Cloudflare Pages**
- **Any web server** (nginx, Apache, Caddy)

## Future Plans

- [ ] XML sitemap generation
- [ ] RSS feed generation
- [ ] Pagination support
- [ ] Search functionality
- [ ] Theme system

---

**Related:**
- [Features](/blog/internals/features)
- [Go vs JavaScript for SSGs](/blog/go/go-vs-js)
