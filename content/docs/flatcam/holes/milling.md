---
title: Milling Holes
weight: 1
---

## Milling Holes

Holes can be milled with a flat end mill or they can be drilled using a drill bit.

Milling allows for non-round holes and avoids having to switch tools when there are multiple hole sizes in the PCB layout.

The process of creating an `.nc` file for milling holes looks like this:

{{< mermaid >}}
graph LR
    A[Open<br>Drill File]-->|.drl|B[Generate<br>Geometry]
    B-->|.drl_mill|C[Generate<br>CNC Job]
    C-->|.drl_mill_cnc|D[Export<br>G-code]
{{< /mermaid >}}

### Open Drill File

1. Choose `File | Open Excellon`, then select the drill file. The holes should immediately be plotted as red circles.

### Generate Geometry

1. In the "Project" tab, double-click the `.drl` list item
2. Using the `Shift` key, select all of the tool numbers shown in the "Tools" list
3. Verify that the settings under "Create CNC Job" match what was entered in the "Exellon Options" section of [Configuring FlatCAM](../../flatcam/configuring)
4. Enter the diameter (in mm) of your flat end mill in the "Tool dia" field
5. Click the "Generate Geometry" button under "Mill Holes"

### Generate CNC Job

1. In the "Project" tab, double-click the `.drl_mill` list item
2. Change the values in the "Create CNC Job" section:
   * Cut Z: -1.7018 *(the thickness of the PCB blank)*
   * Travel Z: 2.0 *(how high to raise the end mill when it's not cutting)*
   * Feed Rate: 100 *(mm/min)*
   * Tool dia: 0.79248 *(1/32" flat end mill)*
3. Tick the "Multi-Depth" checkbox and set "Depth/pass" to **one third** of the "Cut Z" value. (0.57 in our case.) This will require **three** passes for each of the cuts, which can make the job easier on the machine and the bit.
4. Click the "Generate" button under "Create CNC Job"

### Export G-code

1. In the "Project" tab, double-click the `.drl_mill_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the bit to be used for this job. For example, `millholes_1_32_flat.nc`
