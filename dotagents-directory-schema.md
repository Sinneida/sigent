---
name: AI Agents Directory Structure
description: This directory structure is designed to organize the components of an AI agent system, including instructions, context, logs, memory, specialized agents, skills, and specifications.
type: Note
---
# DotAgents Directory Schema

It stems from the [dotagents](https://github.com/bgreenwell/dotagents) standard, so it's universal and can be used with any agent.

| Name | Description | Example |
| --- | --- | --- |
| agents | Custom agents (personas) | `qa.agent.md` → QA Engineer |
| context | Static points of reference **(read-only)** | `- schema.sql` → DB structure - `api.ts` → API interfaces |
| design | DESIGN.md, ALV color palette etc. | `DESIGN.md, alv_colors.md` |
| docs | Logs, project knowledge **(read-write)** | `decisions.md`, `improvements.md` |
| instructions | General behavioral guidelines | `frontend.instruction.md` → rule for frontend |
| skills | Skills for agent | `vueuse/` |
| spec | OpenSpec directories, meant for bigger projects | `specs/`, `changes/`, `config.yaml` |
| tasks | Smaller spec-oriented changes logging system. All MD files contain frontmatter with following properties: - name - description | \* `nginx-docker → task name `- `plan.md → AI-made implementation plan `- `proposal.md → what & why → from user chat `- ``post-notes.md → "What would help you do the job better next time?" * `archive/` → folder for done tasks`` |
| temp | Data which shouldn't or there's no need to commit into the repo. | `evergreen_review.md` → file created by PR prompt, assessing current implementation. |