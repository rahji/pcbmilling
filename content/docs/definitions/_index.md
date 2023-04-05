---
title: Definitions
bookFlatSection: true
weight: 5
bookToc: false
---

## Definitions

EDA software
: Software that allows you to diagram electronic circuits ("schematic capture") and convert those schematics to PCB layouts. This software typically also has features that include checking the validity and manufacturability of your designs, simulating the circuit, 3D modeling the PCB, etc. Examples: DipTrace, Autodesk Eagle, KiCAD, EasyEDA. *Also known as "ECAD software."*

ERC and DRC
: Electrical Rule Check and Design Rule Check. These are two methods used in EDA software to find errors in your circuit design or your PCB layout. A PCB fab will supply details about their manufacturing capabilities, with the DRC check will use to determine the manufacturability of your PCB. It makes sense to run an ERC and DRC check, along with any other checks that your EDA software affords (e.g.: checking net connectivity or comparing a PCB layout to the corresponding schematic) before trying to have the board made or trying to make it yourself.

Excellon/drill files
: The *other* file type that EDA software can produce (see "Gerber files" below). The locations of drilled holes and the IDs of the drill bits to use are stored in these files. An alternative to drilling holes with a drill bit is *milling* them. Milled holes have the benefit of making different sized (and different shaped!) holes with a single tool.

Fab
: A manufacturing facility that makes PCBs. You typically submit Gerber and drill files to a fab. Having a single-sided board made is atypical, as most fabs produce boards with at least two copper layers. Some fabs will also source and solder the components to the board for you. This service is usually called "assembly" or "PCBA." Examples: JLCPCB, OSH Park, PCBWay.

FR-1 and FR-4
: The non-copper substrate in PCBs is either FR-1 or FR-4. PCBs produced at a factory will be FR-4. For milling, we only want to use FR-1 PCB blanks. They can be purchased from [Inventables](https://www.inventables.com/)

G-code / NC files
: NC stands for "numeric control." These files contain instructions for a CNC machine. The instructions take the form of G-code commands. These commands are used by a wide variety of CNC machines (e.g.: laser cutters, 3d printers, milling machines, routers) and can include instructions that set the spindle speed, change the temperature of a nozzle, define which units are used in the rest of the file, etc.

Gerber files
: These types of files are exported by your EDA software. Each Gerber file describes a different layer of your design. Some of those layers may be copper layers. Other types of layers include silkscreen printing or the locations of components to be soldered to the board. These are the files that we use in the process described in this document and are also the files used by a PCB fab. For the PCB milling process described here, we are only interested in the copper layer that contains your boards traces and the board outline layer.

Pads
: The area on a PCB trace where the lead of a component will be soldered. For PTH components, there will be a hole in the center of the pad. For SMD components, the pad serves as the resting place for a component lead when it is soldered in place.

PCB
: A printed circuit board. At their simplest, circuit boards are two thin layers of copper with some substrate sandwiched in between. PCBs that you make yourself are generally produced either by etching or milling the copper away, to leave traces that function as wires connecting the individual components soldered to the board. This document only describes making single-sided boards. While it's possible to make a PCB with more than one layer using the milling process, it probably makes more sense to have it produced by a PCB fab.

Pours or Ground Pours
: A pour is an area of copper on the board that is a part of your circuit. A typical use of a pour is to serve as the ground for your circuit. Any component lead that needs to connect to ground might connect directly to this copper area instead of a specific trace that leads to ground. Since soldering to pours can be difficult (as the copper steals heat away from the joint), it is common to have extremely short traces that connect a pad to the surrounding pour. These are called "thermals."

PTH
: PTH or TH describes "through-hole" devices. These components are installed on the top of your PCB, with their leads poking through holes in the board. The leads are then soldered to pads on the *bottom* of the board.

SMD
: Surface Mount Device. An SMD component is soldered to the top of your PCB and doesn't require any drilled holes through to the bottom side.

Traces
: The copper "wires" on the PCB that make the necessary electrical connections for your circuit. Like wire thickness, the width of a trace is directly related to how much current it can carry. *Also known as "routes" or "tracks"*

Vias
: Vias are holes in a PCB that are plated with copper. They serve as a pathway for electricity from one layer of a PCB to another. We cannot create vias when milling a PCB.
