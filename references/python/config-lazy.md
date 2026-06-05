---
kanon:
  description: "Config class pattern: centralized env-var parsing with a module-level singleton"
  keywords:
    - python
    - config
    - configuration
    - environment variables
    - env vars
    - singleton
---

# Python Config class

Centralize all env-var parsing in a single `Config` class; import the module-level singleton everywhere.

```python
import os
from functools import cached_property
from datetime import timedelta

class Config:
    # Required — fail if absent
    @cached_property
    def database_url(self) -> str:
        return os.environ["KN_DATABASE_URL"]

    # Optional with default
    @cached_property
    def is_development(self) -> bool:
        return os.getenv("KN_ENVIRONMENT", "production").lower() in ("dev", "development")

    # Expose complex types
    @cached_property
    def timeout(self) -> timedelta:
        return timedelta(seconds=float(os.getenv("KN_TIMEOUT_SECONDS", "30")))

config = Config()
```
- Use `cached_property` to load all config lazily.
- Prefix all env vars with a short key distinct to the app.
- Read and parse all values in `__init__`; store as typed attributes — the rest of the codebase works with `int`, `timedelta`, etc., never raw strings
- Use `os.environ[KEY]` (raises `KeyError`) for required values; use `os.getenv(KEY, default)` for optional ones
- For booleans, check against `("true", "1")` — `bool(os.getenv(...))` is always `True` for any non-empty string
