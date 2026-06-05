---
kanon:
  description: "Config class pattern with singleton"
  template: jinja
---

# Python configuration

- Centralize all config in a single `Config` class in `config.py`; instantiate a module-level `config = Config()` and import that object everywhere — do not scatter `os.getenv` calls throughout the codebase
{% if `haondt::python/config` in kanons %}
- See `kanon ref read haondt::python/config` for the full implementation pattern
{% elif `haondt::python/config-lazy` in kanons %}
- See `kanon ref read haondt::python/config-lazy` for the full implementation pattern
{% endif %}
