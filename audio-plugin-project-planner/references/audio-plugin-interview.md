# Audio-plugin interview guide

## Product questions first

Establish the plugin category before selecting technology:

- Effect: time-based, dynamics, frequency, distortion, modulation, or spatial.
- Instrument/synth: voice model, MIDI input, polyphony, envelopes, and modulation.
- Utility: measurement, routing, conversion, analysis, or accessibility needs.
- MIDI effect: input transformation, generation, timing, and host interaction.

For every control, capture its range, default, unit, taper, automation support, and non-negotiable safety limit. Confirm all proposed defaults at once.

Clarify:

- Input/output layout: mono, stereo, multichannel, MIDI, sidechain, or standalone.
- State: parameter recall, preset needs, migration expectations, and A/B behavior.
- Audio behavior: bypass, latency, oversampling, smoothing, tempo sync, and failure modes.
- UI: default controls or custom graphics; meter types; resizability; keyboard/accessibility needs.
- Release scope: plugin formats, operating systems, target DAWs, signing/notarization, and commercial or learning intent.

## Scope-control prompts

Offer only relevant possibilities when defining the first version's boundary:

- tempo sync or host transport;
- modulation/LFOs;
- preset browser or factory content;
- custom graphics or OpenGL rendering;
- sidechain input;
- oversampling;
- multi-band or multichannel processing;
- A/B comparison and undo/redo;
- MIDI learn;
- extra output configurations.

## Technology decision: two layers

Make this decision after requirements are known.

### Layer 1: framework or direct SDK?

Explain the trade-off without ranking it:

| Approach | Strengths | Costs |
|---|---|---|
| Framework | Faster development, cross-format packaging, UI tools, broader abstractions | Framework constraints, licenses vary, less direct format knowledge |
| Direct SDK | Maximum format control and deeper learning | More host boilerplate, narrower format coverage, more maintenance |

### Layer 2: choose within the branch

For frameworks, describe the current candidate set and verify any time-sensitive details (supported formats and licensing) before recommending one:

- JUCE (C++): broad commercial ecosystem and formats; license terms matter.
- iPlug2 (C++): open-source cross-platform framework with graphics support.
- nih-plug (Rust): Rust-first ecosystem with a narrower but growing format set.
- FAUST: DSP language that compiles to several back ends; well suited to DSP-led work.
- DPF: lightweight open-source C++ framework, especially relevant to Linux/open-source targets.
- Cabbage/Csound: sound-design-oriented path with a lower programming barrier.

For direct SDKs, choose based on the required format and host reach: VST3, Audio Unit, CLAP, AAX, or LV2. Verify the latest licensing, SDK terms, and platform support before relying on them.

Questions that help make the choice:

- Which language is preferred or worth learning?
- Is the goal learning, personal use, open source, or commercial distribution?
- Which DAWs, operating systems, and formats are mandatory?
- Is DSP depth, custom UI, or shipping speed the priority?

If the user remains undecided, make a narrowly justified recommendation and label its assumptions.
