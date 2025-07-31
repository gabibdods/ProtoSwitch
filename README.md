# ProtoSwitch

# FPGA-Based System-on-Chip Projects

### Description

- This project collection showcases advanced FPGA designs for high-performance, real-time, and embedded systems using VHDL
- Each subproject explores a different domain: CPU design, high-speed memory, PCIe interfacing, video pipelines, neural network acceleration, ADC front-ends, and Ethernet switches

---

## NOTICE

- Please read through this `README.md` to better understand the project's source code and setup instructions
- Also, make sure to review the contents of the `License/` directory
- Your attention to these details is appreciated — enjoy exploring the project!

---

## Problem Statement

- Modern embedded and high-performance systems require custom SoCs and accelerators that meet strict performance, bandwidth, and real-time constraints
- Off-the-shelf microcontrollers or general-purpose processors often fall short in flexibility and timing
- FPGA-based systems fill this gap

---

## Project Goals

### Develop Reusable FPGA SoC IP Blocks

- Useful for networking, signal processing, AI training, etc.

### Build Expertise Across Hardware and Firmware Layers

- Gain hands-on experience integrating logic, memory, and peripherals in cohesive systems

---

## Tools, Materials & Resources

### Toolchain Setup

- Xilinx Vivado, ModelSim/QuestaSim, SymbiYosys, GTKWave

### Toolchain Setup

- FPGA development boards with DDR3/DDR4, SFP/SFP+ cages, HDMI interfaces, and high-speed ADCs

### Reference Standards and Documentation

- RISC-V ISA specs, AMBA AHB/Wishbone documentation, Ethernet/PCIe standards

---

## Design Decision

### Prioritize Predictable Hardware Behavior

- Use of VHDL for strict hardware determinism, clarity, and toolchain compatibility

### Use Bus-Centric Interconnects for Scalability

- All systems are built around bus-centric architectures (AHB, AXI, Wishbone) for extensibility

### Validate with Simulation Before Synthesis

- Testbenches and formal checks before any synthesis

---

## Features

### Fully Custom RISC-V SoC Architecture

- Custom RV32IM pipelined CPU with CSR, ALU, decoder, and memory controller

### High-Speed Memory Integration

- DDR3/DDR4 controller with PHY calibration, burst scheduling, and memory-mapped I/O

### Peripheral and Accelerator IP Blocks

- PCIe Gen2 x1 DMA engine, RT video processor pipeline, CNN accelerator, and 10G switch fabric

---

## Block Diagram

```plaintext
                                  ┌───────────────────────────┐
                                  │        Peripherals        │
                                  │ UART │ SPI │ GPIO │ HDMI  │
                                  └──────────┬────────────────┘
                                             ↓
                                  ┌──────────┴──────────┐
                                  │ Memory Subsystem    │
                                  │  DDR3 / DDR4 Ctrl   │
                                  └──────────┬──────────┘
                                             ↓
                                  ┌──────────┴──────────┐
                                  │   RISC-V CPU Core   │
                                  │ ALU │ REG │ CSR │ PC│
                                  └──────────┬──────────┘
                                             ↓
                                  ┌──────────┴──────────┐
                                  │ Bus Fabric (AHB/WB) │
                                  └──────────┬──────────┘
                                             ↓
                                  ┌──────────┴──────────┐
                                  │    FPGA I/O + PHYs  │
                                  │ SGMII │ PCIe │ ADC  │
                                  └─────────────────────┘

```

---

## Functional Overview

- This project ecosystem is composed of multiple standalone subprojects that implement high-performance digital systems with reusable and parameterized VHDL modules
- Every block includes testbenches, simulation results, and constraints for real-world synthesis and deployment

---

## Challenges & Solutions

### Timing Closure for High-Speed PHYs

- Used IDELAY/ODDR primitives, phase-aligned constraints, and post-route timing reports to guarantee robust PHY behavior

### Formal Verification of Control Logic

- Applied SymbiYosys to prove liveness/safety properties on finite state machines and memory controllers

---

## Lessons Learned

### High-Speed Design Requires System-Level Thinking

- It demands PCB design, power integrity, and low-jitter clock architecture

### Reusability Depends on Modularity and Interface Contracts

- Modularization and interface standardization are critical to scaling FPGA projects across domains

---

## Project Structure

```plaintext
root/
├── License/
│   ├── LICENSE.md
│   │
│   └── NOTICE.md
│
├── .gitattributes
│
├── .gitignore
│
└── README.md

```

---

## Future Enhancements

- Integrate NoC architecture for better scalability between components
- Add AXI4-Lite interfaces and support for standard IP integration
- Develop custom logic analyzer IP with AXI-stream output
- Expand to multi-core RISC-V with shared cache and interconnect
- Implement a web-based waveform viewer for post-simulation analysis
