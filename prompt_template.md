---
type: Note
---
# Prompt Template

## Role

Define the role or expertise the model should have.

> **Example:** You're an expert ML researcher.

## Context

Provide relevant background information about the issue. It can be a description of the system, architecture, or any other relevant information that can help the agent understand the problem better. Define why the problem has arrived and why it must be resolved.

### Optional: Dictionary

If you use some specific concepts when describing the issue, it's better to create abbreviations for it like Test Order -\> TO. Saves tokens.

## Task

Clearly state what you want the agent to do.

> **Example:** Explain the Transformer architecture in detail.

## Constraints

Specify rules, limitations or requirements. Provide preffered engineering approach, your own thoughts of how to approach the issue.

> **Example:**

- *be concise but technically accurate*
- *include key equations*
- *avoid analogies*
- *use clear terminology*

## Output format

Define the format, style or structure of the output

> **Example:** Markdown with headings, bullet points and equations.

## Goal

Expected final outcome of the problem solution. Conditions under user consider tasks done. Validation list.

## Examples \(optional\)

Provide an example of desired output type.
