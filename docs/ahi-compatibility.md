# AHI compatibility audit

## Source-confirmed capabilities
- `AHISF_KNOWMULTICHANNEL` and `AHIACF_MULTICHANNEL`: https://github.com/aros-development-team/AROS/blob/master/workbench/devs/AHI/Include/C/libraries/ahi_sub.h
- `AHIST_L7_1` selection: https://github.com/aros-development-team/AROS/blob/master/workbench/devs/AHI/Device/audioctrl.c
- Multichannel echo: https://github.com/aros-development-team/AROS/blob/master/workbench/devs/AHI/Device/effectinit.c
- EMU10kx 8-channel deinterleaving: https://github.com/aros-development-team/AROS/blob/master/workbench/devs/AHI/Drivers/EMU10kx/emu10kx-interrupt.c

## Unknowns to resolve
- Which AROS targets ship working AHI multichannel modes?
- Does `ahi.device` accept the required `AHIST_L7_1` buffer and how is that capability reported?
- Is the eight-channel sample layout consistent across drivers?
- Are audio modes exposed for USB Audio, HDA and emulated devices?
- What happens when a device reports only stereo?
- How are underruns, hotplug, output switching and device loss handled?
- Does the chosen backend maintain acceptable latency and memory usage?

## Evidence protocol
For every test record AROS target, build/commit, driver, hardware, output layout, sample rate, sample type, buffer size, observed result, and logs. Never equate a successful compilation with functional playback.
