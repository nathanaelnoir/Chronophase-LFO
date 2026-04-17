[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![Schematic v1.1](https://img.shields.io/badge/Sch-v1.1-blueviolet)](KiCad/Synced_LFO.kicad_sch)
[![PCB v1.1](https://img.shields.io/badge/PCB-v1.1-blue)](KiCad/Synced_LFO.kicad_pcb)
[![PCBs: 1](https://img.shields.io/badge/PCBs-1-brightgreen)](KiCad/Synced_LFO.kicad_pcb)
[![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)](#)
[![License: TBD](https://img.shields.io/badge/License-TBD-lightgrey)](#license--contributing)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

# Chronophase LFO

Chronophase LFO is a clock-synced Eurorack modulation source with an Arduino Nano core, four front-panel controls, one clock input, and separate unipolar, bipolar, and inverted bipolar outputs.

## Contents

- Overview
- Features
- Quick start (KiCad 9)
- Files
- Build & assembly notes
- Testing
- License & contributing

## Overview

This repository contains the KiCad 9 design files for Chronophase LFO, a clocked modulation module for Eurorack. An external clock drives the LFO core, the four main controls adjust `WAVEFORM`, `AMP`, `PHASE`, and `MODULATION`, and the output stage provides `UP_Out`, `BP_Out`, and `BP_Inv_Out` on separate jacks.

The current KiCad 9 project files are named `Synced_LFO`, and the top-level schematic title block still says `Clocked Modulation LFO`. The current documented revision for both the schematic and PCB is `v1.1`.

The hardware clearly includes an `Arduino_Nano_v3.x`, but there is no firmware source in this repository at the moment, only the hardware design files.

## Features

- Clock-synced LFO built around an `Arduino_Nano_v3.x` core and `TL072` output / shaping stages.
- Four front-panel controls: `WAVEFORM`, `AMP`, `PHASE`, and `MODULATION`.
- External `CLK In` jack for sync / clock input.
- Separate `UP_Out`, `BP_Out`, and `BP_Inv_Out` outputs.
- Front-panel activity LED.
- Standard Eurorack power distribution with `+12 V / -12 V / +5 V / GND` through a 16-pin Eurorack header sheet.
- Mixed build: SMD passives, diodes, electrolytics, and SOIC op-amps, with through-hole jacks, pots, LED, and Arduino Nano.

## Quick start

1. Install KiCad 9.
2. Open the project: `KiCad/Synced_LFO.kicad_pro`.
3. Review the top-level schematic and the `EURORACK_POWER` sheet, then run ERC/DRC before exporting manufacturing files.

## Files

- `KiCad/Synced_LFO.kicad_sch` - top-level schematic
- `KiCad/eurorack_power.kicad_sch` - Eurorack power sheet
- `KiCad/Synced_LFO.kicad_pcb` - PCB
- `KiCad/Synced_LFO.kicad_pro` - KiCad 9 project file
- `KiCad/Synced_LFO.kicad_prl` - local KiCad 9 project state
- `KiCad/Synced_LFO.sch` - legacy schematic file
- `KiCad/Synced_LFO.pro` - legacy project file

Note: there is a single PCB layout file (`KiCad/Synced_LFO.kicad_pcb`) for this project.

## Build & assembly notes

- Check orientation on the `Arduino_Nano_v3.x` module before soldering headers or the board directly. The USB end and pin order matter.
- Confirm pin-1 orientation on the `TL072` packages and polarity on the diodes and electrolytics before powering the board.
- Double-check the Eurorack power header orientation before applying power. This design uses `+12 V`, `-12 V`, `+5 V`, and `GND`, so a reversed cable is an easy way to damage parts.
- Panel hardware is straightforward but still substantial: four 100 k pots, four 3.5 mm jacks, and one LED.
- This is a mixed SMD + THT build, so it makes sense to solder the low-profile SMD parts first and leave the pots, jacks, LED, and Nano for later.

## Testing

1. Power the module from a current-limited Eurorack supply and verify `+12 V`, `-12 V`, `+5 V`, and `GND` on the power section before checking the rest of the circuit.
2. Feed a known clock into `CLK In` and confirm the front-panel LED shows activity.
3. Probe `UP_Out`, `BP_Out`, and `BP_Inv_Out` on a scope and confirm all three outputs are present and distinct.
4. Turn `WAVEFORM`, `AMP`, `PHASE`, and `MODULATION` through their full range and verify the outputs respond as expected.
5. If the Arduino Nano is fitted, confirm the module behavior is stable across different clock rates and after power-cycling.

## License & contributing

No `LICENSE` file has been added to this repository yet. Until that changes, assume the design is shared for reference, not under an explicit open-source license.

If a license is added later, this section can be updated properly.
