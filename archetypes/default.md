+++
title = "{{ replace .Name "-" " " | title }}"
date = "{{ .Date }}"
draft = true

#
# Set draft to false (or remove the line) when you are ready to publish.
#
# description is optional
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

#
# tags are optional
#
# tags = [{{ range $plural, $terms := .Site.Taxonomies }}{{ range $term, $val := $terms }}"{{ printf "%s" $term }}",{{ end }}{{ end }}]
+++

This is a page about »{{ replace .Name "-" " " | title }}«.