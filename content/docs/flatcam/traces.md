---
title: 📈 Traces
weight: 4
---

## Traces

The process of creating an `.nc` file for the isolation routing around your circuit's traces and pads looks like this:

{{< mermaid >}}
graph LR
    A[Open Bottom<br>Copper Gerber]-->|.gbr|B[Generate<br>Geometry]
    B-->|.gbr_iso|C[Generate<br>CNC Job]
    C-->|.gbr_iso_cnc|D[Export<br>G-code]
{{< /mermaid >}}

### Open Gerber

1. Choose `File | Open Gerber`, then select the Gerber file for the bottom of your PCB

### Generate Geometry

1. In the "Project" tab, double-click the `.gbr` list item
2. Verify that the settings under "Isolation Routing" match what was entered in [Configuring FlatCAM](../../flatcam/configuring)
3. Click the "Generate Geometry" button

The red paths that are generated are the isolation routes that will be followed by the tools that we define in the next step.

{{< hint danger >}}
Verify that there is at least one red path between all of the traces and pads on your board. If there are areas where the spacing was too tight for a path to be created, you will need to use a smaller end mill or bit. Sometimes these issues can be resolved by moving the traces in your EDA software.
{{< /hint >}}

### Generate CNC Job

1. In the "Project" tab, double-click the `.gbr_iso` list item
2. Verify that the settings under "Create CNC Job" match what was entered in [Configuring FlatCAM](../../flatcam/configuring), under "Geometry Options (for Isolation Routing)"
3. Click the "Generate" button under the "Create CNC Job" section

The blue paths that are generated are the areas of copper that will be cut away by the tool we just specified. Yellow lines are "links": movements where the tool is raised, and not cutting. Again, verify that everything looks correct.

### Export G-code

1. In the "Project" tab, double-click the `.gbr_iso_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the bit to be used for this job. For example, `bottom_60deg_501.nc`
