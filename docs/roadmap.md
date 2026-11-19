# Roadmap

Milestones describe proposed work, not completed features.

## M0 — Research baseline (documentation)
- [x] Record source-confirmed AHI multichannel interfaces and EMU10kx playback path.
- [x] Identify AmigaOS 4 OpenAL Soft AHI backend and its stereo-only limitation.
- [x] Define project boundaries, open questions and acceptance tests.
- [ ] Select target upstream OpenAL Soft release and document licensing/toolchain requirements.

## M1 — Build and port
- [ ] Build a minimal OpenAL Soft library for one AROS target.
- [ ] Adapt AHI backend away from AmigaOS 4-specific APIs.
- [ ] Confirm initialization, teardown and stereo PCM playback.
- [ ] Run a basic 3D moving-source example.

## M2 — Binaural spatial audio
- [ ] Enable and verify HRTF when supported by the selected build.
- [ ] Test front/back and elevation cues on headphones.
- [ ] Measure CPU, memory, underruns and latency.
- [ ] Document graceful fallback without HRTF.

## M3 — Physical surround
- [ ] Audit AHI format negotiation and driver output capabilities.
- [ ] Implement and verify 5.1 channel mapping.
- [ ] Implement and verify 7.1 channel mapping.
- [ ] Validate on supported real devices and document limitations.

## M4 — Integration and upstreaming
- [ ] Provide reusable sample applications and build instructions.
- [ ] Propose generally useful AHI fixes upstream as separate changes.
- [ ] Demonstrate use from a MIDI-controlled application without coupling to CAMD.

## Constraints
Keep m68k overhead optional and measured; do not impose a large spatial engine on minimal AROS installations. One verifiable topic per upstream change.
