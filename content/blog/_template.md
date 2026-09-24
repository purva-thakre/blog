+++
title = "Post Title"
date = "2026-09-24"
draft = true

# description is optional
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = ["tag1", "tag2"]

# Link to a fixed GitHub Discussion thread for this post's comments.
# Create one discussion per post in the repo, then paste its URL here:
# discussion = "https://github.com/purva-thakre/blog/discussions/1"
+++

# Post Title

Intro paragraph — keep it short; it becomes the summary shown on the index
unless you use `<!--more-->` below.

<!--more-->

## Section one

The body goes here. Use `##` subheadings to break up long posts.

## Code block

```python
def hello(name):
    print(f"Hello, {name}!")
```

## Quote

> Keep posts short and focused.

## Checklist before publishing

1. Set `draft = false` (or remove the `draft` line) in the front matter.
2. Preview locally with `hugo server -D`.
3. Push to `main` — the deploy workflow publishes the site.