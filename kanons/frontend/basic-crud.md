---
kanon:
  description: "Basic CRUD frontend pages"
---

# Basic CRUD Pages

When an object needs CRUD UX, implement any required parts as follows:

- **List** — `/<object type plural>`
  - Button to create a new object
  - Optional: search bar
- **Create** — `/<object type plural>/new/<id>`
  - Regular HTML form submitting a `POST` request
  - On invalid create: return `400` with errors shown inline
  - On success: redirect to the detail page
- **Edit** — `/<object type plural>/edit/<id>`
  - Regular HTML form submitting a `POST` request
  - On invalid edit: return `400` with errors shown inline
  - On success: redirect to the detail page
- **Detail** — `/<object type plural>/view/<id>`
  - If an edit page exists, include an "Edit" button linking to it
  - Delete button with confirmation; on deletion, redirect to the list
