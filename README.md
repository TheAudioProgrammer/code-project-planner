# TAP Code Project Planner

**Plan what you're building before you build it.**

An AI skill that interviews you about your audio plugin project — what it should do, what it shouldn't, and the specific details that matter — then generates a focused PRD (Product Requirements Document) and optional AGENTS.md that AI coding tools can follow precisely.

The difference between "build me a delay plugin" and a clean 200-line implementation vs. a bloated 2,000-line one? Usually a 20-minute conversation upfront.

Watch how it works here: https://youtu.be/ky9dfycg1J8

---

## What It Produces

**PRD** (always) — A short, structured document that defines the goal, features with exact parameters, key behaviours, target formats and platforms, and what's explicitly out of scope. Designed for AI coding tools to consume, not to align a product team.

**AGENTS.md** (new projects, optional) — A settings file that tells AI coding tools your tech stack, architecture preferences, real-time constraints, code style, and project constraints. Think of it as onboarding a new team member before they write their first line of code.

## How It Works

The skill runs a guided interview in a strict sequence:

1. **Orient** — Calibrates to your experience level (beginner or experienced)
2. **New or existing?** — Determines whether to generate an AGENTS.md
3. **Plugin type** — Identifies whether you're building an effect, instrument, utility, MIDI tool, or standalone audio application
4. **Core features** — Captures what the plugin does with specific names, types, ranges, defaults, units, and safety constraints
5. **The quirky question** — Asks what's unusual about *your* version of this plugin (the features that standard questions miss)
6. **Confirmation gate** — Ensures nothing is missing before moving on
7. **Out of scope** — Defines what the project should not do, preventing AI tools from over-building
8. **Technology choices** — Framework, SDK, language, format, and platform decisions, presented as trade-offs rather than rankings
9. **Generate** — Outputs the PRD (and optionally AGENTS.md)
10. **Handoff** — Explains how to use the documents with an AI coding tool

## Domain Support

The skill includes a specialized interview template for **audio plugin development** — covering plugin types, parameter design, format/platform decisions, real-time constraints, and a two-layer technology choice (framework vs. core SDK) that presents the full landscape without bias toward any single tool.

The interview covers effects, instruments, utilities, MIDI tools, and standalone audio applications. The architecture is extensible — new references can be added to the `references/` folder without modifying the core skill.

## Examples Included

The skill ships with an annotated example showing the output for a simple digital delay plugin.

It explains why each section works — not just what it looks like. For the skill's self-contained usage notes and resource map, see [its own README](audio-plugin-project-planner/README.md).

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

- "Help me plan an audio plugin"
- "I want to build a delay plugin"
- "Write a spec for this VST"
- "Let's make a CLAP synth"
- "Plan this AU effect"
- "I have an idea for a DAW utility"

It also triggers when you mention building a specific audio software type — plugin, effect, instrument, synth, VST, AU, CLAP, AAX, MIDI tool, or DAW utility — even without the word "plan."

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
