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

New posts start from the theme's [archetype](themes/hugo-bearblog/archetypes/blog.md). A blog post is a Markdown file with front matter at the top:

```markdown
+++
title = "My Post"
date = "2026-09-24"

# description is optional
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = ["example", "hugo"]
+++

Post body in Markdown goes here.
```

- `title` and `date` are required; the rest are optional.
- Use `<!--more-->` to split the summary (shown on the index) from the full body.

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