---
kanon:
  description: "Others edit the workspace too; do not revert changes you didn't make"
---

# Shared workspace

- Assume the user and other sessions edit the workspace at the same time as you
- A file that changed since you last read it: take its current state as authoritative, and comment only if the change breaks the task
- Do not treat unexplained changes as corruption
- Do not restore a file or code the user deleted
- Never run `git checkout`, `restore`, `reset` or `clean` to undo changes you did not make without confirming first
