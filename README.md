# Physical_Design_using_OpenLANE

## Day 1
<details>
<summary>Introduction to RISC-V</summary>
 
**RISC-V** (pronounced "risk-five") is an open-source instruction set architecture (ISA) that has gained significant attention and popularity in recent years. It is designed to be simple, modular, and customizable, making it suitable for a wide range of applications from embedded systems to supercomputers. In this introduction to RISC-V architecture, we'll cover its key concepts and characteristics:

**Open Source Philosophy:**
RISC-V is an open-source ISA, which means its specifications are freely available to the public. This openness encourages collaboration and innovation, allowing anyone to design, implement, and customize RISC-V processors without licensing fees.

**RISC (Reduced Instruction Set Computer):**
RISC-V follows the RISC design philosophy, which emphasizes a small and simple set of instructions. This simplicity makes it easier to design efficient and high-performance processors.

**Modular and Extensible:**
RISC-V is designed with modularity in mind. It provides a base set of instructions, known as the RV32I (for 32-bit) and RV64I (for 64-bit) instruction sets, which serve as a foundation. Beyond these base sets, custom instruction extensions can be added to meet the specific needs of different applications. This extensibility enables the architecture to be tailored for various domains, from IoT devices to data centers.

**Multiple Standard Extensions:**
RISC-V offers several standard extensions, including integer (I), multiplication and division (M), atomic (A), single-precision floating-point (F), double-precision floating-point (D), vector (V), and more. These extensions add functionality to the base architecture as needed.

**Support for Different Bit Widths:**
RISC-V supports various bit widths, such as 32, 64, and 128 bits, making it adaptable to a wide range of computing environments.

**Load-Store Architecture:**
RISC-V follows a load-store architecture, where memory operations are performed using load and store instructions. This design simplifies the instruction set and helps maintain a consistent pipeline for better performance.

**User and Privileged Modes:**
RISC-V has multiple privilege levels, including user mode, supervisor mode, and machine mode. This privilege hierarchy enables secure execution of software and is useful for implementing operating systems.

**Instruction Encoding:**
RISC-V instructions are typically encoded as fixed-length 32-bit or 64-bit words, depending on the chosen bit width. The simplicity of instruction encoding contributes to the architecture's ease of implementation.

**Wide Industry Support:**
RISC-V has gained support from a broad range of industry players, including academia, startups, and established companies. This support has led to the development of RISC-V-based hardware and software ecosystems.
**Applications:**
RISC-V is used in various applications, from low-power IoT devices and microcontrollers to high-performance servers and supercomputers. Its versatility and openness make it a compelling choice for a wide array of computing tasks.
</details>
<details>
<summary>SOC Design and OpenLANE</summary>

**Open Source Digital ASIC Design**

Components of Digital ASIC Design:

![Screenshot from 2023-09-13 00-26-13](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/ad689ae7-82b5-4a0a-abbc-ec3e9eb1309a)

EDA Tools: For digital ASIC (Application-Specific Integrated Circuit) design, various EDA (Electronic Design Automation) tools are essential to complete the design process efficiently like Qflow, OpenROAD, OpenLANE, etc.

RTL: RTL IP blocks are reusable building blocks for digital designs. They encapsulate specific functions or features and are designed to be easily integrated into larger designs, reducing the need for designing these functions from scratch.

PDK: Process Design Kit is the collection of files used to model a fabrication process for the EDA Tools used to design an IC like Google+Skywater FOSS 130nm Production PDK.

**Simplified RTL to GDS Flow**
The RTL to GDS (Register-Transfer Level to Graphic Design System) flow is a series of steps and tools used in the semiconductor industry to transform a digital circuit's high-level description (RTL) into a physical layout that can be fabricated as an integrated circuit (IC) using a specific semiconductor process. Here's an overview of the typical RTL to GDS flow:

Design Specification:
Start with a clear specification of the desired functionality and performance requirements of the digital circuit.

RTL Design:
Create a Register-Transfer Level (RTL) design using a hardware description language (HDL) such as Verilog or VHDL. The RTL code describes the behavior and functionality of the digital circuit.

Simulation and Verification:
Simulate the RTL code using tools like ModelSim or VCS to verify that the design functions correctly. This involves creating testbenches and running simulations to ensure that the RTL code meets the design requirements.

Synthesis:
Use a synthesis tool (e.g., Synopsys Design Compiler, Cadence Genus) to convert the RTL code into a gate-level netlist. The synthesis process optimizes the design for area, power, and speed while targeting a specific semiconductor technology library.

Gate-Level Simulation:
Perform gate-level simulations to verify that the synthesized netlist behaves as expected and is functionally correct.

Floor Planning:
Define the physical layout of the chip, including the placement of logic blocks, standard cells, and I/O pads. This step determines the overall chip size and the placement of key components.

Place-and-Route (P&R):
Use a place-and-route tool (e.g., Cadence Innovus, Synopsys ICC) to map the gate-level netlist onto the physical chip's layout. This step involves placing the cells on the chip and routing the interconnections between them.

Clock Tree Synthesis (CTS):
Create a clock distribution network to ensure that clock signals reach all parts of the chip with minimal skew and jitter.

Power Planning:
Plan the power distribution network to ensure that all components receive the required power supply voltages and currents.

Physical Verification:
Perform physical verification checks, including Design Rule Checking (DRC), Layout vs. Schematic (LVS) checks, and Parasitic Extraction (PEX) to ensure that the layout adheres to the semiconductor process rules and matches the expected functionality.

Timing Analysis:
Perform static timing analysis (STA) to verify that the design meets its timing requirements, such as setup and hold times, clock-to-q delays, and maximum operating frequency.

Mask Generation:
Generate the mask data required for semiconductor manufacturing based on the final layout. This data includes information on the placement of transistor gates and interconnects.

Foundry Services:
Send the mask data to a semiconductor foundry for fabrication. The foundry manufactures the physical ICs using the specified semiconductor process.

Testing and Debugging:
After fabrication, the ICs undergo testing to ensure they function correctly. Any defects or issues discovered during testing may require further debugging and iteration.

Packaging and Assembly:
The fabricated ICs are packaged, which involves placing them in protective enclosures and connecting them to external pins or balls for electrical connections.

Final Testing:
Perform final testing on the packaged ICs to verify their functionality and performance.

Release and Deployment:
The final ICs are ready for deployment in various electronic devices and systems.

![Screenshot from 2023-09-13 00-15-36](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/a09241ee-1923-4a0c-86b7-a31df43b6364)

</details>

<details>
 
<summary>Installation of OpenLANE</summary>

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 


# Check for installation
sudo docker run hello-world
```
OpenLANE installation:

```bash
git clone --depth 1 https://github.com/The-OpenROAD-Project/OpenLane.git --recurse-submodules
cd OpenLane/
make
make test
cd /home/malobi/OpenLane/designs/ci
cp -r * ../
```
</details>
<details>
 
<summary>Steps for Synthesis in OpenLANE:</summary>

```bash
cd ~/OpenLane
make mount
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
run_synthesis
```


<img width="1470" alt="1" src="https://github.com/VaibhavTiwari-IIITB/Physical_Design_using_OpenLANE/assets/140998525/672c926c-cb01-44ca-a411-53195bc24c1b">


To see the synthesis report:

<img width="581" alt="2" src="https://github.com/VaibhavTiwari-IIITB/Physical_Design_using_OpenLANE/assets/140998525/41917610-7120-46ec-a653-7ff7a8e6de43">

<img width="1470" alt="3" src="https://github.com/VaibhavTiwari-IIITB/Physical_Design_using_OpenLANE/assets/140998525/81405ca5-21b4-4e36-af6e-5ca4f026a99a">

```bash

61. Printing statistics.

=== picorv32 ===

   Number of wires:               9824
   Number of wire bits:          10206
   Number of public wires:        1512
   Number of public wire bits:    1894
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:              10104
     sky130_fd_sc_hd__a2111o_2       2
     sky130_fd_sc_hd__a211o_2      101
     sky130_fd_sc_hd__a211oi_2       4
     sky130_fd_sc_hd__a21bo_2       19
     sky130_fd_sc_hd__a21boi_2       7
     sky130_fd_sc_hd__a21o_2       414
     sky130_fd_sc_hd__a21oi_2      127
     sky130_fd_sc_hd__a221o_2       65
     sky130_fd_sc_hd__a221oi_2       1
     sky130_fd_sc_hd__a22o_2       197
     sky130_fd_sc_hd__a22oi_2        2
     sky130_fd_sc_hd__a2bb2o_2      16
     sky130_fd_sc_hd__a311o_2       38
     sky130_fd_sc_hd__a31o_2        90
     sky130_fd_sc_hd__a31oi_2       10
     sky130_fd_sc_hd__a32o_2        89
     sky130_fd_sc_hd__a41o_2         2
     sky130_fd_sc_hd__and2_2       283
     sky130_fd_sc_hd__and2b_2       32
     sky130_fd_sc_hd__and3_2        77
     sky130_fd_sc_hd__and3b_2       76
     sky130_fd_sc_hd__and4_2        46
     sky130_fd_sc_hd__and4b_2        6
     sky130_fd_sc_hd__and4bb_2       3
     sky130_fd_sc_hd__buf_1       2735
     sky130_fd_sc_hd__buf_2         16
     sky130_fd_sc_hd__conb_1       106
     sky130_fd_sc_hd__dfxtp_2     1596
     sky130_fd_sc_hd__inv_2         83
     sky130_fd_sc_hd__mux2_2      1817
     sky130_fd_sc_hd__mux4_2       323
     sky130_fd_sc_hd__nand2_2      250
     sky130_fd_sc_hd__nand2b_2       2
     sky130_fd_sc_hd__nand3_2       18
     sky130_fd_sc_hd__nand3b_2       3
     sky130_fd_sc_hd__nand4_2        2
     sky130_fd_sc_hd__nor2_2       185
     sky130_fd_sc_hd__nor3_2        11
     sky130_fd_sc_hd__nor3b_2        3
     sky130_fd_sc_hd__nor4_2         4
     sky130_fd_sc_hd__nor4b_2        3
     sky130_fd_sc_hd__o2111a_2       1
     sky130_fd_sc_hd__o211a_2      224
     sky130_fd_sc_hd__o211ai_2       6
     sky130_fd_sc_hd__o21a_2       154
     sky130_fd_sc_hd__o21ai_2       94
     sky130_fd_sc_hd__o21ba_2       15
     sky130_fd_sc_hd__o21bai_2       3
     sky130_fd_sc_hd__o221a_2       19
     sky130_fd_sc_hd__o221ai_2       1
     sky130_fd_sc_hd__o22a_2        26
     sky130_fd_sc_hd__o22ai_2        1
     sky130_fd_sc_hd__o2bb2a_2       7
     sky130_fd_sc_hd__o311a_2       31
     sky130_fd_sc_hd__o311ai_2       2
     sky130_fd_sc_hd__o31a_2        21
     sky130_fd_sc_hd__o31ai_2        2
     sky130_fd_sc_hd__o32a_2        14
     sky130_fd_sc_hd__o41a_2         1
     sky130_fd_sc_hd__or2_2        337
     sky130_fd_sc_hd__or2b_2        20
     sky130_fd_sc_hd__or3_2        102
     sky130_fd_sc_hd__or3b_2        17
     sky130_fd_sc_hd__or4_2         29
     sky130_fd_sc_hd__or4b_2         6
     sky130_fd_sc_hd__xnor2_2       78
     sky130_fd_sc_hd__xor2_2        29

   Chip area for module '\picorv32': 102957.494400
```

Flop Ratio:

```bash
Flop ratio = (No.of D flipflops)/(Total no.of cells) =1596/10104 = 0.1579
```
</details>




<h2>Day 2 </h2>
<details>
  <summary><b>Chip Floorplanning considerations</b></summary>
  <h3>Floorplanning</h3>
  <p>Floorplanning is a crucial early-stage step in the physical design process, where the initial layout of the chip is defined. It involves making high-level decisions about how various components will be arranged on the silicon substrate.</p>
  <h3>Core Area Definition:</h3>
  <p>Determine the overall dimensions of the chip and define the core area where the primary functional blocks and standard cells will be placed. This core area is surrounded by peripheral regions that may contain I/O pads and other necessary structures.</p>
  <h4>Utilization Factor</h4>
  <p>The Utilization Factor is calculated as the area occupied by the netlist divided by the total core area. A Utilization Factor of 1 indicates full utilization with no extra space, but in practice, it's typically around 0.5-0.6.</p>
  
```
  Utilization factor = Area occupied by Netlist/Total core Area
```

  <h4>Aspect ratio</h4>
  <p>The Aspect Ratio is the ratio of the chip's height to its width. A value of 1 signifies a square chip, while other values represent a rectangular shape.</p>
  
```
Aspect ratio = Chip Height/Chip Width
```  
  
  

  <h3>Preplaced cells</h3>
  <p>Pre-placed cells are fixed-position Intellectual Properties (IPs) with significant combinational logic. They're positioned before automated placement and routing in integrated circuit design, hence the term "pre-placed."</p>
  <p>Preplaced cells are generally placed at the location from where it is nearest to all the other circuit blocks accessing it. Once placed they are not modified in terms of location thereafter.</p>

  <h3>Decoupling Capacitor</h3>
  <p>
    Pre-placed cells are often accompanied by decoupling capacitors (decaps) in integrated circuit (IC) design. Long wire lengths introduce resistive and capacitive effects that can result in substantial power supply voltage drops before reaching the logic circuits. This can push signal values into undefined regions, beyond the noise margin. Decaps are substantial capacitors charged to the power supply voltage and strategically positioned near the logic circuits. Their primary purpose is to decouple the circuit from the power supply, ensuring a stable voltage and supplying instantaneous current when needed. Decaps also mitigate crosstalk and facilitate efficient local communication.
  </p>
<h3>The problem of unstable ground</h3>
<div align ="center">
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/fc5b5efb-0477-460e-8c4b-cc877733fc59">
  <br>
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/a93a048f-4a54-40c6-b2a6-38ff5284fac8">
  <br>
  
</div> 
<p>Due to this it may happen that some of logic values may break Noise Margin producing errorneous results.</p>
<h3>Power Planning(Solution)</h3>
<p>While each block on the chip cannot have individual decoupling capacitors (decaps) like pre-placed macros, effective power planning ensures that each block is equipped with its dedicated VDD and VSS pads. These pads are strategically connected to the horizontal and vertical power and ground (GND) lines, forming a comprehensive power mesh.</p>

<h3>Pin Placement</h3>
<p>The netlist specifies the interconnections between logic gates within the design. The region between the core and the chip's periphery is designated for the placement of I/O pins. Information regarding connectivity, often described in VHDL or Verilog, is leveraged to determine the precise locations of I/O pads for various pins. Subsequently, logical placement distinguishes the area allocated for pre-placed macros from the dedicated pin area.</p>

<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/d47a9118-5f3d-4b9d-8552-e7f2de7a35de">
  <br>
<img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/9ce61f2a-4d1a-4524-8299-98b528fd4fec">
  
</div>
</details>

<details>
  <summary><b>Floorplan in Openlane</b></summary>
  To perform the floorplanning process for the "picorv32a" design in OpenLANE and visualize the results in Magic, follow these steps, considering the importance files and environment variables:<br>

Important Files (in increasing priority order):<br>

<ul>
 <li>floorplan.tcl - System default environment variables.</li>
<li>config.tcl</li>
<li>sky130A_sky130_fd_sc_hd_config.tcl</li>
</ul>
Floorplan Environment Variables or Switches:
<ul>
<li><b>FP_CORE_UTIL:</b> Specifies floorplan core utilization.</li>
<li><b>FP_ASPECT_RATIO:</b> Sets the floorplan aspect ratio.</li>
<li><b>FP_CORE_MARGIN:</b> Defines the core-to-die margin area.</li>
<li><b>FP_IO_MODE:</b> Determines pin configurations (1 for equidistant, 0 for non-equidistant).</li>
<li><b>FP_CORE_VMETAL:</b> Sets the vertical metal layer.</li>
<li><b>FP_CORE_HMETAL:</b> Sets the horizontal metal layer.<br> 
Typically, these values are one greater than what's specified in the files.</li>
</ul> 

<h4>Command used</h4>

```
run_floorplan
```
<div align="center">


<img width="1080" alt="2-1" src="https://github.com/VaibhavTiwari-IIITB/Physical_Design_using_OpenLANE/assets/140998525/796dd766-605e-4d8a-ada7-965c619ca6c3">
</div>

<h4>Post-Floorplan Run and Viewing the Floorplan in Magic:</h4>
<ul>
<li>After running the floorplan step in OpenLANE, a .def file representing the floorplan will be generated within the results/floorplan directory. This file encapsulates the layout and organization of the integrated circuit components.</li>
<li>To visualize the floorplan layout using the Magic VLSI layout tool, follow these steps:<br>

Open a terminal or command prompt.<br>

Navigate to the ```results/floorplan``` directory within your OpenLANE workspace.<br>
Once you're in the ```results/floorplan``` directory, invoke Magic to view the floorplan by running the following command:<br>

```
magic -T /home/OpenLane/sky130A.tech lef read ../../tmp/merged.min.lef def read picorv32.def &
```

</li>  
<div align="center">
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/4ca2fff9-c9f3-469a-a964-2efd81362f34">
</div>  
</ul>  
In Magic layout design software:<br>
To zoom into a specific area of the layout, you can use the following steps:<br>
<ul>
<li>Select an area by clicking the left mouse button and dragging to create a selection box.</li>
<li>Then, hold the right mouse button and press the 'z' key. This action should zoom in on the selected area.</li>
</ul>
 <br> 
To identify various components within the layout, you can use the `what` command within the tkcon window. After making a selection (e.g., clicking on a component), enter the `what` command to get information about the selected component.
<br>
When you zoom in, you can also get a closer view of the decaps (decapacitors) present in the picorv32a chip or any other components.<br>

<br>
The standard cell can typically be found at the bottom left corner of the layout.<br>
<div>
  <img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/8fd3cab0-704d-4cd8-9fce-af8585b5ef6a">
</div>

</details>
<details>
  <summary><b>Placement</b></summary>
  Placement
The placement step in the OpenLANE ASIC flow involves positioning the synthesized netlist onto the floorplan. This process is performed in two stages:

<b>Global Placement:</b> In this stage, an optimal position for all cells is determined. The positions may not initially be legal, and cells may overlap. Optimization is carried out with the goal of reducing half-parameter wire length.

<b>Detailed Placement:</b> Following global placement, the positions of cells are adjusted to make them legal within the design. Legalizing cells is crucial from a timing perspective, ensuring that the chip meets its performance requirements.

Running the placement step in OpenLANE and visualizing the placement results in Magic can be accomplished with the following command:


```
run_placement
```


<div align="center">
<img width="1080" alt="2-2" src="https://github.com/VaibhavTiwari-IIITB/Physical_Design_using_OpenLANE/assets/140998525/1528c8e9-9166-4a8f-a684-2fe24bfe6512">
  
</div>

After running the placement step, you can use Magic to inspect and analyze the placement of cells, ensuring that they are positioned optimally and legally within the floorplan.


To view the design in magic 

```
magic -T /home/OpenLane/sky130A.tech lef read ../../tmp/merged.max.lef def read picorv32.def &


```
<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/1fb5d2a6-9ce8-48de-a3c7-6edc1bb3c4ad">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/0c54e4a8-5b59-4cbb-8610-67e59155808b">
  
</div>

</details>



<h2>Day 3</h2>
<details>
  <summary><b>CMOS Inverter ngspice simulations</b></summary>
  <h2>SPICE deck</h2>
  <p>A Spice deck, often referred to as a Spice netlist or simply Spice file, is a text-based input file used in electronic circuit simulation. Spice stands for "Simulation Program with Integrated Circuit Emphasis," and it is a widely used tool for simulating and analyzing electronic circuits.<br>

A Spice deck contains a description of the components and connections within an electronic circuit, including resistors, capacitors, inductors, transistors, voltage sources, current sources, and more. It specifies the values of these components, their models (which define their behavior), and the interconnections between them. The Spice deck also defines the simulation settings and analysis directives.</p>

<h4>Sample Spice Deck</h4>

```
* Spice Deck Example
* Comments start with an asterisk

* Circuit components
R1  N1  N2  10k   ; Resistor R1 from node N1 to N2 with a value of 10k ohms
C1  N2  N3  1n    ; Capacitor C1 from node N2 to N3 with a value of 1 nanofarad
V1  N1  0   DC 5V ; DC voltage source V1 from node N1 to ground (0) with 5 volts

* Transistors and other components can also be defined here

* Simulation settings
.TRAN  0.1ms  10ms ; Transient analysis from 0.1ms to 10ms
.DC    V1  0V  10V  1V ; DC sweep of voltage source V1 from 0V to 10V in 1V steps
.AC    DEC  100  1Hz  1MHz ; AC analysis from 1Hz to 1MHz with 100 points per decade

* Analysis directives
.PRINT  TRAN  V(N1) V(N2) ; Print the transient simulation results for nodes N1 and N2
.MEASURE  DC  V(N3) WHEN V(N2)=3V ; Measure voltage at node N3 when V(N2) reaches 3V

```
<h4>CMOS SPICE deck steps</h4>
<div align = "center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/28c828ad-348c-4fd5-96e3-2d10a7cd30bb">
</div>

<p><b>In above figure we have taken size of NMOS and PMOS as equal which is not the case in real cmos circuits.</b></p>

</details>

<details>
  <summary><b>Inception of Layout of CMOS Inverter</b></summary>
  
  ## 16-Mask CMOS Fabrication Process

1. **Substrate Selection:**
   - Choose the appropriate substrate material for the CMOS chip.

2. **Active Region Formation:**
   - Isolate active regions using SiO2 and Si3N4 layers, defined through photolithography and etching.

3. **N-Well and P-Well Creation:**
   - Form N-well and P-well regions via ion implantation:
     - Boron for P-well.
     - Phosphorus for N-well.

4. **Gate Terminal Fabrication:**
   - Create NMOS and PMOS gate terminals using photolithography.

5. **LDD (Lightly Doped Drain) Implementation:**
   - Introduce LDD regions to prevent the hot electron effect.

6. **Source & Drain Formation:**
   - Add screen oxide to prevent channelling during implantation.
   - Perform arsenic ion implantation for source and drain.
   - Anneal to activate dopants.

7. **Local Interconnects:**
   - Remove screen oxide with HF etching.
   - Deposit titanium (Ti) for low-resistance contacts.

8. **Higher-Level Metalization:**
   - Achieve planarization through Chemical Mechanical Polishing (CMP).
   - Deposit TiN and Tungsten for interconnects.
   - Apply a top SiN layer for chip protection.

These steps outline the essential processes in a 16-mask CMOS fabrication, encompassing active region definition, well formation, gate creation, source/drain implantation, interconnects, and chip protection layers.

</details>

<details>
  <summary><b>Tech File Labs</b></summary>

<h2>CMOS Inverter Characterization</h2>  


1. **Clone the `vsdstdcelldesign` Repository:**
   - Clone the `vsdstdcelldesign` repository into your `openlane_working_dir/openlane` directory using the following command:

     ```bash
     git clone https://github.com/nickson-jose/vsdstdcelldesign
     ```

   This command will create a folder named `vsdstdcelldesign` within your `openlane` directory.

2. **Prepare for Magic Invocation:**
   - To invoke Magic and view the `sky130_inv.mag` file, the `sky130A.tech` file must be included in the command along with its path.
   - To simplify this command and reduce complexity, you can copy the `sky130A.tech` file from the `magic` folder to the `vsdstdcelldesign` folder.

3. **Invoke Magic:**
   - Finally, you can easily invoke Magic to view the `sky130_inv.mag` file with the following command:

     ```bash
     magic -T vsdstdcelldesign/sky130A.tech vsdstdcelldesign/sky130_inv.mag &
     ```

   This command launches Magic with the specified technology file and opens the `sky130_inv.mag` layout for viewing and seamless integration.

   <div align="center">
     <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/f37f164f-75fe-4b0c-b5da-f32622f8077b">
   </div>

## Verification and SPICE Extraction for Sky130 CMOS Inverter Layout

To verify that the layout corresponds to a CMOS inverter in the Sky130 process, you can follow these verification steps:

1. **Local Interconnect Layer (Locali):**
   - In Sky130, the first layer is called the local interconnect layer (Locali).

2. **P-Diffusion and N-Diffusion Regions:**
   - Observe the P-diffusion and N-diffusion regions, along with the Polysilicon, to confirm the presence of CMOS transistors.

3. **Drain and Source Connections:**
   - Verify the drain and source connections:
     - The drains of both PMOS and NMOS transistors should be connected to the output port (Y).
     - The sources of both transistors should be connected to the power supply VDD (VPWR).

4. **Library Exchange Format (LEF):**
   - LEF, or Library Exchange Format, provides information about cell boundaries, VDD, and GND lines. It does not contain circuit logic details and is often used to protect intellectual property (IP).

5. **SPICE Extraction:**
   - To extract SPICE data from the Magic layout, follow these commands within the Magic environment using `tkcon`:
     - `extract all`
     - `ext2spice cthresh 0 rethresh 0`
     - `ext2spice`

   This generates the `sky130_in.spice` file.

6. **SPICE Deck Editing:**
   - Edit the `sky130_in.spice` SPICE deck to include the PMOS and NMOS libraries (`pshort.lib` and `nshort.lib`).
   - Incorporate the minimum grid size of the inverter, typically measured from the Magic layout, into the deck as:
     ```
     .option scale=0.01u
     ```
   - Change the model names in the MOSFET definitions to `pshort.model.0` and `nshort.model.0` for PMOS and NMOS, respectively.

7. **Voltage Sources and Simulation Commands:**
   - Define voltage sources and simulation commands as follows for CMOS inverter circuit simulation.
   - `VDD VPWR 0 3.3V`
   - `VSS VGND 0 0V`
   - `Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns 2ns 4ns)`
   - `.tran 1n 20n`
   - `.control`
   - `run`

By following output can be observed

<br>
<div align="center">
  <img src= "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/89a0aff6-dca1-4e33-8f8f-85e7db0afb22">
</div>

<h4>Rise Delay Calculation</h4>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/e92610b4-3675-411e-a295-a13a8e0fb16b">
</div>
  

```
tr = 2.20395 - 2.16095 = 0.043ns
```
<h4>Fall Delay Calculation</h4>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/6da5cfc6-6524-4baf-b342-f69bbfbee5d4">
</div>
  
```
tf = 4.0681 - 4.0392 = 0.0289ns
```

<h4>Propogation Delay Rise</h4>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/d7ecc59c-2643-4d68-9494-a8178e44e0d2">
</div>
  
```
tpdr = 2.1847 - 2.1503 = 0.0343ns
```
<h4>Propogation Delay Fall</h4>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/Physical_Design/assets/140998787/0dcaf738-0a1d-4df1-aa97-5819b7a82ae6">
</div>
  
```
tpdf = 4.05437 - 4.05031 = 0.00406ns
```
</details>

<h2>Day 4</h2>



<details>
  <summary><b>Timing Analysis and Clock Tree Synthesis</b></summary>
  
</details>
<details>
  <summary><b>Clock Tree Synthesis</b></summary>

## Clock Tree Synthesis (CTS)

Clock Tree Synthesis (CTS) is a crucial step in VLSI design, and the choice of a specific technique depends on design requirements, constraints, and goals. Here are various approaches to CTS:

1. **Balanced Tree CTS:**
   - Distributes the clock signal in a balanced manner, resembling a binary tree.
   - Aims to minimize clock skew by providing roughly equal path lengths to all clock sinks.
   - Relatively straightforward but may not be the most power-efficient solution.

2. **H-tree CTS:**
   - Utilizes a hierarchical tree structure resembling the letter "H."
   - Effective for distributing clock signals across large chip areas.
   - Helps reduce clock skew and optimize power consumption.

3. **Star CTS:**
   - Distributes the clock signal from a single central point (star) to all flip-flops.
   - Simplifies clock distribution and minimizes clock skew.
   - May require more buffers near the source.

4. **Global-Local CTS:**
   - Combines elements of both star and tree topologies.
   - Global tree distributes the clock signal to major clock domains.
   - Local trees within each domain further distribute the clock.
   - Balances global and local optimization for chip-wide and domain-specific clocking.

5. **Mesh CTS:**
   - Clock wires arranged in a mesh-like grid pattern.
   - Each flip-flop connects to the nearest available clock wire.
   - Often used in structured designs like memory arrays.

6. **Adaptive CTS:**
   - Adjusts the clock tree structure dynamically based on timing and congestion constraints.
   - Offers flexibility and adaptability but can be more complex to implement.

## Crosstalk in VLSI

**Crosstalk** is a significant concern in VLSI design due to high component integration. It can lead to data corruption, timing violations, and increased power consumption. To mitigate crosstalk, designers employ techniques like optimizing layout and routing, using shielding, implementing clock distribution strategies, and employing clock gating to reduce power consumption during idle states.

## Clock Net Shielding in VLSI

**Clock Net Shielding** is crucial for synchronous operation in VLSI circuits. It isolates the clock network from other signals to reduce interference. Techniques include dedicated clock routing layers, clock tree synthesis algorithms, and buffer insertion for effective clock distribution. Proper clock gating ensures clock signals do not propagate between domains, preventing metastability issues and maintaining synchronization.

 


</details>

<h2>Day 5</h2>
<details>
  <summary><b>Routing and Design Rule Check(DRC)</b></summary>
  
  ## Maze Routing and Lee's Algorithm

Routing, in the context of electronic design automation (EDA), is the process of establishing physical connections between two pins on an integrated circuit. Routing algorithms are designed to take source and target pins and determine the most efficient path between them, ensuring a valid and optimized connection.

One notable routing algorithm is the **Maze Routing algorithm**, which includes approaches like **Lee's algorithm**. This method leverages a grid structure, often resembling the grid used during cell customization, for routing purposes. Lee's algorithm starts with two designated points—the source and target—and utilizes this routing grid to identify the shortest or optimal route between them.

In the Lee algorithm, labels are assigned to neighboring grid cells around the source, incrementing them incrementally from 1 until the path reaches the target (e.g., from 1 to 7). During this process, various paths may emerge, including L-shaped and zigzag-shaped routes. Lee's algorithm prioritizes selecting the best path, typically favoring L-shaped routes over zigzags. If no L-shaped paths are available, it may resort to zigzag routes. This approach proves especially valuable for global routing tasks within the IC design process.

However, it's important to note that while Lee's algorithm is effective for routing between two pins, it can become time-consuming when dealing with a large number of pins, such as those found in complex integrated circuits. In such cases, alternative routing algorithms are often explored to address similar routing challenges efficiently.

<div align="center">
<img src="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/48c7e627-33a7-4cf3-a525-a8f9ff9322f9">
  
</div>

## Design Rule Check (DRC) for Physical Wires

DRC is a critical step in the semiconductor design and manufacturing process, ensuring that a design complies with the predefined process technology rules provided by the foundry. It plays a pivotal role in the physical design flow, guaranteeing that the design adheres to manufacturing requirements and reduces the risk of chip failure, ultimately determining the quality of the chip.

### Some Key Design Rules for Physical Wires

1. **Minimum Width of the Wire:**
   - This rule specifies the minimum acceptable width for wires in the design. Wires must be wide enough to carry the desired current without excessive resistance.

2. **Minimum Spacing Between the Wires:**
   - DRC checks for the minimum allowable distance between adjacent wires to prevent electrical interference or short circuits.

3. **Minimum Pitch of the Wire:**
   - The pitch refers to the center-to-center spacing between wires. DRC verifies that the pitch meets the required minimum value, ensuring proper wire placement and density.

4. **Via Rules:**
   - To address signal short violations or connect wires from one metal layer to another, designers use vias. DRC checks the following aspects of via design:

     - **Via Width:** Ensures that the via's width is within acceptable limits for the chosen technology.
     - **Via Spacing:** Checks the minimum spacing between vias to avoid electrical issues.
     
These design rules for physical wires are crucial for maintaining signal integrity, preventing shorts, and ensuring the manufacturability of integrated circuits.

<div align="center">

<img src ="https://github.com/NiteshIIITB/Physical_Design/assets/140998787/f23f26a3-9d8a-4b58-ba2a-35133404e9be">  
</div>

</details>

<details>
  <summary><b>Power Distribution Network and Routing</b></summary>
</details>


## Reference 
 
- https://github.com/kunalg123/
- https://www.vsdiat.com
- https://github.com/NiteshIIITB/RISC-V










