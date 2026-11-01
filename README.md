# 5v-to-3v3-regulator-board
my first PCB design


# 5 V to 3.3 V Regulator Board

My first PCB design, made in Altium Designer. It's a small board that takes 5 V in and gives 3.3 V out using a low-dropout (LDO) regulator.


## About this project

I'm a Computer Engineering student, and this is the first board I've taken from a blank schematic all the way to a routed layout. I picked a simple power circuit on purpose so I could focus on learning the Altium workflow instead of fighting a complicated design.

3.3 V is a common supply voltage for microcontrollers and sensors, while many power sources (like USB) provide 5 V. A regulator board like this is a small building block I can reuse in bigger projects.

## The circuit

| Part | Value / Model | Purpose |
|------|---------------|---------|
| U1 | MIC5317-3.3YM5-TR | 3.3 V LDO regulator |
| C1 | 1 µF | Input capacitor, steadies the 5 V going into the regulator |
| C2 | 1 µF | Output capacitor, steadies the 3.3 V coming out |
| J1 | SM02B-GHS-TB (JST GH) | 5 V input connector |
| J2 | SM02B-GHS-TB (JST GH) | 3.3 V output connector |

**Connections**
- J1 pin 1 is +5 V and pin 2 is GND. J2 pin 1 is +3.3 V and pin 2 is GND.
- The EN (enable) pin is tied to VIN, so the regulator is always on when 5 V is present.
- The NC pin is not connected to anything, so I marked it with a No ERC flag.
- The MNT pins on each connector are mounting pads, not electrical connections.

## Design choices

- **LDO instead of a switching regulator:** An LDO needs very few external parts, which made it a good first design.
- **1 µF capacitors on both sides:** I used the values recommended in the regulator's datasheet. Reading the datasheet to choose them was one of the most useful parts of the project.
- **Capacitors close to the regulator:** I placed C1 and C2 right next to U1 so the connections between them are short.
- **JST GH connectors:** They're compact and easy to wire into other projects.


## What I learned

- **Annotation matters.** My first validation failed with duplicate designator errors because every capacitor was still named `C?`. Annotating the schematic fixed it, and now I understand what those compiler messages mean.
- **Footprints have to match real parts.** I checked connector orientation and spacing in the 3D view.
- **Placement affects routing.** Putting parts in a sensible order first made the traces much easier to route.
- **A schematic needs a finished title block** with a title, revision, and author to look complete.

## What I want to learn next

- Running and understanding design rule checks (DRC) in more depth
- Choosing trace widths based on current
- Ordering a board and testing it on the bench
- Designing a board with a microcontroller

## Repository contents

```
├── README.md
├── altium/      Altium project, schematic, and PCB files
├── images/      Schematic, layout, and 3D screenshots
└── outputs/     Optional exports such as a schematic PDF
```

To open the design, download the `altium` folder and open the `.PrjPcb` file in Altium Designer.

## Tools

- Altium Designer

## Author

Aloniab Negash, Computer Engineering
