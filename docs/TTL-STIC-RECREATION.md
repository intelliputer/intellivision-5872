# TTL STIC Recreation

## Objective

Recreate the functional behavior of the General Instrument AY-3-8900 STIC with fixed-function TTL logic only. The design must not use an FPGA, CPLD, GAL, or microcontroller in the video/bus path.

The first revision is a separate, bench-testable board. It is **not** a 40-pin, pin-compatible replacement for the original STIC. A socket-compatible implementation can only be considered after the external timing and electrical behavior have been measured against a known-good 5872 board.

## Compatibility target

The board will initially work alongside an original CP1610K, EXEC/GROM, and cartridge. Its behavior must match the original STIC for:

- the 3.579545 MHz NTSC timing domain;
- the shared 14-bit multiplexed CPU/STIC bus and its display-time arbitration;
- STIC register accesses at `$0000`–`$003F`;
- BACKTAB fetches at `$0200`–`$02EF`;
- GROM/GRAM card fetching;
- foreground/background, colour-stack, and coloured-squares rendering;
- eight MOBs (sprites), their priority, mirroring, scaling, and collision latches; and
- blanking, sync, and the STIC-to-colour-output interface.

The STIC documentation identifies a 20 × 12 card background, 8 hardware MOBs, and a 14-bit multiplexed data/address bus shared with the CPU. The register map and BACKTAB location are documented by the [Intellivision Wiki](https://wiki.intellivision.us/index.php/STIC); the original GI data catalogue is the primary reference for electrical/timing values.

## TTL partition

| Block | Fixed-function implementation |
| --- | --- |
| Master timing | crystal oscillator, 74F/74ALS counters, comparators, and flip-flops |
| CPU/STIC arbitration | transparent latches, tri-state bus transceivers, decoders, and one-shot/flip-flop timing control |
| Register file | 74xx registers/latches plus discrete read/write decode |
| BACKTAB/GROM/GRAM sequencer | counters, muxes, latches, and ROM/RAM bus transceivers |
| Card and MOB pixel pipelines | shift registers, mux trees, and colour/priority PLA-equivalent diode/TTL logic |
| Collision unit | per-MOB comparators and set/reset latches |
| Video output | sync/blank generator, colour-code output, and a separate analogue encoder/output stage |

Use 74F or 74ALS parts for the timing-critical pixel, bus, and mux paths. 74HC is acceptable only after propagation-delay margins are measured; it must not be assumed interchangeable with bipolar TTL.

## Build sequence

1. **Capture the reference behavior.** Use the intact 5872 as an oracle. Record clock, bus ownership, sync/blank, colour outputs, and STIC register transactions with a logic analyser. Do not desolder the original STIC for this step.
2. **Timing-only board.** Produce stable NTSC horizontal/vertical timing and blanking. Verify line/frame counts and phase against the original board.
3. **Bus and register board.** Implement CPU access and the `$00`–`$3F` register map; verify reads, writes, active-display strobe, and mode-select behavior.
4. **Background renderer.** Add BACKTAB and GROM/GRAM fetches, then foreground/background, colour-stack, and coloured-squares modes.
5. **MOB pipeline.** Add the eight sprite paths, priority, scaling, reflection, and collision latches.
6. **Video integration.** Reproduce the original board's colour interface, then add an isolated composite/RGB encoder as a separate stage.
7. **Cartridge compatibility.** Exercise a representative set of cartridges and compare captured bus/video traces to the original hardware.

## Required companion logic

A usable console cannot be just CP1610K + recreated STIC + system RAM. The first system build also retains or recreates the EXEC, GROM, GRAM, clock/reset, controller interface, and the colour/video output path. Sound can remain a separate AY-3-8914 subsystem.

The original CP1610K is optional for early testing: the STIC board can first be driven by a TTL bus exerciser. If the original CPU is used later, its legacy power rails and logic levels must be supplied exactly as specified in the CP1610 data sheet.

## Design constraints

- No programmable logic in the compatibility path.
- Preserve the original 5872 logic board and its soldered ICs; use probes, adapters, and a separate test fixture.
- Keep digital TTL and analogue video supplies/returns separated until the encoder stage.
- Treat all unmeasured timing, pinout, and analogue levels as open questions; do not infer them solely from emulator code.

## References

- [General Instrument 1980 Microelectronics Data Catalog — AY-3-8900/AY-3-8900-1, pp. 5-9 to 5-11](https://www.bitsavers.org/components/gi/_dataBooks/1980_GI_Microelectronics_Data_Catalog.pdf)
- [STIC register and display-mode reference](https://wiki.intellivision.us/index.php/STIC)
- [Intellivision II service manual](Intellivision_II_Service_Manual.pdf)
- [CP1610 data catalogue](https://deramp.com/downloads/mfe_archive/050-Component%20Specifications/GI/1980_GI_Microelectronics_Data_Catalog.pdf)
