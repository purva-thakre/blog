+++
title = "Markdown Syntax Guide"
date = "2020-01-03"
description = "How Markdown is used in this blog, with examples of every feature you can use in a post."
tags = [
    "markdown",
    "syntax",
]
+++

Every post on this blog is written in Markdown. This guide shows the syntax I use here, so future posts stay consistent. For a quick cheatsheet, check out https://simplemde.com/markdown-guide.

---
<!--more-->

## Headings

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1
## H2
### H3
#### H4
##### H5
###### H6

## Paragraph

A paragraph is just plain text separated by a blank line. Keep paragraphs short and split long posts with subheadings so they read well on the blog's single-column layout.

## Blockquotes

Use a blockquote to quote another source or call out a note.

#### Blockquote without attribution

> Keep this blog minimal.
>
> **Note** that you can use *Markdown syntax* within a blockquote.

#### Blockquote with attribution

> The best blog posts are short and focused.
>
> — Me[^1]

[^1]: Emphasis on *short* — one idea per post.

## Tables

Tables are rendered out-of-the-box, no setup needed.

   Blog | Status
--------|--------
  Hugo  | Ready
Bearblog theme | In use

#### Inline Markdown within tables

| Italics   | Bold     | Code   |
| --------  | -------- | ------ |
| *italics* | **bold** | `code` |

## Code Blocks

Code blocks are highlighted with the "friendly" style and get line numbers automatically. Dark mode restyles them via `layouts/partials/custom_head.html`.

#### Code block with backticks

```python
def hello(name):
    print(f"Hello, {name}!")
```

#### Code block indented with four spaces

    def hello(name):
        print(f"Hello, {name}!")

#### Code block with Hugo's internal highlight shortcode

You can override the defaults per-block, for example to hide line numbers:

{{< highlight python "lineNos=false" >}}
def hello(name):
    print(f"Hello, {name}!")
{{< /highlight >}}

## List Types

#### Ordered List

1. Write a draft
2. Preview it locally with `hugo server -D`
3. Push to `main` and let the deploy workflow publish it

#### Unordered List

* Keep posts short
* Use `<!--more-->` for the summary
* Tag every post

#### Nested list

* New post
  * Front matter
    * title
    * date
    * tags
  * Body
* New page
  * Just a title