# DESIGN.md Template

Full starter template based on the [google-labs-code/design.md](https://github.com/google-labs-code/design.md) specification (version: alpha).

Replace placeholder values (`<...>`) with your project's actual design tokens and rationale.

---

````markdown
---
version: alpha
name: <Design System Name>
description: <One-line description of the design system>
colors:
  primary: "<#hex>"
  secondary: "<#hex>"
  tertiary: "<#hex>"
  neutral: "<#hex>"
  surface: "<#hex>"
  on-surface: "<#hex>"
  error: "<#hex>"
  # Add more as needed: surface-container, on-primary, inverse-surface, etc.
typography:
  headline-lg:
    fontFamily: <Font Name>
    fontSize: 32px
    fontWeight: 600
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: <Font Name>
    fontSize: 24px
    fontWeight: 500
    lineHeight: 32px
  body-lg:
    fontFamily: <Font Name>
    fontSize: 18px
    fontWeight: 400
    lineHeight: 28px
  body-md:
    fontFamily: <Font Name>
    fontSize: 16px
    fontWeight: 400
    lineHeight: 24px
  label-lg:
    fontFamily: <Font Name>
    fontSize: 14px
    fontWeight: 500
    lineHeight: 20px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: <Font Name>
    fontSize: 12px
    fontWeight: 600
    lineHeight: 16px
    letterSpacing: 0.05em
rounded:
  none: 0px
  sm: 4px
  md: 8px
  lg: 12px
  xl: 16px
  full: 9999px
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  2xl: 48px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.label-lg}"
    rounded: "{rounded.md}"
    padding: 12px
    height: 40px
  button-primary-hover:
    backgroundColor: "<#hex>"
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.primary}"
    typography: "{typography.label-lg}"
    rounded: "{rounded.md}"
    padding: 12px
    height: 40px
  card:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.lg}"
    padding: "{spacing.lg}"
  input-field:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    typography: "{typography.body-md}"
    rounded: "{rounded.md}"
    padding: 12px
    height: 40px
---

## Overview

<!-- Brand personality, target audience, emotional tone, and overall aesthetic direction. -->

<Describe the holistic look and feel. What emotional response should the UI evoke?
Is it playful or professional, dense or spacious? Define the brand personality and
target audience.>

## Colors

<!-- Define color palettes and explain the semantic role of each. -->

- **Primary (<#hex>):** <Role and usage — e.g., headlines, core text, primary actions>
- **Secondary (<#hex>):** <Role — e.g., borders, captions, secondary elements>
- **Tertiary (<#hex>):** <Role — e.g., accent color for interactions, highlights>
- **Neutral (<#hex>):** <Role — e.g., page background, card surfaces>

## Typography

<!-- Define font families, hierarchy, and usage rules. -->

The typography strategy uses **<Primary Font>** for <purpose> and
**<Secondary Font>** for <purpose>.

- **Headlines:** <Font> at <weight> for <reason>.
- **Body:** <Font> at <size> for <readability goal>.
- **Labels:** <Font> at <size> with <treatment> for <purpose>.

## Layout

<!-- Grid system, spacing rhythm, and content grouping strategy. -->

The layout follows a **<Grid Type>** model.

- **Rhythm:** An <N>px base grid governs all dimensions.
- **Grouping:** Related items are housed in <container type> with <padding> internal spacing.
- **Negative Space:** <Margin strategy and reasoning>.

## Elevation & Depth

<!-- How visual hierarchy is conveyed — shadows, tonal layers, borders, etc. -->

<Describe the depth strategy. Does the system use shadows, tonal layers, borders,
or blur? Define the levels and their CSS properties.>

## Shapes

<!-- Corner radius strategy and shape language. -->

<Describe the shape language — sharp, rounded, pill-shaped? What radius scale
is used and why?>

## Components

<!-- Style guidance for component atoms. Expand each as needed. -->

### Buttons

<Primary, secondary, tertiary variants. Sizing, padding, states (hover, active, disabled).>

### Cards

<Surface treatment, padding, border or shadow, content alignment.>

### Input Fields

<Text inputs, labels, helper text, error states, focus rings.>

### Lists

<List items, dividers, leading/trailing elements.>

## Do's and Don'ts

- Do <positive guideline>
- Don't <anti-pattern to avoid>
- Do maintain WCAG AA contrast ratios (4.5:1 for normal text)
- Don't <common mistake in this design system>
````

---

## Token Type Quick Reference

| Type            | Format                            | Example            |
| :-------------- | :-------------------------------- | :----------------- |
| Color           | `#` + hex (sRGB)                  | `"#1A1C1E"`        |
| Dimension       | number + unit (`px`, `em`, `rem`) | `48px`, `-0.02em`  |
| Token Reference | `{path.to.token}`                 | `{colors.primary}` |
| Typography      | object with font properties       | See tokens above   |

## Recommended Token Names

**Colors:** `primary`, `secondary`, `tertiary`, `neutral`, `surface`, `on-surface`, `error`

**Typography:** `headline-display`, `headline-lg`, `headline-md`, `body-lg`, `body-md`, `body-sm`, `label-lg`, `label-md`, `label-sm`

**Rounded:** `none`, `sm`, `md`, `lg`, `xl`, `full`

**Spacing:** `xs`, `sm`, `md`, `lg`, `xl`, `2xl`

## Component Property Tokens

Each component entry supports these properties:

- `backgroundColor`: Color
- `textColor`: Color
- `typography`: Typography
- `rounded`: Dimension
- `padding`: Dimension
- `size`: Dimension
- `height`: Dimension
- `width`: Dimension

Variants (hover, active, pressed) are expressed as separate component entries with a related key name, e.g. `button-primary`, `button-primary-hover`, `button-primary-active`.
