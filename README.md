# mysite

A static personal website. Fast, simple, and clean.

## Structure

```
├── index.md            # Homepage content
├── template.html       # HTML template
├── meta.json           # Site metadata
├── 404.md              # Not found page
├── 403.md              # Forbidden page
├── 500.md              # Server error page
├── public/             # Public assets
│   ├── style.css       # Main stylesheet
│   ├── monokai.css     # Code theme
│   └── robots.txt      # Robots directive
└── assets/             # Static assets
```

## Local Development

```bash
# Serve with any static site generator or file server
python3 -m http.server 8000
```

## License

See [LICENSE](LICENSE) for details.
