---
title: Configuring FlatCAM
weight: 2
bookToc: false
---

## Configuring FlatCAM Defaults

If this is the first time you are using FlatCAM on the computer you're sitting at, you should verify that the application defaults are set to reasonable values. You will have the opportunity to override these values in future steps.

Open FlatCAM and choose the Options tab. Make sure "APPLICATION DEFAULTS" is selected, then change/verify the following values:

{{< details title="Gerber Options" open=false >}}

**Isolation Routing**

* Units: mm
* Tool dia: 0.24435 *(this is the width for the 60&deg; V-bit #501)*
* Width (# passes): 3 *(this is the number of outline cuts to make around the traces)*
* Pass overlap: 0.15
* Tick the "Combine Passes" checkbox

**Board Cutout**

* Tool dia: 1.5875 *(1/16" flat end mill)*
* Margin: 3.0 *(margin to leave inside the board cutout area)*
* Gap Size: 3.0 *(size of the tabs to leave - not really necessary when using double-stick tape)*
* Gaps: 2(L/R) *(the number and location of tabs to leave)*

{{< /details >}}

{{< details title="Excellon (drilling) Options" open=false >}}

* Cut Z: -1.7018 *(the thickness of the PCB blank)*
* Travel Z: 2.0 *(how high to raise the drill bit when it's not drilling)*
* Feed Rate: 90 *(mm/min)*
* Tool dia: 0.79248 *(1/32" flat end mill)*

{{< /details >}}

{{< details title="Geometry Options (for Isolation Routing)" open=false >}}

* Cut Z: -0.1016 *(this is the thickness used in the V-bit tool diameter calculation)*
* Travel Z: 2.0 *(how high to raise the end mill when it's not cutting)*
* Feed Rate: 100 *(mm/min)*
* Tool dia: 0.24435 *(again, this is the width for the 60&deg; V-bit #501)*

{{< /details >}}
