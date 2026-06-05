---
kanon:
  description: "Config class pattern with singleton"
  template: jinja
---

# Python configuration

- Centralize all config in a single `Config` class in `config.py`; instantiate a module-level `config = Config()` and import that object everywhere — do not scatter `os.getenv` calls throughout the codebase
{% if args.lazy %}
- See `kanon ref read {{source}}::python/config-lazy` for the full implementation pattern
{% else %}
- See `kanon ref read {{source}}::python/config` for the full implementation pattern
{% endif %}
