---
name: audio-plugin-project-planner
description: Plan an audio-plugin project or feature before implementation. Use when a user wants to build, scope, or write a specification for a VST, AU, CLAP, AAX, LV2, audio effect, instrument, synth, MIDI plugin, or DAW utility.
---

# Audio Plugin Project Planner

Turn an audio-plugin idea into a concise implementation-ready PRD. For a new project, optionally also create an `AGENTS.md` that records technical and coding constraints for the coding agent. Keep the PRD focused on what the plugin does; put implementation choices in `AGENTS.md`.

## Interview flow

Use this sequence, but combine related questions when the user has already supplied detail. Do not make the interview feel bureaucratic.

1. Establish whether this is a new plugin or an addition to an existing codebase. Inspect the codebase before asking questions it can answer.
2. Identify the plugin type: effect, instrument, utility, MIDI effect, or standalone audio application.
3. Read [the audio-plugin guide](references/audio-plugin-interview.md). Capture the audio and UI requirements before discussing technologies.
4. Build a complete list of user-facing parameters. For every parameter capture name, range, default, unit, automation behavior, and safety constraints. Propose all missing defaults in one table rather than one question per control.
5. Ask this as a dedicated question: “¿Hay algo inusual o peculiar que quieras que haga —algo que probablemente no se me ocurriría preguntar?”
6. Confirm that the feature set is complete. If something new appears, return to parameters and behavior.
7. Define explicit out-of-scope items. Offer only the most relevant options from the guide if the user needs help.
8. Determine formats, target OSes, DAWs, and distribution intent. Only then discuss framework versus direct SDK; use the two-layer decision in the guide.
9. Generate the PRD. For a new project, offer an `AGENTS.md` after the PRD has been accepted.

Do not guess requirements. Mark unresolved details as `[NEED: confirm …]`. Keep guidance neutral: explain trade-offs instead of treating one framework as the universal default.

## PRD output

Save or present the result as `PRD.md` unless the user requests a different location or name.

```markdown
# PRD: [Plugin name]

## Goal
[One or two sentences: who it is for, what it does, and the usable outcome.]

## Formats and platforms
- Formats: [VST3, AU, CLAP, etc.]
- Operating systems: [macOS, Windows, Linux]
- Host/DAW constraints: [if relevant]

## Features
| Parameter or feature | Type/range | Default | Unit | Notes |
|---|---|---|---|---|

## Behaviour
- [One independently testable behavior per bullet.]

## UI and interaction
- [Layout, accessibility, resizability, metering, or intentional lack of UI.]

## Out of scope
- [Explicitly deferred feature.]
```

Target 25–50 lines. Split the work into multiple PRDs if that would make each one more coherent. State DSP invariants explicitly, such as feedback caps, channel handling, latency, bypass behavior, or preset/state recall.

## Optional `AGENTS.md` for a new project

Offer this only for a new project. Read [agent-project-guidance.md](references/agent-project-guidance.md), then use its general principles plus any relevant framework-specific section. Preserve the user's actual choices; do not silently impose JUCE, CMake, or a plugin format.

Keep `AGENTS.md` short and operational. It should contain:

```markdown
# [Project name]

## Purpose
[Brief description]

## Stack and targets
- Framework/SDK: [...]
- Language and build system: [...]
- Plugin formats and platforms: [...]

## Architecture
- [DSP/UI/state ownership and boundaries]

## Real-time constraints
- [No allocation, locks, I/O, or blocking work on the audio thread]

## Project constraints
- [PRD-bound scope, dependencies, testing or compatibility requirements]
```

## Handoff

Tell the user to put `PRD.md` in the target project. If `AGENTS.md` was generated, put it in the same project root. Then ask their coding agent to plan against `PRD.md`, review that plan, and implement only the accepted scope.

## References

- Read [audio-plugin-interview.md](references/audio-plugin-interview.md) for domain questions, technology trade-offs, and scope-control prompts.
- Read [agent-project-guidance.md](references/agent-project-guidance.md) only when producing an `AGENTS.md`.
- Read [delay-plugin-prd.md](examples/delay-plugin-prd.md) when an example would help clarify the desired result.
