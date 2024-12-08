# TABLE OF CONTENTS

-  [Inception of opensource EDA, OpenLANE and Sky130 PDK](#Inception-of-opensource-EDA,-OpenLANE-and-Sky130-PDK)

# Inception of opensource EDA, OpenLANE and Sky130 PDK

# Open source digital asic design flow:
- Open-source ASIC design flows have gained significant traction as they provide accessible, cost-effective alternatives to proprietary tools. These flows facilitate the entire process from RTL to GDSII using free and community-supported tools. Below is an overview of a typical open-source ASIC design flow:
  
  <div align="center">
  <img src="https://github.com/user-attachments/assets/f0ba4865-034a-4fdc-8369-6fc25b6e3614" alt="Description of Image" width="600" height="500">
  </div>
  
<details> <summary> RTL Design </summary>
  
-  The starting point of the flow involves writing a hardware description using languages like Verilog or VHDL.
-  The RTL (Register Transfer Level) code describes the functionality and behavior of the digital circuit without focusing on physical implementation details. 
</details>

<details> <summary> PDK's </summary> 
  
## SKYWATER130 PDK:
- The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility.

- As of May 2020, this repository is targeting the SKY130 process node. If the SKY130 process node release is successful then in the future more advanced technology nodes may become available.

- The SkyWater Open Source PDK documentation can be found at <https://skywater-pdk.rtfd.io>.
  </details>

  <details> <summary> EDA tools </summary>

  - Open-Source EDA Tools: An Overview
Open-source EDA (Electronic Design Automation) tools provide accessible, cost-effective alternatives to proprietary solutions for designing and verifying electronic systems. These tools cater to various stages of digital, analog, and mixed-signal design, from RTL synthesis to layout generation.
  - http://opencircuitdesign.com/open_pdks/

**Below is a categorized explanation of key open-source EDA tools:**

## 1. Front-End Tools
  ### 1.1 Synthesis
- **Yosys:** A versatile open-source synthesis framework.
Translates RTL Verilog into a gate-level netlist.
Features optimization and mapping to standard cells.
- Website: https://github.com/YosysHQ/yosys
- **ABC (And-Inverter Graphs):** Integrated with Yosys for logic optimization and synthesis.
Provides technology mapping and verification features.
## 2. Back-End Tools
  ### 2.1 Floorplanning and Placement
 - **OpenROAD:** Provides tools for floorplanning, placement, CTS, routing, and timing analysis.
Automates the digital layout process.
- Website: https://github.com/The-OpenROAD-Project/OpenSTA
  ### 2.2 Routing
 - **TritonRoute:** A component of OpenROAD for detailed routing.
Supports design rule compliance for advanced nodes.
  ### 2.3 Layout and Verification
 - **Magic:** A VLSI layout editor and verification tool.
Performs DRC (Design Rule Check) and LVS (Layout vs. Schematic) checks.
Converts layouts into GDSII format for fabrication.
- Website: http://opencircuitdesign.com/magic/
- **KLayout:** A powerful layout editor and viewer for large GDSII and OASIS files.
Includes scripting support with Python or Ruby.
- Website: https://www.klayout.de/
## 3.Signoff Tools
   ### 3.1 Timing Analysis
- **OpenSTA:** An open-source Static Timing Analysis (STA) tool.
Ensures the design meets timing constraints.
- Website: https://github.com/The-OpenROAD-Project/OpenSTA
  ### 3.2 Design Rule and Layout Verification
- **Magic:** Performs DRC and LVS checks.
Ensures the design meets foundry-specific fabrication rules.
## 4. Analog and Mixed-Signal Design Tools
 - **Ngspice:** A powerful open-source SPICE simulator for analog and mixed-signal designs.
Supports transient, AC, DC, and noise analyses.
- Website: https://ngspice.sourceforge.io/
## 5. Process Design Kits (PDKs)
 - **SkyWater 130nm PDK:** An open-source PDK for the SkyWater 130nm CMOS process.
Provides standard cell libraries, design rules, and models.
- Website: https://github.com/google/skywater-pdk
 
  ![Screenshot (407)](https://github.com/user-attachments/assets/cb8768f2-2c6a-46bd-882e-d618a22db7ba)
  </details>
  
## RTL to GDS flow:
- The RTL-to-GDSII flow is the cornerstone of digital ASIC (Application-Specific Integrated Circuit) design. It involves transforming a high-level hardware description into a physical layout ready for semiconductor fabrication. Below is a step-by-step explanation of the process:
<div align="center">
  <img src="https://github.com/user-attachments/assets/3a5f3458-22ab-4642-ab9d-929e95fc2842" alt="Description of Image" width="600" height="250">
</div>

<details> <summary> Synthesis </summary> 
  
 ## Synthesis:
- Transform the RTL code into a gate-level netlist using standard cells from a technology library.
- Tool like Yosys Design Compiler map the design to a specific technology library (standard cells like NAND, NOR, flip-flops).
![Screenshot (409)](https://github.com/user-attachments/assets/d0935698-9971-42f3-aa1c-ef4f78522e13)
    </details>

<details> <summary> Floorplanning </summary> 
  
## Floorplanning:
- Floorplanning determines the arrangement of major functional blocks (macros like memory or ALUs) and reserves space for components like I/O pads and power grids.
- Optimize chip area utilization.
- Minimize interconnect delays by placing related components close together.
- Ensure adequate space for routing and clock distribution.
- Outputs include a rough layout of the chip, including regions for standard cells and macro placement.
![Screenshot (410)](https://github.com/user-attachments/assets/00f7c793-3452-4499-a5b2-f609b2398345)
    </details>

<details> <summary> Placement </summary> 
  
## Placement:
- Global Placement: Standard cells are placed within the reserved areas from the floorplan based on their logical connectivity.
- Detailed Placement: Fine-tuning is performed to resolve overlaps and ensure cells meet design rules.
![Screenshot (413)](https://github.com/user-attachments/assets/20ba57c7-1052-4666-b7ee-f0f0c1c27f8d)
    </details>

<details> <summary> Clock Tree Synthesis (CTS): </summary> 
  
## Clock Tree Synthesis (CTS):
- The clock signal is distributed to all sequential elements (like flip-flops) with minimal skew (difference in arrival time) and latency.
- A balanced clock tree network ensures synchronous operation of the design
![Screenshot (415)](https://github.com/user-attachments/assets/e02ff44f-9cf4-4015-900b-e1e1329f6477)
    </details>

<details> <summary> Routing </summary>
  
## Routing:
- Routing connects all the placed cells and macros using metal layers, adhering to the technology design rules.
![Screenshot (416)](https://github.com/user-attachments/assets/c186539f-6da6-4145-b281-ce5003b56770)
    </details>

<details> <summary> Signoff </summary> 
  
## Signoff:
- Perform checks for timing, power, and signal integrity to ensure the design meets all specifications.
- Comprehensive checks ensure the design is ready for manufacturing:
    - Timing Analysis: Verify that the circuit meets its performance requirements.
    - Power Analysis: Evaluate power consumption and thermal performance.
    - Design Rule Checking (DRC): Ensure compliance with the foundry's manufacturing rules.
    - Layout vs. Schematic (LVS): Verify that the physical layout matches the logical design.
      </details>
      
## OpenLane:
[OpenLane](https://openlane.readthedocs.io/en/latest/) is an open-source framework for digital ASIC design, enabling the transformation of high-level RTL (Register Transfer Level) designs into GDSII layouts ready for fabrication. Developed as part of the OpenROAD project, it provides an automated RTL-to-GDSII flow that integrates various open-source EDA tools.

<details> <summary> OpenLane Workflow: </summary> 
  
## OpenLane Workflow
The OpenLane workflow consists of the following steps:

### 1. RTL Synthesis
- Goal: Convert the RTL code into a gate-level netlist.
- Tool: Yosys (integrated with ABC for technology mapping).
- Output: Gate-level netlist mapped to standard cells.
### 2. Floorplanning
- Goal: Define the chip's layout by arranging macros, I/O pads, and creating power grids.
- Tools: OpenROAD (floorplanning module).
- Output: DEF (Design Exchange Format) file with a rough layout.
### 3. Placement
- Goal: Place standard cells within the chip area based on connectivity.
- Steps:
    - Global Placement: Rough placement of cells.
    - Detailed Placement: Resolves overlaps and ensures alignment.
- Tool: OpenROAD (placement module).
- Output: DEF file with placed cells.
### 4. Clock Tree Synthesis (CTS)
- Goal: Build a balanced clock tree to minimize skew and ensure proper signal distribution.
- Tool: TritonCTS (Clock Tree Synthesis tool).
- Output: DEF file with the clock tree inserted.
### 5. Routing
- Goal: Connect all components (macros and cells) using metal layers.
- Steps:
       - Global Routing: High-level path planning.
       - Detailed Routing: Final connections following design rules.
- Tool: TritonRoute (routing tool).
- Output: Routed DEF file.
### 6. Design Rule Checking (DRC)
- Goal: Ensure compliance with manufacturing rules set by the PDK.
- Tool: Magic (layout editor and checker).
- Output: Reports highlighting any violations.
### 7. Static Timing Analysis (STA)
- Goal: Verify that the design meets timing requirements.
- Tool: OpenSTA (Static Timing Analysis tool).
- Output: Timing reports.
### 8. GDSII Generation
- Goal: Convert the layout into a GDSII file for tapeout.
- Tool: Magic.
- Output: GDSII file.
</details>




