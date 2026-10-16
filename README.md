## Intellivision Model 5872

Otherwise known as Intellivision II.

https://saskapriest.com/2022/03/29/repairing-the-intellivision-vintage-gaming-console/

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

### Entertainment Computer System (ECS)

The ECS photograph inventory and identified ROM, PSG, keyboard-matrix, and support devices are documented in [the ECS IC inventory](docs/ECS-IC-INVENTORY.md).

### Intellivision Entertainment Computer System (ECS) Rev C

The Intellivision Master Component had been heavily advertised to be followed up by the release of a 'Keyboard Component' that would turn the Mattel games machine into a home computer.

The Keyboard Component was to be a larger casing that the entire Intellivision Master Component was inserted. Some of the features advertised were a data tape drive, an external port for cartridges (the Intellivisions native port was inaccessible once inside), support for a forty column printer and a keyboard that contained all the smarts the Master Component didn't. The Keyboard Component would have also upgraded the system's memory to 64K and that was very reasonable at the time.

The data tape drive would have had been able to provide an audio track as well as a data track (much like the Atari 1010 drive) making it ideal for educational software as the user could receive spoken information while programs loaded.

Unfortunately, mainly due to it being an amazingly ambitious piece of tech for the time and being prohibitively expensive to manufacture it never got off the ground.
What it did do is trigger enough public outcry that the US Federal Trade Commission fined Mattel $10,000 per day until they made good on their promise to release the hardware to consumers.

Enter the Intellivision Entertainment Computer System (ECS). In 1981 Mattel management had started to become concerned that the Keyboard Component would never get up and running and so had a secret team working on a much cheaper option, the ECS. The team was kept secret purely so it wouldn't enrage the Keyboard Component development team.

When the FTC hit Mattel with the daily fine it was the ECS's time to shine even though barely scraped through the check list to turn the Intellivision into a home computer. Offering only a 2K memory upgrade and limited storage and output capabilities it saved Mattel's collective arses.

The ECS came with a very basic BASIC loaded on ROM. Users could write programs, save/load them and print. So now the Intellivision was a computer with a keyboard that is HORRIBLE to use and prone to stuck keys.

The only really redeeming feature is that the ECS came with a decent sound chip allowing you to plug a dedicated, forty nine key piano keyboard turning it in to a horrible looking, multi-voice synthesizer; admittedly the first of its kind for a game console.

Very shortly after it was released, software development halted for the ECS and Mattel moved away from add-on hardware.

It really is a horrible, brown chunk. It's a genuine shame as if the Intellivision the first genuine 16-bit gaming system) could have been upgraded to a half decent computer, the Commodore 64 may have had a very different history.

### Errata

* A keyboard enhancement [idea](https://intellivisionrevolution.com/ultimate-pc-interface-for-the-intellivision)
