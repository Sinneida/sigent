---
description: "Create or update DESIGN.md from the current browser page or screenshot using the alv-ux-vue DESIGN.md workflow. Use for screenshot-to-DESIGN.md generation, browser-driven design-system capture, and ALV UI extraction."
---

Create or update `DESIGN.md` from the browser page or screenshot currently available in chat.

Use these plugin references as the source of truth:
- [DESIGN.md skill](../skills/design-md-spec/SKILL.md)
- [Generic template](../skills/design-md-spec/references/template.md)
- [ALV template](../skills/design-md-spec/references/alv-template.md)

Workflow requirements:
- Treat the current browser page or screenshot as the primary source of truth.
- Extract visible design tokens and patterns: colors, typography, spacing rhythm, layout structure, shapes, and component treatments.
- Follow the `DESIGN.md` token schema and canonical section order defined in the referenced skill.
- If `DESIGN.md` already exists, read it first and update it in place instead of replacing intentional choices blindly.
- If the source is clearly ALV-branded, reuse ALV defaults where they match the observed design.
- If the source is not clearly ALV-branded, stay faithful to the observed design instead of forcing ALV branding.
- Save the result as `DESIGN.md` in the project root.
- Validate token references and check likely text/background combinations for WCAG AA contrast.
- Do not generate application logic, CSS files, or component code unless the user explicitly asks for that follow-up.

Execution flow:
1. Inspect the available browser or screenshot context.
2. Read any existing `DESIGN.md` in the target project.
3. Map the observations into YAML tokens plus the eight canonical prose sections.
4. Write or update `DESIGN.md`.
5. End with a short summary of what was extracted and any assumptions that need confirmation.