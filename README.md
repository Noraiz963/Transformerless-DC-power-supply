# Transformerless DC Power Supply

A capacitor-dropper based transformerless power supply designed in KiCad, converting AC mains input into a regulated 5V DC output without using a bulky step-down transformer.

## Circuit Overview

The design is broken into functional stages:

1. **AC voltage dropping (capacitive dropper)**: R1 (1MΩ bleeder) and C1 (2.2µF) drop the AC line voltage without a transformer, relying on the capacitor's reactance rather than resistive dissipation to minimize heat loss.
2. **AC to pulsating DC**: Full-wave bridge rectifier using 4x 1N4007 diodes (D1–D4).
3. **Filtering**: C2 (0.1µF) and C3 (1000µF) smooth the rectified output into a steadier DC level.
4. **Voltage fixing (zener clamp)**: Zener diodes D8 and D9 with R2 and R3 (20kΩ) pre-regulate the voltage before the linear regulator stage.
5. **Voltage regulation**: LM7805 (U2) fixed 5V linear regulator, producing a clean, stable 5V output.
6. **Indicator**: LED (D7) with 2.2kΩ resistor (R4) shows when the supply is powered.
7. **Noise filtering**: 470µF output capacitor (C4) to reduce ripple/noise on the final DC output.
8. **Connectors**: 3.5mm connectors for AC input (J1) and DC output (J2).

## Schematic

![Schematic]([images/schematic.png](https://github.com/Noraiz963/Transformerless-DC-power-supply/blob/41bb1f8103dfd90d45387547d027a9882517e033/Screenshot%202026-07-20%20193404.png))

## PCB Layout

![PCB Layout]([images/pcb_layout.png](https://github.com/Noraiz963/Transformerless-DC-power-supply/blob/41bb1f8103dfd90d45387547d027a9882517e033/Screenshot%202026-07-20%20193431.png))

## 3D Render

![3D Render]([images/3d_render.png](https://github.com/Noraiz963/Transformerless-DC-power-supply/blob/41bb1f8103dfd90d45387547d027a9882517e033/Screenshot%202026-07-20%20193452.png))

## Bill of Materials

| Ref | Component | Value |
|-----|-----------|-------|
| R1 | Resistor | 1MΩ |
| C1 | Capacitor (dropper) | 2.2µF |
| D1–D4 | Diode | 1N4007 |
| C2 | Capacitor | 0.1µF |
| C3 | Electrolytic Capacitor | 1000µF |
| D8, D9 | Zener Diode | — |
| R2, R3 | Resistor | 20kΩ |
| R4 | Resistor | 2.2kΩ |
| D7 | LED | Power indicator |
| U2 | Voltage Regulator | LM7805 (TO-220) |
| C4 | Electrolytic Capacitor | 470µF |
| J1 | Connector (3.5mm) | AC Input |
| J2 | Connector (3.5mm) | DC Output |

## Tools Used

- KiCad 10.0 (schematic capture, PCB layout, 3D visualization)

## Status

Completed — second PCB design project, building on the AC to DC converter project with a full regulated, transformerless supply design.

## ⚠️ Safety Note

This is a **transformerless design**, meaning the circuit has a direct (non-isolated) electrical connection to the AC mains line. This is a well-known technique in low-power electronics but carries real shock hazard risk since there is no galvanic isolation from mains voltage. This project was built for learning purposes on the KiCad design workflow (schematic capture, ERC, PCB layout, DRC) — exercise caution and follow proper safety practices (fusing, enclosure, isolation) before powering or handling any physically built version of this circuit.
