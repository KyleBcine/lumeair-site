# Build your own LumeAir

<p class="gh-only">You're reading the source of this page on GitHub. <a href="https://kylebcine.github.io/lumeair-site/Build"><strong>Open it on the LumeAir website</strong></a> for the working Install firmware button.</p>

This guide takes you from a pile of parts to a working LumeAir sensor.

A LumeAir is a small circuit board carrying a Seeed Studio XIAO ESP32-S3, a Sensirion SEN66 air-quality sensor and a Bosch BMP581 barometer, all inside a 3D-printed case. It measures CO₂, particles (PM1.0 to PM10), VOC and NOx indexes, temperature, humidity and pressure, and works with the LumeAir Home app and Home Assistant.

> **Two ways to build one.** Soldering the board yourself takes surface-mount experience: one part is a tiny LGA chip. If that's not for you, [buy a ready-made board](#buy-one-ready-made) and just print and assemble the case.
>
> **Either way, buy a Sensirion SEN66 separately.** It's the air-quality sensor itself, and it doesn't come with the board.

**Downloads** (board revision 1.0, case version 5.3):
[Gerbers](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-gerbers.zip) ·
[Parts list (BOM)](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-BOM.zip) ·
[Case (STL)](https://github.com/KyleBcine/lumeair-hardware/releases/latest/download/LumeAir-case-STL.zip)

All the design files live in the [lumeair-hardware](https://github.com/KyleBcine/lumeair-hardware) repository, under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license: you're welcome to build and share them for non-commercial use.

**The steps:**
[1. What you need](#1-what-you-need) ·
[2. Get a board](#2-get-a-board) ·
[3. Solder the board](#3-solder-the-board) ·
[4. Print the case](#4-print-the-case) ·
[5. Put it together](#5-put-it-together) ·
[6. Install the firmware](#6-install-the-firmware) ·
[7. Set it up](#7-set-it-up)

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

For manufacturer part numbers, see the full
[BOM.csv](https://github.com/KyleBcine/lumeair-hardware/blob/main/pcb/rev-1.0/BOM.csv).

### Everything else

| Qty | Part | Notes |
|---|---|---|
| 1 | Sensirion SEN66 | The air-quality sensor |
| 1 | JST GH 1.25 mm pitch, 6-pin cable, 100 mm | Connects the SEN66 to the board, e.g. [Adafruit 5754](https://www.adafruit.com/product/5754) |
| 4 | M3 × 40 mm countersunk socket-head screws | Close the case |
| 2 | M2 × 4 mm screws | Hold the board |
| 1 | USB-C power supply and cable | Any USB phone charger, 5 V, 1 A or more |
| | PLA filament | For the case |

### Tools

- A fine-tipped soldering iron, flux and tweezers
- Solder paste, and a way to reflow it: a hot plate, reflow oven or hot-air station
- A 3D printer
- A computer with Chrome or Edge, to install the firmware

## 2. Get a board

### Buy one ready-made

Ready-made boards are coming soon, for **$40**. To hear when they're available, email
[lumeair.home@gmail.com](mailto:lumeair.home@gmail.com?subject=Ready-made%20LumeAir%20board).

The SEN66 isn't included, so buy it separately. With a ready-made board, skip ahead to [step 4](#4-print-the-case).

### Or order the bare board and solder it

Upload the Gerber zip to a board maker such as JLCPCB or PCBWay. It's a two-layer board.

- **Board settings:** the board maker's defaults are fine.
- **Stencil:** order one with the board. It makes the BMP581 far easier to solder.

## 3. Solder the board

The order isn't critical, but working from the smallest parts to the largest is easiest.

1. **The BMP581 (U2).** It's a 2 × 2 mm LGA chip with its pads underneath, so spread solder paste through the stencil and reflow it, or use hot air. Mind its orientation mark.
2. **The resistors and small capacitors** (R1, R2, C1, C9, C13).
3. **The larger capacitors and the regulator:** C4, C5 and C2, the tantalum C3 (its stripe marks the + side), then U1.
4. **The SEN66 connector** (CN1).
5. **The XIAO ESP32-S3,** soldered flat by its edge pads.
6. **Check your work** under a magnifier for solder bridges, especially around the BMP581.

## 4. Print the case

Print the **Base**, **MidPlate** and **Shell** from the STL zip in PLA, using your slicer's standard PLA settings.

Want to change the design? The STEP files in the [lumeair-hardware](https://github.com/KyleBcine/lumeair-hardware) repository open in CAD.

## 5. Put it together

1. **Attach the antenna** that comes with the XIAO to its U.FL socket. Without it, Wi-Fi barely works.
2. **Screw the board onto the MidPlate** with the two M2 × 4 mm screws.
3. **Place the SEN66** so its air inlet lines up with the intake vents on the case.
4. **Connect the SEN66** to the board with the JST GH cable.
5. **Close the case** by screwing the Base to the Shell with the four M3 × 40 mm countersunk screws.

## 6. Install the firmware

Plug the XIAO into your computer with a USB-C data cable, then press the button below. It works in **Chrome or Edge on a computer**; Safari, Firefox and phones can't reach USB devices from a web page.

<esp-web-install-button manifest="firmware/flasher.json">
  <span slot="unsupported"><strong>The Install firmware button needs Chrome or Edge on a computer.</strong> It's on the published guide, <a href="https://kylebcine.github.io/lumeair-site/Build">kylebcine.github.io/lumeair-site/Build</a>.</span>
</esp-web-install-button>

1. Press **Connect** and pick the XIAO from the list. It shows up as a USB serial or JTAG device.
2. Press **Install LumeAir**.
3. On a first install, choose to **erase** the board. Installing takes a minute or two.
4. When it's done, unplug the XIAO and plug it back in.

> **Don't see the XIAO in the list?** Hold its **BOOT** button (marked **B**) while you plug it in, let go, then press **Connect** again. If that doesn't help, try another cable: some USB-C cables only carry power.

The button installs the latest release. After that, the sensor keeps itself up to date: the app offers each new version.

The installer runs in your browser and is loaded from unpkg.com. Nothing about your board is sent to LumeAir.

## 7. Set it up

1. Plug the sensor into power.
2. Open **LumeAir Home** on your phone and choose **Set up a new sensor**.
3. The app finds the sensor over Bluetooth as **LumeAir-XXXXXX** and connects it to your Wi-Fi.

Readings start within seconds. The VOC and NOx indexes take a few hours to learn the room before they settle.

Something not working? See [Support](Support.md).
