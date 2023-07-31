# IIITB_Physical_Design_Using_ASIC_Class

## Table of Contents
- [Week - 1](#week---1)
    * [Day - 1](#day---1-software-installation)
- [References](#references)

## Week - 1 
## Day - 1 :Software Installation

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
sudo apt install make (If make is not installed please install it) 
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make 
sudo make install
```
![yosys](./softwares/yosys.png)    




[Icarus Verilog Section]:#
### **ICARUS VERILOG**
Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format (EDIF). It supports the 1995, 2001 and 2005 versions of the standard, portions of SystemVerilog, and some extensions.Icarus Verilog is released under the GNU General Public License, Icarus Verilog is free software. Icarus is composed of a Verilog compiler (including a Verilog preprocessor) with support for plug-in backends, and a virtual machine that simulates the design.

**Steps to install Icarus Verilog**
```
sudo apt-get install iverilog
```
![iverilog](./softwares/iverilog.png)



[GTKWave Section]:#
### **GTKWAVE**
GTKWave is a fully featured GTK+ based wave viewer for Unix and Win32 which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing.
**Steps to install GTKKwave**
```
sudo apt update
sudo apt install gtkwave
```
![gtkwave](./softwares/gtkwave.png)



[Reference Section]:#
## References
1. https://yosyshq.net/yosys/
2. https://steveicarus.github.io/iverilog/
3. https://gtkwave.sourceforge.net/