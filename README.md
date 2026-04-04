# knudge

> *What does today's news mean for you?*

Personalized AI-driven news briefs that translate daily news into specific personal life impact.

Built with **Astro 6** + **Tailwind CSS v4** + **Vercel**.

---

## Stack

| Layer | Tech |
|-------|------|
| Framework | Astro (latest / v6+) |
| Styling | Tailwind CSS v4 via `@tailwindcss/vite` |
| Blog | Astro Content Layer API (Markdown) |
| Hosting | Vercel (static output) |
| Fonts | Google Fonts — Playfair Display + DM Sans + DM Mono |
| Images | Unsplash (external CDN URLs) |

---

## Getting Started

### Prerequisites

- Node.js v22.12.0 or higher
- npm / pnpm / yarn

### Install

```bash
npm install
```

### Dev server

```bash
npm run dev
```

Opens at `http://localhost:4321`

### Build

```bash
npm run build
```

Output goes to `dist/`. Static files, ready to deploy anywhere.

### Preview build locally

```bash
npm run preview
```

---

## Deploying to Vercel

### Option A — Connect GitHub (recommended)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project → Import your repo
3. Vercel auto-detects Astro — no config needed
4. Set your domain to `knudge.in` in Project Settings → Domains

### Option B — Vercel CLI

```bash
npm i -g vercel
vercel
```

---

## Things to edit before launch

### 1. Replace placeholder links

Search for `YOUR_TELEGRAM_LINK` and `YOUR_WHATSAPP_LINK` in:

- `src/pages/index.astro`
- `src/pages/blog/index.astro`
- `src/layouts/BlogLayout.astro`
- `src/components/Footer.astro`

Replace with your actual Telegram invite link (e.g. `https://t.me/knudge`) and WhatsApp broadcast link.

### 2. Update site URL

In `astro.config.mjs`, the `site` is set to `https://knudge.in`. Change if needed.

### 3. Instagram / social links

In `src/components/Nav.astro` and `src/components/Footer.astro`, the Instagram link points to `https://www.instagram.com/lifewithanugrah`. Update if the handle changes.

### 4. OG Image

Drop an `og.png` (1200×630) into `/public/` for social share previews.

---

## Writing Blog Posts

All posts live in `src/content/blog/`. Create a new `.md` file:

```
src/content/blog/your-post-slug.md
```

**Required frontmatter:**

```yaml
---
title: "Your Post Title"
description: "One-line description for the listing page and meta tags."
date: 2026-04-10
readTime: "5 min read"    # optional, defaults to "5 min read"
draft: false              # set true to hide from listing
---
```

**Then write in Markdown below the frontmatter.**

The URL will be `/blog/your-post-slug`.

---

## Project Structure

```
knudge/
├── astro.config.mjs          Astro config — Tailwind v4 vite plugin here
├── src/
│   ├── content.config.ts     Astro 5 Content Layer API (NOT src/content/config.ts)
│   ├── content/blog/         Markdown posts go here
│   ├── styles/global.css     Tailwind v4 config lives here (@theme block)
│   ├── layouts/
│   │   ├── BaseLayout.astro  HTML shell, fonts, nav, footer
│   │   └── BlogLayout.astro  Individual post wrapper
│   ├── components/
│   │   ├── Nav.astro         Sticky nav with scroll effect + mobile menu
│   │   └── Footer.astro
│   └── pages/
│       ├── index.astro       Homepage
│       └── blog/
│           ├── index.astro   Blog listing
│           └── [slug].astro  Dynamic post route
└── public/
    └── favicon.svg
```

---

## Tailwind v4 Notes

Tailwind v4 is CSS-first. Key differences from v3:

- **No `tailwind.config.js`** — all config lives in `src/styles/global.css`
- **`@theme` block** defines custom colors, fonts, etc.
- **`@import "tailwindcss"`** replaces the old `@tailwind base/components/utilities` directives
- **`@tailwindcss/vite`** is the plugin (not `@astrojs/tailwind`)
- Custom colors defined in `@theme` generate utility classes automatically: `--color-gold` → `text-gold`, `bg-gold`, etc.

---

## Customising the Design

All design tokens are in `src/styles/global.css` inside the `@theme` block:

```css
@theme {
  --color-gold:    #C9A468;   /* primary accent */
  --color-cream:   #F0EAD8;   /* primary text */
  --color-ink:     #0C0A07;   /* background */
  /* ... */
}
```

Change values there and it propagates everywhere.

---

## Content Layer API (Astro 5+) Notes

Key differences from legacy Astro collections:

- Config file: `src/content.config.ts` (not `src/content/config.ts`)
- Use `loader: glob(...)` pattern (not `type: 'content'`)
- `render(post)` from `astro:content` (not `post.render()`)
- `post.id` is the slug/identifier (not `post.slug`)

---

*Built by Anugrah. Follow the build on [@lifewithanugrah](https://www.instagram.com/lifewithanugrah).*
