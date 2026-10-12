# RO-3-9506-010 EXEC ROM reference

No original General Instrument RO-3-9506 data sheet has been located in the publicly indexed archives. The evidence below documents the part's identity, capacity, and mapping; it is not a substitute for a pin-level electrical specification.

- The [Intellivision II service-manual extract](RO-3-9506_5872_parts_list.pdf) identifies U3 as an **RO-3-9506 PROM**, Mattel part `5872-0020`.
- The [MAME Intellivision driver](https://github.com/mamedev/mame/blob/master/src/mame/mattel/intv.cpp) identifies `RO-3-9506-010` as a self-decoding mask ROM with bus interface, holding 8 KiB (4,096 10-bit words) plus 512 bytes (256 words). It maps the 256-word section at `$0400`–`$04FF` and the 4,096-word EXEC section at `$1000`–`$1FFF`.
- The [Executive ROM reference](https://wiki.intellivision.us/index.php/Executive_ROM) independently describes the 4,096-word EXEC area and the additional 256 words present in the Intellivision II.
- The MAME dump is named `ro-3-9506-010.ic6`, is 8,704 bytes, and has CRC-32 `DD7E1237`; this identifies the image used by current emulation, not a license to redistribute it.

For a TTL replacement, the missing information is the package pinout, signal polarity, timing, and electrical limits. Those must be recovered from the 5872 schematic, continuity testing, and capture from a working board.
