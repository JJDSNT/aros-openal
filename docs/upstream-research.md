# Upstream research and evidence

Last reviewed: 2026-11-19. Findings are from source inspection, **not runtime testing**.

## OpenAL Soft
- Original project: https://github.com/kcat/openal-soft
- AmigaOS 4 adaptation: https://github.com/salass00/openal_lib
- The latter contains `openal-soft-1.18.2/Alc/backends/ahi.c` and `openal-soft-1.20.1/alc/backends/ahi.cpp`.
- In 1.20.1, `AHIPlayback::reset()` maps mono and stereo byte/short/int formats to AHI formats; the default branch rejects other channel counts with `AHIST_NOTYPE`. This backend is **not** a proven 5.1/7.1 output solution.
- The 1.20.1 backend uses `IExec`, `IDOS`, `ProcessScan`, `CreateNewProcTags`, and `ahi.device`. These require AROS-specific compatibility review; do not assume a drop-in build.
- The implementation creates two AHI requests, mixes through `aluMixData`, and submits `CMD_WRITE` requests. Playback only is advertised in `querySupport`.

Source: https://github.com/salass00/openal_lib/blob/master/openal-soft-1.20.1/alc/backends/ahi.cpp

## AROS AHI
- `workbench/devs/AHI/Include/C/libraries/ahi_sub.h` defines `AHISF_KNOWMULTICHANNEL` and `AHIACF_MULTICHANNEL`.
- `workbench/devs/AHI/Device/audioctrl.c` selects `AHIST_L7_1` for a suitable multichannel control configuration.
- `workbench/devs/AHI/Device/effectinit.c` handles `AHIST_L7_1` with a dedicated multichannel echo routine.
- `workbench/devs/AHI/Drivers/EMU10kx/emu10kx-interrupt.c` contains a concrete `AHIST_L7_1` path that deinterleaves eight channels into four stereo hardware buffers.
- `workbench/devs/AHI/Examples/Low-level/Test-7.1/Test-7.1.c` provides a starting point for test design.

Source tree: https://github.com/aros-development-team/AROS/tree/master/workbench/devs/AHI

## Important distinction
The existence of a format and driver path does **not** establish that a particular AROS build, USB device, HDA device, sound card, or speaker arrangement produces correct 5.1/7.1 sound. Channel order, capability negotiation, buffer semantics, hardware routing and runtime tests remain open.

## Next research
- Identify supported AROS toolchains and required C++ language/library features for a chosen OpenAL Soft release.
- Compare the old AmigaOS 4 backend with current upstream backend APIs; avoid assuming the 1.20.1 code can be copied into current OpenAL Soft.
- Audit `ahi.device` versus low-level AHI APIs for multichannel playback.
- Inspect actual USB Audio and HDA capabilities and avoid claims of support without tests.
- Verify license obligations for any incorporated third-party code.
