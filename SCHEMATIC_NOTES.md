# FASTEST FINGER - Made by Catala - WITH SCHEMATIC

## Files
- `Fastest_Finger_Made_by_Catala.kicad_pro` - open this in KiCad Project Manager.
- `Fastest_Finger_Made_by_Catala.kicad_sch` - new editable electrical schematic.
- `Fastest_Finger_Made_by_Catala.kicad_pcb` - your modified PCB layout, kept in its original placements, with net assignments and schematic UUID links added and the two `REF**` LEDs renamed to `D5` and `D6`.
- `Fastest_Finger_Made_by_Catala.USER_ORIGINAL.kicad_pcb.bak` - exact original PCB from your uploaded ZIP, before these additions.
- `FF_Catala.kicad_sym`, `FF_Catala.pretty`, `sym-lib-table`, `fp-lib-table` - local libraries, including the original custom component footprints.
- `models` - preserve this folder to show custom 3D models.

## Open
1. Extract the ZIP completely (not just one file).
2. Open KiCad Project Manager -> **File > Open Project** -> select the `.kicad_pro`.
3. Open **Schematic Editor** to see all components and provisional electrical connections.
4. Open **PCB Editor** to view your PCB arrangement with nets/airwires.

## Electrical circuit assumed in this schematic
- **U1:** generic 48-pad Tang Nano 9K header symbol. Pads 1 and 2 are provisionally labeled +3V3 and GND; pads 3-7 correspond to the player/start/reset inputs, pads 8-15 to segments A-G and DP, pads 16-19 to digit drive transistors, and pad 20 to buzzer output. This assignment has NOT been verified against the real manufacturer's header drawing or FPGA constraints.
- **DS1:** assumed common-cathode 12-pin display: segment A=11, B=7, C=4, D=2, E=1, F=10, G=5, DP=3; digit cathodes 1=12, 2=9, 3=8, 4=6. **Actual model and pinout not supplied; do not rely on this map until checked.**
- **R1-R8**: 330 ohm segment resistors; **R9-R12**: 1k base resistors for Q1-Q4 digit sinks; **R13-R16**: 10k pull-ups for Player 1, 2, 3, Start; **SW5 RESET**: needs FPGA internal pull-up; **R17**: 1k base resistor for Q5 buzzer driver.
- **Q1-Q5:** assumed generic NPN SOT23 with pad1=base, pad2=emitter, pad3=collector. Confirm before choosing/purchasing the transistor.
- **C1-C2**: 100nF supply bypass capacitors.
- **BZ1**: USB/3.3V-powered piezo device, driven by Q5. Verify piezo current, voltage and waveform requirements; no added external regulator or power connector is present.
- **D1-D4 and D5-D6**: unconnected / marked DNP (do not populate). Their original design intent and wiring are unknown. KiCad footprint `D5` at x=1129mm is VERY FAR outside the 174 x 128mm board and was not moved, in accordance with preserving your edits; `D6` is near the right board edge.
- **H1-H4**: mounting holes with no electrical connections.

### Important design status
This is an **editable preliminary schematic and PCB netlist**, not a validated or manufactured-ready circuit. The *original image, custom footprints, and PCB edits did not provide the electrical schematic, FPGA pin constraints, tested 4-digit display pin assignment, transistor part number, or firmware*. I chose reasonable illustrative values and functional net connections to produce a useful starting schematic, **not guaranteed hardware correctness**.

No tracks were routed; this board will show a ratsnest / unrouted electrical connections until routed. Confirm real hardware part numbers, FPGA 3.3 V IO-bank voltages, pin assignments and display polarity before building, updating the PCB, or fabrication. Do not run the default pin assignment on hardware without checking manufacturer specifications.

### Manufacturer resources
- Official Tang Nano 9K documentation: https://github.com/sipeed/sipeed_wiki/blob/main/docs/hardware/en/tang/Tang-Nano-9K/Nano-9K.md
- Official board schematic: https://dl.sipeed.com/fileList/TANG/Nano%209K/2_Schematic/Tang_Nano_9k_3672_Schematic.pdf

## Verification limitations
The KiCad command-line tools are not installed in the generation environment. The text-format schematic, board, and symbol library were checked for balanced S-expressions, unique component references, and matching PCB/schematic component counts, but **not opened or electrically validated in KiCad**. Run KiCad ERC and DRC after checking the hardware specifications.
