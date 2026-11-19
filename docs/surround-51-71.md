# Physical surround: 5.1 and 7.1

## Existing starting point
AHI includes `AHIST_L7_1` and the EMU10kx driver contains an eight-channel playback path. That does not establish generic 5.1 or 7.1 support.

## Required work
1. Document the channel order used by OpenAL Soft for each requested layout.
2. Determine AHI's actual `AHIST_L7_1` channel order from implementation and examples.
3. Build an explicit, tested channel-remapping table; do **not** assume orders match.
4. Determine how a six-channel 5.1 mix should be carried to an eight-channel AHI mode, including unused channels and physical routing.
5. Verify center, LFE, side and rear semantics, not only that eight buffers are filled.
6. Define fallback to stereo (with or without HRTF) if surround is unavailable.
7. Validate on real hardware with isolated speaker-identification signals.

## Non-goals for initial milestone
- Dolby Atmos or DTS proprietary encoding/decoding.
- HDMI bitstream passthrough.
- System-wide audio server or replacement for AHI.
- Assuming USB Audio multichannel works before auditing the driver.

## Acceptance
Each test signal must emerge from exactly the intended physical speaker, with documented fallback behavior and no swapped channels. 5.1 and 7.1 are separate test cases.
