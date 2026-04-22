# Claude Code Power Setup

> A fully loaded Claude Code configuration featuring workflow automation skills, design intelligence plugins, and productivity tools — ready to clone and use across all your projects.

---

## Table of Contents

- [Overview](#overview)
- [Quick Install](#quick-install)
- [Marketplace Plugins](#marketplace-plugins)
  - [Superpowers](#-superpowers)
  - [Context7](#-context7)
  - [Caveman](#-caveman)
  - [UI/UX Pro Max](#-uiux-pro-max)
  - [Impeccable](#-impeccable)
- [MCP Servers](#mcp-servers)
- [Skills Reference](#skills-reference)
  - [Workflow Skills](#workflow-skills)
  - [Development Skills](#development-skills)
  - [Configuration Skills](#configuration-skills)
- [Manual Installation](#manual-installation)
- [File Structure](#file-structure)

---

## Overview

This setup extends Claude Code with:

| Category | Count | What it adds |
|---|---|---|
| Marketplace Plugins | 5 | Workflow, design, docs, and token efficiency |
| MCP Servers | 4 | Canva, Google Drive, Gmail, Google Calendar |
| Skills (Superpowers) | 14 | Structured dev workflows |
| Built-in Skills | 10 | Config, reviews, scheduling, and more |

---

## Quick Install

Clone this config into your Claude user directory:

```bash
# Backup your existing settings first
cp ~/.claude/settings.json ~/.claude/settings.json.bak

# Copy settings.json from this repo to your Claude directory
cp settings.json ~/.claude/settings.json
```

Then open Claude Code and run:

```
/plugins
```

Claude Code will automatically download and install all registered marketplace plugins on first launch.

---

## Marketplace Plugins

### 🦴 Superpowers

**Source:** [`obra/superpowers-marketplace`](https://github.com/obra/superpowers-marketplace)  
**Plugin ID:** `superpowers@claude-plugins-official`

The backbone of this setup. Superpowers is a collection of structured workflow skills that enforce professional software development discipline inside Claude Code. It installs 14 skills covering the full development lifecycle.

**Skills included:** See [Skills Reference → Workflow Skills](#workflow-skills) below.

**How it works:** Every time you start a session, the `using-superpowers` skill activates automatically and checks which skill should guide your current task before Claude responds to anything.

---

### 📚 Context7

**Source:** [`anthropics/claude-plugins-official`](https://github.com/anthropics/claude-plugins-official)  
**Plugin ID:** `context7@claude-plugins-official`

Fetches live, up-to-date documentation for any library, framework, SDK, or CLI tool directly into Claude's context.

**Use when you ask about:**
- React, Next.js, Tailwind, Prisma, Express, Django, Spring Boot
- Any API syntax, configuration options, or version migrations
- Library-specific debugging or setup instructions

**Tools exposed:**
| Tool | Purpose |
|---|---|
| `resolve-library-id` | Look up the correct library ID by name |
| `query-docs` | Fetch current documentation for that library |

**Example usage:**
```
Tell me how to use useOptimistic in React 19
```
Context7 will fetch the latest React 19 docs before answering — no stale training data.

---

### 🪨 Caveman

**Source:** [`JuliusBrussee/caveman`](https://github.com/JuliusBrussee/caveman)  
**Plugin ID:** `caveman@caveman`

Switches Claude into an ultra-compressed communication mode that cuts approximately 75% of output tokens while preserving full technical accuracy. Ideal for long coding sessions where you're burning through context fast.

**How to activate:**
```
/caveman
```

**What changes:**
- Responses become terse, direct, and stripped of filler
- Code stays complete and correct
- No markdown fluff, no explanations unless asked
- Full technical precision maintained

**When to use:** Long refactoring sessions, large codebases, when you want answers not essays.

---

### 🎨 UI/UX Pro Max

**Source:** [`nextlevelbuilder/ui-ux-pro-max-skill`](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)  
**Plugin ID:** `ui-ux-pro-max@ui-ux-pro-max-skill`  
**Version:** 2.2.1

A comprehensive design intelligence skill containing curated databases of styles, colors, typography, charts, and UX guidelines.

**What's included:**

| Database | Count |
|---|---|
| Design styles | 67 |
| Color palettes | 96 |
| Font pairings | 57 |
| Chart types | 25 |
| Stack guidelines | 13 |

**Supported frameworks:**
React · Next.js · Astro · Vue · Nuxt.js · Nuxt UI · Svelte · SwiftUI · React Native · Flutter · Tailwind CSS · shadcn/ui · Jetpack Compose

**How to activate:**
```
/ui-ux-pro-max
```

**Example usage:**
```
Design a dark mode dashboard using shadcn/ui with a cyberpunk aesthetic
```
The skill selects appropriate palettes, typography, and component patterns from its curated database.

---

### ✨ Impeccable

**Source:** [`pbakaus/impeccable`](https://github.com/pbakaus/impeccable)  
**Plugin ID:** `impeccable@impeccable`  
**Version:** 2.1.1  
**Homepage:** [impeccable.style](https://impeccable.style)

Design vocabulary and frontend fluency for AI-assisted development. Includes 18 specialized slash commands and a skill with curated anti-patterns to avoid.

**Available commands:**

| Command | Purpose |
|---|---|
| `/polish` | Refine UI details and visual consistency |
| `/distill` | Simplify overcomplicated designs |
| `/audit` | Review design for issues and anti-patterns |
| `/typeset` | Improve typography hierarchy and spacing |
| `/overdrive` | Push design to its maximum potential |
| `/impeccable` | Run the full design intelligence skill |
| + 12 more | Cover layout, motion, accessibility, and more |

**When to use:** Any frontend project where visual quality matters — landing pages, dashboards, component libraries, design systems.

---

## MCP Servers

MCP (Model Context Protocol) servers extend Claude Code with tools that connect to external services.

### Canva

Integrates Claude Code directly with the Canva design platform.

**Capabilities:**
- Create, edit, export, and comment on designs
- Browse and apply brand kits
- Manage folders and design assets
- Generate designs from structured prompts
- Resize, merge, and iterate on designs

**Tools:** 30+ tools covering the full Canva editing workflow.

---

### Google Drive

Connect Claude Code to your Google Drive files.

**Capabilities:**
- Authenticate and browse Drive files
- Read file contents for context
- Use documents as input for code generation or analysis

---

### Gmail

Connect Claude Code to your Gmail inbox.

**Capabilities:**
- Read and analyze emails
- Draft replies and compose messages
- Process email data for automation tasks

> **Note:** Requires authentication on first use via `/gmail authenticate`

---

### Google Calendar

Connect Claude Code to your Google Calendar.

**Capabilities:**
- Read and query calendar events
- Schedule and manage meetings
- Use calendar context for planning tasks

> **Note:** Requires authentication on first use via `/google-calendar authenticate`

---

## Skills Reference

Skills are invoked with `/skill-name` or automatically when Claude detects they apply.

### Workflow Skills

These come from the **Superpowers** plugin and enforce structured development discipline.

---

#### `superpowers:brainstorming`

**Trigger:** Before any creative work — new features, components, functionality changes.

Explores user intent, requirements, and design space before writing a single line of code. Prevents premature implementation of the wrong thing.

**When Claude uses it:** Anytime you say "build X", "add Y", "create Z".

---

#### `superpowers:writing-plans`

**Trigger:** When you have a spec or multi-step requirements.

Produces a structured implementation plan with steps, files to change, and architectural decisions — before touching code.

---

#### `superpowers:executing-plans`

**Trigger:** When executing a written plan in a separate session.

Runs through a plan step by step with review checkpoints, ensuring nothing is skipped.

---

#### `superpowers:test-driven-development`

**Trigger:** Before writing any implementation code.

Enforces the TDD red-green-refactor cycle: write failing tests first, then make them pass.

---

#### `superpowers:systematic-debugging`

**Trigger:** When encountering any bug, test failure, or unexpected behavior.

Prevents jumping to fixes before understanding root causes. Structured diagnosis: reproduce → isolate → hypothesize → verify → fix.

---

#### `superpowers:verification-before-completion`

**Trigger:** Before claiming any work is done, fixed, or passing.

Requires running actual verification commands and confirming output before making any success claims. Evidence before assertions.

---

#### `superpowers:requesting-code-review`

**Trigger:** After completing tasks or implementing major features.

Prepares a structured code review request before merging.

---

#### `superpowers:receiving-code-review`

**Trigger:** When receiving code review feedback.

Processes feedback with technical rigor — not performative agreement. Verifies suggestions before blindly implementing them.

---

#### `superpowers:finishing-a-development-branch`

**Trigger:** When implementation is complete and all tests pass.

Guides the decision of how to integrate work: merge, PR, or cleanup. Structured options, not guesswork.

---

#### `superpowers:dispatching-parallel-agents`

**Trigger:** When facing 2+ independent tasks.

Spawns multiple subagents to work on independent tasks simultaneously, reducing total wall-clock time.

---

#### `superpowers:subagent-driven-development`

**Trigger:** When executing plans with independent tasks in the current session.

Uses subagents within the current conversation to parallelize implementation work.

---

#### `superpowers:using-git-worktrees`

**Trigger:** Before starting feature work that needs isolation.

Creates isolated git worktrees with smart directory selection and safety checks, so feature work doesn't pollute the main workspace.

---

#### `superpowers:writing-skills`

**Trigger:** When creating or editing skills.

Structured process for authoring new Claude Code skills with correct format and validation.

---

#### `superpowers:using-superpowers`

**Trigger:** Automatically at session start.

Bootstraps the skills system — teaches Claude which skills exist and enforces that the right skill is invoked before any response. This skill runs silently in the background.

---

### Development Skills

Built-in Claude Code skills for common development tasks.

---

#### `claude-api`

Guides building, debugging, and optimizing apps that use the Claude API / Anthropic SDK.

**Auto-triggers when:**
- Code imports `anthropic` or `@anthropic-ai/sdk`
- You ask about Claude API features (caching, thinking, tool use, batch, files)
- You're migrating between Claude model versions

**Example:**
```
Add prompt caching to my Anthropic SDK app
```

---

#### `init`

Initializes a new `CLAUDE.md` file with codebase documentation for a project.

**Usage:**
```
/init
```

Scans your codebase and generates a `CLAUDE.md` with architecture, conventions, and project-specific guidance for Claude.

---

#### `review`

Reviews a pull request systematically.

**Usage:**
```
/review
```

---

#### `security-review`

Performs a security review of pending changes on the current branch, checking for OWASP Top 10 vulnerabilities and other common issues.

**Usage:**
```
/security-review
```

---

#### `simplify`

Reviews recently changed code for reuse opportunities, quality issues, and efficiency improvements, then fixes what it finds.

**Usage:**
```
/simplify
```

---

### Configuration Skills

Skills for managing Claude Code's own settings and behavior.

---

#### `update-config`

Modifies `settings.json` files — adds hooks, permissions, environment variables, MCP server config, and plugins.

**Use for:**
- Adding hooks (`PostToolUse`, `PreToolUse`, etc.)
- Setting permissions (`allow`, `deny`, `ask` arrays)
- Configuring environment variables
- Any automated behaviors ("run prettier after every file write")

**Usage:**
```
After writing files, auto-format with prettier
```
```
Allow all npm commands without prompting
```

---

#### `keybindings-help`

Customizes keyboard shortcuts and key bindings in `~/.claude/keybindings.json`.

**Usage:**
```
/keybindings-help
```
```
Rebind ctrl+s to submit
```

---

#### `fewer-permission-prompts`

Scans your session transcripts for common read-only Bash and MCP tool calls, then builds a prioritized allowlist to reduce how often Claude asks for permission.

**Usage:**
```
/fewer-permission-prompts
```

---

#### `loop`

Runs a prompt or slash command on a recurring interval.

**Usage:**
```
/loop 5m /security-review
/loop 30s check if the build is passing
```

---

#### `schedule`

Creates, updates, lists, or runs scheduled remote agents on a cron schedule or at a specific time.

**Usage:**
```
/schedule
Run the test suite every day at 9am
Run this once tomorrow at 3pm
```

---

## Manual Installation

If you prefer to install individual plugins instead of copying the full `settings.json`:

### Step 1 — Open your global settings

```bash
# Edit the file directly
nano ~/.claude/settings.json
# or on Windows:
notepad %USERPROFILE%\.claude\settings.json
```

### Step 2 — Register the marketplaces

Add to `extraKnownMarketplaces`:

```json
{
  "extraKnownMarketplaces": {
    "claude-plugins-official": {
      "source": { "source": "github", "repo": "anthropics/claude-plugins-official" }
    },
    "superpowers-marketplace": {
      "source": { "source": "github", "repo": "obra/superpowers-marketplace" }
    },
    "caveman": {
      "source": { "source": "github", "repo": "JuliusBrussee/caveman" }
    },
    "ui-ux-pro-max-skill": {
      "source": { "source": "github", "repo": "nextlevelbuilder/ui-ux-pro-max-skill" }
    },
    "impeccable": {
      "source": { "source": "github", "repo": "pbakaus/impeccable" }
    }
  }
}
```

### Step 3 — Enable the plugins

Add to `enabledPlugins`:

```json
{
  "enabledPlugins": {
    "context7@claude-plugins-official": true,
    "superpowers@claude-plugins-official": true,
    "caveman@caveman": true,
    "ui-ux-pro-max@ui-ux-pro-max-skill": true,
    "impeccable@impeccable": true
  }
}
```

### Step 4 — Reload

Open Claude Code and run `/plugins` to trigger the install, or restart the app.

---

## File Structure

```
~/.claude/
├── settings.json          # Global config — plugins, permissions, hooks, env vars
├── keybindings.json       # Custom keyboard shortcuts
├── README.md              # This file
└── projects/
    └── <project>/
        └── memory/        # Per-project auto-memory files
```

Project-level overrides go in `.claude/settings.json` inside each repo (committed) or `.claude/settings.local.json` (gitignored, personal).

---

## Requirements

- [Claude Code](https://claude.ai/code) — CLI, desktop app, or IDE extension
- Git (for marketplace plugin downloads)
- A Claude Pro, Max, or API account

---

## License

Config files are public domain. Individual plugins are subject to their own licenses — see each plugin's repository.
