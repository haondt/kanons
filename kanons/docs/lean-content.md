---
kanon:
  description: "Keep documentation focused and context-free"
---

# General documentation guidance

## Keep it concise

- Scope information to its audience: implementation comments omit usage details, usage docs omit implementation details
- State a limitation once, where the reader would look, and only if they would plausibly hit it

## Avoid extra context

- Write for someone who has never seen the project — no assumed context
- The documentation should describe the project as it is now, as if it had always been this way: no history, roadmap, or lists of what it lacks
- Do not correct assumptions a new reader would never make ("doesn't X" / "missing Y" / "not Z" / "unlike A")
- Avoid filler phrases ("This project is a...", "Welcome to...", "Feel free to...")

## Less is more

- Write no code comments unless the why is non-obvious; never restate what the code does
