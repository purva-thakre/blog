# blog

🚧 **Under construction.** A minimalistic blog built with [Hugo](https://gohugo.io/) and the [Hugo Bear Blog](https://github.com/janraasch/hugo-bearblog) theme.

## Test the build locally

Make sure [Hugo](https://gohugo.io/installation/) is installed, then:

```sh
# Start a local dev server with live reload (drafts included)
hugo server -D
```

Open http://localhost:1313 in your browser. Press `Ctrl+C` to stop.

To build the static site into the `public/` folder without a server:

```sh
hugo
```

## Add content

```sh
# New blog post
hugo new blog/my-post.md

# New page
hugo new my-new-page.md
```

## Blog post template

New posts start from the site's [archetype](archetypes/blog.md). A blog post is a Markdown file with front matter at the top:

```markdown
+++
title = "My Post"
date = "2026-09-24"
draft = true

# description is optional
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = ["example", "hugo"]
+++

Post body in Markdown goes here.
```

- `title` and `date` are required; the rest are optional.
- New posts start as drafts (`draft = true`) and don't appear in the built site. Set `draft = false` (or remove the line) to publish.
- Use `<!--more-->` to split the summary (shown on the index) from the full body.

## Comments (Reply on GitHub)

Comments are handled with GitHub Discussions — no third-party app needed. Each post links to its **own, fixed discussion thread** that everyone replies to.

Setup:

1. Enable **Discussions** in the repo (**Settings → General → Features → Discussions**).
2. Create one discussion per post, e.g. "Comments: Markdown Syntax Guide".
3. Paste that discussion's URL into the post's front matter:

```toml
discussion = "https://github.com/purva-thakre/blog/discussions/1"
```

The **Reply on GitHub** link at the bottom of the post then points straight to that thread. If a post has no `discussion` set yet, the link falls back to opening a new discussion with the title pre-filled. The link is rendered by `layouts/partials/reply_on_github.html` and only appears on blog posts. To change the target repo, edit the `githubRepo` param in `config.toml`.

## Search

A client-side search box sits in the site header (no backend). On build, Hugo writes `index.json` (post titles, dates, summaries and content) and the search box filters it in the browser.

- Index template: `layouts/index.json` — includes only posts in the `blog` section.
- Search UI: `layouts/partials/header.html`.
- To include other pages in search, add them to the `range where .Site.RegularPages "Section" "blog"` line in `layouts/index.json`.

## Code blocks

Fenced code blocks are enabled by default (`codeFences = true` in `config.toml`). To get syntax highlighting, add a language tag after the opening backticks:

````markdown
```python
def greet(name):
    print(f"Hello, {name}!")
```
````

Code blocks get line numbers automatically (`lineNos = true` in `config.toml`). The styling follows the "friendly" highlight style and is adjusted for dark mode via `layouts/partials/custom_head.html`.

For more control you can also use Hugo's built-in `highlight` shortcode (for example, to disable line numbers for one block):

```
{{< highlight python "lineNos=false" >}}
def greet(name):
    print(f"Hello, {name}!")
{{< /highlight >}}
```

Use triple backticks with no language tag for a plain, unhighlighted code block:

````markdown
```
plain text block
```
````

See `content/blog/markdown-syntax.md` for live examples of all of these.

## About the `themes/hugo-bearblog` submodule

The theme is added as a [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) (as recommended by the theme's installation guide), so it shows up in source control. Git tracks only a pinned commit reference to the theme repo (via `.gitmodules`), not the theme files themselves. When cloning this repo:

```sh
git clone --recursive https://github.com/purva-thakre/blog.git
```

To update the theme to the latest commit:

```sh
git submodule update --remote themes/hugo-bearblog
```

## Deploy to GitHub Pages

Deployment is handled automatically by a [GitHub Actions](https://github.com/features/actions) workflow (`.github/workflows/deploy.yml`). Every push to `main` builds the site with Hugo and publishes it to GitHub Pages.

The blog appears at:

```
https://purva-thakre.github.io/blog/
```

### One-time setup in GitHub

GitHub Pages must be enabled manually once (the workflow can't do it — it needs repo admin rights):

1. Push this repo to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **GitHub Actions**.
4. Push to `main` again — the workflow builds the site and deploys it.

The `baseURL` in `config.toml` is already set to the published URL.