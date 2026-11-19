# AROS OpenAL

Research and porting project for **OpenAL Soft on AROS**, using AHI for playback. The goal is portable 3D positional audio, optional binaural HRTF, and eventually verified 5.1/7.1 output.

**Status:** research and planning; no AROS build or hardware playback has been demonstrated. This repository does not claim an implemented port.

## Scope
- Port a suitable upstream OpenAL Soft release to AROS, initially with stereo AHI output.
- Validate positional audio and optional HRTF using headphones.
- Audit and test the existing AHI multichannel path before adding 5.1/7.1 playback.
- Keep audio rendering independent from MIDI/CAMD and application-specific transport.
- Prefer reusable upstream AROS fixes over project-local forks of AHI.

## Reading order
1. [Upstream references and verified findings](docs/upstream-research.md)
2. [Architecture and boundaries](docs/architecture.md)
3. [AHI compatibility audit](docs/ahi-compatibility.md)
4. [5.1/7.1 design questions](docs/surround-51-71.md)
5. [Milestones and acceptance criteria](docs/roadmap.md)
6. [Test plan](tests/README.md)

## Implementation policy
No bundled third-party source until the version, licensing obligations, build prerequisites and maintenance strategy are recorded. Treat source inspection, compilation, runtime verification and hardware validation as distinct evidence levels.

## Related projects
- [OpenAL Soft](https://github.com/kcat/openal-soft)
- [AmigaOS 4 OpenAL Soft port](https://github.com/salass00/openal_lib)
- [AROS](https://github.com/aros-development-team/AROS)

OpenAL Soft and AHI are separate projects; this repository is not an official upstream port.
