# Audio Plugin Skills

Reusable Agent Skills for planning and building audio-plugin projects.

## Included skills

| Skill | Purpose |
|---|---|
| [`audio-plugin-project-planner`](audio-plugin-project-planner/) | Interview an idea for an audio plugin and produce a focused `PRD.md`, plus an optional project `AGENTS.md`. |

## Use with Codex

Install or copy `audio-plugin-project-planner/` into a directory your Agent Skills-compatible tool discovers. In Codex, a personal skill normally lives under `~/.codex/skills/audio-plugin-project-planner/`; a repository can also carry skills in its local agent-skill configuration.

## Attribution

`audio-plugin-project-planner` is derived from [The Audio Programmer's Code Project Planner](https://github.com/TheAudioProgrammer/claude-audio-plugin-project-planner-skill), which declares the MIT license. This fork preserves the upstream history and adapts the original audio-plugin interview flow for Agent Skills/Codex, replacing Claude-specific output and handoff instructions with `PRD.md` and optional `AGENTS.md` guidance.
