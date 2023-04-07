---
title: Using DipTrace
weight: 1
---

## Exporting Gerber and Drill Files from DipTrace

All of the following is done in the PCB Layout application within Diptrace.

### Exporting the Bottom Layer

1. Choose `File | Export | Gerber`
2. Click "Bottom" from the list of Layers
3. Verify that *only* Traces, Pads, and Vias are selected from the list of Objects
4. Change units to "Metric"
5. Verify that the X and Y offsets are both 0
6. **Because this is the bottom layer, tick the "Mirror" checkbox**
7. Click "Export Layer" to save the Bottom layer as a Gerber (.gbr) file

### Exporting the Board Outline

1. In the same Export Gerber dialog from above, choose the "Board Outline" layer from the list of Layers
2. Verify that the X and Y offsets are both 0
3. **Because this is the bottom layer, tick the "Mirror" checkbox**
4. Click "Export Layer" to save the Board Outline layer as a Gerber (.gbr) file

### Exporting the Drill File

1. Choose `File | Export | N/C Drill`
2. Highlight both layers
3. Click the "Auto" button to assign tool numbers to each size hole
4. Tick all the checkboxes in the Objects, Plating, and Manufacturing Process groups
5. Verify that the X and Y offsets are both 0
6. **Even though we are using metric units, choose Inches**
7. **Tick the "Mirror" checkbox**
8. Click "Export All" to save the drill file
