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
  <div align="center">
  <img src="https://github.com/user-attachments/assets/00f7c793-3452-4499-a5b2-f609b2398345" alt="Description of Image" width="600" height="300">
  </div>
    </details>

<details> <summary> Placement </summary> 
  
## Placement:
- Global Placement: Standard cells are placed within the reserved areas from the floorplan based on their logical connectivity.
- Detailed Placement: Fine-tuning is performed to resolve overlaps and ensure cells meet design rules.
  <div align="center">
  <img src="https://github.com/user-attachments/assets/20ba57c7-1052-4666-b7ee-f0f0c1c27f8d" alt="Description of Image" width="600" height="300">
  </div>
    </details>
    
<details> <summary> Clock Tree Synthesis (CTS): </summary> 
  
## Clock Tree Synthesis (CTS):
- The clock signal is distributed to all sequential elements (like flip-flops) with minimal skew (difference in arrival time) and latency.
- A balanced clock tree network ensures synchronous operation of the design
  <div align="center">
  <img src="https://github.com/user-attachments/assets/e02ff44f-9cf4-4015-900b-e1e1329f6477" alt="Description of Image" width="600" height="300">
  </div>
    </details>
    
<details> <summary> Routing </summary>
  
## Routing:
- Routing connects all the placed cells and macros using metal layers, adhering to the technology design rules.
  <div align="center">
  <img src="https://github.com/user-attachments/assets/c186539f-6da6-4145-b281-ce5003b56770" alt="Description of Image" width="600" height="300">
  </div>
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
  <div align="center">
  <img src="https://github.com/user-attachments/assets/b7e9e0e1-e5d6-4d40-b3d5-48dc2c583de2" alt="Description of Image" width="600" height="300">
  </div>


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


# Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells
<details> <summary> Floorplanning consideration </summary>
  
## Floorplanning consideration

Gates---->Physical dimentions
  <div align="center">
  <img src="https://github.com/user-attachments/assets/084907a0-624e-4d97-933e-1969aa90bec2" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/084907a0-624e-4d97-933e-1969aa90bec2)

Die and core area
  <div align="center">
  <img src="https://github.com/user-attachments/assets/b08cbcf4-9d90-4cec-8819-3671eef91e6d" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/b08cbcf4-9d90-4cec-8819-3671eef91e6d)

      -Utilization Factor = (Area occupied by netlist/Total area of the core)

      -Aspect Ratio = (Height/Width)

Aspect ratio: It is calculated by the height and core,Aspect ratio for rectangular core is 0.5 and square core is 1.
</details>

<details> <summary> Preplaced cells </summary>
  
## Preplaced cells:

Spliting the combinational logic into two parts
  <div align="center">
  <img src="https://github.com/user-attachments/assets/38a9ebdd-53b8-4481-9388-67040eca9c39" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/38a9ebdd-53b8-4481-9388-67040eca9c39)

Creating a block box called IP
  <div align="center">
  <img src="https://github.com/user-attachments/assets/5ae6a3f0-ade7-413b-9310-edb0e8e92f16" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/5ae6a3f0-ade7-413b-9310-edb0e8e92f16)

- The arrangement of these IP's in a chip is referred as Floorplanning 
- These IP's/blocks have user-defined locations, and hence are placed in chip before automated placement-and-routing and are called as pre-placed cells. 
- Automated placement and routing tools places the remaining logical cells in the design onto chip

Examples for IP
  <div align="center">
  <img src="https://github.com/user-attachments/assets/6cd7313d-071c-4244-a747-187c1e23f768" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/6cd7313d-071c-4244-a747-187c1e23f768)

Preplaced cells in core
  <div align="center">
  <img src="https://github.com/user-attachments/assets/d81f123b-2c86-4bdd-ba30-1817d98ce3ac" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/d81f123b-2c86-4bdd-ba30-1817d98ce3ac)

- Decoupling Capacitor:
     - Physical wire connection have a resistance in nature
     - Switching wants to be n proper one volt for switching from 0 to 1
     - If the vdd goes below the noise margin the switching will not happen
    <div align="center">
  <img src="https://github.com/user-attachments/assets/60447cd2-1b0d-4c9e-9cff-904e89ce9127" alt="Description of Image" width="600" height="300">
  </div>
  
![Screenshot (588)](https://github.com/user-attachments/assets/60447cd2-1b0d-4c9e-9cff-904e89ce9127)

- Noise margin:
     - The minimum acceptable voltage level for a logic gate input signal to be recognized as a logical “0” (LOW)
     - The maximum acceptable voltage level for it to be recognized as a logical “1” (HIGH)
  <div align="center">
  <img src="https://github.com/user-attachments/assets/86a2d7c9-bc4c-45fb-8764-e761e81078b" alt="Description of Image" width="600" height="300">
  </div>
  
![Screenshot (590)](https://github.com/user-attachments/assets/86a2d7c9-bc4c-45fb-8764-e761e81078b1)

     - placing a capacitor infront of the circuit is decoupling
    - It decoples the circuit form main power supply
    <div align="center">
  <img src="https://github.com/user-attachments/assets/08fa2e56-f97b-4ed6-9341-2fbba19e0f42" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/08fa2e56-f97b-4ed6-9341-2fbba19e0f42)
</details>

<details> <summary> Power Planning </summary>
  
  ## Power Planning
- Eventhough we are using decap the single power supply cannot able to give proper power to circuit
  <div align="center">
  <img src="https://github.com/user-attachments/assets/c7f3f3ed-df26-4881-88ae-f777f7f5daea" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/c7f3f3ed-df26-4881-88ae-f777f7f5daea)

- To overcome this problem we are using power mesh as shown in below img
  <div align="center">
  <img src="https://github.com/user-attachments/assets/e970823f-9340-4721-89fb-8d5df5172d54" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/e970823f-9340-4721-89fb-8d5df5172d54)

- Power mesh in core
  <div align="center">
  <img src="https://github.com/user-attachments/assets/47fb1d30-4cf3-49e9-a4e2-7c163474659d" alt="Description of Image" width="600" height="300">
  </div>
  
![Screenshot (592)](https://github.com/user-attachments/assets/47fb1d30-4cf3-49e9-a4e2-7c163474659d)
</details>

<details> <summary> Pin Placement </summary>
  
## Pin placement

- Combinational Circuit
  <div align="center">
  <img src="https://github.com/user-attachments/assets/5494705b-9fed-4997-9895-03b9a80622a6" alt="Description of Image" width="600" height="300">
  </div>
  
![Screenshot (594)](https://github.com/user-attachments/assets/5494705b-9fed-4997-9895-03b9a80622a6)

- Placing pins
   - We can place Din,Dout where ever we want,Placing near to our block is preferrable
   - CLk pin should be bit thicker since it has driven for all flops.
    <div align="center">
  <img src="https://github.com/user-attachments/assets/8114ed7e-8190-4c08-95a3-34f54a899345" alt="Description of Image" width="600" height="300">
  </div>
  
  ![Screenshot (595)](https://github.com/user-attachments/assets/8114ed7e-8190-4c08-95a3-34f54a899345)

## Placement

 - Binding netlist with physical cells
   <div align="center">
  <img src="https://github.com/user-attachments/assets/3782d3a5-ed80-4adf-94ec-7a56b1fdd09a" alt="Description of Image" width="600" height="300">
  </div>
  
 ![Screenshot (596)](https://github.com/user-attachments/assets/3782d3a5-ed80-4adf-94ec-7a56b1fdd09a)
   <div align="center">
  <img src="https://github.com/user-attachments/assets/e2599864-0b71-461b-926c-43c5b5dcc1df" alt="Description of Image" width="600" height="300">
  </div>
  
 ![Screenshot (597)](https://github.com/user-attachments/assets/e2599864-0b71-461b-926c-43c5b5dcc1df)

- Library
    - It is just like our real library
    - It consists all details of circuits for example delay,length,width
    <div align="center">
  <img src="https://github.com/user-attachments/assets/3466261c-269c-4b97-ae51-07be487ad862" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/3466261c-269c-4b97-ae51-07be487ad862)

-Optimize placement using estimated wire-length and capacitance
  <div align="center">
  <img src="https://github.com/user-attachments/assets/77af2d74-5bcf-4f0d-8546-3596d4c20632" alt="Description of Image" width="600" height="300">
  </div>
  
![image](https://github.com/user-attachments/assets/77af2d74-5bcf-4f0d-8546-3596d4c20632)
  <div align="center">
  <img src="https://github.com/user-attachments/assets/32708099-2ef5-4e7f-9b08-2aba63b87173" alt="Description of Image" width="600" height="300">
  </div>
  
![Screenshot (600)](https://github.com/user-attachments/assets/32708099-2ef5-4e7f-9b08-2aba63b87173)

- Buffer/Repeaters:
   - It is used to transmit a signal from one place to another,when the circuit block is far from each other
  <div align="center">
  <img src="https://github.com/user-attachments/assets/c96edd24-fde3-4999-80fb-7db2b1b0d2fd" alt="Description of Image" width="600" height="300">
  </div>
  
      ![Screenshot (601)](https://github.com/user-attachments/assets/c96edd24-fde3-4999-80fb-7db2b1b0d2fd)
  <div align="center">
  <img src="https://github.com/user-attachments/assets/3bc3e874-93c5-46b6-9e24-f4296b0d891c" alt="Description of Image" width="600" height="300">
  </div>
  
     ![Screenshot (602)](https://github.com/user-attachments/assets/3bc3e874-93c5-46b6-9e24-f4296b0d891c)

   - You may see the cirs cross line in placement it is fine, we will place this in seperare layer(Metal-1,2,3)
  <div align="center">
  <img src="https://github.com/user-attachments/assets/36f9cd6c-2a8d-4d40-a242-29da179f6348" alt="Description of Image" width="600" height="300">
  </div>
  
     ![Screenshot (604)](https://github.com/user-attachments/assets/36f9cd6c-2a8d-4d40-a242-29da179f6348)
</details>

## SKY130_D2_SK3 - Cell design and characterization flows
- Let's reverse engineering the standard cell
  <div align="center">
  <img src="https://github.com/user-attachments/assets/d6a5b4c0-40c3-4d64-9772-563ab3a90588" alt="Description of Image" width="600" height="300">
  </div>
  
- Standard consist of a library which has and,or,not etc...
- These Cells are come in diffrents sizes,Vt
  <div align="center">
  <img src="https://github.com/user-attachments/assets/910296fe-9faa-4df1-92f9-8017a8ff6df4" alt="Description of Image" width="600" height="300">
  </div>
  
- Lets break down the Inverter
    - Input
    - Design Flow
    - Output
  
<details> <summary> Input </summary>
  
- Input -->
     - Process design kits PDK's:
          - DRC & LVS rules,
          - SPICE models,
          - library and user defined-specs
    <div align="center">
  <img src="https://github.com/user-attachments/assets/a8671004-0dfa-455c-8c32-d60bec85ad65" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/a8671004-0dfa-455c-8c32-d60bec85ad65)

  - DRC & LVS rules:
      - Tech files has set of rules which explanis length and width of library.
      - It si provided by the foundry. 
  <div align="center">
  <img src="https://github.com/user-attachments/assets/b7e9e0e1-e5d6-4d40-b3d5-48dc2c583de2" alt="Description of Image" width="600" height="300">
  </div>
  
   ![image](https://github.com/user-attachments/assets/ac70cac2-90b7-4a65-a5fa-3d6fb34f3b8f)
      - Examples of DRC rules:
    <div align="center">
  <img src="https://github.com/user-attachments/assets/ac70cac2-90b7-4a65-a5fa-3d6fb34f3b8f" alt="Description of Image" width="600" height="300">
  </div>
  
  ![Screenshot (610)](https://github.com/user-attachments/assets/ac70cac2-90b7-4a65-a5fa-3d6fb34f3b8f)

  - SPICE models:
      - It should be provided by foundry 
      <div align="center">
  <img src="https://github.com/user-attachments/assets/dd4ed7d6-1d30-455f-8d74-53aa0c6341dd" alt="Description of Image" width="600" height="300">
  </div>
  
    ![image](https://github.com/user-attachments/assets/dd4ed7d6-1d30-455f-8d74-53aa0c6341dd)
      <div align="center">
  <img src="https://github.com/user-attachments/assets/adba3918-62b1-4d0f-a2f3-ebef760a4f42" alt="Description of Image" width="600" height="300">
  </div>
  
    ![Screenshot (612)](https://github.com/user-attachments/assets/adba3918-62b1-4d0f-a2f3-ebef760a4f42)

  - library and user defined-specs:
      - It defines cell height, supply voltage, metal layers, pin location,
    <div align="center">
  <img src="https://github.com/user-attachments/assets/7b0b5fd3-d084-4d48-9f2a-21ab16d5bcbc" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/7b0b5fd3-d084-4d48-9f2a-21ab16d5bcbc)
    <div align="center">
  <img src="https://github.com/user-attachments/assets/c84d58ef-c317-403b-aa93-36cf04478879" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/c84d58ef-c317-403b-aa93-36cf04478879)
   <div align="center">
  <img src="https://github.com/user-attachments/assets/b115523a-a9b3-4ec4-a36c-12cca86964bf" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/b115523a-a9b3-4ec4-a36c-12cca86964bf)
   <div align="center">
  <img src="https://github.com/user-attachments/assets/f31a744d-4347-4532-a327-94e242c01b28" alt="Description of Image" width="600" height="300">
  </div>
  
  ![image](https://github.com/user-attachments/assets/f31a744d-4347-4532-a327-94e242c01b28)

</details>

<details> <summary> Design Flow </summary>
  
- Design Flow -->
  
    1.Circuit design
    2.Layout design
    3.Characterization
      
  1.Circuit design:
    - Implement the function
    - Model the pmos and nmos
    - W,L Drain current needs to be library standard
      
  <div align="center">
  <img src="https://github.com/user-attachments/assets/3459e422-9d9e-4551-81d7-a97b2c55b588" alt="Description of Image" width="600" height="300">
  </div>

  2.Layout design:
    - Euler's Path
    - Stick diagram
    - Layout
                  
  <div align="center">
  <img src="https://github.com/user-attachments/assets/e7d89856-3f73-4488-962f-5bf247d399bb" alt="Description of Image" width="600" height="300">
  </div>
      
  <center> Euler's Path </center>
       
  <div align="center">
  <img src="https://github.com/user-attachments/assets/7f3b6c1c-4619-4fc1-8302-1d2b880b86fa" alt="Description of Image" width="600" height="300">
  </div>
     
   <center> Stick diagram </center>                                                   
  
  <div align="center">
  <img src="https://github.com/user-attachments/assets/1e9e04ad-c684-452d-9e8c-4dc035d23df4" alt="Description of Image" width="300" height="300">
  </div>
  
   <center> Layout </center>                                                     

  3.Characterization:
    - Circuit
  <div align="center">
  <img src="https://github.com/user-attachments/assets/e7021019-7e49-485f-b07f-b988d42ad5e0" alt="Description of Image" width="600" height="300">
  </div>
  
   - Circuit netlist ---> .subckt ---> .model
        - Circuit netlist is consist of description of circuit with inveter,VDD,VSS,Pulse etc...
        - .subckt which describes the inverter
        - .model which describes the nmos,pmos 
          
  <div align="center">
  <img src="https://github.com/user-attachments/assets/86f970f0-29cd-4101-81d8-b3b4d84fb19c" alt="Description of Image" width="600" height="300">
  </div>
        
  </details>
      
# SKY130_D2_SK4 - General timing characterization parameters
 
  
## Timing Thershold definition

<details> <summary> Transition time </summary> 

### Transition time
 It is calcuated from output of buffer vs input to inverter two
  <div align="center">
  <img src="https://github.com/user-attachments/assets/05674382-11d8-4048-ade1-21274c28e247" alt="Description of Image" width="600" height="300">
  </div>
  
- slew_low_rise_thr -20% of input
   <div align="center">
  <img src="https://github.com/user-attachments/assets/1908a149-449e-49d9-ab5d-3143d036f651" alt="Description of Image" width="600" height="300">
  </div>
  
- slew_high_rise_thr -80% of Input
  <div align="center">
  <img src="https://github.com/user-attachments/assets/3a5cb048-6471-4071-8a9c-1bdaa8d1ad6e" alt="Description of Image" width="600" height="300">
  </div>
  
- slew_low_fall_thr  -20% buf output
  <div align="center">
  <img src="https://github.com/user-attachments/assets/646d4d68-327b-479b-93a0-09d00609cec5" alt="Description of Image" width="600" height="300">
  </div>
  
- slew_low_fall_thr -80% buf output
  <div align="center">
  <img src="https://github.com/user-attachments/assets/78826d09-96ee-4d15-80ed-cd55a6bf42d3" alt="Description of Image" width="600" height="300">
  </div>

</details>

 <details> <summary> Propagation delay </summary> 
   
### Propagation delay
      Propagation delay= time(out_*_thr) - time(in_*_thr)
  - We have to take of 50% of rise and fall

  In_rise_thr
  <div align="center">
  <img src="https://github.com/user-attachments/assets/4cc3566b-2698-4d63-a1a3-49329f568f0c" alt="Description of Image" width="600" height="300">
  </div>
  
  In_fall_thr
     <div align="center">
  <img src="https://github.com/user-attachments/assets/69979edd-8666-4ae5-9b6f-82e7ac77658c" alt="Description of Image" width="600" height="300">
  </div>
  
  out_rise_thr
     <div align="center">
  <img src="https://github.com/user-attachments/assets/69f72eb3-ea89-486d-a9bd-c7936ffc2a12" alt="Description of Image" width="600" height="300">
  </div>
  
  out_fall_thr
      <div align="center">
  <img src="https://github.com/user-attachments/assets/67ddf168-1b8c-49b4-b949-f011bba3a4f8" alt="Description of Image" width="600" height="300">
  </div>
  
</details>










 






