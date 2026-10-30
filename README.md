# FASTEST FINGER — Made by Catala

This is an **editable KiCad PCB Editor board layout** recreated from the supplied reference image.

**Changes from the reference**
- All six names across the top have been removed.
- The bottom-center text now reads **Made by Catala**.
- The original title, three-player layout, approximate placement, and white decorative graphics are retained.

## Open in KiCad
1. Extract the whole ZIP; keep the `models` folder with the project files.
2. In KiCad Project Manager choose **File → Open Project** and select `Fastest_Finger_Made_by_Catala.kicad_pro`.
3. Double-click `Fastest_Finger_Made_by_Catala.kicad_pcb` from the project tree, or choose the PCB Editor shortcut.
4. In PCB Editor, use **View → 3D Viewer** (`Alt+3` on many systems) to see the approximate component models.
5. Edit text and locations directly on the **F.SilkS** and other PCB layers.

Alternatively, start standalone PCB Editor and use **File → Open** to select the `.kicad_pcb` file. Do not try to select `.kicad_pcb` from KiCad Project Manager's **Open Project** file dialog, which filters for `.kicad_pro`.

## Important limitation
This is a **visual/layout reconstruction, not a working, manufacturing-ready electronic design**.
The picture contains no schematic, netlist, pin assignments, resistor values, control wiring, FPGA code, or trace routing. Thus the components use **editable, representative footprints with no electrical nets or copper tracks**; do not send to fabrication or assume functionality without designing and verifying the actual circuit. Real footprints/dimensions must be checked against the specific parts to be installed, especially the four-digit display, buttons, buzzer and diodes. Visual models are approximations, not manufacturer STEP models.

- Board nominal dimensions: **174 mm × 128 mm**.
- Tang Nano 9K: represented by a **2 × 24 pin, 2.54 mm pitch** carrier footprint.
- Editable silkscreen labels and PCB features are part of the `.kicad_pcb` file.
