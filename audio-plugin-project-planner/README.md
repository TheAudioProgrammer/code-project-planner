# Audio Plugin Project Planner

Plan an audio-plugin project before implementation. This skill turns an idea for an effect, instrument, utility, MIDI plugin, or standalone audio application into a focused `PRD.md` and, for a new project, can also produce an `AGENTS.md` with implementation constraints.

## When to use it

Use the skill when planning or scoping a VST, AU, CLAP, AAX, LV2, effect, synth, MIDI processor, or DAW utility. Typical requests include:

- “Help me plan a delay plugin.”
- “Write a spec for this VST.”
- “Scope a CLAP synthesizer.”
- “What should be in version one of this audio effect?”

## What it does

The interview records exact parameters, defaults, units, safety limits, audio and UI behaviour, formats, operating systems, and DAW constraints. It then explicitly defines features that should wait for a later version.

Only after the product scope is clear does it guide the framework-versus-direct-SDK decision. The resulting `PRD.md` describes *what* to build; the optional `AGENTS.md` captures *how* the coding agent should respect the selected stack and real-time constraints.

## Resources

- [`SKILL.md`](SKILL.md) contains the workflow and output templates.
- [`references/audio-plugin-interview.md`](references/audio-plugin-interview.md) contains domain questions, scope prompts, and technology trade-offs.
- [`references/agent-project-guidance.md`](references/agent-project-guidance.md) provides reusable guidance for generated `AGENTS.md` files.
- [`examples/delay-plugin-prd.md`](examples/delay-plugin-prd.md) is a compact example of the expected PRD.
