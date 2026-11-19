# Architecture and project boundaries

```text
AROS applications (games, players, MIDI-controlled synths, telepresence)
              |
         OpenAL API
              |
     OpenAL Soft rendering
  sources / 3D / optional HRTF
              |
       AROS AHI backend
       /             \
 stereo PCM       multichannel PCM (future)
       \             /
             AHI
              |
       AROS audio drivers
```

## Principles
1. Port OpenAL Soft rather than designing an incompatible new spatial-audio API.
2. Keep the renderer in user space; do not embed HRTF processing in drivers.
3. Preserve the existing AHI API and ABI unless a verified deficiency requires an upstream change.
4. Treat stereo binaural rendering and physical surround as separate output targets.
5. Do not couple the implementation to CAMD, MIDIHub, WebRTC, JackTrip or any single application.
6. Make computationally expensive effects optional, especially on low-memory and m68k systems.
7. Separate audio sample formats, channel layout, channel mapping, transport and device capability discovery.

## Proposed backend stages
- Initial backend: AROS-compatible `ahi.device` stereo PCM playback.
- Extended backend: verify whether `ahi.device` supports the needed multichannel format; consider low-level AHI only after that audit.
- Hardware-specific improvements belong upstream in AROS when generally useful.

## Open design decisions
- Target OpenAL Soft release and C++ runtime requirements.
- Native build versus cross-compilation strategy.
- Backend buffering and shutdown synchronization.
- Resampling, latency and underrun diagnostics.
- Channel layout conversion and speaker routing.
- Build-time or runtime disabling of HRTF for constrained targets.
