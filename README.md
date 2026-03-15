## Hardware Specifications & Bill of Materials (BOM)
*** Sry this board is still in production but I'll reship it once it's delivered!!!

This project is inspired by Hyperspace Pirate: https://youtu.be/X31B1pVow1o?si=pDOqtu37fK6EBQ2z

<img width="1920" height="1080" alt="cpu" src="https://github.com/user-attachments/assets/85bccea8-594a-406f-a8d3-cba3b08d6690" />
This DIY 4-but CPU uses BJT logic to build various logic gates, while using discrete NPN transistors as saturated switches

| Component Class | Specification / Part Number | Function |
| --- | --- | --- |
| **Active Switching** | 2N3904 (NPN BJT) | Core logic gates (amplification and switching) |
| **Passive Routing** | Standard Rectifier Diodes | Signal isolation and OR-tie routing |
| **Pull-up/Pull-down** | 10kΩ Resistors | Ensuring definitive HIGH/LOW logic states |
| **Base Biasing** | 4.7kΩ Resistors | Base current limiting to prevent thermal runaway |
| **Current Limiting** | 1kΩ Resistors | Collector current limiting |

---

## Schematic & Architectural Design

The architecture has both **SUM** and **CARRY (Cout)** logic using fundamental logic gates built from scratch
<img width="997" height="965" alt="adder" src="https://github.com/user-attachments/assets/a00223e5-2a39-4aae-9def-56aeb554a02e" />

### Logic Gate Topologies

The computational core relies on three primary gate topologies designed from discrete NPN transistors:

1. **NAND Gate:** Series-connected BJTs requiring all inputs to be HIGH to pull the output LOW
2. **NOR Gate:** Parallel-connected BJTs where any HIGH input pulls the output LOW
3. **XOR Gate:** A composite gate critical for the SUM generation

*Gate Implementation Reference:*

* [XOR Gate Schematic](https://github.com/user-attachments/assets/9e057bf3-4b33-4ee1-a783-3fd075c37234)
* [NOR Gate Schematic](https://github.com/user-attachments/assets/835cebbe-9da9-4931-9af1-0fc856e21aca)
* [NAND Gate Schematic](https://github.com/user-attachments/assets/38a2fae2-0add-45c0-82a7-d2f594ea8222)

---

## Validation Using Truth Table

The circuit has been validated against the standard 1-bit full adder truth table, successfully transitioning between all 8 states cleanly:

| Input A | Input B | Carry In (Cin) | SUM Output | Carry Out (Cout) |
| --- | --- | --- | --- | --- |
| 0 | 0 | 0 | **0** | **0** |
| 0 | 0 | 1 | **1** | **0** |
| 0 | 1 | 0 | **1** | **0** |
| 0 | 1 | 1 | **0** | **1** |
| 1 | 0 | 0 | **1** | **0** |
| 1 | 0 | 1 | **0** | **1** |
| 1 | 1 | 0 | **0** | **1** |
| 1 | 1 | 1 | **1** | **1** |

---

## Technical Challenges

To build this, I was forced to learn many things that I hadn't even seen before, such as truth table and logic gates. Truth table is the foundation of computing logic, while logic gates are the way to implement the the logic

* **Fan-Out Limitations & Signal Integrity:** Driving multiple inputs from a single output stage caused severe voltage drops. This required very careful pull-up and base resistor values to ensure subsequent transistor stages have adequate saturation current without dragging the logic HIGH state into the regions that should be low
* **XOR Current Starvation:** The initial Exclusive-OR (XOR) architecture failed due to a topology that tried to drive two separate transistor bases from a single unbuffered node. And this caused current to split in two parallel streams, preventing either transistor from fully switching
