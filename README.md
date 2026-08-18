# ilexiv.ir

One repo, two things:

- `index.html` at the root — your existing landing page, plain static HTML, untouched by Jekyll.
- `/blog` — a Jekyll blog with the same terminal look, served at `ilexiv.ir/blog/`.

GitHub Pages runs a single Jekyll build over the whole repo. `index.html` has no
front matter, so Jekyll copies it through byte-for-byte — your landing page
behaves exactly as before. Everything blog-related (layouts, posts, styling)
is scoped under its own paths and only touches `/blog/...` URLs.

## Add a post

Create a file in `_posts/` named `YYYY-MM-DD-your-slug.md`:

```markdown
---
title: "Your title here"
date: 2026-08-19
tags: [dev, notes]
---

Write in normal markdown here.
```

It'll be published at `ilexiv.ir/blog/your-slug/`. Push it — GitHub Pages
rebuilds automatically. Delete `_posts/2026-08-18-hello-world.md` and
`_posts/2026-08-18-rtl-support.md` whenever you're ready — they're just demos.

## Writing in Persian (RTL)

Add `rtl: true` to a post's front matter and it renders right-to-left with a
Persian typeface (Vazirmatn):

```markdown
---
title: "عنوان فارسی"
date: 2026-08-19
tags: [dev]
rtl: true
lang: fa
---

متن نوشته اینجا.
```

Code blocks inside an RTL post automatically stay left-to-right and
monospace — code shouldn't mirror even in a Persian post. You can mix English
and Persian posts freely in the same `_posts/` folder; each one is
independent. Post titles in the home listing auto-detect direction even
without the flag, so a Persian title in the list still displays correctly.

## Tags

Every post's `tags:` front matter is clickable — it links to `/blog/tags/`,
which lists every tag with the posts under it. No extra setup needed, it's
built from whatever tags your posts already have.

## Run it locally (optional)

```bash
bundle install
bundle exec jekyll serve
```

Landing page: http://localhost:4000/
Blog: http://localhost:4000/blog/

## Deploy on GitHub Pages

1. Push this repo to GitHub (same repo as before, `CNAME` already points at
   `ilexiv.ir` — no DNS changes needed).
2. Repo Settings → Pages → Source: deploy from `main` (root).
3. Done. Landing page at `ilexiv.ir/`, blog at `ilexiv.ir/blog/`.

## Structure

```
index.html              landing page (static, untouched)
CNAME / robots.txt / sitemap.xml / rss.xml   landing page's existing files
_config.yml              Jekyll config (blog only)
_posts/                  your posts, one markdown file each
_layouts/default.html    terminal window chrome, shared by every blog page
_layouts/home.html       blog post list ("ls -la posts/")
_layouts/post.html       single post ("cat slug.md")
blog/index.html          blog homepage entry point → /blog/
assets/css/style.css     theme + typography
assets/css/syntax.css    code block colors
```

## Notes

- The blog's RSS feed is generated at `/blog/rss.xml` (via `jekyll-feed`) so
  it doesn't collide with the landing page's existing `/rss.xml`.
- `jekyll-sitemap` is intentionally not enabled, since there's already a
  hand-written `sitemap.xml` for the landing page at the same path. Add a
  `<url>` entry for new posts yourself, or switch to the plugin if you'd
  rather it be automatic — just delete the static `sitemap.xml` first.
