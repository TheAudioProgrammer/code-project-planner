# TAP Code Project Planner

**Plan what you're building before you build it.**

An AI skill that interviews you about your software project — what it should do, what it shouldn't, and the specific details that matter — then generates a focused PRD (Product Requirements Document) and optional CLAUDE.md that AI coding tools can follow precisely.

The difference between "build me a delay plugin" and a clean 200-line implementation vs. a bloated 2,000-line one? Usually a 20-minute conversation upfront.

Watch how it works here: https://youtu.be/ky9dfycg1J8

---

## What It Produces

**PRD** (always) — A short, structured document that defines the goal, features with exact parameters, key behaviours, and what's explicitly out of scope. Designed for AI coding tools to consume, not to align a product team.

**CLAUDE.md** (new projects, optional) — A settings file that tells Claude Code your tech stack, architecture preferences, code style, and constraints. Think of it as onboarding a new team member before they write their first line of code.

## How It Works

The skill runs a guided interview in a strict sequence:

1. **Orient** — Calibrates to your experience level (beginner or experienced)
2. **New or existing?** — Determines whether to generate a CLAUDE.md
3. **Domain detection** — Loads specialized interview guides for known domains (e.g., audio plugins)
4. **Core features** — Captures what the project does with specific names, types, ranges, defaults, and units
5. **The quirky question** — Asks what's unusual about *your* version of this project (the features that standard questions miss)
6. **Confirmation gate** — Ensures nothing is missing before moving on
7. **Out of scope** — Defines what the project should *not* do, preventing AI tools from over-building
8. **Technology choices** — Framework and language decisions, presented as trade-offs rather than rankings
9. **Generate** — Outputs the PRD (and optionally CLAUDE.md)
10. **Handoff** — Step-by-step instructions for using the documents with Claude Code

## Domain Support

The skill includes a specialized interview template for **audio plugin development** — covering plugin types, parameter design, format/platform decisions, and a two-layer technology choice (framework vs. core SDK) that presents the full landscape without bias toward any single tool.

For all other project types, the general interview flow handles web apps, CLI tools, APIs, mobile apps, and anything else. The architecture is extensible — new domain references can be added to the `references/` folder without modifying the core skill.

## Examples Included

The skill ships with two annotated examples showing the interview flow, the output, and "good vs. bad" comparisons:

- **Task management web app** — Full greenfield flow (PRD + CLAUDE.md) using Next.js/TypeScript
- **Simple digital delay plugin** — Single-feature PRD for an audio effect

Both examples explain *why* each section works — not just what it looks like.

---

## Install

### Claude.ai (web or desktop)

1. Download the latest `.skill` file from [Releases](../../releases)
2. In Claude, go to **Settings > Customize > Skills**
3. Upload the `.skill` file
4. The skill appears in your Skills list — toggle it on

### Claude Code (terminal)

Copy the skill folder into your personal skills directory:

```bash
# Clone this repo
git clone https://github.com/TheAudioProgrammer/code-project-planner.git

# Copy to Claude Code skills directory
cp -r code-project-planner ~/.claude/skills/code-project-planner
```

### Project-level (shared with teammates)

Commit the skill folder to your repo:

```
your-project/
├── .claude/
│   └── skills/
│       └── code-project-planner/
│           ├── SKILL.md
│           ├── references/
│           └── examples/
```

Anyone who clones the repo gets the skill automatically.

---

## Trigger Phrases

The skill activates when you say things like:

- "Help me plan a new project"
- "I want to build a delay plugin"
- "Let's make a CLI tool for..."
- "Write a spec for this feature"
- "Create a CLAUDE.md"
- "I have an idea for an app"

It also triggers when you mention building a specific software type — plugin, app, tool, extension, CLI, library, API, bot, or service — even without the word "plan."

---

## Skill Structure

```
code-project-planner/
├── SKILL.md                                    # Core interview workflow
├── references/
│   ├── audio-plugins-interview-template.md     # Audio plugin domain guide
│   ├── claude-md-principles-general.md         # Universal coding principles
│   └── claude-md-template-juce.md              # JUCE/C++ project template
└── examples/
    ├── prd-example-webapp.md                   # Task app (PRD + CLAUDE.md)
    └── prd-example-plugin.md                   # Delay plugin (PRD only)
```

## Extending with New Domains

To add support for a new domain (e.g., web apps, mobile, CLI tools):

1. Create a new file in `references/` following the pattern of `audio-plugins-interview-template.md`
2. Include: why this domain needs special handling, domain-specific interview questions (product first, technology second), the technology landscape with trade-offs, and common out-of-scope items
3. Add a routing line to Step 3 in `SKILL.md`

The audio plugin template is roughly 130 lines — that's a good target for new domains.

---

## Compatibility

This skill follows the [Agent Skills open standard](https://github.com/anthropics/agent-skills) and works with:

- **Claude.ai** (web, desktop, mobile)
- **Claude Code** (terminal)
- **OpenAI Codex CLI** (uses the same SKILL.md format)
- Any AI tool that supports the Agent Skills specification

---

## License

MIT

---

Built by [The Audio Programmer](https://theaudioprogrammer.com)
