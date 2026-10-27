---
kanon:
  description: "Guidelines for using Bulma CSS framework"
---

# Bulma

Bulma is a CSS-only framework based on Flexbox. It has no JavaScript.

- When creating a new project with bulma, refer to the `haondt::bulma/bootstrap` reference

# Buttons
- Never use `is-light`
- Use no style non-mutating actions (Cancel, Back, Continue, etc)
- Use `is-primary` for create and update actions
- Use `is-danger` for destructive (Delete) actions
- Use `is-ghost` for icon buttons

# Spacing
- Prefer flexboxes (`is-flex`) and grids with gaps (`is-gap-1`) over boxes (`box`) for spacing
