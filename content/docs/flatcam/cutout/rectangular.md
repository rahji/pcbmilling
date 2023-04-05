---
title: Rectangular
weight: 1
---

## Rectangular Board Shape

While FlatCAM has a fairly simple method for cutting a board outline based on the extents of the board's traces, it doesn't allow for cutting non-rectangular PCBs. The process below uses the board outline Gerber file that you exported earlier. Unfortunately, it requires an extra step of editing the finished `.nc` file. 
The process of creating an `.nc` file for cutting out the finished PCB looks like this:

{{< mermaid >}}
graph LR
    A[Open Gerber]-->|.gbr|B[Generate Geometry]
    B-->|.gbr_iso|C[Generate CNC Job]
    C-->|.gbr_iso_cnc|D[Export G-code]
{{< /mermaid >}}

### Open Gerber

1. Choose `File | Open Gerber`, then select the Gerber file for the bottom of your PCB

### Generate Geometry

1. In the "Project" tab, select the `.gbr` list item
2. Click the tab labeled "Selected"
3. Verify that the settings under "Isolation Routing" are the same as what we entered in [Configuring FlatCAM](../../flatcam/configuring)
4. Click the "Generate Geometry" button

The red paths that are generated are the isolation routes that will be followed by the tools that we define in the next step.

{{< hint danger >}}
Verify that there is at least one red path between all of the traces and pads on your board. If there are areas where the spacing was too tight for a path to be created, you will need to use a smaller end mill or bit. Sometimes these issues can be resolved by moving the traces in your EDA software.
{{< /hint >}}

### Generate CNC Job

1. In the "Project" tab, double-click the `.gbr_iso` list item
2. Verify that the settings under "Create CNC Job" are the same as what we entered in [Configuring FlatCAM](../../flatcam/configuring)
3. Tick the "Multi-Depth" checkbox and set "Depth/pass" to half of the "Cut Z" value. (.5008 in our case.) This will require two passes for each of the cuts, which can make the job easier on the machine and the bit.
4. Click the "Generate" button under the "Create CNC Job" section

The blue paths that are generated are the areas of copper that will be cut away by the tool we just specified. Yellow lines are "links": movements where the tool is raised, and not cutting. Again, verify that everything looks correct.

### Export G-code

1. In the "Project" tab, double-click the `.gbr_iso_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the bit to be used for this job. For example, `bottom_60deg_501.nc`