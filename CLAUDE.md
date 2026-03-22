# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```sh
npm run dev       # Start dev server at localhost:4321
npm run build     # Build production site to ./dist/
npm run preview   # Preview production build locally
npm run astro ... # Run Astro CLI commands (e.g. astro check, astro add)
```

There are no tests or a linter configured in this project.

## Architecture

This is an Astro 5 personal/professional site for Andrew Vieau (andrewvieau.com) using the Content Collections API with MDX and sitemap integrations.

**Content layer:** Blog posts live in `src/content/blog/` as `.md` or `.mdx` files. The collection schema is defined in `src/content.config.ts` — required frontmatter fields are `title`, `description`, and `pubDate`; optional fields are `updatedDate` and `heroImage`.

**Routing:** `src/pages/blog/[...slug].astro` generates static paths from the blog collection at build time. The slug maps to `post.id`, which is the filename without extension (e.g. `back-to-drawing-board.md` → `/blog/back-to-drawing-board/`).

**Global config:** `src/consts.ts` holds `SITE_TITLE` (`'Andrew Vieau'`) and `SITE_DESCRIPTION`. The site URL is set in `astro.config.mjs`.

**Layout:** `src/layouts/BlogPost.astro` wraps individual blog post pages. The homepage (`src/pages/index.astro`) and about page (`src/pages/about.astro`) are standalone pages that use BaseHead + Header + Footer directly — they do not use the BlogPost layout.

**`BaseHead` component:** Included on every page via the layout or standalone pages. Handles all `<head>` metadata (OpenGraph, Twitter cards, canonical URLs, RSS link, font preloads). Global styles are in `src/styles/global.css` and loaded via `BaseHead`.

**Images:** Static assets go in `public/`. In-source images (e.g. blog hero images referenced in frontmatter) go in `src/assets/` and are processed by Astro's image optimization pipeline using `sharp`.

**RSS:** `src/pages/rss.xml.js` generates the RSS feed using `@astrojs/rss`.
