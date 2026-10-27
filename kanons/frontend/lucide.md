---
kanon:
  description: "Guidelines for using Lucide icons"
  template: jinja
---

# Lucide

Lucide is an icon library.

{% if args.static %}
- Use icons from `lucide-static/icons/*.svg` — copy or serve them as static assets
{% else %}
- Use the `lucide` package to render icons
{% endif %}
