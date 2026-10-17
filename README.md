# Digitally Controlled Interleaved Buck Converter

A two-phase interleaved synchronous buck converter controlled by an STM32G474RET6. The control approach uses state-space Linear Quadratic Regulator (LQR) feedback.

<img height="350" alt="Top view of the 2Phase SynchBuck board" src="https://github.com/Natchpai/LQRx_InterleavedBuck/blob/main/documents/Images/Render-Board/2Phase_SynchBuck_Topview_v1-1(Large).png" />

<img height="350" alt="Top view of the 2Phase SynchBuck board" src="https://github.com/Natchpai/LQRx_InterleavedBuck/blob/main/documents/Images/Render-Board/2Phase_SynchBuck_Bottomview_v1-1(Large).png" />


## Key Features

- Two interleaved phases, with 180° phase shift.
- State feedback with integral action and delay compensation.
- 200 kHz switching frequency per phase, with a 400 kHz equivalent ripple frequency.

## Specifications

| Parameter | Specification |
| --- | --- |
| Input voltage | 24 VDC nominal, 28 V maximum |
| Output voltage | 12 VDC nominal; the reference voltage can be changed |
| Maximum load current | 20 A total, 10 A per phase |
| Output power | 200 W+ continuous rating |
| Switching frequency | 200 kHz per phase |
| Equivalent ripple frequency | 400 kHz with 180° interleaving |
| Controller | STM32G474RET6, state feedback |
| Firmware execution time | Approximately 2.2 µs within a 5 µs timing window |

These values are design specifications. The README does not document measurements or test results.

## Hardware

- High-side MOSFET: OptiMOS-6 BSZ018N04LS6
- Low-side MOSFET: OptiMOS-6 IQE013N04LM6
- Power inductors: 10 µH
- Capacitors: 140 µF

## Control Approach

- Delay compensation models computation and ADC sampling delays in the state vector.
- Integral action adds an error-integral state for output-voltage tracking.
- Anti-windup clamps the integral accumulator at duty-cycle limits.

## Repository Structure

```text
2Phase_SynchBuck/
├── documents/       Supporting images, manufacturing files, schematics, and simulations
├── Library/         KiCad libraries
├── Manufacturing/   Manufacturing files
├── Templates/       Manufacturing templates
├── 2Phase_SynchBuck.kicad_pro
├── 2Phase_SynchBuck.kicad_sch
└── 2Phase_SynchBuck.kicad_pcb
```

## Documentation

- [Assembly drawing](documents/Manufacturing/Assembly/2Phase_SynchBuck-v1.1-24-08-2026__Assembly.pdf)
- [Bill of materials](documents/Manufacturing/bom/BOM_2Phase_SynchBuck_v1.1_2026-09-01.csv)
- [Fabrication outputs](documents/Manufacturing/Fabrication/)
- [Schematic PDF](documents/Schematics/)
- [Simulation files](documents/Simulation/)

## License

Licensed under the [Apache License 2.0](LICENSE).
