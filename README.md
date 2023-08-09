# IIITB_Physical_Design_Using_ASIC_Class

## Table of Contents
- [Week - 1](#week---1)
    * [Day - 1 : Software Installation](#day---1--software-installation)
- [Week - 2](#week---2)
    * [Day - 1 : Introduction to Verilog RTL Design and Synthesis](#day---1--introduction-to-verilog-rtl-design-and-synthesis)
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