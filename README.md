# INFER — Digital Logic Trainer

**INFER** is a browser-based digital logic trainer that behaves like a real bench trainer kit. Place 74xx TTL ICs on virtual breadboards, connect them with colour-coded jumper wires, flip logic switches, and watch LEDs and a BCD 7-segment display react in real time. When your circuit works, generate a **truth table** or a **timing diagram** straight from the live circuit.

It is a single HTML file with no backend, no build step, and no installation. It is built for students and hobbyists learning digital electronics.

> Version 1.0 · Desktop browsers recommended

---

## Table of contents

- [Quick start](#quick-start)
- [Features in detail](#features-in-detail)
- [IC library](#ic-library)
- [Built-in labs](#built-in-labs)
- [Controls and shortcuts](#controls-and-shortcuts)
- [Step-by-step: your first circuit](#step-by-step-your-first-circuit)
- [Saving and loading](#saving-and-loading)
- [Requirements and limitations](#requirements-and-limitations)
- [Tech](#tech)
- [License](#license)
- [Author](#author)

---

## Quick start

**Run locally:** download `index.html` and open it in a modern browser (Chrome, Edge, Firefox, or Safari). An internet connection is needed on first load for Tailwind CSS and Google Fonts.

Then click **Get Started** on the splash screen (or press Enter).

---

## Features in detail

### Virtual hardware

- **Dual breadboards.** Two full breadboards with power rails, so you can build larger circuits and link boards with jumpers.
- **Power supply.** A regulated **+5V / GND** supply with a main power switch. Turning power off plays a rail-discharge animation, and all IC outputs, LEDs, and the 7-segment display go dark, just like cutting power on real hardware.
- **Short-circuit protection.** Connecting +5V directly to GND trips the protection, shows a warning, and cuts power until you remove the offending wire.
- **Auto-wire rails.** One click connects the power rails on both boards.
- **12 logic input switches (SW11–SW0).** Toggle UP for logic 1 and DOWN for logic 0. Includes an **All LOW** reset button.
- **8 output LEDs (L7–L0).** A lit LED means logic HIGH.
- **BCD 7-segment display.** Four inputs (A=1, B=2, C=4, D=8) drive a display that also shows the hexadecimal value.
- **Clock and pulser.** A manual momentary pulse button, plus automatic clock rates of **1 Hz, 2 Hz, and 5 Hz**. Two clock outputs are provided: **CLK HIGH** (the clock or pulser output) and **CLK LOW** (a constant logic-low connection).
- **Logic probe.** Touch any node to see whether it is HIGH, LOW, or floating, and highlight every point on the same net.

### Building and editing

- **Four editing modes:** Wire, Probe, Move, and Delete, switchable with keyboard shortcuts.
- **Colour-coded jumper wires.** Pick from Red, Black, Blue, Green, Yellow, Orange, Purple, or White to keep complex circuits readable.
- **Drag-and-place ICs.** Choose an IC from the library, then place it on a breadboard. The ghost preview shows where it will land.
- **Hover for datasheets.** Hover over an IC in the library to see its pinout.
- **Live pin inspector.** Click a placed IC to see the live state of every pin, and remove the IC or a selected wire from the inspector.
- **Pin labels overlay.** Toggle pin labels on all placed ICs.
- **Unlimited undo and redo.** Made a mistake? Press `Ctrl+Z`. This also reverses loading a lab or clearing the board.

### Analysis tools

- **Truth table generator.** Select up to 8 input switches and any output LEDs. INFER tests every input combination on your live circuit without disturbing your switch positions. Results can be **copied** to the clipboard or **exported as CSV**. A "clock sequence only" option ignores the switches for clocked circuits.
- **Timing diagram.** Runs 10 clock pulses and plots the clock, every wired switch, and every LED output as waveforms. Edge markers follow the flip-flop type: rising edges for the 7474, falling edges for the 7476.
- **Safety checks.** Truth tables and timing diagrams refuse to run while a +5V–GND short exists, and tell you why.

### Quality of life

- **Dark and light themes.** Your choice is remembered between visits.
- **Lite effects mode.** Turns off glow and blur for smoother performance on older devices. This is also remembered.
- **Save and load circuits** as `.json` files.
- **Splash screen** with an animated intro.

---

## IC library

| Category | ICs |
|---|---|
| **Basic logic gates** | 7400 Quad 2-input NAND · 7402 Quad 2-input NOR · 7404 Hex Inverter (NOT) · 7408 Quad 2-input AND · 7410 Triple 3-input NAND · 7432 Quad 2-input OR · 7486 Quad 2-input XOR |
| **Flip-flops and sequential** | 7474 Dual D Flip-Flop · 7476 Dual JK Flip-Flop |
| **Decoders** | 74138 3-to-8 Line Decoder · 74139 Dual 2-to-4 Line Decoder |
| **Multiplexers** | 74157 Quad 2-to-1 · 74153 Dual 4-to-1 · 74151 8-to-1 |
| **Encoders** | 74148 8-to-3 Priority Encoder · 4-to-2 Priority Encoder |

Each IC must be powered correctly (VCC and GND pins) to work, just like on real hardware. Note that the 7476 uses a different power-pin layout from most 14-pin parts.

---

## Built-in labs

Seven ready-made experiments you can load with one click. Loading a lab replaces the current board, and `Ctrl+Z` brings your previous work back.

1. **Basic Gates** (7408 AND + 7404 NOT)
2. **Half Adder** (7486 XOR + 7408 AND)
3. **Full Adder** (7486 + 7408 + 7432)
4. **NAND SR Latch** (7400)
5. **D Flip-Flop** with active-high SET/RST (7474)
6. **JK Flip-Flop** with active-low SET/RST (7476)
7. **Two-Board Demo** (7408 on board 1 feeding a 7404 on board 2 through a jumper)

---

## Controls and shortcuts

| Action | Shortcut |
|---|---|
| Undo / Redo | `Ctrl+Z` / `Ctrl+Y` |
| Wire mode | `W` |
| Probe mode | `P` |
| Move mode | `M` |
| Delete mode | `D` |
| Cancel the current action | `Esc` |
| Remove the selected wire | `Del` |
| Remove a placed IC | Right-click it |
| Enter the app from the splash screen | `Enter` |

---

## Step-by-step: your first circuit

1. Click **Get Started**.
2. Open the **ICs** tab and choose a **7408 (AND)**, then place it on Breadboard 1.
3. Click **Auto-Wire Rails** to connect the power rails, then wire +5V to the IC's VCC pin and GND to its GND pin.
4. Switch to **Wire** mode (`W`). Connect SW0 and SW1 to the gate's inputs, and its output to LED L0.
5. Turn the main power **ON**.
6. Flip the switches and watch L0 light only when both inputs are 1.
7. Open **Tools → Truth Table**, pick SW0, SW1, and L0, and click **Generate**.

Or skip the setup: open the **Labs** tab and load **Basic Gates**.

---

## Saving and loading

Use **File → Save circuit** to download your work as a `.json` file, and **Open file…** to restore it later. **Clear wires** and **Clear all** are also available there, and both can be undone.

---

## Requirements and limitations

- **Desktop-oriented.** The trainer panel has a fixed 1080px width, so phones and small tablets will scroll sideways.
- **Internet on first load** for Tailwind CSS (CDN) and Google Fonts.
- **Local storage** is used only to remember your theme and Lite-effects preference. Nothing is sent anywhere.
- The simulation is a **logic-level** model of the supported ICs. It does not simulate analog behaviour such as propagation delay or fan-out limits.

---

## Tech

Plain HTML, CSS, and vanilla JavaScript in a single file, styled with [Tailwind CSS](https://tailwindcss.com) (Play CDN). Fonts: Inter, JetBrains Mono, and Bitcount Single from Google Fonts.

---

## License

Copyright © 2026 Md. Tasdiqul Islam. All rights reserved.

The source code is publicly visible for viewing only. You may not copy, modify, host, or redistribute it without written permission. See [LICENSE](LICENSE) for the full terms.

---

## Author

**Md. Tasdiqul Islam**
