# Validation plan

No test execution is claimed here. This directory documents acceptance criteria until executable tests are added.

## Stereo / binaural
- Open and close AHI repeatedly without leaked ports, signals or I/O requests.
- Render a fixed sine signal to left and right independently.
- Move a mono source in 3D; compare expected directional behavior.
- Verify HRTF enabled, disabled and unavailable paths.
- Record sample rate, buffer duration, CPU, peak memory and underruns.
- Stress stop/start, device failure, process termination and repeated initialization.

## Multichannel
- Test isolated FL, FR, FC, LFE, side and rear channels for 5.1 and 7.1.
- Check channel permutation, silence of unused channels and downmix behavior.
- Verify output with a real device, not just a software buffer.
- Confirm no buffer overrun and correct interleaving at sample boundaries.
- Repeat with at least two buffer sizes and two supported sample rates.

## Test evidence template
```text
AROS commit / target:
OpenAL Soft version:
Driver and audio device:
Output layout / format / sample rate:
Test procedure:
Expected:
Observed:
CPU / peak memory / latency:
Logs / reproduction steps:
```
