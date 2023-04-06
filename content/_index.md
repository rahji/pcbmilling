---
title: PCB Prototyping Overview
type: docs
bookToc: false
---

## PCB Prototyping Overview

This website describes how to produce a printed circuit board using the Carbide Nomad desktop CNC milling machine.

The process is broken into several steps:

1. Creating Gerbers and drill files, demonstrated using Diptrace or Autodesk Eagle
2. Generating G-code, using FlatCAM
3. Milling the PCB, using Carbide Motion and the Carbide Nomad

{{< mermaid >}}
graph LR
    A[EDA software<br>Diptrace/Eagle]-->|Gerber & Drill Files|B[FlatCAM]
    B-->|NC Files|C[Carbide Motion]
{{< /mermaid >}}

{{< hint warning >}}
**Single-sided and PTH**  
The workflow described here assumes that you are making a single-sided PCB with traces and pads on the *bottom layer*. In other words, it's a circuit made up of PTH components. The process will be slightly different (and easier) for an SMD board, without holes.
{{< /hint >}}

Much of the information on this site comes from [Lars Mattern's FAB Academy pages](http://fabacademy.org/2021/labs/bottrop/students/lars-mattern/assignments/10.%20Input%20devices/4_flatcam/).
