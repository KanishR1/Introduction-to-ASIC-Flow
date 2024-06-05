# Introduction to ASIC Flow 

## Table of Contents
- [Week - 1](#week---1)
    * [Day - 1 : Software Installation](#day---1--software-installation)
- [Week - 2](#week---2)
    * [Day - 1 : Introduction to Verilog RTL Design and Synthesis](#day---1--introduction-to-verilog-rtl-design-and-synthesis)
	* [Day - 2 : Timing libs, Hierarchical vs Flat Synthesis and Efficient flop coding styles](#day---2--timing-libs-hierarchical-vs-flat-synthesis-and-efficient-flop-coding-styles)
	* [Day - 3 : Combinational and Sequential Optimisations](#day---3--combinational-and-sequential-optimisations)
	* [Day - 4 : Gate Level Simulation (GLS), Blocking Vs Non-blocking assignment and Synthesis-Simulation Mismatch](#day---4--gate-level-simulation-gls-blocking-vs-non-blocking-assignment-and-synthesis-simulation-mismatch)
	* [Day - 5 : If, case, for and for generate](#day---5--if-case-for-and-for-generate)
- [Acknowledgement](#acknowledgement)
- [References](#references)

## Week - 1 
## Day - 1 : Software Installation

[Yosys Section]:#
### **YOSYS**
Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. Selected features and typical applications:

   1. Process almost any synthesizable Verilog-2005 design
   2. Converting Verilog to BLIF / EDIF/ BTOR / SMT-LIB / simple RTL Verilog / etc.
   3. Built-in formal methods for checking properties and equivalence
   4. Mapping to ASIC standard cell libraries (in Liberty File Format)
   5. Mapping to Xilinx 7-Series and Lattice iCE40 and ECP5 FPGAs
   6. Foundation and/or front-end for custom flows 

Yosys can be adapted to perform any synthesis job by combining the existing passes (algorithms) using synthesis scripts and adding additional passes as needed by extending the Yosys C++ code base. Yosys also serves as backend for several tools that use formal methods to reason about designs, such as sby for SMT-solver-based formal property checking or mcy for evaluating the quality of testbenches with mutation coverage metrics.
Yosys is free software licensed under the ISC license (a GPL compatible license that is similar in terms to the MIT license or the 2-clause BSD license). 

**Steps to install Yosys**

```
git clone https://github.com/YosysHQ/yosys.git
cd yosys 
sudo apt install make
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make 
sudo make install
```
![yosys](./softwares_images/yosys.png)    




[Icarus Verilog Section]:#
### **ICARUS VERILOG**
Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format (EDIF). It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.Icarus Verilog is released under the GNU General Public License, Icarus Verilog is free software. Icarus is composed of a Verilog compiler (including a Verilog preprocessor) with support for plug-in backends, and a virtual machine that simulates the design.

**Steps to install Icarus Verilog**
```
sudo apt-get install iverilog
```
![iverilog](./softwares_images/iverilog.png)



[GTKWave Section]:#
### **GTKWAVE**
GTKWave is a fully featured GTK+ based wave viewer for Unix and Win32 which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing.

**Steps to install GTKKwave**
```
sudo apt install gtkwave
```
![gtkwave](./softwares_images/gtkwave.png)




[Ngspice Section]:#
### **NGSPICE**
ngspice is the open source spice simulator for electric and electronic circuits comprising of JFETs, bipolar and MOS transistors, passive elements like R, L, or C, diodes, transmission lines and other devices, all interconnected in a netlist. Digital circuits are simulated as well, event driven and fast, from single gates to complex circuits. And you may enter the combination of both analog and digital as a mixed-signal circuit. ngspice offers a wealth of device models for active, passive, analog, and digital elements. Model parameters are provided by our collections, by the semiconductor device manufacturers, or from semiconductor foundries. The user can add their circuits as a netlist, and the output is one or more graphs of currents, voltages and other electrical quantities or is saved in a data file.

**Steps to install ngspice**</br>
Download the tarball from ***https://sourceforge.net/projects/ngspice/files/*** to a local directory and then follow the commands given below :
```
# Dependency for ngspice:
sudo apt-get install build-essential
sudo apt-get install libxaw7-dev

# ngspice installation:
tar -zxvf ngspice-40.tar.gz
cd ngspice-40
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install

```
![ngspice](./softwares_images/ngspice.png)




[OpenSTA Section]: #
### **OPENSTA**
OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats such as Verilog netlist, Liberty library, SDC timing constraints, SDF delay annotation and SPEF parasitics. OpenSTA uses a TCL command interpreter to read the design, specify timing constraints and print timing reports.

**Steps to install OpenSTA**</br>
Prior to the installation of the OpenSTA install the dependencies using the command shown below :</br>
``` 
sudo apt-get install cmake clang gcc tcl swig bison flex 
```

After installing the dependencies use the following command to install OpenSTA:
```
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
sudo make install
```
![opensta](./softwares_images/OpenSTA.png)




[Magic Section]:#
### **MAGIC**
Magic is an electronic design automation (EDA) layout tool for very-large-scale integration (VLSI) integrated circuit (IC) originally written by John Ousterhout and his graduate students at UC Berkeley. Work began on the project in February 1983. The main difference between Magic and other VLSI design tools is its use of "corner-stitched" geometry, in which all layout is represented as a stack of planes, and each plane consists entirely of "tiles" (rectangles). Magic is primarily famous for writing the scripting interpreter language Tcl.

**Steps to install magic**</br>
```
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
```
![magic](./softwares_images/magic.png)


[OpenLane Section]:#
### **OPENLANE**
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. It also provides a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII. Currently, it supports both A and B variants of the sky130 PDK, the C variant of the gf180mcu PDK, and instructions to add support for other (including proprietary) PDKs are documented. OpenLane abstracts the underlying open source utilities, and allows users to configure all their behavior with just a single configuration file.

Prior to the installation of the OpenLane install the dependencies and packages using the command shown below :</br>
``` 
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation :</br>
```
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

**Steps to install OpenLane, PDKs and Tools**</br>
```
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```



## Week - 2
## Day - 1 : Introduction to Verilog RTL Design and Synthesis

### **Introduction to Simulator**
A simulator is a software tool that can be used to check the functionality of a circuit design before it is implemented in hardware. It does this by simulating the behavior of the design in software, using a Hardware Description Language (HDL) such as Verilog or VHDL. The Register Tranfer Level (RTL) design is the actual Verilog code that implements the circuit i.e., the behavioural representation of the specification in a HDL language. To verify the correctness of the RTL design with the specification, a testbench is written in HDL and simulated using the open-source simulator, Icarus Verilog. The testbench generates stimulus signals that are applied to the RTL design, and the simulator monitors the output signals to ensure that they are correct. The simulator monitors changes in the input signals. When an input signal changes, the simulator re-evaluates the RTL design and updates the output signals. The simulator records the changes in the input and output signals in a file called a Value Change Dump (VCD) file. This file is used to visualize the behavior of the design over time in the form of waveforms. A tool called GTKWave is used to open the VCD file and view the which helps in debugging the design and verifying its functionality in accordance with the specification.

![iverilog_based_simulation flow](./images/week_2_day_1/iverilog_based_simulation_flow.png)

**Steps to download the lab folder**</br>
```
mkdir ASIC
cd ASIC
git clone https://github.com/kunalg123/vsdflow.git
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

Command to view the folder structure of the lab, and list the contents of the directory:
```
cd ASIC/sky130RTLDesignAndSynthesisWorkshop/
ls -l
```
![folder_structure](./images/week_2_day_1/folder_structure.png)

The lib folder contains all the library files needed for the lab, including the sky130 standard cell library. The verilog_model folder in ***/home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/my_lib*** contains the verilog models of the standard cells present in the .lib file. The verilog_files folder contains all the lab experiment verilog source files and corresponding testbench files needed to simulate the designs.

---

**Standard cell library** - It is a collection of well defined and appropriately characterized logic gates that can be used to implement a digital design. Timing data of standard cells is provided in the Liberty format.

The lib directory contains the library file **sky130_fd_sc_hd__tt_025C_1v80.lib**. Libraries in the SKY130 PDK are named using the following scheme:</br>
***<Process_name>_<Library_Source_Abbreviation>_<Library_type_abbreviation>[_<Library_name]***</br>

sky130 - Process Technology of the PDK sky130</br>
fd - SkyWater Foundry</br>
sc - Digital standard cells</br>
hd - High density</br>
tt - Typical Timing</br>
025C - 25 degree celsius Temperature</br>
1v80 - 1.8V Supply Voltage</br>

---

### **Demostration of the Icarus Verilog and GTKWave**
Change the current working directory to the directory containing the Verilog files using the following command :
```
cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
Simulate the RTL design and testbench using the following command:
```
iverilog good_mux.v tb_good_mux.v 

``` 
The above command will compile and check for the syntax errors in both the design and testbench. Upon compiling successfully it will generate an executable file ***a.out***.</br>

Execute the a.out using the command **```./a.out ```**, resulting in the generation of a tb_good_mux.vcd file that captures changes in the input and output values.
This vcd file is given as the input to the GTKWave to view the wave form.
In GTKWave drag and drop the required input and output signals to view the waveform. Since the simulation is done for long amount of time use the zoom to fit option to view the entire waveform.

Commands to execute to view the waveform :
```
./a.out
gtkwave tb_good_mux.vcd
```

![iverilog_gtkwave_demo](./images/week_2_day_1/ievrilog_gtkwave_demo.png)


### **Description of the Verilog code**
To view the contents of the verilog files good_mux.v and tb_good_mux.v use the following command:
```
gvim -o good_mux.v tb_good_mux.v # -o is to open multiple windows at a time.
```
The verilog code of the good_mux.v is given below:
```
// Verilog Code for 2:1 Mux

/*
All verilog code starts with module, ends with endmodule and within them the logic is written. 
For RTL design portlist should be mentioned in the module and it should have atleast one input port and one output port.
In this design there are two data input ports, one select line input port and one output port. 
*/

module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*) // Whenever any one of the input changes execute the code enclosed between begin ... end
begin
	if(sel) //If sel = 1 then output y follows i1 else output y follows i0 
		y <= i1;
	else 
		y <= i0;
end
endmodule
```

The verilog code for the tb_good_mux.v is given below:
```
`timescale 1ns / 1ps // defines the time units and time precision for simulation.
module tb_good_mux; // AS mentioned earlier testbench doesnot have input and output ports
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;

        // Instantiate the Unit Under Test (UUT)
	good_mux uut (
		.sel(sel),
		.i0(i0),
		.i1(i1),
		.y(y)
	);

	initial begin
	$dumpfile("tb_good_mux.vcd"); //This system task specifies the name of the VCD file where simulation waveform data will be written
	$dumpvars(0,tb_good_mux); //This system task is used to specify which signals within a module should be included in the VCD file for waveform dumping.
	// Initialize Inputs
	sel = 0;
	i0 = 0;
	i1 = 0;
	#300 $finish; //Terminate the simulation after 300ns
	end

always #75 sel = ~sel;  //Toggle the value of the select line after 75ns
always #10 i0 = ~i0;   //Toggle the value of the select line after 10ns
always #55 i1 = ~i1;  //Toggle the value of the select line after 55ns
endmodule

```

### **Introduction to Synthesizer**
Synthesis is the process that converts RTL into a technology-specific gate-level netlist, optimized for a set of pre-defined constraints.Synthesizer is a tool used to convert the RTL from the netlist. Yosys is one such open source synthesizer.  A netlist is a file that represents the gates and flip-flops required to implement the design in hardware and the ineterconnections between them which is a result of the synthesis process. Yosys is provided with both the design and its corresponding .lib file, and its task is to generate the netlist. The netlist generated is a depiction of the input design provided to Yosys, contructed using the standard cells available in the .lib file. To validate the synthesis output, the netlist is verified in a manner analogous to how  the RTL design is verified. This involves using the same testbench and stimulus set to confirm that the outcomes obtained from the netlist correspond to those acquired when using the RTL design. The block diagram representation of the yosys flow and the netlist verification is shown below:

![yosys_flow](./images/week_2_day_1/yosys_flow.png)

![netlist_verification](./images/week_2_day_1/netlist_verification.png)



### **Liberty (.lib): Introduction**
The .lib file is a library of standard cells that can be used to implement any logic function. It includes different versions of the same standard cell, such as low speed, high speed etc., Why is there a necessity for various gate versions? The maximum speed of a digital circuit is determined by the combinational delay within its logic path. To achieve high circuit speed, particularly for high-frequency clock operation, a small Tcomb (combinational delay) is crucial. A higher frequency inherently results in high performance. However, if only high performance is neede, faster cells would appear to suffice, raising the question of why medium and slower cell options are necessary. The requirement for slower cells is to address hold time issues. In digital logic circuits, the load takes the form of capacitance. Faster charging and discharging induce minimal delays. Propagation delay, a key concept, refers to the time it takes for a change in the input of a digital logic gate or circuit to result in a corresponding change in its output. It is the duration between when the input transition begins and when the output transition completes. For larger capacitance (C), slow driving occurs, while smaller capacitance results in swift driving. For rapid charging and discharging of capacitance, a greater current sourcing capability is required. However, this leads to broader transistors, resulting in the increase in  area usage and higher power consumption. Narrower transistors offer reduced area usage and lower power consumption. The swiftness of cells brings with it the trade-off of area utilization and power consumption.


It is necessary to provide information for the synthesis toolregarding the choice of cells. Overuse of faster cells increases area and power demands, while also it leads to hold time violations. Conversely, excessive use of slower cells results in poor performance requirements. The optimal cell selection for the synthesizer is guided by constraints that dictate the appropriate cell set to use.

### **Setup Time and Hold Time**

### **Yosys Illustration**
**Step 1:** Change the current working directory to the directory containing the Verilog files using the following command :
```
cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```

**Step 2:** Invoke the yosys 
```
yosys
```

**Step 3:** Read the liberty file 
```
read_liberty -lib /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```


**Step 4:** Read the verilog design file
```
read_verilog good_mux.v 
```

---

**read_liberty** - Read cells from liberty file as modules into current design. The ***-lib*** switch creates empty blackbox modules.</br>
**read_verilog** - Loads modules from  verilog file to the current design.

---

![read_yosys_commands](./images/week_2_day_1/read_yosys_commands.png)



**Step 5:** Synthesize the verilog file.
```
synth -top good_mux
```

___
**synth** - command runs the default synthesis script. The ***-top*** switch use the specified module as top module.
___

![synth_op](./images/week_2_day_1/synth_op.png)

The output of the synthesis displays the number of wires used , number of standard cells used and the name of the standard cell. 


**Step 6:** Generate the netlist
```
abc -liberty /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

___
**abc** -  This command uses the ABC tool for technology mapping of yosys's internal gate library to a target architecture. The ***-lib*** switch liberty <file>
generate netlists for the specified cell library using the liberty file format.
___

![abc_op](./images/week_2_day_1/abc_op.png)

The output of the synthesis displays the number of input and output signals and the name of the standard cell that is used. 


**Step 7:** View the netlist
```
show
```

___
**show** - Creates a graphviz DOT file for the selected part of the design and compile it to a graphics file. It generates a schematic.
___

![show_op](./images/week_2_day_1/show_op.png)

In the schematic there is sky130 based 2:1 multiplexer standard cell with three inputs and one output.


**Step 8:** Write the netlist
```
write_verilog -noattr good_mux_netlist.v
```
___
**write_verilog** - Writes the current design to a Verilog file. The ***-noattr** switch skips the attributes from included in the output netlist.
___

The netlist and the write_verilog command is shown below:

![write_op](./images/week_2_day_1/write_op.png)

![netlist_op](./images/week_2_day_1/netlist_op.png)




## Day - 2 : Timing libs, Hierarchical vs Flat Synthesis and Efficient flop coding styles
### **Exploring the Contents of .lib File**
To view the contents inside the .lib file type the following command :
```
cd ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/
gvim sky130_fd_sc_hd__tt_025C_1v80.lib
```
![lib_img](./images/week_2_day_2/lib_img.png)

One of the fundamental parameter stored within .lib files comprises PVT parameters, where P signifies Process, V represents Voltage, and T denotes Temperature. 
The variations in these parameters can cause significant changes in the performance of circuits.

1. Process Variation: During the manufacturing process, there may be some deviations in the transistor characteristics, causing non-uniformity across the semiconductor wafer. Critical parameters like oxide thickness, dopant concentration, and transistor dimensions experience alterations.

2. Voltage Variation: Voltage regulators might exhibit variability in their output voltage over time, inducing fluctuations in current and impacting the operational speed of circuits. 

3. Temperature Variation: The functionality of a semiconductor device is sensitive to changes in temperature, particularly at the internal junctions of the chip. 

Further it contains the technology that is used is CMOS for which delay are modelled  through table lookup. This file also defines the units for parameters like voltage, power, current, capacitance, and resistance. Within the .lib library, each standard cell consists a  set of parameters specific to that cell's features.

Consider the a2111oi gate whose parameters and verilog files is shown below:

![a2111o_img](./images/week_2_day_2/a2111o_img.png)
![a2111o](./images/week_2_day_2/a2111o.png)

This is a 2-input AND gate and a 4-input NOR gate. Within the .lib file, sevetral parameters specific to this particular standard cell is given, including leakage power values for every possible input combination, specifications regarding pin type and pin capacitances, internal power metrics, timing-related particulars, as well as area measurements and power-related specifics for the standard cells. Similarly for all the standard cells the parameters above mentioned is listed in the .lib file.

Consider the different versions of the same logic gate shown below:
![area_depict](./images/week_2_day_2/area_dep.png)

In all the three the logic inferred is same bu the area is different. Wider cells consume more power but delay wise it is less. The leakage power in the wider cell is more compared to the narrow cell which is depicted in the image .

### **Hiererchical Synthesis and Flat Synthesis**
Hierarchical synthesis is breaking a comples modules into smaller, more manageable sub-modules or blocks. Each of these sub-modules can be synthesized or designed independently before being integrated into the larger system. This approach allows for efficient design, optimization, and verification of individual components while maintaining a structured and organized design process. An illustration of the hierarchical synthesis is shown below :

Consider the verilog file multiple module which is given in the verilog_files directory

 ```
module sub_module2 (input a, input b, output y);
	assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
	assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
	wire net1;
	sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
	sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
 ```

 In this case the module multiple_modules iinstantiates two sub_modules where the sub_module1 implements the AND gate and sub_module2 implemets the OR gate which are integrated in the multiple_modules.  Synthesis the multiple module using the sollowing commands:
 ```
 # Remove "#" if needed
 cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
 yosys
 read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 read_verilog 
 read_verilog multiple_modules.v 
 synth -top multiple_modules
 abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 show multiple_modules
 write_verilog multiple_modules_hier.v
 ``` 
 ___
 **Note:**</br>
 When using hierarchical design instead of enetering the ***show*** command to view the file ***show <module_name>*** must be otherwise yosys will generate the following error : "ERROR: For formats different than 'ps' or 'dot' only one module must be selected."
 ___

 ![hier_show](./images/week_2_day_2/hierarchi_des.png)
 ![netlist_hier](./images/week_2_day_2/netlist_hier.png)
 
 Yosys does not show the AND gate and OR gate in the synthesis instead it shows the submodule names. The netlist also contains the AND and OR logic in separate submodules. Some times yosys may optimize the design such that the OR gate will be created using NAND gates. It is because the CMOS structure of the OR gate which is shown below has two pmos transistors stacked together. The mobility of the holes is less than the mobility of the electrons , since mosfets are majority carrier devices and majority carrier of the pmos is holes it increases the delay hence it becomes a bad circuit. In NAND gate implementation only the nmos are stacked.
 ![cmos_or](./images/week_2_day_2/CMOS_OR.jpg)

Flattening the hierarchy means simplifying the hierarchical structure of a design by collapsing or merging lower-level modules or blocks into a single, unified representation. In yosys the flattening can be done with ***flat*** command. Yosys illustration of flattening the hiererchy.

```
 cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
 yosys
 read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 read_verilog 
 read_verilog multiple_modules.v 
 synth -top multiple_modules
 abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 flatten
 show
 write_verilog multiple_modules_flat.v
```
![flat_des](./images/week_2_day_2/flat_des.png)
![netlist_flat](./images/week_2_day_2/netlist_flat.png)

The flatten command breaks the hierarchy and makes the design into a single module by creating AND and OR gates for the logics inferred by the submodule which is shown in the images above.

### **Synthesising a Submodule :**
Suppose a multiplier design needs to be used in numerous instances. Rather than undergoing synthesis six times independently, the preferred approach is to synthesize it once and then duplicate it within the primary module. Using module-level synthesis becomes advantageous when dealing with multiple occurrences of identical modules. Another reason for synthesizing submodule is to follow the principle of divide and conque for extensive designs that may not be optimized effectively, synthesizing the design module by module ensures that each module is effectively optimized.

**Steps to synthesis submodule :**

```
cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog multiple_modules.v 
synth -top sub_module
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
```
![submodule_demo](./images/week_2_day_2/submodule_synth.png)


### **Flip-FLops**
A flip-flop is a fundamental sequential synchronous electronic circuit that is capable of storing information. A single flip-flop can store 1- bit of information and several flip-flops can be grouped together to form registers and memory that can store multiple bits of information. There are several types of flip-flops like JK flip-flop, D flip-flop, T flip-flop and SR flip-flop but D flip-flop is widely and most commanly used since it transmits the input data to the output without performing any modifications. A D flop-flop needs two inputs : data and clock. The flip-flop can be positive-edge triggered or negative-edge triggered i.e, the output makes transition during the rising edge of the clock pulse if it is positive-edge triggered and if the output makes transition during the falling edge of the clock pulse then it is said to be negative- edge triggered.

### **Need of flip-flops**</br>
In any electronic circuit there will always be an propagation delay. These delays may cause glitches in the output which may cause the output state to change when it is not supposed to. Glitches are unwanted transitions in the output. As an illustration consider the circuit shown below:

![glitch](./images/week_2_day_2/glitch.png)

![glitch_plot](./images/week_2_day_2/glitch_plot.png)

The propagation delay of the OR gate is 1ns and AND gate is 2ns. Initially a,b,c are 0,0,1 and the internal node i0 is 0 and the output Y is high. At t=0ns there is change in the inputs a,b,c becomes 1,1,0. Because of the propagation delays of the AND gate and OR gate at t=1ns the output node transits from high to low and since the input to the OR gate both i0 and c are 0. At t=2ns the internal node i0 transists from 0 to 1 and  the inputs to the OR gate becomes 1 and 0. Since the propagation delay of the OR gate is 1ns the output Y becomes high at 3ns and remains stable. Between 1ns and 3ns the output made an unwanted change in the transition resulting in a glitch.  

In order to avoid the glitches a D flip-flop can be connected at the output so that the output will change only at the rising or falling edge of the clock. As mentioned earlier flip-flops generally needs two inputs: data and clock. But the problem is the initial state of the flip-flop is unknown. So in order to set the initial value of the flip-flop, two more inputs are provided : preset/set and reset. These additional inputs can be synchronous with clock or asynchronous with clock.

**Steps to simulate and generate the netlist for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

___
***Note***:</br>
**dfflibmap** - technology mapping of flip-flops</br>
dfflibmap  -liberty - Maps internal flip-flop cells to the flip-flop cells in the technology library specified in the given liberty file.

Generally in the flow there will be a separate .lib file for the flip-flops which needs to be used with the dfflibmap command.
___

### **Illustration of Different types of Flip-flop** 
**1. D flip-flop with Synchronous reset**</br>
A D flip-flop with synchronous reset  combines the functionality of a D flip-flop with the ability to reset its state synchronously. This means that the flip-flop's stored value can be reset to 0 or low state based on a clock signal and a reset input, ensuring that the reset operation occurs when the clock signal transits.
The verilog code, simulation and synthesis results are shown below:
```
module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if (sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

![sync_res](./images/week_2_day_2/sync_res.png)

![sync_res_netlist](./images/week_2_day_2/sync_res_netlist.png)

**2. D flip-flop with Asynchronous reset**</br>
A D flip-flop with asynchronous reset combines the functionality of a D flip-flop with the ability to reset its state asynchronously. This means that the flip-flop's stored value can be reset to 0 or low state regardless of the clock signal's state.
The verilog code, simulation and synthesis results are shown below:
```
module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

![async_simu](./images/week_2_day_2/async_simu.png)

![async_res](./images/week_2_day_2/async_res.png)

**3. D flip-flop with Asynchronous set**</br>
A D flip-flop with asynchronous set combines the functionality of a D flip-flop with the ability to set its state asynchronously. This means that the flip-flop's stored value can be set to 1 or high state regardless of the clock signal's state.
The verilog code, simulation and synthesis results are shown below:

```
module dff_async_set ( input clk ,  input async_set , input d , output reg q );
always @ (posedge clk , posedge async_set)
begin
	if(async_set)
		q <= 1'b1;
	else	
		q <= d;
end
endmodule
```

![async_set_simu](./images/week_2_day_2/async_set_simu.png)

![async_set_net](./images/week_2_day_2/async_set_net.png)


**4. D flip-flop with Asynchronous and Synchronous reset**</br>
A D flip-flop with both asynchronous and synchronous reset that combines the features of a D flip-flop with the ability to reset its state using either an asynchronous reset input or a synchronous reset input. This provides flexibility in resetting the flip-flop's state under different conditions.

The verilog code, simulation and synthesis results are shown below:

```
module dff_asyncres_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else if (sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

![async_sync_reset](./images/week_2_day_2/async_sync_reset.png)

![async_sync_reset_netlist](./images/week_2_day_2/async_sync_reset_net.png)



### **Optimizations**
During synthesis yosys will perform optimisations based on the logic that is being designed. An illustration of the yosys optimization is given below:

**1. Optimisation Example 1**

Consider the verilog design given below:
```
module mul2 (input [2:0] a, output [3:0] y);
	assign y = a * 2;
endmodule
```
This code performs multiplication of the input number by 2. Since the input is 3-bit binary number all the input and output combinations are as follows:
| a2 a1 a0  |y3 y2 y1 y0   |
|:---:|:---:|
| 0 0 0 | 0 0 0 0  |
| 0 0 1 | 0 0 1 0  |
| 0 1 0 | 0 1 0 0  |
| 0 1 1 | 0 1 1 0  |
| 1 0 0 | 1 0 0 0  |
| 1 0 1 | 1 0 1 0  |
| 1 1 0 | 1 1 0 0  |
| 1 1 1 | 1 1 1 0  |

y0 is always 0 and the code doesn't need any hardware and it only needs the proper wiring of the input bits to the output and grounding the bit y0. The netlist of the design is shown below:

![opt_1](./images/week_2_day_2/opt_1.png)

![opt_net](./images/week_2_day_2/opt_net.png)

**2. Optimisation Example 2**

Consider the verilog design given below:
```
module mult8 (input [2:0] a , output [5:0] y);
	assign y = a * 9;
endmodule
```
In this design the 3-bit input number "a" is multiplied by 9 i.e.,(a*9) which can be re-written as (a\*8) + a . The term (a\*8) is nothing but a left shifting the number a by three bits. Consider that a = a2 a1 a0. (a\*8) results in a2 a1 a0 0 0 0. (a\*9)=(a\*8)+a = a2 a1 a0 a2 a1 a0 = aa(in 6 bit format). Hence in this case no hardware realization is required. The synthesized netlist of this design is shown below:

![opt_2](./images/week_2_day_2/opt_2.png)

![opt_2_net](./images/week_2_day_2/opt2_net.png)


## Day - 3 : Combinational and Sequential Optimisations
### **Logic Optimisations**
In a broader context, Digital electronics encompasses two types of optimisations: Combinational and Sequential optimisations. These optimisations are done inorder to achieve designs that are efficient in terms of area, power, and performance.

### **Combinational Optimisations**
The techniques used for optimising the combinational Circuits are as follows:
1. Constant Propagation (Direct Optimisation)
2. Boolean Logic Optimisation (using K-Map or Quine McCluskey method)

#### **1. Constant Propagation Illustration**
Consider the combinational circuit shown below :

![const_propag](./images/week_2_day_3/const_propag.png)

The boolean logic inferred is Y = ((AB)+C)'. If A is always tied to ground i.e., A = 0, then the expression will always evaluate to C'. In this case instead of having a AND gate and a NOR gate the circuit can be simplified by using a single NOT gate with C as its input. Even though both of then represent the same logic since the number of transistors used in the optimised design is less compared to that of the given circuit which shown in the above figure. The transistor level implementation of the given circuit and the optimised circuit is shown below :

![gc_tran](./images/week_2_day_3/gc_tran.png)

![oc_tran](./images/week_2_day_3/oc_tran.png)

The circuit that is given is implemented in NAND logic in order to prevent the stacking of the pmos. The transistor implementation clearly demonstrates a reduction in the required number of transistors for designing, decreasing from 12 to 2 in the optimised design. This will result in reduced power consumption and occuppies less area.

#### **2. Boolean Logic Optimisation Illustration**
Consider the verilog statement below : 
```
assign y = a?(b?c:(c?a:0)):(!c);
```
The ternary operator **(?:)** will realize a mux upon synthesis. The combinational circuit that corresponds to the above statement is shown below:

![bl_gc](./images/week_2_day_3/bl_gc.png)

This circuit can be optimised by writing the equivalent expression (or function) in boolean variables and minimising the function that will result in more optimised design which is shown below:

![bl_opt](./images/week_2_day_3/bl_opt.png)


### **Sequential Optimisations**
The sequential logic optimisations techniques are broadly classified into two categories :
1. Basic Techniques
	a. Sequential Constant Propagation
2. Advanced Techniques
	a. State Optimisation
	b. Retiming
	c. Sequential Logic Cloning (Floor aware Synthesis)

#### **1. Sequential Constant Propagation**
Consider the sequential circuit shown below :

![so_opt](./images/week_2_day_3/so_opt.png)

The D flip-flop shown in the figure is positive edge triggered with asynchronous reset and the data input D is always tied to the ground (i.e, low state or logic 0). When reset is applied the output of the flop becomes low and if reset it deasserted the output of the flop still remains low. Hence one of the input to the NAND gate is always low resulting in the output Y to be always in high stae (logic 1 or VDD). Hence the optimised version of this circuit is connecting the output port Y directly to VDD i.e., the supply voltage.

___
***Note***: </br>
Consider the circuit shown below :
![set_clar](./images/week_2_day_3/set_clar.png)

This circuit is similar to the one that is discussed above except that it doesn't have asynchronous reset instead it has asynchronous set. When the set input is logic 1 then output of the flop i.e., Q becomes high otherwise Q follows D input which is logic 0. This circuit can't be optimised like the previous circuit discussed in the above section. Consider the waveform between timestamp 1 and timestamp 2, the set pin is deasserted before the rising edge of the clock. The output Q remains high until the next rising edge even though the set input is deasseretd. The output of thr flop Q makes transition only at timestamp2. Therefore set input must be considered as Q'. This circuit can't be optimised.
___

#### **2. State Optimisation**
State optimization refers to the process of minimizing the number of unused states in a digital circuit's state machine.

#### **3. Sequential Logic Cloning**
Sequential logic cloning is used to replicate or clone a portion of a sequential logic circuit while maintaining its functionality and behavior. The goal is to exploit the benefits of parallelism and redundancy while ensuring that the cloned circuit produces identical outputs to the original circuit for the same inputs.
This technique is commonly employed in various scenarios such as redundancy for fault tolerance, speed improvement, and power optimization. This technique is generally used when a physical aware synthesis is done.

Consider the circuit shown below : 

![clo](./images/week_2_day_3/clo.png)

Consider flop A has large positive slack. The flops B and C are far from flop A. Hence there will be a large routing delay from A to B and A to C. To avoid this flop A and the combinational logic 2 is replicated  or cloned in the paths of B and C as shown in the figure below. Since flop A has large positive slack the delay introduced because of the cloning will be compensated and the further delay in the circuit is mainly depended on flop B and flop C.

![clo_opt](./images/week_2_day_3/clo_opt.png)

#### **4. Retiming**
Retiming  used to improve the performance interms of better timing characteristics by repositioning the registers (flip-flops) within the circuit without altering its functionality. In a digital circuit, registers (flip-flops) are used to store intermediate results and control the flow of data. The placement of these registers can significantly impact the circuit's overall performance, including its critical path delay, clock frequency, and power consumption. Retiming aims to optimize these factors by moving registers to appropriate locations within the circuit.

Consider the circuit shown below :

![rt](./images/week_2_day_3/rt.png)

Consider the C-Q delay and set up time is 0ns. The combinational circuits have finite amount of the propagation delay. The maximum clock frequency with which the circuit operates depends on the propagation delay of the combinational logic. From flop A to B the propagation delay is 5ns and the maximum frequency with which this portion of circuit can be operated is 200MHz. Fom flop B to C the propagation delay is 2ns and the maximum frequency with which this portion of circuit can be operated is 500MHz. The effective frequency is minimum of the both which is 200MHz.

Suppose some part of the logic from combinational circuit between flop B and C is placed with the combinational circuit between the flop A and flop B in such a way that the propagation delay of the circuit between flop A and flop is reduced while propagation delay between flop B and flop C is increased by a small amount as show below :

![rt_opt](./images/week_2_day_3/rt_opt.png)

The maximum frequency with which the portion of circuit between A and B can be operated is 250MHz and the maximum frequency with which the portion of circuit between B and C can be operated is 333MHz. The effective frequency is minimum of the both which is 250MHz. Thus the effective maximum frequency has increased after performing the retiming.

### **Illustration of Combinational Optimizsation:**

**Steps to generate the netlist for the below designs**

Generating netlist steps :
```
# Remove "#" if needed
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
# flatten # Use if multiple modules are present
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

___
**opt_clean** - remove unused cells and wires. The ***-purge*** switch removes internal nets if they have a public name. This command identifies wires and cells that are unused and removes them.  This command can be used to clean up after the commands that do the actual work.
___

#### **Example 1**
The verilog code for the example 1 is given below :
```
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```
The above code infers a multiplexer as shown below :

![opt_1](./images/week_2_day_3/opt_1.png)

Since one of the inputs of the multiplexer is always connected to the ground it will infer an AND gate on optimisation.

![opt_1_opt](./images/week_2_day_3/opt_1_opt.png)

The synthesis result and the netlist are shown below :

![opt_1_synth](./images/week_2_day_3/opt_1_synt.png)

![opt_1_net](./images/week_2_day_3/opt_1_netl.png)

#### **Example 2**
The verilog code for the example 2 is given below :
```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
The above code infers a multiplexer as shown below :

![opt_2](./images/week_2_day_3/opt_2_opt.png)

Since one of the inputs of the multiplexer is always connected to the logic 1 it will infer an OR gate on optimisation. The OR gate will be NAND implementation since NOR gate has stacked pmos while NAND implementation has stacked nmos.

![opt_2_opt](./images/week_2_day_3/opt_2_opt_des.png)

The synthesis result and the netlist are shown below :

![opt_2_synth](./images/week_2_day_3/opt_2_synth.png)

![opt_2_net](./images/week_2_day_3/opt_2_net.png)


#### **Example 3**
The verilog code for the example 3 is given below :
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
The above code infers two multiplexers as shown below : 

![opt_3](./images/week_2_day_3/opt_3.png)

On optimisation the above design becomes a 3 input AND gate as shown below :

![opt_3_opt](./images/week_2_day_3/opt_3_opt.png)

The synthesis result and the netlist are shown below :

![opt_3_synth](./images/week_2_day_3/opt_3_synth.png)

![opt_3_net](./images/week_2_day_3/opt_3_net.png)


#### **Example 4**
The verilog code for the example 4 is given below :
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
The above code infers two multiplexers as shown below : 

![opt_4](./images/week_2_day_3/opt_4.png)

On optimisation the above design becomes a 2 input XNOR gate as shown below :

![opt_4_opt](./images/week_2_day_3/opt_4_opt.png)

The synthesis result and the netlist are shown below :

![opt_4_synth](./images/week_2_day_3/opt_4_synth.png)

![opt_4_net](./images/week_2_day_3/opt_4_net.png)

#### **Example 5**
The verilog code for the example 5 is given below :
```
module sub_module1(input a , input b , output y);
 assign y = a & b;
endmodule


module sub_module2(input a , input b , output y);
 assign y = a^b;
endmodule


module multiple_module_opt(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
sub_module2 U3 (.a(b), .b(d) , .y(n3));

assign y = c | (b & n1); 


endmodule
```

The circuit inferred by the code is shown below : 

![opt_5](./images/week_2_day_3/opt_5.png)

On optimisation the above design becomes a AND OR gate as shown below :

![opt_5_opt](./images/week_2_day_3/opt_5_opt.png)

The synthesis result and the netlist are shown below :

![opt_5_synth](./images/week_2_day_3/opt_5_synth.png)

![opt_5_net](./images/week_2_day_3/opt_5_net.png)



#### **Example 6**
The verilog code for the example 6 is given below :
```
module sub_module(input a , input b , output y);
 assign y = a & b;
endmodule



module multiple_module_opt2(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
sub_module U2 (.a(b), .b(c) , .y(n2));
sub_module U3 (.a(n2), .b(d) , .y(n3));
sub_module U4 (.a(n3), .b(n1) , .y(y));


endmodule
```

The circuit inferred by the code is shown below : 

![opt_6](./images/week_2_day_3/opt_6.png)

On optimisation the above design becomes a direct connection of ground (logic 0) to output as shown below :

![opt_6_opt](./images/week_2_day_3/opt_6_opt.png)

The synthesis result and the netlist are shown below :

![opt_6_synth](./images/week_2_day_3/opt_6_synth.png)

![opt_6_net](./images/week_2_day_3/opt_6_net.png)


### **Illustration of Sequential Optimizsation:**

**Steps to simulate and generate the netlist for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
# flatten # use if the multiple modules are present
opt_clean -purge
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

#### **Example 1**
The verilog code for the example 1 is given below :
```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
```
The above code infers the circuit as shown below :

![sq_opt_1](./images/week_2_day_3/sq_opt_1.png)

Since this code doesn't need optimisation it will infer a D flip-flop with asynchronous reset as shown above.

The simulation, synthesis result and the netlist are shown below :

![sq_opt_1_sim](./images/week_2_day_3/sq_opt_1_sim.png)

![sq_opt_1_synth](./images/week_2_day_3/sq_opt_1_synth.png)

![sq_opt_1_net](./images/week_2_day_3/sq_opt_1_net.png)

All the standard cells by default have negative logic for reset and since in the code reset is mentioned as positive, an inverter is used for the reset signal. 



#### **Example 2**
The verilog code for the example 2 is given below :
```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```
The above code infers a D flip-flop with asynchronous set (reset signal is applied to set input) as shown below :

![sq_opt_2](./images/week_2_day_3/sq_opt_2.png)

The optimised design infers a direct connection of VDD (logic 1) to the output q as shown below:

![sq_opt_2_opt](./images/week_2_day_3/sq_opt_2_opt.png)

The simulation, synthesis result and the netlist are shown below :

![sq_opt_2_sim](./images/week_2_day_3/sq_opt_2_sim.png)

![sq_opt_2_synth](./images/week_2_day_3/sq_opt_2_synth.png)

![sq_opt_2_net](./images/week_2_day_3/sq_opt_2_net.png)

#### **Example 3**
The verilog code for the example 3 is given below :
```
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
The above code infers a two D flip-flop with asynchronous set and reset (reset signal is applied to set and reset input) as shown below :

![sq_opt_3](./images/week_2_day_3/sq_opt_3.png)

Since this code doesn't need optimisation it will infer two D flip-flop with asynchronous set and reset as shown above.

The simulation, synthesis result and the netlist are shown below :

![sq_opt_3_sim](./images/week_2_day_3/sq_opt_3_sim.png)

At the timestamp 1550 the signal q1 changes from 0 to 1 but the output q transits from 1 to 0 for a clock cycle. It is because there will be a finite clock to q delay so the second flip-flop will sample the logic 0 at that rising edge of the clock. Hence there is a change in the output signal for one clock cycle. 

![sq_opt_3_synth](./images/week_2_day_3/sq_opt_3_synth.png)

![sq_opt_3_net](./images/week_2_day_3/sq_opt_3_net.png)


#### **Example 4**
The verilog code for the example 4 is given below :
```
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
The above code infers a two D flip-flop with asynchronous set(reset signal is applied to set input ) as shown below :

![sq_opt_4](./images/week_2_day_3/sq_opt_4.png)

The optimised design infers a direct connection of VDD (logic 1) to the output q as shown below:
![sq_opt_4_opt](./images/week_2_day_3/sq_opt_4_opt.png)

The simulation, synthesis result and the netlist are shown below :

![sq_opt_4_sim](./images/week_2_day_3/sq_opt_4_sim.png)
 

![sq_opt_4_synth](./images/week_2_day_3/sq_opt_4_synth.png)

![sq_opt_4_net](./images/week_2_day_3/sq_opt_4_net.png)


#### **Example 5**
The verilog code for the example 5 is given below :
```
module dff_const5(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b0;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```


The above code infers a two D flip-flop with asynchronous reset  as shown below :

![sq_opt_5](./images/week_2_day_3/sq_opt_5.png)

Since this code doesn't need optimisation it will infer two D flip-flop with asynchronous reset as shown above.


The simulation, synthesis result and the netlist are shown below :

![sq_opt_5_sim](./images/week_2_day_3/sq_opt_5_sim.png)
 

![sq_opt_5_synth](./images/week_2_day_3/sq_opt_5_synth.png)

![sq_opt_5_net](./images/week_2_day_3/sq_opt_5_net.png)


### **Optimisation of Unused States**

**Steps to simulate and generate the netlist for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
opt_clean -purge
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```


Consider the verilog code shown below :
```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```

This verilog code will infer a 3-bit counter with asynchronous reset.
The possible states of the counter are as follows :
| count[2] count[1] count[0]  |COUNT[2] COUNT[1] COUNT[0] |
|:---:|:---:|
| 0 0 0 | 0 0 1  |
| 0 0 1 | 0 1 0 |
| 0 1 0 | 0 1 1 |
| 0 1 1 | 1 0 0 |
| 1 0 0 | 1 0 1 |
| 1 0 1 | 1 1 0 |
| 1 1 0 | 1 1 1 |
| 1 1 1 | 0 0 0 |

where </br>
count - Previous count</br>
COUNT - Preset count

Since the output q is always assigned COUNT[0]. The other bits of the count are not used and not required. Instead of infering three flip-flops , on optimising the design it will infer a single D flip-flop and an inverter as shown below :

![us_opt](./images/week_2_day_3/us_opt.png)

The simulation, synthesis result and the netlist are shown below :

![us_sim](./images/week_2_day_3/us_sim.png)

![us_synth](./images/week_2_day_3/us_synth.png)

![us_net](./images/week_2_day_3/us_net.png)


Consider another verilog code shown below :
```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count==3'b100;

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
In this case since q is asserted only when count == 3'b100, all the three flip-flops are used. Hence even after optimisation , the code will infer three flops.

The simulation, synthesis result and the netlist are shown below :

![us1_sim](./images/week_2_day_3/us1_sim.png)

![us1_synth](./images/week_2_day_3/us1_synth.png)

![us1_net](./images/week_2_day_3/us1_net.png)




## Day - 4 : Gate Level Simulation (GLS), Blocking Vs Non-blocking assignment and Synthesis-Simulation Mismatch

### **Gate Level Simulation**
Gate Level Simulation helps ensure that the synthesized version of the design matches the specification both in terms of functionality and  timing. It helps identify mistakes and differences in the synthesised netlist and ensures that the final design functions as intended. Generally GLS is done to ensure that there is no synthesis-simulation mismatch. To perform the GLS the testbench that is used to verify the RTL is used. The GLS flow is similar to the testbench flow except that gate level verilog models are also used. It is necessary to mention the gatelevel verilog models  to iverilog to make the iverilog understand about the standard cell given in the library .GLS requires adding information about timing delays. Gate level Verilog models can be functional and timing aware. If the gate level models are delay annotated then it can used for timing validation. 

![gls](./images/week_2_day_4/gls.png)

### **Synthesis-Simulation Mismatch**
Synthesis-simulation mismatch refers to the differences between the behavior of a digital circuit as simulated at the Register Transfer Level (RTL) and its behavior after being synthesized to gate-level netlists. Synthesis-simulation mismatch can occur because of the following reasons:
1. Missing Sensitivity List
2. Blocking vs Non-blocking assignments
3. Non standard verilog coding

#### **1. Missing Sensitivity List**
Consider the verilog code and its corresponding graph shown below :
```
module mux(
	input i0,i1,s,
	output reg y
)
	always @(sel) begin
		if(sel)
			y = i1;
		else
			y = i0;
	end
endmodule
```
![mux_eg](./images/week_2_day_4/mux_eg.png)

The "always" block is sensitive only to the "sel" signal. Whenever there's a modification in the "sel" output, it triggers a change in the output value. However, as this piece of code implies a multiplexer, the output should also change if the input changes. Since the sensitivity list includes only "sel," the output remains unaffected and it doesn't follow the input i0 when the sel is logic 0. Hence this a circuit behaves like a latch.

In order to solve the problem all the critical signals needed to be mentioned in the sensitivity list. So the corrected code is given below :
```
module mux(
	input i0,i1,s,
	output reg y
)
	always @(*) begin //* - It considers changes in all the input signals. So always is evaluated whenever any signal changes.
		if(sel)
			y = i1;
		else
			y = i0;
	end
endmodule
```
#### **2. Blocking and Non-Blocking Statements in Verilog**
Blocking and Non-Blocking statemnets are very important statements. They must used with utmost care so that intended logic is created. These statements are used inside the always block.
**1. Blocking Assignment:**
Blocking assignments are denoted using the "=" operator. When a blocking assignment is executed, it directly assigns the right-hand side value to the left-hand side variable immediately within the current simulation cycle. The subsequent statements in the procedural block  will wait for this assignment to complete before proceeding. Blocking assignments are sequentially executed.

**2. Non-blocking Assignment:**
Non-blocking assignments are denoted using the "<=" operator. When a non-blocking assignment is encountered, the right-hand side value is scheduled to be assigned to the left-hand side variable at the end of the current simulation cycle. This means that all non-blocking assignments within a procedural block are executed simultaneously, updating variables concurrently. The value changes take effect in the next simulation cycle. Non-Blocking assignments are executed in parallel.

#### **Caveats with Blocking Assignment**
**Example 1**
Consider the verilog code given below:
```
module code(
	input clk,reset,d,
	output reg q
)
	reg q0;
	always @(posedge clk, posedge reset) begin
		if(reset) begin
			q=1'b0;
			q0=1'b0;
		end
		else begin
			q = q0; //Line 1
			q0=d; // Line 2
		end
	end
endmodule
```
The inetent of this code is to create a 2-bit shift register. Since blocking assignmnet is used for Line 1 and Line 2 both the lines will be executed sequentially. First line 1 will be executed creating a flip-flop whose input is q0 and output is q. Then line 2 will be executed which creates a second flip-flop whose input is d and output is q0 thereby connecting two flip-flops and creating a 2-bit shift register shown below:

![cav_block](./images/week_2_day_4/cav_block.png)

Consider the verilog code shown below :
```
module code(
	input clk,reset,d,
	output reg q
)
	reg q0;
	always @(posedge clk, posedge reset) begin
		if(reset) begin
			q=1'b0;
			q0=1'b0;
		end
		else begin
			q0 = d; //Line 1
			q=q0; // Line 2
		end
	end
endmodule
```
This code looks similar to the previous one except that line 1 and line 2 are interchanged. Since , blocking assignment is used line 1 and line 2 will be executed sequentially. First line 1 will be executed which creates a D flip-flop with the input d and output q0, then line 2 is executed. Since q0 is already defined assigning q0 to q creates wire . Hence only flip-flop is inferred instead of two. The circuit corresponding to the code is shown below :

![cav_block_1](./images/week_2_day_4/cav_block_1.png)


**Example 2**
Consider the verilog code shown below :
```
module(
	input a,b,c,
	output reg y
)
	reg q0;
	always @(*) begin
		y = q0 & c; //Line 1
		q0 = a|b; //Line 2
	end
endmodule
```
In line 1 the output y is assigned with q0&c. But q0 is not mentioned anywhere before. Hence the previous value of the q0 will be taken and this will not infer a combinational circuit as expected instead a latch based circuit will be inferred. The corrected version of the code is shown below:
```
module(
	input a,b,c,
	output reg y
)
	reg q0;
	always @(*) begin
		q0 = a|b; //Line 1
		y = q0 & c; //Line 2
		
	end
endmodule
``` 

### **Illustration of GLS and Synthesis Simulation Mismatch**

**Steps to simulate, generate the netlist and to perform the GLS for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
# opt_clean -purge # If optimisation has to be done
# dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib # if sequential circuit is used 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

Steps to perform GLS:
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v <netlist_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

#### **Example 1**
Consider the verilog code shown below :
```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
endmodule
```
In verilog ternary operator will realize  multiplexer upin synthesis. If the operand left of the ? is true then output follows the immediate operand right of  ? otherwise the ouput follows the immediate operand to the right of :.

The simulation, synthesis result , the netlist and the GLS are shown below :

![gls_1_sim](./images/week_2_day_4/gls_1_sim.png)

![gls_1_synth](./images/week_2_day_4/gls_1_synth.png)

![gls_1_net](./images/week_2_day_4/gls_1_net.png)

![gls_1_gls](./images/week_2_day_4/gls_1_gls.png)

In this case there is no synthesis and simulation mismatch.

#### **Example 2**
Consider the verilog code shown below :
```
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```
This code only has sel signal in sensitivity list. Hence the RTL simulation output will not match the expected specification.

The simulation, synthesis result , the netlist and the GLS are shown below :

![gls_2_sim](./images/week_2_day_4/gls_2_sim.png)

![gls_2_synth](./images/week_2_day_4/gls_2_synth.png)

![gls_2_net](./images/week_2_day_4/gls_2_net.png)

![gls_2_gls](./images/week_2_day_4/gls_2_gls.png)

In this case there is a synthesis and simulation mismatch. While performing synthesis yosys has corrected the sensitivity list error.


#### **Example 3**
Consider the verilog code shown below :
```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c; //Line 1
	x = a | b; //Line 2
end
endmodule
```
This code only has signal x in line which is not defined before. Hence the previous value of x will be taken and the expression will be evaluated. Hence the RTL simulation output will not match the expected specification and will infer a latch based circuit instead of the combinational circuit.

The simulation, synthesis result , the netlist and the GLS are shown below :

![gls_3_sim](./images/week_2_day_4/gls_3_sim.png)

![gls_3_synth](./images/week_2_day_4/gls_3_synth.png)

![gls_3_net](./images/week_2_day_4/gls_3_net.png)

![gls_3_gls](./images/week_2_day_4/gls_3_gls.png)

In this case there is a synthesis and simulation mismatch. While performing synthesis yosys has corrected the latch error.



## Day - 5 : If, case, for and for generate

### **If statement**
if is a conditional statement that is used to execute the particular piece of the code  if the condition evaluates to true i.e, logic high otherwise the code inside the body of the else part will be executed. if statement is mainly used to create a priority logic.

**Syntax for if-else**
```
if (cond) begin
	<body>
end
else begin
	<body>
end
```
**Syntax for if-else if -else**
```
if (cond1) begin
	<body>
end
else if (cond2) begin
	<body>
end
else begin
	<body>
end
```
Since if statement is priority based the equivalent hardware realization of the if - else if - else is shown below :

![if_elseif](./images/week_2_day_5/if_else_hard.png)

In terms of hardware cond 1 gets the highest priority, then cond 2 gets the second priority and else part gets the least priority. In code perspective if any one of the condition evaluates to true then the body of that particular condition will be evaluated and then the execution leaves the entire if  else statements i.e, it will not evaluate the remaining conditions and it will start executing the statement after the if else statements.

#### Danger/Caution with if 
If the "if else" statement is not properly coded i.e., "incomplete if" then it may result in inferred latches. An inferred latch is an unintended storage element that can be generated in a hardware design when a synthesizer cannot determine a unique value for a signal under certain conditions. This can occur when a signal is assigned a value inside an "if-else" block without providing values for all possible conditions.

Consider the piece of code shown below:
```
if(cond1)
	y=a;
else if(cond2)
	y=b;
```
In this code else part is not given. As a result if both the condition evaluates to false then the hardware will latch i.e, it will retain the previous value and crete the combinational loop. The hardware and the logic diagram realization of the code is shown below :


![comb_loop](./images/week_2_day_5/comb_loop.png)


![hardware_comb_loop](./images/week_2_day_5/hardware_comb_loop.png)


There should not be an latch until it is intended. For example in counter incomplete if statement is written in order to create a latch. Consider the counter code shown below :
```
always @(posedge clk, posedge reset) begin
	if(reset)
		count<=3'b000;
	else if(en)
		count<=count+1;
end
```
This code will realize a latch as else part is not mentioned and it will not have any adverse effects. The counter should retain its previous value if en is not asserted. The hardware realization diagram is shown below :

![counter_latch](./images/week_2_day_5/counter_latch.png)


### **Case Statement**
If and case statement are used inside the always block. The variables that are assigned inside case should be reg datatype. case statement is used to implement multi-way branching based on the value of an expression. It provides an alternative to using multiple if-else statements when needed to compare a single value against a set of possible values. The difference between case and if else statement is case statement is not priority based and it will infer a single multiplexer with 2^n inputs whereas if else statement is based on the priority and it will infer multiple 2:1 multiplexers.

**Syntax for case statement**
```
case (expression)
    value_1: // Code to execute if expression matches value_1
    value_2: // Code to execute if expression matches value_2
    // ...
    value_n: // Code to execute if expression matches value_n
    default: // Code to execute if none of the values match
endcase
```

cosider an example code shown below:
```
always @(*) begin
	case(sel)
		2'b00 : y=a;
		2'b01 : y=b;
		2'b10 : y=c;
		2'b11 : y=d;
	endcase
end
```
The equivalent hardware realization diagram is shown below:

![case_hardware](./images/week_2_day_5/case_hardware.png)


#### **Caveats with case**
**1. Incomplete case statement**
Incomplete case statement i.e., case statement without all the possible values of the expression will result in inferred latch. Consider the piece of code given below :
```
always @(*) begin
	case(sel)
		2'b00 : y=a;
		2'b01 : y=b;
	endcase
end
```
Since for the other two combinations of the sel signal the output is not specified. Hence it will infer a latch as shown below :

![case_latch](./images/week_2_day_5/case_latch.png)

In order to avoid the inferred latch in case statement, it is recommended to code case with deafault statement as shown below :  
```
always @(*) begin
	case(sel)
		2'b00 : y=a;
		2'b01 : y=b;
		default : y=c;
	endcase
end
```
When sel is 2'b10 or 2'b11 then the default statement in case will be executed. The equivalent hardware realization diagram is shown below :

![case_default](./images/week_2_day_5/case_default.png)

**2. Partial assignment**
Consider the code given below :
```
always @(*) begin
	case(sel)
		2'b00 : begin x=a; y=b; end
		2'b10 : y=a;
		default : begin x=c;y=d; end
	endcase
end
```
In this code when the sel signal is 2'b10, the value of x is not assigned. Even though default statement is given because of the partial assignment it will infer an latch as shown below :

![partial_assignment](./images/week_2_day_5/partial_ass.png)

**3. Overlapping Case**
Consider the code given below :
```
always @(*) begin
	case(sel)
		2'b00 : body 1;
		2'b01 : body 2;
		2'b10 : body 3;
		2'b1? : body 4;
	endcase
end
```
? - Take any value.
Unlike if statement if one condition evaluates to true then rest of the condition are not checked, in case all the values are checked even if a value matches. In this code if sel == 2'b10, the body 3 will be executed. After completing the body 3 , body 4 will also be executed since sel == 2'b1?. ? can take 0 or 1. Thus there will be an unpredictable output.

### **Illustration of inferred latches in if statement**

**Steps to simulate, generate the netlist and to perform the GLS for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
# opt_clean -purge # If optimisation has to be done
# dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib # if sequential circuit is used 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

Steps to perform GLS:
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v <netlist_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

#### **Example 1**
Consider the verilog code shown below : 
```
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
end
endmodule
```
In this code the else statement is not mentioned. Hence it will infer a latch with input to the en pin as i0. When i0 is 0 the previous output value will be retained.

The simulation , synthesis result, netlist and GLS is shown below :

![if_1_sim](./images/week_2_day_5/if_1_sim.png)

![if_1_synth](./images/week_2_day_5/if_1_synth.png)

![if_1_net](./images/week_2_day_5/if_1_net.png)

![if_1_gls](./images/week_2_day_5/if_1_gls.png)

#### **Example 2**
Consider the verilog code shown below : 
```
module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

end
endmodule
```
In this code the else statement is not mentioned. Hence it will infer a latch with input to the en pin as (i0 OR i2). When i0 and i2 both 0 simultaneously the previous output value will be retained.

The simulation , synthesis result, netlist and GLS is shown below :

![if_2_sim](./images/week_2_day_5/if_2_sim.png)

![if_2_synth](./images/week_2_day_5/if_2_synth.png)

![if_2_net](./images/week_2_day_5/if_2_net.png)

![if_2_gls](./images/week_2_day_5/if_2_gls.png)



### **Illustration of inferred latches in case statement**

**Steps to simulate, generate the netlist and to perform the GLS for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
# opt_clean -purge # If optimisation has to be done
# dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib # if sequential circuit is used 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

Steps to perform GLS:
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v <netlist_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

#### **Example 1**
Consider the verilog code shown below : 
```
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
	endcase
end
endmodule
```
In this code the if sel is 2'b10 or 2'b11 the assignment value of y is not specified and also there is no default statement. Hence it will infer a latch with input to the en pin as sel[1]'. When sel == 2'b10 or 2'b11 the previous output value will be retained.

The simulation , synthesis result, netlist and GLS is shown below :

![case_1_sim](./images/week_2_day_5/case_1_sim.png)

![case_1_synth](./images/week_2_day_5/case_1_synth.png)

![case_1_net](./images/week_2_day_5/case_1_net.png)

![case_1_gls](./images/week_2_day_5/case_1_gls.png)

#### **Example 2 : case with default**
Consider the verilog code shown below : 
```
module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
		default : y = i2;
	endcase
end
endmodule
```
In this code the if sel is 2'b10 or 2'b11 the assignment value of y is not specified but default statement is provided. Hence it will infer not infer a latch when sel == 2'b10 or 2'b11 instead it will execute the default statement and assign default value given to output .

The simulation , synthesis result, netlist and GLS is shown below :

![case_2_sim](./images/week_2_day_5/case_2_sim.png)

![case_2_synth](./images/week_2_day_5/case_2_synth.png)

From synthesis report it is evident that latches are not inferred.

![case_2_net](./images/week_2_day_5/case_2_net.png)

![case_2_gls](./images/week_2_day_5/case_2_gls.png)


#### **Example 3 : Partial case assignment**
Consider the verilog code shown below : 
```
module partial_case_assign (input i0 , input i1 , input i2 , input [1:0] sel, output reg y , output reg x);
always @ (*)
begin
	case(sel)
		2'b00 : begin
			y = i0;
			x = i2;
			end
		2'b01 : y = i1;
		default : begin
		           x = i1;
			   y = i2;
			  end
	endcase
end
endmodule
```
In this code the if sel is 2'b10 or 2'b11 the assignment value of x is not specified and evn though there is a default statement it will infer a latch with input to the en pin as sel[1] OR sel[0]' for x because of the partial assignment. When sel == 2'b10 or 2'b11 the previous output value of x will be retained.

The simulation , synthesis result, netlist and GLS is shown below :

![case_3_sim](./images/week_2_day_5/case_3_sim.png)

![case_3_synth](./images/week_2_day_5/case_3_synth.png)

![case_3_net](./images/week_2_day_5/case_3_net.png)

![case_3_gls](./images/week_2_day_5/case_3_gls.png)

#### **Example 4 : Overlapping case assignment**
Consider the verilog code shown below : 
```
module bad_case (input i0 , input i1, input i2, input i3 , input [1:0] sel, output reg y);
always @(*)
begin
	case(sel)
		2'b00: y = i0;
		2'b01: y = i1;
		2'b10: y = i2;
		2'b1?: y = i3;
		//2'b11: y = i3;
	endcase
end

endmodule
```
In this code the if sel is 2'b10, then there is an overlapping case with 2'b10 and 2'b1? as ? can take both 0 and 1. This will not infer a latch but there will be a synthesis simulation mismatch and output is unpredictable.

The simulation , synthesis result, netlist and GLS is shown below :

![case_4_sim](./images/week_2_day_5/case_4_sim.png)

From simulation it is evident that when sel == 1'b0 then somehow the output becomes high. But when sel == 2'b11, the output follows i3. 

![case_4_synth](./images/week_2_day_5/case_4_synth.png)

![case_4_net](./images/week_2_day_5/case_4_net.png)

![case_4_gls](./images/week_2_day_5/case_4_gls.png)

Upon synthesis yosys has rectified the mistake and it inferred a 4:1 multiplexer and when sel == 2'b10 output follows i2. This is evident from the GLS shown in the above figure. 

### **Looping Constructs**
In verilog there are two synthesizable looping constructs :
	1. for loop
	2. generate for
For loop is used inside the always blovk while the generate for is used outside the always block.

#### **For loop**
For loop is a construct that allows  to repeatedly execute a block of code for a fixed number of iterations. It is commonly used for generating sequences, initializing arrays, and performing repetitive operations.

**Syntax of for loop**
```
for (initialization; condition; increment) begin
    // Code to execute in each iteration
end
```
Consider the example for the for loop given below :

```
integer i;
always @(*) begin
	for(i=0;i<32;i=i+1)
		if(i==sel)
			y=inp[i];
end
``` 
The above code creates a 32:1 multiplexer. If the multiplexer is created using if or case statement it is difficult to list out all possible combinations for the select statement when the number of inputs increase. But using for loop it is easier to code and it can be easily converted into other higher input multiplexers by changing the condition.

Consider another example for the for loop shown below:
```
integer i;
always @(*) begin
	op_bus = 8'b0;
	for(i=0;i<8;i=i+1)
		if(sel==i)
			op_bus[i]=inp;
end
```
The above code creates a 8:1 demultiplexer. In this code blocking statement is used to initialize the op_bus to zero. It is done to ensure the functionality of the demultiplexer since only one of the channel in the output bus will be high and rest of the channel will be zero.

#### **Generate for**
Generate for loop is used to replicate or generate multiple instances of a logic block based on a loop. Generate statements are particularly convenient when the same operation or module instance is repeated for multiple bits of a vector, or when certain Verilog code is conditionally included based on parameter .definitions.

**Syntax for generate for loop**
```
genvar index; // Declare a generate variable
generate
    for (index = initial_value; index < limit_value; index = index + step_value) begin
        // Logic to be generated
    end
endgenerate
```

Consider the example shown below:
```
genvar i;
generate 
	for(i=0;i<8;i=i+1) begin
		and u(.a(in1[i]),..b(in2[i]), .y(op[i]));
	end
endgenerate
```
The above code will create 10 instances of the AND gate at a time and all the 10 instances will work independently. Another example is ripple carry adder which can be coded using generate for loop since it consists of four full adders. 



### **Illustration of for and generate for loops**

**Steps to simulate, generate the netlist and to perform the GLS for the below designs**

Simulation steps :
```
iverilog <rtl_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

Generating netlist steps :
```
# Remove "#" if needed

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog <module_name.v> 
synth -top <top_module_name>
#flatten # if hierarchy is given
# opt_clean -purge # If optimisation has to be done
# dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib # if sequential circuit is used 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr <netlist_name.v>
```

Steps to perform GLS:
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v <netlist_name.v> <tb_name.v>
./a.out
gtkwave <dump_file_name.vcd>
```

#### **Example 1 : Mux using for loop**
Consider the verilog code shown below : 
```
module mux_generate (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;
always @ (*)
begin
for(k = 0; k < 4; k=k+1) begin
	if(k == sel)
		y = i_int[k];
end
end
endmodule
```

The simulation , synthesis result, netlist and GLS is shown below :

![for_1_sim](./images/week_2_day_5/for_1_sim.png)

![for_1_synth](./images/week_2_day_5/for_1_synth.png)

![for_1_net](./images/week_2_day_5/for_1_net.png)

![for_1_gls](./images/week_2_day_5/for_1_gls.png)


#### **Example 2 : Demux using for loop**
Consider the verilog code shown below : 
```
module demux_generate (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
for(k = 0; k < 8; k++) begin
	if(k == sel)
		y_int[k] = i;
end
end
endmodule
```

The simulation , synthesis result, netlist and GLS is shown below :

![for_2_sim](./images/week_2_day_5/for_2_sim.png)

![for_2_synth](./images/week_2_day_5/for_2_synth.png)

![for_2_net](./images/week_2_day_5/for_2_net.png)

![for_2_gls](./images/week_2_day_5/for_2_gls.png)


#### **Example 3 : Illustration of generate for using Ripple Carry Adder**
Consider the verilog code shown below : 
```
module fa (input a , input b , input c, output co , output sum);
	assign {co,sum}  = a + b + c ;
endmodule

module rca (input [7:0] num1 , input [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0]int_co;

genvar i;
generate
	for (i = 1 ; i < 8; i=i+1) begin
		fa u_fa_1 (.a(num1[i]),.b(num2[i]),.c(int_co[i-1]),.co(int_co[i]),.sum(int_sum[i]));
	end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));


assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```
The above ripple carry adder code consists of a full adder submodule which is instantiated 7 times inside the generate for loop. This creates a 8 bit ripple carry adder.

The simulation , synthesis result, netlist and GLS is shown below :

![gen_1_sim](./images/week_2_day_5/gen_1_sim.png)

![gen_1_synth](./images/week_2_day_5/gen_1_synth.png)

![gen_1_net](./images/week_2_day_5/gen_1_net.png)

![gen_1_gls](./images/week_2_day_5/gen_1_gls.png)




[Acknowledgement Section]:#
## Acknowledgement
1. Kunal Ghosh, VSD Corp. Pvt. Ltd.
2. Sumanto Kar, Sr. Project Technical Assistant , IIT Bombay
3. Alwin Shaju, Colleague IIITB
4. Adam Teman, Associate Professor at Bar-Ilan University in Ramat Gan, Israel   

[Reference Section]:#
## References
1.  https://yosyshq.net/yosys/
2.  https://steveicarus.github.io/iverilog/
3.  https://gtkwave.sourceforge.net/
4.  https://ngspice.sourceforge.io/
5.  https://github.com/The-OpenROAD-Project/OpenSTA
6.  http://opencircuitdesign.com/magic/
7.  https://github.com/The-OpenROAD-Project/OpenLane
8.  https://www.eng.biu.ac.il/temanad/digital-vlsi-design/
9.  https://yosyshq.readthedocs.io/projects/yosys/en/latest/cmd_ref.html
10. https://www.youtube.com/watch?v=EczW2IWdnOM
11. https://learn.digilentinc.com/Documents/277

