---
title: Rectangular
weight: 1
---

## Cutting a Rectangular Board Shape

FlatCAM has a built-in "Cutout Generator" that can provide a toolpath for cutting out a rectangular board without using the board outline Gerber generated earlier. The size of the board is based on the size of the layout of the board's traces and pads. It also includes tabs that keep the board from coming loose from the larger PCB blank when it is cut out. The tabs are not really necessary if the PCB blank is adhered using double-stick tape, but will be useful if the blank is *clamped* down.

The process of creating an `.nc` file for cutting out the finished *rectangular* PCB looks like this:

{{< mermaid >}}
graph LR
    A[Select<br>Existing Bottom<br>Copper Gerber]-->|.gbr|B[Generate<br>Geometry]
    B-->|.gbr_cutout|C[Generate<br>CNC Job]
    C-->|.gbr_cutout_cnc|D[Export<br>G-code]
{{< /mermaid >}}

### Select Existing Bottom Copper Gerber

1. In the "Project" tab, double-click the existing `.gbr` list item

### Generate Geometry

1. Under "Board Cutout", verify that the "Tool dia" matches what was entered in [Configuring FlatCAM](../../flatcam/configuring) (1.5875 mm, 1/16")
2. Optionally adjust the "Margin", "Gap Size", and "Gaps"
3. Click the "Generate Geometry" button under "Board cutout"

The red paths that are generated will be followed by the tools that we define in the next step.

### Generate CNC Job

1. In the "Project" tab, double-click the `.gbr_cutout` list item
2. Change the values in the "Create CNC Job" section:
   * Cut Z: -1.7018 *(the thickness of the PCB blank)*
   * Travel Z: 2.0 *(how high to raise the end mill when it's not cutting)*
   * Feed Rate: 90 *(mm/min)*
   * Tool dia: 1.5875 *(1/16" flat end mill)*
3. Tick the "Multi-Depth" checkbox and set "Depth/pass" to **one third** of the "Cut Z" value. (0.57 in our case.) This will require **three** passes for each of the cuts, which can make the job easier on the machine and the bit.
4. Click the "Generate" button under "Create CNC Job"

The blue paths that are generated are the areas of the board that will be cut by the tool we just specified.

{{< hint info >}}
If the placement or quantity of tabs does not look correct, you will need to restart the above process and delete any outdated geometries from the "Project" list afterward. Enabling and disabling plots via the `View` menu, or by ticking the "Plot" checkbox in individual geometries, can be helpful in identifying which geometries are which.
{{< /hint >}}

### Export G-code

1. In the "Project" tab, double-click the `.gbr_cutout_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the bit to be used for this job. For example, `cutout_1_16_flat.nc`
