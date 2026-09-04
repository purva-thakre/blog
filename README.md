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

1. Push this repo to GitHub.
2. On the next push to `main`, the workflow runs, enables GitHub Pages, and your blog goes live.

If Pages is already enabled with a different source, set **Settings → Pages → Build and deployment → Source** to **GitHub Actions**.

The `baseURL` in `config.toml` is already set to the published URL.