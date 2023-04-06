---
title: Non-Rectangular
weight: 2
---

## Non-Rectangular Board Shape

While FlatCAM has a fairly simple method for cutting a board outline based on the extents of the board's traces (see [Rectangular Board Cutout](../../cutout/rectangular)), that method doesn't allow for cutting non-rectangular PCBs. The process below uses the board outline Gerber file that you exported earlier to create toolpaths for any board shape. Unfortunately, it requires an extra step of editing the finished `.nc` file.

The process of creating an `.nc` file for cutting out the finished *non-rectangular* PCB looks like this:

{{< mermaid >}}
graph LR
    A[Open Board<br>Outline Gerber]-->|.gbr|B[Generate<br>Geometry]
    B-->|.gbr_iso|C[Generate<br>CNC Job]
    C-->|.gbr_iso_cnc|D[Export<br>G-code]
    D-->|.nc file|E[Edit<br>G-code]
{{< /mermaid >}}

### Select Existing Bottom Copper Gerber

1. In the "Project" tab, double-click the existing `.gbr` list item

### Generate Geometry

1. Under "Board Cutout", verify that the "Tool dia" matches what was entered in [Configuring FlatCAM](../../flatcam/configuring) (1.5875 mm, 1/16" is a good choice for cutting out the board)
2. Optionally adjust the "Margin", "Gap Size", and "Gaps"
3. Click the "Generate Geometry" button under "Board cutout"

The red paths that are generated will be followed by the tools that we define in the next step. Note that there are two paths. We will remedy by editing the `.nc` file at the end.

### Generate CNC Job

1. In the "Project" tab, double-click the `.gbr_cutout` list item
2. Change the values in the "Create CNC Job" section:
   * Cut Z: -1.7018 *(the thickness of the PCB blank)*
   * Travel Z: 2.0 *(how high to raise the end mill when it's not cutting)*
   * Feed Rate: 90 *(mm/min)*
   * Tool dia: 1.5875 *(1/16" flat end mill)*
3. Tick the "Multi-Depth" checkbox and set "Depth/pass" to **one third** of the "Cut Z" value. (0.57 in our case.) This will require **three** passes for each of the cuts, which can make the job easier on the machine and the bit.
4. Click the "Generate" button under "Create CNC Job"

The blue paths that are generated are the areas of the board that will be cut by the tool we just specified. Again, note that there are two paths. We will remedy by editing the `.nc` file at the end.

{{< hint info >}}
If the placement or quantity of tabs does not look correct, you will need to restart the above process and delete any outdated geometries from the "Project" list afterward. Enabling and disabling plots via the `View` menu, or by ticking the "Plot" checkbox in individual geometries, can be helpful in identifying which geometries are which.
{{< /hint >}}

### Export G-code

1. In the "Project" tab, double-click the `.gbr_cutout_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the bit to be used for this job. For example, `cutout_1_16_flat.nc`

### Edit G-code

Because the `.nc` file you just created includes two cuts, with one being offset from the other, the file will need to be edited to remove the unwanted *inner* shape.

1. Open the `cutout_1_16_flat.nc` file in the [NC Viewer website](https://ncviewer.com/)
2. Delete the G-code lines *below* the `G4 P1` command, up to and *including* the `G00 Z2.0000` command below
3. Click the "PLOT" button to update the 3D preview
4. Verify the remaining G-code by scrolling through the lines, from top to bottom, using the down arrow
5. Save the edited file as `cutout_1_16_flat_edited.nc`

{{< hint warning >}}
Note that the remaining geometry is offset from the original board outline defined in the Gerber file. This may result in rounded corners instead of sharp corners.
{{< /hint >}}
