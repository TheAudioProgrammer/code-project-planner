# PRD: Simple Digital Delay Plugin

## Goal

Build a straightforward stereo digital delay that gives musicians a usable echo on any audio source with three controls.

## Formats and platforms

- Formats: [NEED: confirm VST3, AU, CLAP, or other]
- Operating systems: [NEED: confirm]

## Features

| Parameter or feature | Type/range | Default | Unit | Notes |
|---|---|---:|---|---|
| Delay time | 1–2000 | 500 | ms | Smooth changes to avoid clicks |
| Feedback | 0–95 | 30 | % | Enforce the 95% cap in DSP |
| Mix | 0–100 | 50 | % | Dry/wet blend |

## Behaviour

- Process stereo input to stereo output; use the same settings independently for left and right channels.
- Use a circular delay buffer.
- Pass audio through unchanged when bypassed.
- Restore all parameter values when a host session is reopened.

## UI and interaction

- Provide the three parameters with the framework's standard controls for V1.

## Out of scope

- Tempo sync.
- Modulation or chorus.
- Ping-pong or multi-tap delays.
- Preset browser.
- Custom UI graphics.
