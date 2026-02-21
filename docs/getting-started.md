---
title: Get Started
description: Quick start guide to build your first site with Electrostatic
keywords: tutorial, installation, quick start, guide
date: 2025-02-21
---

# Get Started

Get your first Electrostatic site running in under 5 minutes.

## Prerequisites

- **Go 1.25+** installed

## Installation

```bash
git clone https://github.com/laranatech/electrostatic
cd electrostatic
```

## Create Your First Site

```bash
go run . -m init -r ./mysite
```

## Development Mode

```bash
go run . -m serve -r ./mysite -p :3030
```

Visit `http://localhost:3030`

## Production Build

```bash
go run . -m export -r ./mysite -d ./dist
```

Deploy `dist/` to any web server!
