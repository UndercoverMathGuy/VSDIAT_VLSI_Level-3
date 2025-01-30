# VSD-IAT VLSI for High School Level 3
## Design Flow
<details>
<summary>Expand or collapse</summary>

### Understanding Embedded Boards and Chip Structure
- In embedded boards, what appears as the chip is actually its package, which acts as a protective layer.  
- The actual silicon chip is placed inside the package, typically at its center.  
- Wire bonding is used to connect the chip to the package, creating electrical pathways.  

### Internal Structure of a Chip  
- Pads facilitate communication between the chip and the external world.  
- The core is the central area within the pads, where digital logic is implemented.  
- The die consists of both the core and pads, serving as the fundamental unit in semiconductor manufacturing.  

### Semiconductor Manufacturing & Foundries  
- Foundries are facilities where semiconductor chips are fabricated.  
- Foundry IPs (Intellectual Properties) are specialized design elements created for a specific manufacturing process.  
- Macros refer to reusable digital logic blocks within a design.  

### Instruction Set Architecture (ISA) & Program Execution  
- A C program targeting specific hardware undergoes multiple processing stages.  
- It is first compiled into assembly language, aligning with a specific ISA (e.g., RISC-V).  
- Assembly code is then translated into machine code (binary format of 0s and 1s).  
- This machine code is executed by hardware following a standard RTL to GDSII flow.  

### Software-Hardware Interaction  
- System software translates application programs into binary instructions.  
- Key system software components include:  
  - Operating System (OS): Generates functional outputs in C, C++, Java, etc.  
  - Compiler: Converts these outputs into architecture-specific instructions.  
  - Assembler: Translates instructions into binary machine code.  
- The final binary code is processed by the hardware for execution.  

### Hardware Design & Implementation  
- Register Transfer Level (RTL): Describes hardware behavior using HDLs (e.g., Verilog, VHDL).  
- Synthesis: Converts RTL into a gate-level netlist composed of standard logic gates.  
- The netlist is fabricated into a physical chip through semiconductor manufacturing. 

### Open-Source ASIC Design & Evolution  
- Key enablers for open-source ASIC development:  
  - RTL designs (digital logic descriptions).  
  - EDA tools (Electronic Design Automation software).  
  - PDK data (Process Design Kits for fabrication).  
- Early IC manufacturing was restricted to a few companies (e.g., Intel, TI).  
- In 1979, Lynn Conway & Carver Mead introduced structured VLSI design, leading to the rise of:  
  - Fabless companies (design-only firms).  
  - Pure play fabs (fabrication-only firms).  
- Process Design Kits (PDKs) provide manufacturing specifications but were historically locked under NDAs.  
- In 2020, Google & SkyWater released the first open-source PDK for the 130nm process.  

### ASIC Design Flow  
- ASIC implementation requires multiple EDA tools and methodologies.  
- ASIC Flow: A software-driven approach integrating various tools to execute design steps.  

### OpenLANE ASIC Design Flow  
- Converts RTL code into GDSII format, required for chip fabrication.  
- Synthesis transforms RTL descriptions into circuits composed of Standard Cell Libraries (SCLs).  
- The result is a Gate-Level Netlist, functionally identical to the RTL.  

### Standard Cells & Their Views  
- Standard cells have regular layouts and multiple representations:  
  - Liberty view: Electrical properties.  
  - HDL model: Behavioral description.  
  - SPICE/CDL views: Circuit-level details.  
  - GDSII view: Detailed physical layout.  
  - LEF view: Abstract representation.  

### Chip & Macro Floor Planning  
- Chip floor planning defines component placement on the chip.  
- Macro floor planning arranges larger blocks (e.g., memory, logic units).  

### Power Planning  
- Uses upper metal layers for power distribution due to lower resistance.  
- Ensures electromigration & IR drop issues are minimized.  

### Placement Process  
- Global placement: Provides approximate locations for components.  
- Detailed placement: Refines positions to ensure legal (non-overlapping) placement.  

### Clock Tree Synthesis (CTS)  
- Distributes the clock signal across the design.  
- Minimizes clock skew (timing variations across the chip).  

### Finalization & Verification  
- Sign-Off Checks ensure design correctness before fabrication:  
  - DRC (Design Rule Checking): Verifies fabrication constraints.  
  - LVS (Layout vs Schematic): Confirms layout matches the netlist.  
  - STA (Static Timing Analysis): Ensures correct timing operation.
</details>

## Section 1

### 1. Initialise OpenLane Flow Docker and Perform Synthesis
```bash

    cd Desktop/work/tools/openlane_working_dir/openlane
    #Opens OpenLane folder

    docker
    #Activates Docker container for OpenLane

    pwd
    #Unlocks Docker container

```
    
```bash

    ./flow.tcl -interactive
    #Activates interactive mode in OpenLane

    package require openlane 0.9
    #Adds the required OpenLane package to run

    prep -design picorv32a
    #Prepares pre-installed picorv32a design and prepares it for synthesis

    run_synthesis
    #Runs the synthesis in interactive mode in OpenLane on pre-prepared design and returns design statistics on completion

    exit

    exit
    #Exits the OpenLane flow and the docker sub-container
```

&nbsp;
### Images of code running

![](sources/image.png)
![](sources/image2.png)
![](sources/image3.png)

&nbsp;

### 2. Completion of Task 1 (Finding of Flop Ratio)
$$
    \text{Flop Ratio} = \frac{\text{Number of D Flip Flops}}{\text{Number of Cells}}
$$
$$
    \text{Flop Ratio Percentage} = \text{Flop Ratio} * 100
$$
### Image of synthesis results
![](sources/image4.png)

### Calculation of Flop Ratio:
$$
    \text{Flop Ratio}=\frac{1613}{14876}=0.1084296853993009
$$
$$
    \text{Flop Ratio percentage}=0.1084296853993009*100=10.84296853993009\%
$$
