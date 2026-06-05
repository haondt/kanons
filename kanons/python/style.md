---
kanon:
  description: "General style guidance for python code"
---

# Python style

- Use `pathlib.Path` over `os.path` or plain strings
- Raise specific exceptions; avoid bare `except:`
- Use `from __future__ import annotations` for deferred type hint evaluation
- Above 200 lines, consider splitting at natural seams (distinct responsibilities, separable layers); extract a sub-package if the architecture encourages it.
- Do not split arbitrarily — a long but cohesive class or algorithm is fine as one file
- Use absolute imports over relative ones
- Use modern type hints - `list[x]` over `List[x]`, `x | None` over `Optional[x]`, etc
- Use fully qualified type hints everywhere except `isinstance` checks. `dict[Any, Any]` is preferred to `dict`.

