# Build your own LumeAir

A LumeAir is a small circuit board with a Sensirion SEN66 air-quality
sensor, a Bosch BMP581 barometer and a Seeed Studio XIAO ESP32-S3, in a
3D-printed case. It measures CO₂, particles (PM1.0 to PM10), VOC and NOx
indexes, temperature, humidity and pressure, and works with the LumeAir Home
app and Home Assistant.

This guide takes you from parts to a working sensor. Soldering the board
yourself takes surface-mount experience (one part is a tiny LGA chip), so
you can also [buy a ready-made board](#buy-one-ready-made) and only print
and assemble the case.

All the design files are in the
[lumeair-hardware](https://github.com/KyleBcine/lumeair-hardware)
repository, under the
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
license: build and share them for non-commercial use.

**Downloads** (board revision 1.0, case version 5.3):
[Gerbers](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-gerbers.zip) ·
[Parts list (BOM)](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-BOM.zip) ·
[Case (STL)](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-case-STL.zip)

## 1. What you need

### Parts on the board

| Qty | Part | Value | LCSC |
|---|---|---|---|
| 1 | Seeed Studio XIAO ESP32-S3, the **standard** model (not Sense or Plus) | | |
| 1 | Bosch BMP581 barometer (U2) | | C5362283 |
| 1 | TI TLV75533PDBVR 3.3 V regulator (U1) | | C404027 |
| 1 | JST SM06B-GHS-TB connector, for the SEN66 (CN1) | | C133065 |
| 1 | Capacitor, 0603 (C1) | 100 nF | C1591 |
| 2 | Capacitor, 0603 (C9, C13) | 100 nF | C45000 |
| 1 | Capacitor, 1206 (C2) | 22 µF | C12891 |
| 2 | Capacitor, 0805 (C4, C5) | 10 µF | C15850 |
| 1 | Tantalum capacitor (C3) | 100 µF | C116740 |
| 2 | Resistor, 0603 (R1, R2) | 4.7 kΩ | C99782 |

The full list, with manufacturer part numbers, is
[BOM.csv](https://github.com/KyleBcine/lumeair-hardware/blob/main/pcb/rev-1.0/BOM.csv).

### Everything else

| Qty | Part | Notes |
|---|---|---|
| 1 | Sensirion SEN66 | The air-quality sensor |
| 1 | JST GH 1.25 mm pitch, 6-pin cable, 100 mm | SEN66 to the board, e.g. [Adafruit 5754](https://www.adafruit.com/product/5754) |
| 4 | M3 × 40 mm countersunk socket-head screws | Close the case |
| 2 | M2 × 4 mm screws | Hold the board |
| 1 | USB-C power supply and cable | Any USB phone charger, 5 V, 1 A or more |
| | PLA filament | For the case |

### Tools

A fine-tipped soldering iron, solder paste and a way to reflow it (a hot
plate, reflow oven or hot-air station), flux, tweezers, a 3D printer, and a
computer with Chrome or Edge to install the firmware.

## 2. Get a board

### Buy one ready-made

Ready-made boards are coming soon, for **$40**. Email
[lumeair.home@gmail.com](mailto:lumeair.home@gmail.com?subject=Ready-made%20LumeAir%20board)
to be told when they're available.

With a ready-made board, you can skip to [step 4](#4-print-the-case).

### Or order the bare board and solder it

Upload the Gerber zip to a board maker such as JLCPCB or PCBWay. It's a
two-layer board.

- **Board settings:** the board maker's defaults are fine.
- **Stencil:** order a stencil with the board. It makes the BMP581 far
  easier to solder.

## 3. Solder the board

The order isn't critical. Working from the smallest parts to the largest is
easiest:

1. **The BMP581** (U2): it's a 2 × 2 mm LGA chip with its pads underneath,
   so spread solder paste through the stencil and reflow it (or use hot
   air). Mind its orientation mark.
2. **The resistors and small capacitors** (R1, R2, C1, C9, C13), then the
   larger capacitors (C4, C5, C2, and the tantalum C3, whose stripe marks
   the + side) and the regulator (U1).
3. **The SEN66 connector** (CN1).
4. **The XIAO ESP32-S3**, soldered flat by its edge pads.
5. **Check** for bridges under a magnifier, especially on the BMP581.

## 4. Print the case

Print **Base**, **MidPlate** and **Shell** from the STL zip in PLA, with your
slicer's standard PLA settings. The STEP files in the repository let you
change the parts in CAD.

## 5. Put it together

1. **Attach the antenna** that comes with the XIAO to its U.FL socket.
   Without it, Wi-Fi barely works.
2. **Screw the board onto the MidPlate** with the two M2 × 4 mm screws.
3. **Place the SEN66** so its air inlet lines up with the intake vents on
   the case.
4. **Connect the SEN66** to the board with the JST GH cable.
5. **Close the case:** screw the Base to the Shell with the four M3 × 40 mm
   countersunk screws.

## 6. Install the firmware

Plug the XIAO into your computer with a USB-C data cable, then press the
button. It works in **Chrome or Edge on a computer**: Safari, Firefox and
phones can't reach USB devices from a web page.

<esp-web-install-button manifest="firmware/flasher.json">
  <span slot="unsupported"><strong>The Install firmware button needs Chrome or Edge on a computer.</strong> It's on the published guide, <a href="https://kylebcine.github.io/lumeair-site/Build">kylebcine.github.io/lumeair-site/Build</a>.</span>
</esp-web-install-button>

1. Press **Connect**, pick the XIAO from the list (it shows as a USB serial
   or JTAG device), then **Install LumeAir**.
2. For a first install, choose to **erase** the board. It takes a minute or
   two.
3. When it's done, unplug the XIAO and plug it back in.

**The XIAO isn't in the list?** Hold its **BOOT** button (marked **B**)
while you plug it in, release it, then press Connect again. Try another
cable too: some USB-C cables only carry power.

The button installs the latest release. After that the sensor updates
itself: the app offers each new version. The installer runs in your
browser, loaded from unpkg.com; nothing about your board is sent to
LumeAir.

## 7. Set it up

Power the sensor, open **LumeAir Home** on your phone and choose
**Set up a new sensor**. The app finds it over Bluetooth as
**LumeAir-XXXXXX** and connects it to your Wi-Fi.

Readings start within seconds. The VOC and NOx indexes take a few hours to
learn the room. For anything that doesn't work, see [Support](Support.md).
