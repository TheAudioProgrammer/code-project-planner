# Guidance for generated `AGENTS.md`

Use only sections relevant to the project. Do not turn preferences into requirements that conflict with the user or existing codebase.

## General engineering principles

- Keep each function and type responsible for one clear concern.
- Prefer composition to deep inheritance.
- Use descriptive names; comments explain non-obvious reasons rather than restating code.
- Validate inputs at boundaries and surface failures clearly.
- Keep the implementation aligned with the accepted PRD; request approval before adding unrelated features or dependencies.

## Real-time audio constraints

- Do not allocate memory, acquire locks, perform I/O, log synchronously, or block from the audio callback.
- Prepare buffers and DSP state before processing starts.
- Smooth audible parameter changes where needed.
- Make channel and latency behavior explicit and test state restoration.

## JUCE baseline

Use only when JUCE is selected. Adapt versions and formats to the project.

- Keep DSP in the processor and UI drawing in the editor; connect user parameters through `AudioProcessorValueTreeState`.
- Define the full parameter layout in one place and implement state save/restore.
- Prefer RAII and explicit `juce::` qualification.
- Keep `processBlock()` allocation-free and lock-free; use `prepareToPlay()` for preparation.
- Consider `juce::SmoothedValue` and `juce::dsp` before writing equivalent custom code.
