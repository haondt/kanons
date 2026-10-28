---
kanon:
  description: "Kill only the processes you started, by PID"
---

# Processes

- Capture the PID when you start a process, and kill only that PID
- Never use `pkill -f`, `killall` or any pattern that could match a process you did not start
- Run throwaway servers on a non-default port
