%% Delete or send to backlog, this is just a general scope based on basic research. *most will not be touched.* %%


- C programming
- Linux Terminal
	- arch install?
- personal website


# I don't even know what this is
### idk what this is
- Write code without libraries — configure a GPIO pin by writing to registers directly using the datasheet 
	- Stop when: You've blinked an LED, read a button, and sent text over UART 
- Learn SPI, I2C, UART by actually wiring up sensors and displays Read datasheets for the chips you're connecting
	- Use an oscilloscope or logic analyzer to see the signals 
	- Stop when: You can connect an unfamiliar sensor, read its datasheet, and get data out of it
- Build something with a purpose — a data logger, a motor controller, a wireless sensor node
	- Stop When: it works usually
- Learn FreeRTOS basics: tasks, queues, semaphores
	- Learn basic firmware architecture (separating hardware drivers from application logic)
	- Stop when: You can structure a multi-task firmware project cleanly

### SoC prototype Multi-Project 
***GOAL:***
*I designed a retro-style personal computer from scratch — custom instruction set, 5-stage RTL pipeline in SystemVerilog, full SoC with VGA, UART, SPI, and SD card, verified with a UVM environment wired to a C gold model, then pushed the whole thing through an RTL-to-GDSII flow to a DRC/LVS-clean layout on Sky130. It boots a custom Linux distro and runs games. The GDSII is on my GitHub."*

**Phase 0: Learn Basics**

- Nand2tetris
- Python/C basics
- Super Starter kit for UNO R3
- Semiconductor Fundamentals** (part 1) (Energy Bands/Doping)
---
 **Phase 1: Architectural Specification & ISA** 

Before touching RTL, you must define the "contract" between your hardware and software.

- **Define ISA Manual:** Document your registers, instruction formats (R-type, I-type, etc.), and opcode map.
    
- **Software Toolchain:** Build a basic assembler (Python is fine) that converts your custom assembly mnemonics into machine code binaries.
    
- **Architectural Gold Model:** (Optional but pro) Write a simple C or Python simulator that executes your ISA. This acts as your "truth" for verification.
**Semiconductor Fundamentals** (part 2) (Energy Bands/Doping)
Learn industry EDA tools

---
**Phase 2: RTL Design (The Core)** 

This is where you build the "brain" of the computer.

- **5-Stage Pipeline Implementation:** Code the Fetch, Decode, Execute, Memory, and Writeback stages in Verilog/SystemVerilog.
    
- **Hazard Unit:** Implement forwarding logic to handle data hazards and stalling logic for load-use cases.
    
- **Branch Handling:** Implement a branch comparator in the Decode or Execute stage and handle pipeline flushes.
    
- **Memory Interface:** Design a basic Load/Store unit that interfaces with instruction and data caches (or tightly coupled memories).
- **Scan chain**: `scan_en` input, a mux on every flip-flop's data path, and proper chain ordering. DFM / DFT constraints

---
**Phase 3: SoC Integration & Peripherals** 

Moving from a CPU to a functional Computer.

- **System Bus:** Create a simple bus (like AHB-Lite or a custom Wishbone bus) to connect the CPU to peripherals.
    
- **VGA Controller:** Design the logic to generate H-Sync, V-Sync, and RGB signals from a frame buffer.
    
- **I/O Controllers:** Implement the UART (serial comms), Keyboard (PS/2 or HID), and a simple SPI/SD-Card controller for storage.
    
- **Memory Mapping:** Define the address space (e.g., `0x0000` is RAM, `0x8000` is VGA, `0x9000` is UART).
**MOSFET Physics** (IV Curves, Threshold Voltage)
    

---
 **Phase 4: Verification** 

- **Unit Testbenches:** Create individual testbenches for the ALU, Decoder, and Memory Controller.
    
- **Integration Tests:** Run "Assembly Torture Tests" (small programs designed to trigger hazards) on the full CPU.
    
- **FPGA Prototyping:** Synthesize and flash to your FPGA board. Verify that your code actually prints to a screen or responds to a keyboard.
    **Nanoscale Effects** (Tunneling, Leakage at 2nm)

---

**Phase 5: The "Tape-Out" Path (OpenLane/Silicon)** 

- [ ] **Constraint Definition:** Write a basic SDC (Synopsys Design Constraints) file defining your clock frequency (e.g., `create_clock -name clk -period 20`).
    
- [ ] **Synthesis (Yosys):** Convert your RTL into a gate-level netlist using the Sky130 cells.
    
- [ ] **Floorplanning:** Define the chip size and place the I/O pins (where the VGA/UART wires connect to the silicon).
    
- [ ] **Placement & Routing:** Run the automated flow to place 2 WEEKScells and route the copper wires.
    
- [ ] **DRC/LVS Checks:** Run Design Rule Checks (physics) and Layout vs. Schematic (logic) to ensure the chip is manufacturable.
    **Advanced Nodes** (FinFET vs. Nanosheet architecture)

---
**Phase 6: Documentation & Portfolio**

- [ ] **The "Beauty Shot":** Generate the GDSII layout view (the "rainbow" transistor map) and put it on your GitHub README.
    
- [ ] **The Performance Spec:** Document your Max Frequency (Fmax​), Total Area (mm2), and Power consumption (estimated).
    
- [ ] **Demo Video:** Record a video of the FPGA board running your custom assembly software (e.g., a simple game or text editor).
- [ ] per-corner STA table

--- 
Extra Credit:

**Verification**


**1. ALU testbench (start here)**

Simplest DUT with the richest existing gold model (your Phase 1 C simulator). Add a sequence item, driver, monitor, and scoreboard. Wire the scoreboard to your C model via DPI-C. Every opcode is auto-checked. This is the canonical UVM entry point.


**2. UART agent (highest industry relevance)**

UART is a standard protocol — an agent you write here is directly reusable on any SoC project. Constrained-random byte stimulus, parity error injection, framing error detection. This is exactly the "build a UVM environment for SPI or I2C" exercise that Berkeley and CMU recommend for portfolios.


**3. CPU pipeline integration test (hardest, most impressive)**

A hazard sequence that systematically exercises every forwarding path and flush scenario, paired with a scoreboard that compares the register file state after each instruction against your gold model. The functional coverage report showing 100% hazard-type coverage is what converts this from "I wrote tests" to "I verified the design."


**Analog/mixed signal**

**Start: add a Verilog-AMS PLL model to your clock architecture**

Drop a behavioral PLL into your SoC clock tree. Document the VCO frequency, divide ratio, and lock time. This requires no schematic work but gives you Verilog-AMS experience and forces you to write a jitter specification — a real AMS design skill.

**Add: R-2R DAC on VGA or audio output pin**

Your VGA controller already drives digital color signals. Add an R-2R resistor ladder schematic (Xschem) for one color channel. Simulate the output voltage swing in ngspice. Now you have a real analog output with a simulation trace you can include in your portfolio.

**Build: Sky130 bandgap reference in Xschem + Magic**

Use Sky130's native NPN BJTs (sky130_fd_pr__npn_05v5_W1p00L1p00). Design the PTAT + CTAT summation network in Xschem, simulate with ngspice across TT/FF/SS corners, then lay it out in Magic. Run DRC and LVS. This is a self-contained mixed-signal block you can instantiate as a hard macro in OpenLane.

**Stretch: 6-bit SAR ADC — comparator + DAC + RTL control**

Split the design: RTL SAR controller in SystemVerilog (fits naturally into your existing flow), analog comparator in Sky130 transistors (Xschem), R-2R DAC as a schematic. Connect them via a Verilog-AMS boundary. This is exactly the mixed-signal design split that industry SoC teams use — and what Stanford EE272 teaches at the graduate level.




### End
