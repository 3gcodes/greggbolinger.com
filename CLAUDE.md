# Project: 3GCodes.com (greggbolinger.com)

Personal blog and website built with Astro.

## Tech Stack

- **Framework**: Astro 5 (static site generation)
- **Content**: MDX blog posts via Astro Content Collections (glob loader)
- **Integrations**: `@astrojs/mdx`, `@astrojs/sitemap`, `@astrojs/rss`
- **Image processing**: sharp
- **Package manager**: pnpm
- **TypeScript**: strict mode (`astro/tsconfigs/strict`)

## Commands

- `pnpm dev` — Start dev server
- `pnpm build` — Build for production (output in `dist/`)
- `pnpm preview` — Preview production build locally

## Project Structure

```
src/
├── assets/            # Images (hero images, blog placeholders)
├── components/        # Astro components (Header, Footer, BaseHead, etc.)
├── content/
│   └── blog/          # MDX blog posts
├── layouts/           # BaseLayout.astro, BlogPost.astro
├── pages/
│   ├── index.astro    # Homepage (lists blog posts in grid)
│   ├── about.astro    # About page
│   ├── blog/
│   │   ├── index.astro      # Redirects to /
│   │   └── [...slug].astro  # Dynamic blog post pages
│   └── rss.xml.js     # RSS feed
├── styles/
│   └── global.css     # Global styles and CSS custom properties
├── consts.ts          # Site title and description
└── content.config.ts  # Content collection schema
public/
├── favicon.ico
├── favicon.svg
└── fonts/             # Atkinson font files (legacy, unused)
```

## Content Schema

Blog posts (`src/content/blog/*.mdx`) use this frontmatter:

```yaml
title: string          # Required
description: string    # Required
pubDate: date          # Required
updatedDate: date      # Optional
heroImage: image path  # Optional (relative to src/assets/)
heroImageCaption: string # Optional (supports HTML)
tags: string[]         # Optional
```

## Design System

- **Theme**: Retro/pixel-art aesthetic with light background
- **Fonts**: Press Start 2P (headings), VT323 (body), IBM Plex Mono (prose/code)
- **Fonts loaded via**: Google Fonts CDN
- **Layout**: `--content-width: 720px`, `--page-width: 960px`
- **Code highlighting**: Shiki with `vitesse-light` theme
- **CSS approach**: CSS custom properties in `global.css` + scoped `<style>` blocks per component
- **Links in prose**: Styled as pixel-art buttons with borders

## Key Conventions

- Site URL: `https://3gcodes.com`
- Blog posts are sorted newest-first on the homepage
- `/blog` redirects to `/` (homepage is the blog index)
- The homepage displays posts in a 2-column grid (1-column on mobile)
- Blog post routes: `/blog/{post-id}/`
- RSS feed at `/rss.xml`, sitemap at `/sitemap-index.xml`
