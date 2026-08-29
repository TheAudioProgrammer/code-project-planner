# TAP Audio Plugin Project Planner

**Plan the audio plugin before building it.**

An Agent Skill that interviews you about an audio-plugin project — what it should do, what it should not do, and the technical details that matter — then produces a focused Product Requirements Document (PRD) for an AI coding agent to follow.

The difference between “build me a delay plugin” and a clean, focused implementation versus a bloated one is often a short planning conversation up front.

Watch the original project demonstration: https://youtu.be/ky9dfycg1J8

---

## What It Produces

**PRD.md** (always) — A short, structured document defining the goal, controls and exact parameter values, plugin behaviour, target formats/platforms, and explicitly deferred features.

**AGENTS.md** (new projects, optional) — Project guidance for an AI coding agent: the selected stack, architecture boundaries, real-time audio constraints, and project-specific rules.

Both documents are designed to be concise, specific, and directly useful during implementation.

## How It Works

The skill follows a guided interview:

1. **New or existing?** — Distinguishes a new plugin from a feature in an existing codebase.
2. **Plugin type** — Establishes whether this is an effect, instrument, utility, MIDI effect, or standalone audio application.
3. **Core controls and features** — Captures precise ranges, defaults, units, automation expectations, and DSP safety constraints.
4. **The unusual question** — Asks what is distinctive about this particular plugin.
5. **Confirmation and scope boundary** — Confirms the feature set and records what is explicitly out of scope.
6. **Formats and technology** — Captures target hosts and platforms, then presents framework-versus-SDK trade-offs only after the product is clear.
7. **Generate and hand off** — Produces `PRD.md` and, for new projects, optionally `AGENTS.md`.

The technology guide covers the two layers that are easy to conflate in audio development: choosing between a framework and a direct SDK, then choosing the appropriate option within that path. It presents trade-offs rather than ranking tools.

## Audio Plugin Support

The interview is specialized for effects, instruments, utilities, and MIDI plugins. It covers parameter design, audio-thread constraints, channel layout, state recall, UI scope, plugin formats, target operating systems, and DAW requirements.

It also helps define common first-version exclusions such as tempo sync, modulation, preset browsers, custom graphics, sidechain inputs, oversampling, multi-band processing, or MIDI learn.

## Example Included

The repository includes a [simple digital delay PRD](audio-plugin-project-planner/examples/delay-plugin-prd.md). It demonstrates how exact parameter ranges, defaults, DSP safety limits, and scope boundaries make an implementation request unambiguous.

For the skill's self-contained usage notes and resource map, see [its own README](audio-plugin-project-planner/README.md).

---

## Install

This repository uses the standard Agent Skills directory layout. The skill is located at `audio-plugin-project-planner/` and can be used by Agent Skills-compatible tools.

### Codex

Copy the skill directory into your personal skills directory:

```bash
git clone https://github.com/TheAudioProgrammer/claude-audio-plugin-project-planner-skill.git
cp -r claude-audio-plugin-project-planner-skill/audio-plugin-project-planner ~/.codex/skills/
```

### Claude Code

Copy the same directory into Claude Code's skills directory:

```bash
git clone https://github.com/TheAudioProgrammer/claude-audio-plugin-project-planner-skill.git
cp -r claude-audio-plugin-project-planner-skill/audio-plugin-project-planner ~/.claude/skills/
```

### Project-level use

Commit the skill folder to the repository where it should be shared, using the local Agent Skills configuration supported by your coding tool. The folder itself is portable:

```text
your-project/
└── audio-plugin-project-planner/
    ├── SKILL.md
    ├── references/
    └── examples/
```

## Trigger Phrases

The skill applies to requests such as:

- “Help me plan an audio plugin.”
- “I want to build a delay plugin.”
- “Write a spec for this VST.”
- “Scope a CLAP synth.”
- “Plan this AU effect.”
- “I have an idea for a DAW utility.”

## Skill Structure

```text
audio-plugin-project-planner/
├── README.md
├── SKILL.md
├── references/
│   ├── agent-project-guidance.md
│   └── audio-plugin-interview.md
└── examples/
    └── delay-plugin-prd.md
```

## Compatibility

The skill uses the [Agent Skills open standard](https://github.com/anthropics/agent-skills). It is designed for Codex, Claude Code, and other tools that discover `SKILL.md`-based skills.

## License

MIT

Built by [The Audio Programmer](https://theaudioprogrammer.com)
