# RSLogix 500 — PLC Control

This folder contains the PLC program for the automated mixing, filling, capping and packaging line.

## Project File

```text
mixing_process_control.RSS
```

---

## I/O Configuration

The simulated PLC configuration includes:

- 8 digital inputs
- 8 digital outputs

<p align="center">
  <img src="../assets/plc/plc_io_configuration.png" width="750">
</p>

---

## Ladder Logic

The PLC program coordinates the complete production sequence using ladder logic.

```mermaid
flowchart LR
    A["Start / Acknowledge"]
    B["Mixing"]
    C["Transfer"]
    D["Bottle Filling"]
    E["Capping"]
    F["Packaging"]
    G["Carton Output"]

    A --> B --> C --> D --> E --> F --> G
```

The control logic uses:

- internal relays,
- timers,
- sequence conditions,
- actuator control,
- start / stop logic,
- acknowledgement logic,
- controlled reset behavior.

<p align="center">
  <img src="../assets/plc/plc_ladder_sequence.png" width="850">
</p>

---

## Timing Logic

Multiple timers are used to coordinate:

- bottle movement,
- carton movement,
- pneumatic cylinders,
- filling duration,
- sequential process operations.

The sequence prevents conflicting actuator commands by requiring the previous state to be confirmed before progressing.

---

## Simulation

The project was tested with **RSLogix Emulate 500**.

<p align="center">
  <img src="../assets/plc/rslogix_emulate500_simulation.png" width="750">
</p>

This allows the PLC logic to be validated without requiring a physical controller.

---

## Communication

RSLinx provides the communication layer between the virtual PLC and RSView32.

<p align="center">
  <img src="../assets/plc/rslinx_emulator_driver.png" width="700">
</p>
