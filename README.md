## Intellivision Model 5872

Otherwise known as Intellivision II.

_Video Modification_

Given the age of the unit, the addition of a RCA system replacing the RF modulator is the best approach. First described [here](https://wiki.intellivision.us/index.php/Intellivision_Composite_Video_Modification).

### ICs visible in the 5872 photographs

The following markings are visible in [`images/5872-01.jpg`](images/5872-01.jpg) and [`images/5872-02.jpg`](images/5872-02.jpg):

- GI **CP1610** — CPU (the package marking in the photograph is unclear; the 5872 service manual identifies U1 as CP1610)
- GI **RA-3-9600A** — RAM
- GI **RO-3-9503-003** — graphics ROM (GROM). It holds the built-in character/card patterns used by the STIC, including the default character set; it is CPU-visible at `$3000`–`$37FF`. [Intellivision Wiki: GROM](https://wiki.intellivision.us/index.php/GROM)
- GI **RO-3-9506-010** — Intellivision II Executive ROM (EXEC). It contains the console's startup/reset, vertical-blank interrupt, and common system routines. The Intellivision II combines the two EXEC ROMs used by the original model into this one device; its 4,096 10-bit words are mapped at `$1000`–`$1FFF`, with an additional 256 words at `$0400`–`$04FF`. [Intellivision Wiki: Executive ROM](https://wiki.intellivision.us/index.php/Executive_ROM) · [MAME ROM declaration](https://github.com/mamedev/mame/blob/master/src/mame/mattel/intv.cpp)
- GI **AY-3-8900-1** — STIC
- GI **AY-3-8914** — sound
- GI **AY-3-8915** — colour processor
- Four 2114L-class graphics/scratchpad RAM positions (the package markings need a clearer photograph; the service manual identifies U7, U8, U12, and U13 as 2114L RAM)
- **LAD** — board-specific logic/address-decoder IC at U9 (Mattel part `5872-0010`)

The added wiring obscures some RAM-package markings, so the manufacturer/date-code transcription remains to be confirmed from a clearer image.

### TTL STIC recreation

The project direction is a fixed-function, TTL-only recreation of the STIC; it deliberately excludes FPGA, CPLD, GAL, and microcontroller logic from the video and bus-compatibility path. The staged design and validation plan are in [the TTL STIC recreation document](docs/TTL-STIC-RECREATION.md).

The relevant pages from the GI data catalogue have been extracted into [GI chip data-sheet extracts](docs/GI-chip-extracts/README.md).
