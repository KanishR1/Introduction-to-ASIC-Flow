# IIITB_Physical_Design_Using_ASIC_Class

## Table of Contents
- [Week - 1](#week---1)
    * [Day - 1 : Software Installation](#day---1--software-installation)
- [Week - 2](#week---2)
    * [Day - 1 : Introduction to Verilog RTL Design and Synthesis](#day---1--introduction-to-verilog-rtl-design-and-synthesis)
	* [Day - 2 : Timing libs, Hierarchical vs Flat Synthesis and Efficient flop coding styles](#day---2--timing-libs-hierarchical-vs-flat-synthesis-and-efficient-flop-coding-styles)
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

![iverilog_based_simulation flow](./images/day_1/iverilog_based_simulation_flow.png)

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
![folder_structure](./images/day_1/folder_structure.png)

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

![iverilog_gtkwave_demo](./images/day_1/ievrilog_gtkwave_demo.png)


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

![yosys_flow](./images/day_1/yosys_flow.png)

![netlist_verification](./images/day_1/netlist_verification.png)



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

![read_yosys_commands](./images/day_1/read_yosys_commands.png)



**Step 5:** Synthesize the verilog file.
```
synth -top good_mux
```

___
**synth** - command runs the default synthesis script. The ***-top*** switch use the specified module as top module.
___

![synth_op](./images/day_1/synth_op.png)

The output of the synthesis displays the number of wires used , number of standard cells used and the name of the standard cell. 


**Step 6:** Generate the netlist
```
abc -liberty /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

___
**abc** -  This command uses the ABC tool for technology mapping of yosys's internal gate library to a target architecture. The ***-lib*** switch liberty <file>
generate netlists for the specified cell library using the liberty file format.
___

![abc_op](./images/day_1/abc_op.png)

The output of the synthesis displays the number of input and output signals and the name of the standard cell that is used. 


**Step 7:** View the netlist
```
show
```

___
**show** - Creates a graphviz DOT file for the selected part of the design and compile it to a graphics file. It generates a schematic.
___

![show_op](./images/day_1/show_op.png)

In the schematic there is sky130 based 2:1 multiplexer standard cell with three inputs and one output.


**Step 8:** Write the netlist
```
write_verilog -noattr good_mux_netlist.v
```
___
**write_verilog** - Writes the current design to a Verilog file. The ***-noattr** switch skips the attributes from included in the output netlist.
___

The netlist and the write_verilog command is shown below:

![write_op](./images/day_1/write_op.png)

![netlist_op](./images/day_1/netlist_op.png)




## Day - 2 : Timing libs, Hierarchical vs Flat Synthesis and Efficient flop coding styles
### **Exploring the Contents of .lib File**
To view the contents inside the .lib file type the following command :
```
cd ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/
gvim sky130_fd_sc_hd__tt_025C_1v80.lib
```
![lib_img](./images/day_2/lib_img.png)

One of the fundamental parameter stored within .lib files comprises PVT parameters, where P signifies Process, V represents Voltage, and T denotes Temperature. 
The variations in these parameters can cause significant changes in the performance of circuits.

1. Process Variation: During the manufacturing process, there may be some deviations in the transistor characteristics, causing non-uniformity across the semiconductor wafer. Critical parameters like oxide thickness, dopant concentration, and transistor dimensions experience alterations.

2. Voltage Variation: Voltage regulators might exhibit variability in their output voltage over time, inducing fluctuations in current and impacting the operational speed of circuits. 

3. Temperature Variation: The functionality of a semiconductor device is sensitive to changes in temperature, particularly at the internal junctions of the chip. 

Further it contains the technology that is used is CMOS for which delay are modelled  through table lookup. This file also defines the units for parameters like voltage, power, current, capacitance, and resistance. Within the .lib library, each standard cell consists a  set of parameters specific to that cell's features.

Consider the a2111oi gate whose parameters and verilog files is shown below:

![a2111o_img](./images/day_2/a2111o_img.png)
![a2111o](./images/day_2/a2111o.png)

This is a 2-input AND gate and a 4-input NOR gate. Within the .lib file, sevetral parameters specific to this particular standard cell is given, including leakage power values for every possible input combination, specifications regarding pin type and pin capacitances, internal power metrics, timing-related particulars, as well as area measurements and power-related specifics for the standard cells. Similarly for all the standard cells the parameters above mentioned is listed in the .lib file.

Consider the different versions of the same logic gate shown below:
![area_depict](./images/day_2/area_dep.png)

In all the three the logic inferred is same bu the area is different. Wider cells consume more power but delay wise it is less. The leakage power in the wider cell is more compared to the narrow cell which is depicted in the image .

## **Hiererchical Synthesis and Flat Synthesis**
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
 Note:
 When using hierarchical design instead of enetering the ***show*** command to view the file ***show <module_name>*** must be otherwise yosys will generate the following error : "ERROR: For formats different than 'ps' or 'dot' only one module must be selected."
 ___

 ![hier_show](./images/day_2/hierarchi_des.png)
 ![netlist_hier](./images/day_2/netlist_hier.png)
 
 Yosys does not show the AND gate and OR gate in the synthesis instead it shows the submodule names. The netlist also contains the AND and OR logic in separate submodules. Some times yosys may optimize the design such that the OR gate will be created using NAND gates. It is because the CMOS structure of the OR gate which is shown below has two pmos transistors stacked together. The mobility of the holes is less than the mobility of the electrons , since mosfets are majority carrier devices and majority carrier of the pmos is holes it increases the delay hence it becomes a bad circuit. In NAND gate implementation only the nmos are stacked.
 ![cmos_or](./images/day_2/CMOS_OR.jpg)

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
![flat_des](./images/day_2/flat_des.png)
![netlist_flat](./images/day_2/netlist_flat.png)

The flatten command breaks the hierarchy and makes the design into a single module by creating AND and OR gates for the logics inferred by the submodule which is shown in the images above.

**Synthesising a Submodule :**
Suppose a multiplier design needs to be used in numerous instances. Rather than undergoing synthesis six times independently, the preferred approach is to synthesize it once and then duplicate it within the primary module. Using module-level synthesis becomes advantageous when dealing with multiple occurrences of identical modules. Another reason for synthesizing submodule is to follow the principle of divide and conque for extensive designs that may not be optimized effectively, synthesizing the design module by module ensures that each module is effectively optimized.

**Steps to synthesis submodule :**
 
```
cd /home/kanish/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog 
read_verilog multiple_modules.v 
synth -top sub_module
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
```
![submodule_demo](./images/day_2/submodule_synth.png)

[Reference Section]:#
## References
1. https://yosyshq.net/yosys/
2. https://steveicarus.github.io/iverilog/
3. https://gtkwave.sourceforge.net/
4. https://ngspice.sourceforge.io/
5. https://github.com/The-OpenROAD-Project/OpenSTA
6. http://opencircuitdesign.com/magic/
7. https://github.com/The-OpenROAD-Project/OpenLane
8. https://www.eng.biu.ac.il/temanad/digital-vlsi-design/
9. https://yosyshq.readthedocs.io/projects/yosys/en/latest/cmd_ref.html
10. https://www.youtube.com/watch?v=EczW2IWdnOM