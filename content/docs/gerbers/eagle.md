---
title: Using Autodesk Eagle
---

## Exporting Gerber and Drill Files from Autodesk Eagle

Autodesk Eagle is now Autodesk Fusion 360. All of the following is done in the Electronics Design workspace of Fusion 360, with a PCB document open.

### Download the CAM Processor Job File

To make the export process simpler, I have created a CAM Processor job file. [Download it here](/pcbmilling/assets/bottom_outline_drill_mirrored.cam) before continuing. This file is configured to mirror the Gerber and drill file outputs. (For non-mirrored output, [use this file instead](/pcbmilling/assets))

### Export the Gerber and Drill Files

1. Press the `/` key to activate the command line
2. Type the command `camprocessor`
3. Choose the document icon at the top of the CAM Processor window, select "Open CAM File..."
4. Select the CAM Processor job file you downloaded earlier
5. Click "Process Job" and choose a destination folder for your Gerber and drill files

{{< hint danger >}}
**Bad Drill File**  
Fusion 360 seems to create drill files that are formatted incorrectly. When opened in FlatCAM, the holes will be in the wrong location. To resolve this issue, *before opening the drill file in FlatCAM*, enter the following command in the command-line area at the bottom of the FlatCAM window:

```text
set_sys excellon_zeros T
```
{{< /hint >}}
