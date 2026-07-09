---
name: design-md-spec
description: "Create, read, apply, or generate a DESIGN.md design-system specification. USE FOR: generating DESIGN.md from screenshots or browser pages, applying an existing DESIGN.md to a project, creating a new DESIGN.md from scratch, reviewing design tokens, extracting visual identity from UI. DO NOT USE FOR: general CSS or layout debugging, writing application logic, non-design file generation."
context: fork
argument-hint: "Describe the design task: generate from screenshot, apply to project, create new, or review existing DESIGN.md"
---

# DESIGN.md — Design System Specification

Create, apply, or generate a `DESIGN.md` file following the [google-labs-code/design.md](https://github.com/google-labs-code/design.md) specification.

## When to Use

- Generate a `DESIGN.md` from a screenshot or browser page the agent has read
- Apply an existing `DESIGN.md` to a new or existing project
- Create a new `DESIGN.md` from scratch based on user requirements
- Review or lint an existing `DESIGN.md` for completeness

## What is DESIGN.md

A `DESIGN.md` is a self-contained, plain-text representation of a design system. It combines:

1. **YAML front matter** — machine-readable design tokens (colors, typography, spacing, components)
2. **Markdown body** — human-readable design rationale organized into `##` sections

The tokens are the normative values. The prose provides context for *how and why* to apply them.

## Procedure

### Mode A — Generate from Visual Source (Screenshot / Browser Page)

1. **Inspect the visual source.** Identify from the screenshot or page:
   - Color palette (extract dominant + accent hex values)
   - Typography (font families, sizes, weights visible)
   - Layout rhythm (spacing, grid patterns)
   - Component styles (buttons, cards, inputs, shapes)
   - Overall mood and brand personality
2. **Map findings to the token schema.** See [template](./references/template.md) for the full token schema.
3. **Draft the DESIGN.md.** Fill in both YAML tokens and prose sections.
4. **Validate.** Check WCAG contrast ratios for `backgroundColor`/`textColor` component pairs (minimum 4.5:1 for AA). Verify all `{token.references}` resolve.
5. **Save** as `DESIGN.md` in the project root.

### Mode B — Apply Existing DESIGN.md to a Project

1. **Read the project's `DESIGN.md`.** Parse the YAML front matter for tokens and the prose for guidance.
2. **Identify the target framework.** Determine if the project uses Tailwind, plain CSS, SCSS, CSS-in-JS, etc.
3. **Generate framework artifacts:**
   - **Tailwind v3**: Create a `tailwind.config.js` `theme.extend` from tokens.
   - **Tailwind v4**: Create a CSS `@theme { ... }` block with CSS custom properties.
   - **CSS/SCSS**: Generate custom properties or variables from tokens.
4. **Apply component tokens** to matching UI elements. Map `components.*` tokens to actual component styles.
5. **Follow prose guidance** for layout, elevation, shapes, and do's/don'ts sections.

### Mode C — Create New DESIGN.md from Requirements

1. **Clarify** the brand personality, target audience, and emotional tone with the user.
2. **Define the color palette.** At minimum: `primary`, `secondary`, `tertiary`, `neutral`. Add semantic roles (`surface`, `on-surface`, `error`) as needed.
3. **Define typography.** Choose font families, set levels (headline, body, label). Use 9–15 levels for a complete system.
4. **Define spacing, shapes, and elevation.** Pick a base unit (usually 8px) and build a scale.
5. **Define components.** Map tokens to at least: buttons, cards, inputs. Include hover/active variants as separate entries.
6. **Write the prose sections** explaining *why* each choice was made.
7. **Use the [template](./references/template.md)** as the starting scaffold.

## Token Schema Reference

```yaml
version: <string>          # optional, current: "alpha"
name: <string>             # required
description: <string>      # optional
colors:
  <token-name>: <Color>    # "#" + hex (sRGB), e.g. "#1A1C1E"
typography:
  <token-name>: <Typography>
    # fontFamily, fontSize, fontWeight, lineHeight, letterSpacing, fontFeature, fontVariation
rounded:
  <scale-level>: <Dimension>  # e.g. sm: 4px, md: 8px
spacing:
  <scale-level>: <Dimension | number>
components:
  <component-name>:
    <property>: <string | token reference>
    # Valid properties: backgroundColor, textColor, typography, rounded, padding, size, height, width
```

**Token references** use `{path.to.token}` syntax, e.g. `"{colors.primary}"`.

## Section Order

Sections use `##` headings. Omit if irrelevant, but preserve this order:

| # | Section | Aliases |
|:--|:--------|:--------|
| 1 | Overview | Brand & Style |
| 2 | Colors | |
| 3 | Typography | |
| 4 | Layout | Layout & Spacing |
| 5 | Elevation & Depth | Elevation |
| 6 | Shapes | |
| 7 | Components | |
| 8 | Do's and Don'ts | |

## Quality Checks

- [ ] All `{token.references}` in components resolve to defined tokens
- [ ] `primary` color exists when colors section is defined
- [ ] Typography tokens exist when colors are defined
- [ ] Component `backgroundColor`/`textColor` pairs meet WCAG AA (4.5:1)
- [ ] Sections appear in canonical order
- [ ] Prose explains *why*, tokens define *what*

## CLI (Optional)

If `@google/design.md` is available:

```bash
npx @google/design.md lint DESIGN.md          # Validate structure
npx @google/design.md diff old.md new.md      # Compare versions
npx @google/design.md export --format css-tailwind DESIGN.md  # Export tokens
npx @google/design.md spec                    # Output the spec for prompt context
```

## Resources

- [DESIGN.md Template](./references/template.md) — Full starter template with all sections and example tokens