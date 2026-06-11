---
name: feedback-formatting
description: How to format equations and math in responses and markdown files
metadata:
  type: feedback
---

Use ASCII notation for equations in chat (not LaTeX), because the VS Code Claude Code extension does not render LaTeX. When writing to .md files, LaTeX is fine since it can be rendered with Markdown Preview extensions.

**Why:** VS Code extension chat window does not render LaTeX — user sees raw code instead of formatted equations.

**How to apply:** In chat responses, write equations like `Q[k+1] = I1[k] · (T1[k] + Q[k])`. In .md files, use `$$...$$` LaTeX syntax as normal.
