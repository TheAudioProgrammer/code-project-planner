# TAP Code Project Planner

**Plan what you're building before you build it.**

An AI skill that interviews you about your software project — what it should do, what it shouldn't, and the specific details that matter — then generates a focused PRD (Product Requirements Document) and optional AGENTS.md that AI coding tools can follow precisely.

The difference between "build me a delay plugin" and a clean 200-line implementation vs. a bloated 2,000-line one? Usually a 20-minute conversation upfront.

Watch how it works here: https://youtu.be/ky9dfycg1J8

---

## What It Produces

**PRD** (always) — A short, structured document that defines the goal, features with exact parameters, key behaviours, and what's explicitly out of scope. Designed for AI coding tools to consume, not to align a product team.

**AGENTS.md** (new projects, optional) — A settings file that tells AI coding tools your tech stack, architecture preferences, code style, and constraints. Think of it as onboarding a new team member before they write their first line of code.

## How It Works

The skill runs a guided interview in a strict sequence:

1. **Orient** — Calibrates to your experience level (beginner or experienced)
2. **New or existing?** — Determines whether to generate an AGENTS.md
3. **Domain detection** — Loads specialized interview guides for known domains (e.g., audio plugins)
4. **Core features** — Captures what the project does with specific names, types, ranges, defaults, and units
5. **The quirky question** — Asks what's unusual about *your* version of this project (the features that standard questions miss)
6. **Confirmation gate** — Ensures nothing is missing before moving on
7. **Out of scope** — Defines what the project should *not* do, preventing AI tools from over-building
8. **Technology choices** — Framework and language decisions, presented as trade-offs rather than rankings
9. **Generate** — Outputs the PRD (and optionally AGENTS.md)
10. **Handoff** — Step-by-step instructions for using the documents with AI coding tools

## Domain Support

The skill includes a specialized interview template for **audio plugin development** — covering plugin types, parameter design, format/platform decisions, and a two-layer technology choice (framework vs. core SDK) that presents the full landscape without bias toward any single tool.

For all other project types, the general interview flow handles web apps, CLI tools, APIs, mobile apps, and anything else. The architecture is extensible — new domain references can be added to the `references/` folder without modifying the core skill.

## Examples Included

The skill ships with two annotated examples showing the interview flow, the output, and "good vs. bad" comparisons:

- **Task management web app** — Full greenfield flow (PRD + CLAUDE.md) using Next.js/TypeScript
- **Simple digital delay plugin** — Single-feature PRD for an audio effect

---

## Install

The repository uses the Agent Skills directory layout. Copy the `audio-plugin-project-planner` folder into the skills directory for your tool.

### Codex

Copy the skill folder into your personal skills directory:

```bash
# Clone this repo
git clone https://github.com/TheAudioProgrammer/claude-audio-plugin-project-planner-skill.git

# Copy to Codex skills directory
cp -r claude-audio-plugin-project-planner-skill/audio-plugin-project-planner ~/.codex/skills/audio-plugin-project-planner
```

### Claude Code

Copy the same skill folder into Claude Code's personal skills directory:

```bash
# Clone this repo
git clone https://github.com/TheAudioProgrammer/claude-audio-plugin-project-planner-skill.git

# Copy to Claude Code skills directory
cp -r claude-audio-plugin-project-planner-skill/audio-plugin-project-planner ~/.claude/skills/audio-plugin-project-planner
```

### Project-level (shared with teammates)

Commit the skill folder to your repo using the local Agent Skills location supported by your coding tool:

```text
your-project/
└── audio-plugin-project-planner/
    ├── SKILL.md
    ├── references/
    └── examples/
```

Anyone who clones the repo gets the skill automatically once their tool is configured to discover that location.

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

```text
audio-plugin-project-planner/
├── README.md                                    # Skill overview and resource map
├── SKILL.md                                     # Core interview workflow
├── references/
│   ├── agent-project-guidance.md                # General and JUCE project guidance
│   └── audio-plugin-interview.md                # Audio plugin domain guide
└── examples/
    └── delay-plugin-prd.md                      # Simple digital delay PRD
```

## Extending with New Domains

To add support for a new audio-related domain:

1. Create a new file in `references/` following the pattern of `audio-plugin-interview.md`
2. Include: why the domain needs special handling, domain-specific interview questions, technology trade-offs, and common out-of-scope items
3. Add a routing line to `SKILL.md`

---

## Compatibility

This skill follows the [Agent Skills open standard](https://github.com/anthropics/agent-skills) and works with:

- **Claude Code** (terminal)
- **OpenAI Codex** (uses the same SKILL.md format)
- Any AI tool that supports the Agent Skills specification

---

## License

MIT

---

Built by [The Audio Programmer](https://theaudioprogrammer.com)
