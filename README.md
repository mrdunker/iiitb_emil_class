# RTL Workshop
This GitHub repository summarises the class work done on Physical Design for ASICs (VL508)

[Day 0 : Open Source Labs installation](#day-0)

[Day 1 : Introduction to Verilog RTL design and Synthesis](#day-1)

[Day 2 : Introduction to timing libs, Efficient flop coding styles, Hierarchical vs. Flat](#day-2)

[Day 3 : Combinational and Sequential optimizations](#day-3)

[Day 4 : Introduction to GLS, blocking vs. non-blocking, Synthesis-Simulation mismatch](#day-4)

[Day 5 : Overview of If, case,for loops, and for generating loops](#day-5)

# Day 0
Following are the steps for the installation of necessary tools:
<details>
<summary> Yosys</summary>
<br />
Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Selected features and typical applications:

- Process almost any synthesizable Verilog-2005 design
- Converting Verilog to BLIF / EDIF/ BTOR / SMT-LIB / simple RTL Verilog / etc.
- Built-in formal methods for checking properties and equivalence
- Mapping to ASIC standard cell libraries (in Liberty File Format)
- Mapping to Xilinx 7-Series and Lattice iCE40 and ECP5 FPGAs
- Foundation and/or front-end for custom flows<br />

Steps to install Yosys:
  
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex 
    libreadline-dev gawk tcl-dev libffi-dev git 
    graphviz xdot pkg-config python3 libboost-system-dev
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install
```
Image after Installation:
![yosys](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/345a1e66-96c9-4baa-b543-4c54a83c7f80)
</details>
<details>
<summary> Icarus verilog</summary>
<br />    
Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format (EDIF). It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.<br />
Icarus Verilog is available for Linux, FreeBSD, OpenSolaris, AIX, Microsoft Windows, and Mac OS X. Released under the GNU General Public License, Icarus Verilog is free software.<br /><br />
Step to install iverilog: 
    
```
sudo apt-get install iverilog
```
Image after Installation:
![iverilog](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/bb03caee-57ee-4d01-bd57-25e85e0f302f)
</details>
<details>
<summary> GTKWave </summary>
<br />
GTKWave is a VCD waveform viewer based on the GTK library. This viewer supports VCD and LXT formats for signal dumps.<br />
Waveform dumps are written by the Icarus Verilog runtime program vvp. The user uses $dumpfile and $dumpvars system tasks to enable waveform dumping, then the vvp runtime takes care of the rest. The output is written into the file specified by the $dumpfile system task. If the $dumpfile call is absent, the compiler will choose the file name dump.vcd or dump.lxt, depending on runtime flags. The example below dumps everything in and below the test module.<br /><br />
Steps to install GTKWave:

```
sudo apt update
sudo apt install gtkwave
```
Image after Installation:
![gtkwave](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/61dea6a3-487c-4308-a8c4-f1d4477c992a)
</details>

<details>
<summary>OpenSTA</summary>
<br />
OpenSTA is a gate-level static timing verifier. As a stand-alone executable, it can be used to verify the timing of a design using standard file formats.

- Verilog netlist
- Liberty library
- SDC timing constraints
- SDF delay annotation
- SPEF parasitics

OpenSTA uses a TCL command interpreter to read the design, specify timing constraints, and print timing reports.<br /><br />
Steps to install OpenSTA:
```
Went to the GitHub repo: https://github.com/The-OpenROAD-Project/OpenSTA
and did the process mentioned within (installed the prerequisites and installed OpenSTA with Cmake).
```
Image after installation:
![opensta png](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/bcc4cf94-2696-4f19-bfcd-20a48424276f)
</details>
<details>
<summary>Ngspice</summary>   
<br />
Ngspice is an open-source electronic circuit simulator software that allows engineers, researchers, and hobbyists to simulate and analyze electronic circuits. It is a part of the Spice (Simulation Program with Integrated Circuit Emphasis) family of circuit simulation tools, which have been widely used since the 1970s.

Ngspice is an evolution of the well-known Spice3 program, incorporating additional features and improvements. It is compatible with various operating systems, including Windows, Linux, and macOS. The software is primarily used for simulating analog, digital, and mixed-signal circuits.<br /><br />
Steps to install Ngspice:

```
After downloading the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory, unpack it using:
$ tar -zxvf ngspice-40.tar.gz
$ cd ngspice-40
$ mkdir release
$ cd release
$ ../configure  --with-x --with-readline=yes --disable-debug
$ make
$ sudo make install

```
Image after installation:
![ngspice](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/22a4dab7-b6dc-4d07-b2a8-8f2d24b06568)
</details>

<details>
<summary>magic</summary>
<br />
Magic is a popular open-source tool used for ASIC (Application-Specific Integrated Circuit) design and layout. It is part of the Electric VLSI Design System and provides capabilities for creating and editing integrated circuit layouts. Magic is widely used in the semiconductor industry and academic settings for various ASIC design tasks.

<br /> Steps to install magic:

```
$   sudo apt-get install m4
$   sudo apt-get install tcsh
$   sudo apt-get install csh
$   sudo apt-get install libx11-dev
$   sudo apt-get install tcl-dev tk-dev
$   sudo apt-get install libcairo2-dev
$   sudo apt-get install mesa-common-dev libglu1-mesa-dev
$   sudo apt-get install libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
make install

```
Image after installation:
![magic](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/79c38c91-a0be-4b4b-a334-bb1ef3754af8)
</details>

<details>
<summary>OpenLANE</summary>
<br />
OpenLANE is an open-source ASIC (Application-Specific Integrated Circuit) design flow and methodology that aims to automate and standardize the process of designing and fabricating custom digital integrated circuits. It is developed and maintained by the OpenROAD (Open Research for Advanced Nanotechnologies) project, which is a collaboration of various academic and industrial organizations.

Key components and features of OpenLANE include:<br />
- RTL Synthesis: The flow starts with RTL synthesis, where the RTL code is converted into a gate-level representation using synthesis tools.
- Floorplanning: OpenLANE performs automatic floorplanning, which involves arranging the logical blocks and components on the chip's physical layout.
- Placement: It automatically places the gates and cells on the chip, optimizing for area, power, and performance.
- Clock Tree Synthesis (CTS): OpenLANE generates a clock tree to efficiently distribute the clock signal across the chip.
- Routing: The tool performs automatic routing to connect all the elements on the chip while adhering to design rules and constraints.
- Static Timing Analysis (STA): OpenLANE performs static timing analysis to verify that the design meets the required timing specifications.
- Design Rule Check (DRC) and Layout versus Schematic (LVS) verification: OpenLANE checks the physical layout against manufacturing rules (DRC) and compares the layout to the original schematic (LVS) to ensure consistency.
- Configuration and customization: OpenLANE allows users to configure various aspects of the design flow and customize different steps based on specific design requirements.
<br />
Steps to install OpenLANE:
    
```
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git

sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 

# After reboot
docker run hello-world

```
Image after installation:
![docker](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ee51e4a0-bb4e-4e41-8ff6-e4cf30dcfcb7)
</details>

# Day 1
<details>
  <summary>Introduction</summary>
  <br />
  This section mainly focuses on Iverilog,GTKwave, and Yosys. The simulation and synthesis of a basic 2x1 mux is also done.<br /><br />
 A simulator refers to a software tool or program that simulates the behavior of the digital design described at the RTL level. It allows designers to test and verify 
 the functionality of their digital designs before actual hardware is fabricated. Simulators take the RTL description and execute it in a software 
 environment, allowing the designer to observe how the design behaves under different conditions and inputs. The simulator looks for changes in the input.Upon change inn 
 the input the output is evaluated. If no change in input is observed, there will be no change in output. 
 Icarus Verilog is an open-source RTL simulator that supports Verilog. It's widely used in academia and smaller projects due to its free and open nature.<br /><br/>
 A test bench is a set of simulation codes and associated data that is used to verify the correctness and functionality of a digital design described at the Register 
 Transfer Level (RTL) or other abstraction levels. It serves as a virtual environment in which the design can be tested before it's physically implemented in 
 hardware.The design may have  more than one input and output, while the Test bench doesn't a primary input or a primary output.<br /><br />

 **The Iverilog-based simulation flow is that of below:** <br />
 ![simulation flow](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/3d965540-bb96-4bb3-9284-b446b57621fb)

 After Simulation Synthesis is required. For this, we are using a tool called Yosys, which will give us a netlist, which is a representation of the design in standard 
 cells. There are certain commands like read_verilog, read_liberty, and write_verilog used for the synthesis process. After Synthesis verification of the netlist is also 
 done. <br /><br />
**A basic synthesis flow is as shown below:** <br />
 ![synthesis flow](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/abcd8a60-8222-433e-a53e-ff1485ecd810)
 <br />( .lib is explained in the 'Other Relevant Data' section)<br />
 <br />The set of primary inputs or primary outputs will remain the same in both RTL design and netlist,i.e. The testbench used for simulation and verification is same.<br />
</details>
<details>
    <summary>Verilog codes</summary>
  We are simulating a simple 2x1 mux using iverilog and GTKwave, the codes have been taken from the GitHub repo:<br />
  https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
  <br /><br />
  The above git has been cloned and saved in the local system as shown below.<br />
  
  ![git_clone](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/05e19c55-237f-47b0-b2df-4a4839a12e2c)
  
</details>

<details>
    <summary>Simulation: iverilog and GTKwave</summary>
  <br />
  The below Linux shell commands are typed into the terminal to get execute the mux design file and the test bench. A vcd(value change dump) file is generated
  and that is opened using GTKwave as shown below. 
  
```
iverilog good_mux.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```
Below are the Shell commands screenshot for the execution of both .v files (design and test bench):<br />
![iverilog_gtk](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/69775736-ff34-4c3c-8231-87dd9f111e2b)
<br />
<br />
Below is the GTKwave output for the same:<br />
![gtk](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/af652fdb-1222-484f-820c-51f3d4de732f)
</details> 
<details>
    <summary>Synthesis: Yosys</summary>
<br />
Here we are Synthesizing a basic 2x1 mux which we have simulated in iverilog and GTKwave as shown in the above sections.<br />
In the directory, we need to input the shell terminal command yosys for synthesis below shown are the commands used:
  
  ```
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> read_verilog good_mux.v
yosys> synth -top good_mux
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
yosys> show
  ```
To generate the netlist and view the 'netlist.v' file following commands are used:

 ```
yosys> write_verilog -noattr good_mux_netlist.v
yosys> !gvim good_mux_netlist.v
  ```

<br /> **The Screenshot below shows how commands read_liberty and read_verilog are done:** <br />
![synth1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ef674f5e-94f0-4310-bd4a-dd87ab9c6a24)
<br />

**The Screenshot below is of the syth -top <name.v> command:** <br />
![synth2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/35ee2316-6785-4509-a254-1d9e7607336f)
<br />

**The Screenshot below shows how the command abc -liberty is done:** <br />
![synth3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/2f53dd5c-b782-4f0b-8185-c334c9d3f13a)
<br />

**The Screenshot below shows how the show command is done:** <br />
![synth4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f944ec4b-904a-45c4-8f3a-833a0753d9cb)
<br />

**The Figure below is the generated synthesized design:** <br />
![synth5_img](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/e036f7ba-aa4c-46ba-bfec-f26cdb14a426)
<br />

**The Screenshot below shows the 'write_verilog -noattr<'name of netlist'>' command and the <netlist>.v file:** <br />
![synth6_final](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/c0691b18-bae6-46ac-bd23-f03e20d01d6b)
  
</details>
<details>
    <summary>Other Relevant data</summary>
  <br />
  
  **RTL Design:** <br />
RTL stands for "Register Transfer Level," and in the context of digital hardware design, RTL design refers to the process of describing the behavior of a digital circuit 
or system using a hardware description language (HDL) at the register transfer level. It's a crucial step in designing complex digital systems such as microprocessors, 
application-specific integrated circuits (ASICs), field-programmable gate arrays (FPGAs), and more.
<br /><br />
In RTL design, the designer specifies the functionality and behavior of the digital system using a high-level hardware description language like Verilog or VHDL. This description focuses on the flow of data between registers and the operations that take place on that data.<br />

**Synthesis:** <br />
RTL design is the process of transforming a high-level functional description of a digital system into a gate-level netlist that can be physically implemented on 
hardware platforms. This process involves mapping the logic to standard cells, optimizing for performance, and ensuring timing requirements are met.
A Design is converted into gates and the connections are made between those gates, the final output file is what is termed as a netlist.<br /><br />

### What is .lib ?

1. .lib is a collection of various logical modules
2. It includes basic gates like and, or etc...
3. There are different flavours(versions) of the same gate
    - Slow
    - Medium
    - Fast

We need different flavors of gates because combinational delays in logical paths will determine the maximum speed of operation of digital logic circuits.<br />
<br />
### Why do we need different flavors of gates?

1. Different flavors of gates are necessary to provide a diverse toolkit for designing and implementing electronic circuits. They cater to various logical functions,
  optimization requirements, noise considerations, and implementation constraints, enabling the creation of complex and efficient systems.
2. Combinational delays in the logic path determine the max speed of operation of a digital logic circuit.

<br />

![dff_combi](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/01b72e99-69f9-4453-9e17-8f2a082de217)

- Based on the figure shown above, Tclk **Tcq_a**,**Tcombi**,**Tsetup_b** are the time period of the clock,propagation delay of A, Combinational delay, setup time of B 
  respectively.
- **Tclk > Tcq_a + Tcombi + Tsetup_b**
- one clock pulse should be long enough for the delay of the 'A'-D.FF,combinational delay and setup time for 'B'-D.FF to be incorporated.
- **Tsetup_b** is the time required for the the 'B'-D.FF data to be stable.

There is also a need for slow cells. The question of why we need them arises.<br />
- To ensure there are no 'HOLD' issues at B-D.FF, we need certain cells to work slowly
- We need cells that work fast to meet the required performance and we need cells that work slow to meet HOLD.

## Faster Cells Vs. Slower Cells:
- A load in digital logic is a capacitor
- A faster charging or discharging means less delay
- To increase the rate of charging or discharging we need to widen the transistors.
- Wider transistor gives lower delay: but more is required and more power is required
- Narrow transistors give out more delay  : we need less area and less power is consumed.


</details>

# Day 2
<details>
  <summary>Introduction</summary>
  In this section, we will briefly go about understanding a bit more about the .lib file and other stuff.
</details>
<details>
  <summary>Overview on .lib</summary>
  Firstly lets open the sky130_fd_sc_hd__tt_025C_1v80.lib using the Vim editer.<br />
 
  ```
  gvim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  ```
The nomenclature of the above .lib file is :
1. sky - skywater
2. 130 - 130 nanometer(nm)
3. tt - typical  library
4. 025C - Temperature
5. 1v80 - Voltage
<br />

When we look into a library 'Process Voltage Temparature' is relevant for a design to work.<br />
1. Process is important because of variations in the fabrication.
2. Voltage is important because there will be variations in circuit behaviour due to the same.
3. Semiconductors are very dependent on temperature and we would need the design to work in a wide range of        geographies having different temperatures.

We need to factor in all these conditions when designing and so our libraries will also model these specifications.<br />

Below figure shows the the library sky130_fd_sc_hd__tt_025C_1v80.lib on Vim edior:<br />
![day1_1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/e2e76a6b-3316-45ee-9b08-71f0ba45e4e8)

The Below figure shows both the library sky130_fd_sc_hd__tt_025C_1v80.lib and the .v file sky130_fd_sc_hd.v which consists of the design of any given cell in the above-mentioned library:<br/>
![day1_2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/cb52c2a2-9905-42a5-8c7d-1b8e9b9c0d05)

The Below side by side figure shows the details of different flavours of a 2 input and gate:<br />
Here it is seen that the area of all three are different.On Day 1 we discussed the effect of the area in efficiency and delay etc..<br />
![day1_3x](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/6d5738b1-5fa3-4a08-8103-c7ff45b55afe)

Below are some of the Vim commands used:<br />
```
:syn off "turn off highlighting
:se hls  "highlight cell
:se nu   "see line numbers
:g//     "see all the cells('highlighted ones')
:sp <directory>    "open a file with a directory along with 
:vsp     "opens the same file again side by side         

```
</details>
<details>
  <summary>Hierarchical Vs. Flat Synthesis</summary>
  
  ### Hierarchical Synthesis:
In hierarchical synthesis, the design of a complex digital circuit is divided into smaller, more manageable modules or blocks. Each module represents a functional unit or a specific sub-task the 
overall design. These modules are designed and optimized separately, and then they are integrated into the larger system. The design hierarchy can have multiple levels, with modules containing sub-
modules and so on.<br />

  ### Flat Synthesis:
  In flat synthesis, the entire digital circuit is synthesized as a single monolithic unit, without breaking it down into smaller modules. This approach is suitable for smaller designs where the 
  complexity doesn't warrant a hierarchical organization.<br />

  In this section, we will synthesize the same design in both Hierarchical and Flat to illustrate the difference in the netlist of both.<br />
  <br />
  **Hierarchical illustration**<br />
  (The Figure below shows the schematic diagram of a design named multiple_module.v:)<br />
![heir1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/602be1f3-2704-4d82-b754-688b467b89cb)
<br />
It is seen that everything is divided into smaller submodules.<br />

(The figure below is the netlist for the hierarchical design:)<br />
![heir_netlist](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/cd4d44e5-2681-4387-a000-87b4f1668e5f)
<br />
<br />
**Flat illustration**<br />
(The figure below shows the flattened-out netlist for the flattened design:)<br />
![flat](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/39b67082-8c56-4b3a-812c-03ef7bc66d34)
<br />
We write the 'flatten' command just before the write_verilog command to flatten the netlist.<br />
<br />
(The figure below shows the schematic diagram of the design).<br />
![flatten](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ebb93a7c-9fee-40a7-b18a-637c54bdfc6f)
<br />
<br />

**Submodule Level Synthesis**<br />
Why is this done?
1. When we have multiple instantiations of the same module we prefer the submodule level by synthesis.
2. We might also want to use the divide and concur procedure, divide up the circuit to get the best possible design at the top level.

We need to make a small change in the synth command in yosys:

```
synth -top <sub_module_name>
```

<br />
(Illustrated below:)<br />

![submd1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/6ea4c027-ad4f-4a37-9fe8-bed3113761db)
<br />
(The design diagram for the same is shown below:)<br />

![sub1netlist](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/df1060dc-50eb-4943-8862-b787ace3629c)
  
  
</details>

<details>
  <summary>Various Flops and Flop coding styles</summary>
  <br />
  Here we are going to look at some questions such as the ones below:
  
  1. How to code a flop.
  2. What are the flops that are present
  3. What are the coding standards for it.
     
  #### Why do we need to use flops? <br />
  Consider the logic diagram given below consisting of an and gate and or gate.<br />
  there exists a propagation delay, and due to this the output glitches. This is a serious issue as the number of combinational circuits increases the number of glitches also increases.<br />
  
  ![logicdiagram](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f20e2466-21d0-4a3a-974f-010eb8ef45d5)

  (In the figure below the glitch caused in the above logic diagram is illustrated in the blue shaded area:)<br />
  ![glitch](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/701d8ca3-badb-4587-8324-c110309eef6c)

  <br />
  Like mentioned above, more combinational circuits mean more glitches so to avoid glitches, we need to store the data, for that we use flops.<br />
  (The figure below illustrates the above problem and solution:)<br />
  
  ![combi](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/841dc701-aad2-4e15-82d9-d969d0ab10cc)
  <br />
  D-ff's give output only at the posedge of the clk. So, the next combinational circuit (block) will see only a stable input.

  ### How do I code the Flop?
  Below are the three different ways in which we can code the flop.
  1. Synchronous & Asynchronous reset
  2. Syncranous reset
  3. Asynchronous reset

  ![dffs](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/19af309b-8fa9-49bd-b0f4-4c235a07bc1c)

</details>
<details>
  <summary>Lab flop synthesis simulations</summary>
  <br />
  Here we are going to simulate D-Flip flops with Asynchronous reset & set, Synchronous, and Synchronous & Asynchronous reset with Iverilog and GTKwave.<br />

  ### Asynchronous reset:

  Here we are going to be using a .v file 'dff_asyncres.v' and its corresponding testbench. Run it on verilog and simulate it on GTKwave ash shown below.<br />
  ![d](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/72d36956-ffea-401c-ba45-2cb08adf5ce1)
  <br />
  Below we can see the output waveform of the design.<br />
  In this case, at around the 550ns range, we see that the output q follows the clk. i.e. q is synchronous with the clock.<br />
  ![d1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/81d9993f-d83b-48d0-a963-18b7afa9923c)
  <br />
  If we consider this point around the 1090ns-1100ns range. when the async_reset is high the output 'q' will immediately go low. This is called asynchronous reset. As illustrated below.<br />
  ![d2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a286d6dc-876b-4044-99bb-16ad429947be)

  ### Asynchronous set:
  <br />
  Here we do the same. The simulation output waveforms are shown below.<br />
  In the below waveform, in between the ranges of 500ns to 600 ns the async_set is low which makes the output looks for changes in 'd' upon the clock.<br />
  
  ![ds1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/46d2c9c8-fa56-40a7-9f5f-ef59a4265537)
  <br /><br />
  In the following waveform, when the async_set is high the output will be set high and will not follow  the 'd' input.<br />
  
  ![ds2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/b203a94a-7fc0-4772-8787-d3b0afe513a4)
  
  ### Synchronous reset:
  <br />
  The steps for simulation are the same except here we use the dff_syncres.v file and its corresponding test bench.<br />
  In the below waveform, we can see between the 500ns-600ns range, when the sync_reset is high, the output follows the clock.<br /> As shown below:<br />
  
  ![db1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/aefed66f-eae9-498d-b0e5-57fa561f8fae)

  ### Synthesis of the above three designs:
  <br />
  Synthesis diagram for Asynchronous reset:<br />
  
  ![nl1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1dd3e6a7-d365-46ee-ba6b-695e74024159)
  Synthesis diagram for Asynchronous set:<br />
  
  ![nl2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8d59f4b8-ea11-44eb-adf7-928cd7b16495)
  Synthesis diagram for Synchronous reset:<br />
  
  ![nl3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/fe0a583c-c216-482e-816a-2ea4b3d2a88b)
  <br />
  <br />
  During synthesis, after the **synth -top** command in Yosys, we should use the following command to map DFF cells to sequential cells.
  
  ```
  dfflibmap -liberty ..<directory of the .lib file>
  ```
  
  
</details>
<details>
  <summary>Optimizations</summary>
  <br />
  This section deals with some special cases. Particularly two peculiar .v files.<br />
  let's open them in the Vim editor using the following Shell command:<br />
  
  ```
  gvim mult_*.v -o
  ```
Here we are opening two files mult_2.v and mult_8.v.<br />
<br />
**Let us consider the first one 'mult_2.v' :** <br />
The below figure shows the mult_2.v file.<br />
![ex3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/9fa56ed3-a9ab-412a-9e15-24a3dc92c83b)
<br /><br />
The block diagram below explains the basic functionality of the design:<br />
![ex1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/d4237401-d4f0-4ed5-b891-ea6a58106ddd)
<br /><br />
But as being a special case there must be a **twist** to it.<br />
Apparently, there is no need for any extra hardware components. In the below figure, we can see the input 'a' and output 'y'.<br />
(The output y is basically zero appended to 'a' {a,1'b0}. It is illustrated below.)<br />

![ex2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/d32db5ed-227b-47ef-a8b6-1e38c4ede5bd)
<br />
(In the below screenshot, we can see there are no hardware components required.)<br />
![m1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f7a2e0ac-482f-4f5b-95b6-6d2a40efa952)
<br />
(The below diagram shows the schematic diagram for the same:)<br />
![m1a](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/78f32166-5c88-44ad-95be-0ea497aaeba0)

**Let us consider the second one 'mult_8.v' :** <br />
(The below figure shows the mult_8.v file)<br />
![t1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/5f27eee1-ffd6-4a05-b034-0b473b2d555f)
<br />
Here we are doing ax9=y, which can be rewritten as {ax(8+1)=y}<br />
ax9 = {a,0,0,0} + a ----> {a,a}<br />
![t2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/dae94818-b88d-427f-892b-9ee7736f0c04)
<br />
(In the below screenshot, we can see there are no hardware components required.)<br />
![m2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/acef047d-27cd-4ba0-b233-3042b8f70059)
<br />
(The below diagram shows the schematic diagram for the same:)<br />
![m2a](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8ac4fe85-e8c8-4267-95d6-1b573f5c6815)


</details>

# Day 3
<details>
<summary>Introduction to optimizations</summary>
  <br />
  Here we are going to be looking at logic optimizations.<br />
  
  There are two kinds of logic optimizations:<br />
  
  1. Combinational Logic optimizations
  2. Sequential Logic optimizations
<br />
 Let us look into those.<br/>

 ## Combinational logic optimization: 

- It is done to get the most optimized design
- The most optimized design will be very efficient in both its area and power characteristics.

  Below are the two techniques used for the same:<br />

  1. Constant Propagation
  2. Boolean logic optimizations

  ### Constant propagation

  Let's consider Fig: A having an output Y. When deriving that circuit using MOS transistors we will need six MOSFETS.<br />
  if we consider input a = low. The total logic circuit will reduce to Fig: B. And has only a requirement of one inverter i.e 2 MOSFETS.<br />
  
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/79f55e71-4505-40e9-8284-53224481bd08)
<br />

  ### Boolean logic optimizations

   In case of this, the synthesizer uses either KMAPS or Quinse McCluskey methord to find the most optimized logic.<br />
   Let us consider the image below:<br />
   ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f43837bd-ca89-45df-885d-31d1bd5bf91d)
   <br /><br />
   Here we are implementing y = a?(b?c:(c?a:0)):(!c).Which is not optimized<br />
   The general output will be y = a'.b' + a.[ b.c + b'.a.c ]. In simplifying this we will get ~( a ^ b ).<br />
   The Synthesis tool does these kinds of optimizations to get the most optimized logic.<br />

## Sequential logic optimizations:
  There are two types mostly:
  
  1. Basic : (Sequential constant)
  2. Advanced : (State optimization, Retiming, Cloning)
     
 ### Sequential Constant
 ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8a0d82fa-4735-4273-9562-6bbb62a545d0)

 Consider the above figure Fig: A.<br />
 if there is a reset q =0, if there is no reset 'q' is again 0 since it follows 'd' and d=0.<br />
 And so it propagates y=1 always for this case. Effectively we don't have a need for the logic gates in the figure.<br /> 
 <br />
 Now in another case in the figure below:<br />
 ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/0a0913a2-8c7e-46d7-84a8-a8136f48b97a)
 <br />
 When the set is applied q=1 and when set in not applied q=0.<br />
 It can be explained through the timing diagram Fig: C. q will wait till the next **posedge** of the clock to go down. There will be a slack for q.<br />

 ### State optimization

 State optimization in ASIC design is about finding the best trade-offs among performance, power efficiency, area utilization, and other design objectives
 to create an effective and efficient custom integrated circuit for a particular application.<br />

 ### Re-timing

It is a technique used to optimize the timing performance of a digital circuit by moving registers (flip-flops) to different locations within the circuit <br />
without changing its functionality. The primary goal of retiming is to improve the critical path delay, which is the longest path through the logic circuit that determines the maximum operating frequency.<br />

### Sequential logic cloning

Also known as flip-flop cloning or state machine cloning, is a technique used to replicate or duplicate certain portions of sequential logic circuits.
This technique is employed to improve performance, reduce critical path delays, or optimize power consumption in a design without altering its functional behavior.<br />

</details>

<details>
  <summary>Lab Combination logic optimizations</summary>
  <br />
  Here we will be doing the labs that illustrate combinational logic optimizations.<br />
  We will also be using a Yosys command to purge all unused cells:

  ```
  opt_clean -purge
  ```
  <br />
  
  ### LAB 1:  
  
  ![x0](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/66b55f2f-84db-4585-9092-fef98a2ba084)
  <br />
  In the above code, if we look at it. It is effectively a 2x1 mux which can be simplified to a 2 input and gate.<br />
  So, by doing the opt_clean -purge command we can purge unnecessary cells to make it optimized.<br />
  ![x1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/9c697ebe-6d6c-4a0b-af66-d8dd6a7d642f)
  <br />
  The Schematic diagram is shown below and as expected we have a 2 input and gate.<br />
  ![x2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/4304212b-e48e-4f64-81f7-cb648caeea5f)

  ### LAB 2:
  
  Here we are performing the synthesis of opt_check2.v. it is done the same way as **LAB 1** <br />
  We get an optimized design of a 2-input or gate.<br />
  Relevent Screenshots are attached below.<br />
  ![a0](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8484ce20-e2a9-49f5-a96d-b7db0c2b46f7)
  ![a1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/3c3571d9-0498-4ff9-8a3e-516c513056fa)


  ### LAB 3:
  
  Here we are performing the synthesis of opt_check3.v. it is done the same way as the above labs <br />
  Relevent Screenshots are attached below.<br />
  ![y0](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/846bfd51-46b1-4e91-87ab-a03184260c38)
  ![y1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/563d5225-85bf-4d71-a8bf-dbecc13e41a3)


  ### LAB 4:
    
  Here we are performing the synthesis of opt_check4.v. it is done the same way as the above labs <br />
  Relevent Screenshots are attached below.<br />
  ![t1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/55b15def-41ee-46d5-bfe9-dbcac222f34b)
  ![t2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/cd28a54d-c45f-4d07-99db-f84912724f1f)


  ### LAB 5:

  Here we are performing the synthesis of multiple_modules_opt.v. it is done the same way as before but here we have to flatten the design.<br />
  Relevent Screenshots are attached below.<br />
  ![r0](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/6aac57c4-eaa9-4766-bfed-1c7c855620d4)
  ![r1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/79488696-2c93-4336-aeef-b6b058dc03f1)

</details>
<details>
  <summary>Lab Sequential logic optimizations</summary>

  ### LAB 1:

  Here we are going to simulate and synthesize two .v files,'dff_const1.v' and 'dff_const2.v'.<br />
  Below are the .v files of the above-mentioned:<br />
  ![dff1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8e643380-c45f-49fa-a7fb-dd9cea1f4393)
  <br />
  The simulations of the same are shown below:<br />
  ![dff2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8cf12e40-2aa6-4c38-94e5-9cfe934e2c54)
  <br />
  The optimized synthesized diagram of dff_const1.v is shown below and is as expected.<br />
  ![dff3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a3744ab6-08b6-4fbb-b5c1-1cc61a76f21b)
  <br />
  The optimized synthesized diagram of dff_const2.v is shown below.<br />
  Here as per the simulation, we saw regardless of input and reset the output is always high.<br />
  ![dff4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1b36fbe1-6925-493c-873d-9e35bbd6d36d)
  <br />

  ### LAB 2:

  Here we are going to simulate and synthesize dff_const3.v .<br />
  ![dff1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/d7d5c0d7-2ca7-4d75-93f1-df91cc68bb58)
  ![dff2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ea204811-7f02-4302-9734-254ba6d8e115)
  ![dff3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a5dab47a-cc74-472b-b252-cdf9b60093b5)

  ### LAB 3: 
  
  Here we are going to simulate and synthesize dff_const4.v .<br />
  ![l41](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a8da7d99-7ad6-4674-8d9c-8836579889aa)
  ![l42](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ab799a5b-4526-4468-a8c0-7c83ed1661da)
  ![l43](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/80089a11-d320-40ab-b780-ae7a512405be)

  ### LAB 4:

  Here we are going to simulate and synthesize dff_const5.v .<br />
  ![dff1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/93d6183a-3fe2-43a7-857c-474975f031c4)
  ![dff2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8c3c93c7-f778-4ded-809e-72c4f4b5a42a)
  ![dff3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/913c8492-d63c-44b0-8381-9d3366ca8ac0)
  
</details>

<details>
  <summary>Sequential optimization for unused outputs</summary>
  <br />
  <br />
  This is a very important optimization technique which can be illustrated by the example below:<br /><br />
  First, we are going to synthesize ' counter_opt.v ' and see the synthesized design diagram.<br />
  
  ![ct1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/497d7fe1-d70e-46b1-876b-7944a1363651)
  <br />
   ![ctx](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/04e0dc24-f48d-4c02-8c2d-36b5575e9214)
  <br />
  The two states count[2] and count[1] are **unused**.<br />
  The synthesizer automatically optimizes the design to make it like the below, only using **one FF instead of three**.<br />
  ![ct2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a7d3f233-67f2-4d59-9f9d-30abf3a498b9)
  <br />
  ![ct3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/28ea9f29-4cf5-46e6-8dc4-b06d8d6c94da)
  <br />
  <br />

  ### If we were using count[2] and count[1] also in the above code:<br />
  ![x1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a0be1de9-9c36-4b67-86f6-4728b66e11b3)
  <br />
  The synthesizer would use **three FF's** as shown below:<br />
  ![x2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f9edfbec-e202-484e-8d1b-ebea6d5dca3f)
  <br />
  ![x3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a9030b45-457f-4d69-9e15-f230cac3d39f)
  <br />
  This optimization is so important as illustrated because it saves a ton of space, and speed, and improves efficiency in general.

  
</details>

# Day 4

<details>
  <summary>Gate Level Simulations (GLS) and Synthesis level mismatch</summary>
  <br />
  
  ### What is GLS?

  It is basically running the testbench with netlist as Design under Test (DUT).<br />
  Netlist is logically the same as that of RTL code so the same testbench will fit.<br />
  <br />

  Why do we use GLS?<br />
  1. To verify logical correctness after synthesis
  2. To ensure the timing of the design is met: for this, GLS needs to be run with delay annotation.

  GLS using verilog is as illustrated in the picture below:<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/7780810d-1928-44ad-91ce-9f140f877c7a)
  <br />
  If gate-level models are delay annotated then we can use GLS for timing validation.<br />
  <br />

  ### Synthesis Simulation mismatch

Synthesis simulation mismatch refers to a discrepancy or misalignment between the expected behavior of a system or device, as predicted by a simulation or modeling process, and the actual behavior 
observed in the physical implementation or real-world operation of that system or device. This term is often used in fields such as electronics, engineering, and computer science, where 
simulations are employed to model the behavior of complex systems before they are physically constructed or deployed.<br />

Synthesis simulation mismatch can lead to unexpected problems, performance degradation, or failure of the designed system. Engineers and designers often work to minimize these mismatches by 
refining simulation models, improving manufacturing processes, and conducting thorough testing and validation of designs.<br />

There are mainly three ways mismatches occur:<br />
1. Missing sensitivity list
2. Blocking vs Non-Blocking assignments
3. nonstandard verilog codes

### Missing sensitivity list

Let us remember that a simulator checks for changes in activity, and look at the code shown below.<br />

```
always @(sel)
begin
if (sel)
 out = i1;
else
 out = i0;
end

```
In the above code the always block only checks for 'sel' changes hence we don't get the exact required output.<br />
To resolve this we should use:<br />

```
always @(*)
```
Here the always block will get evaluated for any signal change. Hence, we will get the expected output.<br />

### Blocking & Non-Blocking assignments

Assignments happen inside the always block.<br />

Blocking:<br />
- The '=' sign is used to represent blocking assignments
- It executes the statements in the order it is written.
  
Non-Blocking:<br />
- The '<=' sign is used to represent non-blocking.
- This executes all the RHS when always block is executed and assigned to LHS.
- Parallel evaluation is being occurred here.

### Caveats with blocking

Let's consider the below codes:<br />

```
code 1:
if (reset)
  begin
    q0=1'b0;
    q =1'b0;
  end
else
  begin
    q=q0;
    q0=d;
  end

code 2:
if (reset)
  begin
    q0=1'b0;
    q =1'b0;
  end
else
  begin
    q0=d;
    q=q0;
  end
```

Here you can see there is not much difference between code1 and code2 except we are interchanging the positions of assignments in the else condition of code2.<br />
we will get a drastic mismatch because of this as illustrated by the figure below.<br />

![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/208bf03e-bd09-49cb-a578-7bd0133a8a89)
<br />
The mismatch is very much evident here and for this reason, we must use non-blocking codes. Which will give no mismatch.<br />
The keynote is we always use non-blocking for writing sequential circuits.<br />
<br />

Let us consider another example, a combinational circuit this time.<br />

```
code 1:
always @(*)
begin
  y  =  q0 & c;
  q0 =  a  | b;
end

code 2:
always @(*)
begin
  q0 =  a  | b;
  y  =  q0 & c;
end

```

For code 1: The **old** q0 value is used in the second statement.<br />
For code 2: The **new** q0 value is used in the second statement.<br />
<br />
The funny thing here is that both the circuits after simulation will be the same but the synthesized circuits will be different.<br />
<br />
Due to all these issues, it is very paramount to check for synthesis & simulation mismatches. So for that, we use **GLS**

</details>

<details>
  <summary>Lab GLS & mismatch</summary>
  
  ### LAB 1
  
  The below-given file is the .v file that we have to simulate and synthesize:<br />
  ![t1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/0cc82ee6-0333-420f-8d56-a9409bc77bfe)
  <br />
  First, we are going to simulate the file with iverilog and GTKwave using the testbench.<br />
  ![t2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ddb56453-993d-42b3-a92b-e9168fcf4ac8)
  <br />
  Then we are going to synthesize and create a netlist file for the same.<br />
  ![t3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/24f5a9b4-8e3e-4e02-86c5-212d80121de3)
  <br />
  Then we are going to simulate it again with the newly created netlist file, the Verilog models, and the testbench using iverilog and GTKwave.
  <br />
  ![t4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/9a3f4be1-e597-4fb8-b11d-e85f7a04e8e1)
  <br />
  We will get the following waveform in the GTKwave which matches our previous waveform.<br />
  ![t5](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/29db9b6d-99fc-43f5-aec7-db04b0e1516d)
  <br />
  
  ### LAB 2

  The below-given file is the .v file that we have to simulate and synthesize:<br />
  ![bm0](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/01bce409-7839-41b5-9aeb-3683dc541288)
  <br />
  We will get a waveform like this which is not matching a 2x1 mux waveform(it is seen as incorrect):<br />
  ![bm1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/b4345419-94da-4e24-aeb0-84e5a538de05)
  <br />
  On synthesizing it, it is seen as a normal mux. We create a netlist for it also.<br />
  ![bm2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/72cf06dd-2d0f-42ed-bb51-b59c72a53cc0)
  We will see a stark difference in the pre and post-synthesis waveforms. This is the Synthesis-Simulation mismatch.<br />
  ![bm3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/e8dfca35-4c4a-4db1-b921-8371eb6d84c3)
  <br />

</details>

<details>
  <summary>Labs Blocking and Non-Blocking</summary>

  ### LAB 1

  We are going to see the Synthesis-Simulation mismatch caused by **blocking statement**.<br />
  The below-given file is the .v file that we have to simulate and synthesize:<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/6b7d94cf-7a1b-424f-91f5-917ea0104d91)
  <br />
  We will get a waveform like this which is not matching the design **d = ((a|b)&c)**.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/64e334d3-1a21-4229-ac1c-f107c0ed1136)
  <br />
  On synthesizing it, we will get the required design diagram. A netlist is also created for the same.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/b5afb83b-99f5-4276-94ac-b675358843cd)
  <br />
  We will see a stark difference in the pre and post-synthesis waveforms. This is the Synthesis-Simulation mismatch caused by **blocking statement**.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/76580932-811c-4bc4-94d2-e403f2bfa3af)

</details>

# Day 5

<details>
  <summary>If case constructs </summary>
  <br />
  <br />
  Here we are going to discuss If else statements, case statements and the effect of them.<br />
  if statements are going to be of the below syntax.<br />

  ```
  if <condition 1>
    statements
  else if <condition 1>
    statements
  else
    statements
  ```
 
 The equivalent logic diagram is:<br />
 ![Screenshot from 2023-08-14 21-36-51](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ce708333-4177-42a2-9af6-ee21ed1561fb)
 <br />

 There is an issue with if statements:<br />
 
 - It can cause inferred latches.
 - Inferred latches are caused because of unknown cases. eg: if we forget to put the else condition.
 - We can say Inferred latches are due to bad coding styles.

 ![Screenshot from 2023-08-14 21-45-48](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1b66f734-7568-4753-b9a6-b50ed2dfab19)
 <br />

 ### Exceptional cases

 There are some exceptional cases to the above-mentioned.<br />
 for example, In the case of counters, we can avoid the use of the else condition.<br />
 Let us consider the code below for a counter.<br />

 ```
 always @(posedge clk, posedge reset)
 begin
  if (reset)
    count <=3'b000;
 else if(en)
    count <=count + 1;
 end
 
 ```
 The above code will result in a latch which we will need for the counter to function properly.<br />
 if no enable is set the count should latch to the previous value.<br />
 ![Screenshot from 2023-08-14 21-57-37](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/14aab491-154d-4ef8-9212-7f1dc2b0957d)
 <br />

 **Note 1: Combinational circuits should not have inferred latches** <br />
 <br />
 **Note 2: If statements and case statements should always be used in an always block**<br />
 <br />
 It is recommended to use reg type for the assigned variables.<br />

 ```
  reg y;
  always @(*)
  begin
    case(sel)
      2'b00: y = <some value 1>;
      2'b01: y = <some value 2>;
    endcase
  end
 ```
 ### Caveats with case:

 It should be known that incomplete cases would result in inferred latches. Such us the above code above.<br />
 To avoid this we must use default statements at the end of the case.<br />

 ```
  reg [1:0] sel;
  always @(*)
  begin
    case(sel)
      2'b00:<some code>;
      2'b01:<some code>;
      default:<some code>;
    endcase
   end
 ```

 It should also be noted that we need to assign all outputs in all the cases.<br />
 If not, like in the below code where partial assignments are made some issues might come in the design.<br />
 
 ```
 reg [1:0] sel;
 always @(*)
  begin
    case(sel)
      2'b00: begin
              x=a;
              y=b;
             end
      2'b01: begin
              x=c;
             end 
      default: begin
                x=d;
                y=b;
              end
    endcase
   end
 ```

![Screenshot from 2023-08-14 22-20-39](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1ba6168c-02ad-485a-8c24-76937e13d6ab)
<br />
To resolve the above issue assign all the outputs in all the cases and do no partial assignments.<br />
<br />
**Note: It is important to not have overlapping case statements**<br />


</details>

<details>
  <summary>Lab Incomplete If case</summary>
  
  ### LAB 1

  Below is the .v  file that we are going to simulate. We are expecting a mux ideally with the use of if statements.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/b56fe6d1-3a5b-4234-aa01-009a183b69b2)
  <br />
  In the below waveform, you can see that the design becomes a DFF and the y follows i1 for the i0 as enable.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/59e3644d-6f7d-4ebb-ab7e-27bd59391f1f)
  <br />
  During synthesis, we can see that a D latch is generated instead of a mux.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1503570d-55e0-4293-a874-3c7ca72eabfe)
  <br />
  The below figure shows the design synthesis diagram.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/5c8dfeaa-cf28-4526-9a56-29b9aaefb1eb)
  <br />
  <br />

  ### LAB 2
  
  Below is the .v  file that we are going to simulate. We are expecting two muxes ideally but like above what we get is quite different.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/5652a70d-f996-43eb-b45f-55816ceb04a2)
  <br />
  Below is the waveform of the same.<br />
  You can see that y(output) follows i1 when i0 is high.<br />
  if i0 is low and i2 is high, y follows i3.<br />
  for the rest a DFF is inferred as shown in the waveform:<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1d7489ad-d8b9-4733-94ad-cdabfc5316b2)
  <br />
  The above statement of the inferred D latch is confirmed with the below screenshot.<br/>
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/4797f2ed-1807-4946-95e0-881150d58c5e)
  <br />
  Below is the synthesized design.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/5ce3f1fb-d68a-49f9-911c-14a15b735e7b)
  <br />
  
</details>

<details>
  <summary>Lab Incomplete Overlap case</summary>

  ### LAB 1

  Below is the .v  file that we are going to simulate. We are expecting a mux ideally but what we get is quite different.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/d6a5e5a0-28f0-47bd-bccb-d2377462274f)
  <br />
  Below is the waveform of the incomp_case.v RTL.<br />
  Here the output follows the logic for a mux for select lines 00 and 01 but the case for 10 and 11 are not defined so an inferred D latch will be formed.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/e04e524a-7bfe-47d5-a6ed-335c01607150)
  <br />
  The below diagram shows the synthesized diagram and like we thought a D latch is there.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/c4e71730-180a-4318-9368-41b4f3cb3161)
  <br />

  ### LAB 2

  Here were are going to simulate and synthesize a code that fixes the above-said problem.<br /> 
  Here, a latch will not be inferred as we are using **default**.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/319e81eb-d1ba-4d37-b208-8a7be5a1f6a7)
  Below is the simulation of the RTL. In contrast to the previous waveform, this is correct.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/0713f46f-584c-4aed-bb4d-f99fa950c9ef)
  <br />
  As shown below, there is no D Latch inferred.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/f6ffc923-9d85-4fb2-aaf4-507046659323)
  <br />

  ### LAB 3

  Here we are going to simulate and synthesize ' partial_case_assign.v '.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/b1ba1ff6-c40c-4324-954d-22b2fdcf83fc)
  <br />
  The figure below shows the simulation of the RTL. Due to the partial assignments in different cases, latches will be inferred.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/cbb65fa5-bc31-45f1-ac4f-c93a44b709c9)
  The synthesized design diagram is shown below. As expected there is a D latch because of partial assignments.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/51694a7a-66e5-4130-b984-f88049100b1c)
  <br />

  ### LAB 4

  In this particular lab, we are going to see ' bad_case.v ', which will have a synthesis simulation mismatch.<br />
  In the code below the simulator will get confused for sel '10' and '11' and will cause a latch-like action.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/702cf0a9-cc5a-4899-a629-0f4ba2912811)
  <br />
  Below is the simulation on GTKWave.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/efd3889a-6b82-445f-a568-3fd935e32bef)
  <br />
  After synthesis, we will get this design diagram which has no D-latch, so to investigate we simulate the netlist.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/43990a3b-fb94-48b6-bac7-ff4bffa527ac)
  <br />
  After the simulation of the netlist, we will get the following waveform which is correct. Hence a synthesis-simulation mismatch.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/a7320bcc-00fd-4ceb-a669-0a6e132a94ad)

</details>

<details>
  <summary>For loop and For generate</summary>
  <br />
  <br />
  In this section, we are going to be looking at the for loop and generate for looping statements.<br />
  Looping constructs are two types:<br />
  
  - For loop
  - generate for loop

  ### For loop

  The **for loop** is used to evaluate expressions.<br />
  It should always be used inside the **always** block.<br />
  It is not and should not be used for generating or instantiating hardware.<br />
  <br />
  example:

  ```
  input reg [31:0] inp;
  integer i;
  always @(*)
  begin
    for (i=0;i<32;i=i+1)
    begin
      if(i == sel)
        y = inp[i];
    end
  end 

  ```

  ### Generate for loop

  The **generate for loop** is used for replicating the hardware.<br />
  It should be used outside the always block.<br />
  <br />
  example:

  ```
  genvar i;
  generate
    for(i=0;i<3;i=i+1)
      begin
        and u1 (.a(a[i]) , .b(b[i]) , .y(y[i]));
      end
  endgenerate
  ```
  
  
</details>

<details>
  <summary>Labs "For loop" and "For generate"</summary>
  <br />

  ### LAB 1

  Below is the RTL code for mux_generate.v.<br />
  It is a 4x1 mux using for loop in the logic.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/cb7dc93f-7d39-4d3e-9621-48a4851e25de)
  <br />
  The simulated output waveform is shown below and it coming out as expected.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/60563471-a8db-4f68-8bce-b945cb1af9ea) 
  <br />
  After synthesis, we get the design layout as such.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/43ed9af8-d2ab-4917-bcad-56166b8eb8e2)
  <br />
  We generate a netlist for the same and simulate it. As expected we get the output as the previous waveform.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/98cb07c3-3436-45f9-a369-fef813a51b32)
  <br />

  ### LAB 2

  Below is the RTL code for demux_generate.v.<br />
  It is a 1x8 demultiplexer using **for loop** in the logic.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/ff179083-c6de-4945-980a-7abcc21ee4b0)
  <br />
  The simulated output waveform is shown below and it coming out as expected.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1e863df3-1fce-4b38-8970-226e66d6ccb1)
  <br />
  After synthesis, we get the design layout as such.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/af8a9601-ed0a-485c-bc61-3bd732a81436)
  <br />
  We generate a netlist for the same and simulate it. As expected we get the output as the previous waveform.<br />
  ![4](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/5dcd2348-1753-4264-82f6-9f6d7cfc1464)
  <br />

  ### LAB 3

  Here shown below are the RTL codes for a ripple carry adder.<br />
  We are using **generate for loop** to replicate the full adder hardware.<br />
  ![1](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/c483f7c0-2408-4ef4-bac2-57e35d35a2ed)
  <br />
  Below given is the simulation of fa.v and rca.v.It is obtained as expected.<br />
  ![2](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/09774bf7-b628-4971-9e8b-7e5bc62fcdcd)
  Below is the synthesized design diagram for the same.<br />
  The yosys commands are a bit different for this, as we are using two .v files.<br />

  ```
  read_liberty -lib <dir>  // same as usual
  read_verilog fa.v rca.v  // since there are two .v files
  synth                    // just write synth without anything else
  abc -lib <directory>     // same as usual
  show rca                 // instead of just show (you can write <show fa> to see the fa layout)
  write_verilog rca_net.v  // same as usual

  ```
  ![3a](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/1a5bac6a-9f9b-4e21-ba71-ac2c8d05534b)
  <br />
  Simulate the netlist file along with the Verilog models and testbench.<br />
  We find the output waveform to be the same as the RTL simulation.<br />
  ![3](https://github.com/mrdunker/iiitb_emil_class/assets/38190245/8f4fc7d8-cabe-43cd-af08-6cfe4ec42aa9)

</details>

# Acknowledgement

- Kunal Ghosh,Director, **VSD Corp.Pvt Ltd**.
- Skywater Foundry
- Chat-GPT (OpenAi)
- Kanish R, Colleague, **IIIT-B**
- Alwin Shaju, Colleague, **IIIT-B**
- Madhav Rao, Professor, **IIIT-B**
- Nanditha Rao, Professor, **IIIT-B**
- Manikandan RR, Professor, **IIIT-B**
- Mariam Rakka

# References
1. https://yosyshq.net/yosys/
2. https://en.wikipedia.org/wiki/Icarus_Verilog
3. https://iverilog.fandom.com/wiki/GTKWave
4. http://ngspice.sourceforge.net/
5. https://github.com/The-OpenROAD-Project/OpenSTA
6. http://opencircuitdesign.com/magic/
7. https://github.com/The-OpenROAD-Project/OpenLane
8. https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop
9. https://github.com/mariamrakka/vsd-hdp.git

