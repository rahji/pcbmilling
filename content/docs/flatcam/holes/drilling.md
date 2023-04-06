---
title: Drilling Holes
weight: 2
---

## Drilling Holes

Holes can be milled with a flat end mill or they can be drilled using a drill bit.

When drilling holes (as opposed to milling them), there will be a different .nc file for each size drill bit.

The process of creating a *single* `.nc` file for drilling holes looks like this:

{{< mermaid >}}
graph LR
    A[Open<br>Drill File]-->|.drl|B[Generate<br>Geometry]
    B-->|.drl_cnc|D[Export<br>G-code]
{{< /mermaid >}}

### Open Drill File

1. Choose `File | Open Excellon`, then select the drill file. The holes should immediately be plotted as red circles.

### Generate Geometry

1. In the "Project" tab, double-click the `.drl` list item
2. Select a single tool number in the "Tools" list
3. Verify that the settings under "Create CNC Job" match what was entered in the "Exellon Options" section of [Configuring FlatCAM](../../flatcam/configuring)
4. Click the "Generate" button under "Create CNC Job"

### Export G-code

1. In the "Project" tab, double-click the `.drl_cnc` list item
2. Click the "Export G-Code" button
3. Select a destination folder for the file and give it a name that includes the size of the drill bit to be used for this job. For example, `drillholes_.89916.nc`

### Repeat for Addition Drill Sizes

Repeat all of the steps after the "Open Drill File" above, for each of the different sized holes in the list. When generating each `.nc` file, be sure to include the size of the bit in the filename.
