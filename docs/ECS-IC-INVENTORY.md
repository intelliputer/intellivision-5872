# ECS IC inventory

This inventory is based on [`images/ecs/ECS-Module-011.jpeg`](../images/ecs/ECS-Module-011.jpeg), [`images/ecs/ECS-Module-014.jpeg`](../images/ecs/ECS-Module-014.jpeg), and [`images/ecs/ECS-Module-023-Keyboard.jpeg`](../images/ecs/ECS-Module-023-Keyboard.jpeg).

| Visible marking / board item | Identification | Function |
| --- | --- | --- |
| `4182-0128 BG`, `83 35 REV H`, `SINGAPORE` | ECS EXEC/BASIC ROM | 12K ROM containing the ECS EXEC extensions and ECS BASIC. The ECS maps its ROM across `$2000`, `$7000`, and `$E000` pages. |
| GI `AY-3-8917` / Mattel `0098-0580` | ECS programmable sound generator (PSG) | Adds three tone channels plus noise, and provides the two bidirectional 8-bit I/O ports used by the ECS keyboards/controllers. |
| 24-pin custom device marked `4182-0039` (manufacturer logo unclear) | **Unconfirmed** ECS support/custom device | Candidate for the ECS SDCC ("Super-Duper Custom Chip"), which coordinates ECS bus traffic. The present photograph is not sufficient to establish that attribution or its pinout. |
| 16-pin support IC below the AY-3-8917 | **Unidentified** | Its marking is not legible in the photographs. |
| Black epoxy-covered component at left | **Unidentified** | May be a potted/custom component; no marking is visible. |

The separate keyboard photograph contains no ICs: it is the passive key-matrix board and its cable assembly. The ECS scans its keyboards through the AY-3-8917 I/O ports.

## Sources

- [ECS technical overview](https://www.intellivision.us/intvlibrary/Games/Trivia/consoles.htm) — 12K EXEC/BASIC ROM, additional RAM, UART, I/O ports, and SDCC function.
- [ECS keyboard and AY-3-8917 register reference](https://wiki.intellivision.us/index.php/Entertainment_Computer_System) — keyboard scanning and PSG mapping at `$00Fx`.
- [ECS memory-map note](https://www.intvprime.com/intellivision-faq/intellivision-faq-section-2-0-hardware/) — ECS ROM pages.
- [ECS board-variant discussion](https://www.forum64.de/index.php?pageNo=1&thread%2F37485-intellivision-ecs-prototyp%2F=) — independently records the normal-production `4182-0128 BG`, `83 35 REV H`, `SINGAPORE` ROM marking visible here.
- [AY-3-8910/AY-3-8912 PSG family reference](GI-chip-extracts/AY-3-8910_AY-3-8912_PSG_family_reference.pdf) — related family documentation only; it is not a data sheet for AY-3-8917.
