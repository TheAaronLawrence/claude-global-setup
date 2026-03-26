---
paths:
  - "**/*.vue"
  - "**/*.css"
  - "**/*.scss"
  - "**/*.less"
  - "**/*.pcss"
---

# Frontend Styling Rules

Always use the `frontend-design` skill when working on frontend styling.

## Branding Consistency

Before writing any styles:

1. Search the codebase for existing design tokens, CSS variables, theme files, and utility classes.
2. Identify the established visual language: colors, spacing scale, typography, border radii, shadows, transitions.
3. Match it exactly. Do not invent new values.

## Rules

- Never hardcode a color, spacing value, or font size if a variable or token already exists for it.
- If a new design token is genuinely needed, add it to the shared theme/variables file, not inline.
- Follow the existing component library's sizing and spacing conventions.
- Every new UI element should look like it was built by the same team that built the rest of the application.
