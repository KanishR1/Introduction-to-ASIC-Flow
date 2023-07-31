# IIITB_Physical_Design_Using_ASIC_Class

## Week -1

## Software Installation

### Yosys

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


### Icarus Verilog

**Steps to install Icarus Verilog**
```
sudo apt-get install iverilog
```

![iverilog](./softwares/iverilog.png)

### Gtkwave

**Steps to install GTKKwave**
```
sudo apt update
sudo apt install gtkwave
```

![gtkwave](./softwares/gtkwave.png)