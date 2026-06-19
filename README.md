# Portfolio — Alireza Naghdipour

Personal portfolio and blog built with [Astro](https://astro.build) and Tailwind CSS.

## Stack

- **Framework:** Astro 6
- **Styling:** Tailwind CSS
- **Syntax highlighting:** Shiki (dual light/dark themes)
- **Content:** Astro Content Collections (Markdown)

## Getting Started

```bash
npm install
npm run dev
```

Open [http://localhost:4321](http://localhost:4321) in your browser.

## Commands

| Command | Description |
|---|---|
| `npm run dev` | Start dev server at `localhost:4321` |
| `npm run build` | Build for production into `dist/` |
| `npm run preview` | Preview the production build locally |

## Writing Posts

Create a `.md` file in `src/content/posts/`:

```md
---
title: "Your Post Title"
description: "Brief description"
date: 2026-06-19
tags: ["tag1", "tag2"]
---

Post content here...
```

The filename becomes the URL slug — `my-post.md` → `/posts/my-post`.

To keep a post hidden, add `draft: true` to the frontmatter.

## Project Structure

```
src/
  content/
    posts/          # Markdown blog posts
  content.config.ts # Content collection schema
  layouts/
    Layout.astro    # Base HTML layout
  components/
    Nav.astro
    Hero.astro
    Experience.astro
    Skills.astro
    Education.astro
    Footer.astro
  pages/
    index.astro     # Homepage
    posts/
      index.astro   # Posts listing
      [slug].astro  # Individual post
```
