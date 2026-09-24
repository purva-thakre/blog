+++
title = "{{ replace .Name "-" " " | title }}"
date = "{{ .Date }}"
draft = true

#
# Set draft to false (or remove the line) when you are ready to publish.
#
# description is optional
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = [{{ range $plural, $terms := .Site.Taxonomies }}{{ range $term, $val := $terms }}"{{ printf "%s" $term }}",{{ end }}{{ end }}]

# Link to a fixed GitHub Discussion thread for this post's comments.
# Create one discussion per post in the repo, then paste its URL here:
# discussion = "https://github.com/purva-thakre/blog/discussions/1"
+++

This is a page about »{{ replace .Name "-" " " | title }}«.