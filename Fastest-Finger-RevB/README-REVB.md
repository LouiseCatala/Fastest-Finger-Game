# Fastest Finger Rev B

Open `Fastest_Finger_RevB.kicad_pro` in KiCad 10. This revision replaces the original spare diode positions with four wired LED indicators (D1-D3 player winners, D4 ready), corrects the 4-digit display to Kingbright CC56-12EWA, and routes the two-layer PCB. Tang Nano 9K is USB powered. The project uses local symbol and footprint libraries.

## Checks, 22 November 2026

- Native KiCad ERC: 0 errors, 0 warnings.
- Native KiCad DRC after routing and ground pour fill: 0 violations, 0 unconnected items.
- Native netlist versus PCB: 69 components and 182 connected pin assignments match.
- Gerber and drill files exported in `gerbers/`.
- Automated PCB and Gerber analyses: no error findings; PCB analyzer notes limited test-point coverage. EMC analysis is heuristic and still flags return-path/decoupling risks. Thermal analysis could not quantify junction temperatures without extracted power data. No physical prototype was tested.

## Electrical contract

- Buttons are active-low with 10 kOhm pullups and 1 nF capacitors. Debounce in FPGA logic.
- U2 SN74LVC244ADWR buffers eight 3.3 V segment signals. R1-R8 are 330 Ohm. For CC56-12EWA, the datasheet lists 1.9 V typical forward voltage at 10 mA; estimated peak segment current is approximately (3.3-1.9)/330 = 4.2 mA, with 1/4 multiplex duty.
- Q1-Q4 AO3400A select each common cathode, one at a time. Q5 drives TDK PS1240P02BT piezo. R19 is a 1 kOhm discharge path. Gate pulldowns hold drivers off during FPGA configuration.
- U1 carrier header pin 47 is GND, 48 is 3.3 V. J5 pins 5-22 and J6 pins 19-22 are assigned to controls, display, and indicators. The exact header-to-FPGA-pad list is in `design-data.json`. All used I/O is from 3.3 V banks according to Sipeed's board pinout. Verify physical module orientation before insertion.
- Firmware and FPGA pin constraint file are not included. Hardware function and response-time accuracy remain unproven until firmware and bench testing are completed.

## Before assembly

Check ordered part packages and orientation against the BOM and datasheets. Inspect the display pin 1 and module header pin 1 marking. With no module fitted, check for 3.3 V-to-GND shorts and continuity. Power through the module USB with a current-limited source, measure TP1 to TP2, then program a simple LED/display/button test before full game logic. Do not treat the exported manufacturing files as a measured product qualification.

## Sources

- Sipeed Tang Nano 9K: https://dl.sipeed.com/fileList/TANG/Nano%209K/2_Schematic/Tang_Nano_9k_3672_Schematic.pdf
- Kingbright CC56-12EWA: https://www.kingbrightusa.com/images/catalog/SPEC/CC56-12EWA.pdf
- TI SN74LVC244A: https://www.ti.com/lit/ds/symlink/sn74lvc244a.pdf
- AOS AO3400A: https://www.aosmd.com/sites/default/files/res/datasheets/AO3400A.pdf
- TDK piezo: https://product.tdk.com/system/files/dam/doc/product/sw_piezo/sw_piezo/piezo-buzzer/catalog/piezoelectronic_buzzer_ps_en.pdf
