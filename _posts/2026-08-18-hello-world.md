---
title: "Hello, world"
date: 2026-08-18
tags: [meta]
---

This is the first post on the blog. Delete this file whenever you're ready to publish something real — it's just here to show how the layout handles headings, code, and links.

## Writing a post

Every post lives in `_posts/` as a markdown file named `YYYY-MM-DD-slug.md`. The front matter at the top controls the title, date, and tags:

```yaml
---
title: "Your title here"
date: 2026-08-19
tags: [dev, notes]
---
```

Everything below the front matter is normal markdown — headings, lists, links, images, and fenced code blocks all render through the same theme.

## Code blocks

```python
def greet(name):
    return f"hello, {name}"

print(greet("ilexiv"))
```

## What's next

- Push this repo to GitHub, enable Pages in the repo settings
- Point your domain at it if you want a custom URL
- Add new posts by dropping a new file in `_posts/`

That's it — no build step to remember, GitHub Pages compiles it on push.
