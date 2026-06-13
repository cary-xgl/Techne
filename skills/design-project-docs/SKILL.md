---
name: design-project-docs
description: Interactive project documentation design for AGENTS.md and README.md. Use when Codex needs to interview a user, elicit a project's purpose, scope, architecture, development conventions, design principles, tooling, workflows, and constraints, then draft, revise, or update project-level AGENTS.md and README.md files.
---

# Design Project Docs

## Overview

Use this skill to turn a loosely described project into clear project guidance. The output is usually an `AGENTS.md`, a `README.md`, or both, grounded in an interview plus facts discovered from the repository.

Act like a project documentation facilitator: ask just enough questions, synthesize decisions, and make the resulting documents useful for future humans and agents.

## Core Rules

- Prefer an interactive interview before writing or heavily revising docs.
- Ask 1-3 concise questions at a time; avoid overwhelming the user.
- Inspect existing files first: `AGENTS.md`, `README.md`, package manifests, build configs, docs folders, and visible project structure.
- Separate discovered facts from user-stated intent. Do not invent architecture, commands, policies, or design principles.
- Preserve existing useful content unless the user asks for a rewrite.
- When existing docs conflict with user answers or repo evidence, call out the conflict and ask which source should win.
- Write docs in the language already used by the project unless the user requests another language.
- Keep AGENTS.md operational and constraint-focused; keep README.md user-facing and project-focused.

## Workflow

### 1. Discover

Read enough local context to avoid asking obvious questions:

- `AGENTS.md` for agent rules, commit policy, and repository-specific instructions.
- `README.md` for current project positioning and usage.
- File tree for project shape, especially `skills/`, `src/`, `docs/`, manifests, config files, CI files, and tests.
- Existing conventions such as language, naming, formatting, test commands, and commit style.

Summarize what is already known in 3-6 bullets before interviewing if the project is non-trivial.

### 2. Interview

Gather the missing decisions in small rounds. Prioritize these topics:

- Project identity: name, purpose, target users, and what the project is not.
- Scope: core capabilities, boundaries, expected inputs/outputs, and non-goals.
- Architecture: major folders/modules, ownership boundaries, data flow, dependencies, and extension points.
- Development workflow: setup, run, test, lint, build, release, and validation commands.
- Coding/content conventions: style, naming, comments, language, documentation expectations, and review standards.
- Agent rules: what agents may edit, what they must ask before doing, preferred tools, verification, and commit behavior.
- Design principles: product/design philosophy, UX tone, accessibility, performance, security, privacy, and maintainability.
- Tooling: package managers, frameworks, CLIs, MCP/connectors, scripts, external services, and required credentials.

Use progressive questioning. Start broad, then refine:

```text
To make AGENTS.md and README.md specific enough to guide future work, I need three decisions first:
1. What problem does this project solve, and who is it for?
2. Which hard rules should future agents follow in this repository?
3. Which confirmed stack, commands, or tools must be documented?
```

If the user wants speed, offer a quick mode: ask only for purpose, hard rules, commands, and architecture; mark unresolved details as TODOs only when the user approves.

### 3. Synthesize

Before editing files, produce a compact "project brief" for user confirmation when enough new information was gathered:

- Purpose
- Audience
- Scope and non-goals
- Architecture or repository layout
- Development commands
- Agent constraints
- Documentation tone and language

For small updates, summarize the intended file changes instead of producing a full brief.

### 4. Draft AGENTS.md

Make `AGENTS.md` a practical operating guide for agents. Prefer this shape:

```markdown
# Agent Guide

## Project Overview

## Repository Structure

## Development Workflow

## Coding and Content Standards

## Architecture and Design Principles

## Tools and Integrations

## Validation

## Commits
```

Include only sections that have real content. Keep instructions concrete:

- Use imperative rules: "Run...", "Prefer...", "Ask before...".
- Name exact commands when known.
- Distinguish required checks from optional checks.
- State commit conventions and whether agents should commit automatically.
- Include safety boundaries for destructive actions, generated files, credentials, and external services.

### 5. Draft README.md

Make `README.md` useful for humans discovering or using the project. Prefer this shape:

```markdown
# Project Name

## Overview

## Features

## Repository Structure

## Getting Started

## Usage

## Development

## Contributing

## License
```

Include only sections that the project can support. Keep README factual, approachable, and less agent-specific than `AGENTS.md`.

### 6. Edit and Verify

Before editing, state which files will change. After editing:

- Review the diff.
- Run available lightweight validation when appropriate, such as markdown linting, formatting, or project-specific checks.
- If no validation command exists, at least inspect rendered-sensitive Markdown structure manually.
- Report unresolved assumptions or TODOs clearly.
- Commit changes when the repository's instructions require it and validation has passed or been explicitly skipped.

## Output Quality

Good project docs should answer:

- Why does this project exist?
- What is inside and how is it organized?
- How does someone work on it safely?
- What constraints should future agents obey?
- Which choices are intentional, and which are still undecided?

Avoid generic filler such as "write clean code" unless the project defines what that means. Prefer specific, enforceable rules and concise explanations.
