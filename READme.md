# 3 Bit CMOS Wallace Tree Multiplier

* The purpose of this project is to design a CMOS 3-Bit Wallace Tree Multiplier using an Opensource EDA Tool called eSim, an Opensource Spice Simulator called ngspice and Sky130 PDK.

# Table of Contents

1. [Introduction](#Introduction)
2. [Installation of the tools](#installation-of-the-tools)
3. [Methodology](#Methodology)
    - [Step1 Construct AND Gate](#step1-construct-and-gate)
    - [Step2 Construct XOR Gate](#Step2-Construct-XOR-Gate)
    - [Step3 Construct Half Adder](#step3-construct-half-adder)
    - [Step4 Construct Full Adder](#step4-construct-full-adder)
    - [Step5 Construct 3-Bit Wallace Multiplier](#step5-construct-3-bit-wallace-multiplier) 
4. [Results](#results)
    - [Command Window](#command-window)
    - [Obtained Output Waveforms](#obtained-output-waveforms)
5. [References](#references)
6. [Acknowledgement](#Acknowledgement)
7. [Author](#author)


## Introduction 

#### Wallace Multiplier

* A Wallace Multiplier is nothing but a Binary Multiplier. a digital circuit that multiplies two integers. It uses a selection of full and half adders to sum the partial products 
in stages until only two numbers are left. Wallace multipliers reduce as much as possible on every layer that it passes through.
* Wallace multipliers were devised by the Australian computer scientist Chris Wallace in 1964.
* The Wallace tree has three steps:
  1. Multiply each bit of one of the arguments, by each bit of the other.
  2. Reduce the number of partial products to two by layers of full and half adders.
  3. Group the wires into two numbers and then add them with a conventional adder.
* For more information you may wish to visit : [Link](https://en.wikipedia.org/wiki/Wallace_tree#:~:text=A%20Wallace%20multiplier%20is%20a,until%20two%20numbers%20are%20left)

#### Ngspice 

- Ngspice is the open source spice simulator for electric and electronic circuits. 
- Ngspice implements various circuits elements, like resistors, capacitors, inductors (single or mutual), transmission lines and a number of semiconductor devices like 
  diodes, bipolar transistors, MOSFETs, MESFETs, JFETs and HFETs.
- For more information about ngspice : [Link](http://ngspice.sourceforge.net/)

#### Sky130 PDKs : Opensource PDK

- The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which 
  can be used to create manufacturable designs at SkyWater's facility.
- For more information about Sky130 : [Link](https://www.layouteditor.org/schematiceditor/libraries/skywater)

## Installation of the Tools

- eSim : [Link](https://esim.fossee.in/downloads)
- Ngspice : [Link](https://sourceforge.net/projects/ngspice/files/)
- Sky130 PDK : [Link](https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip)

Follow these steps for Sky130 download and implementaion :
1. Download sky130 from this link mentioned above and unzip it.
2. Save the .cir.out file in the sky_fd_pr folder as .cir file.
3. Open with notepad and add the path .lib "models/sky130.lib.spice" tt at the top.
4. Replace with CMOSP, mos_p with sky130_fd_pr_pfet_01v8 and CMOSN, mos_n with  sky130_fd_pr_nfet_01v8.
5. To replace inductor, capacitor, resistor do it this way, for Ex : L1 out gnd 1m by x1  out gnd mid 0 sky130_fd_pr__ind_03_90.

```
Note: For more details go to the cells folder in sky_fd_pr. 
Open the specific component folder which you want to use. 
Then open the test folder and check the SPICE file. 
The SPICE file is an example of implementation of that component. 
You will get to know how to use the component in your ckt.

```

6. Now Run the circuit with ngspice.

To Run the ckt using ngspice:
1. Right click on .cir file.
2. Click on Open With.
3. Browse for the ngspice.
4. If ngspice not present scroll down click on More Apps.
5. Go to the FOSSEE folder search for Ngspice and Run it.

- For reference to download the tools and get an exposure to simulation using eSim, ngspice and Sky130, you may want to check the course : [Link](https://www.udemy.com/share/104Ie63@EAkZWPY9P8VxMdqx7DK4NzA2SwmLzfA1pfjL_MLTmkTV9O283uXSWpJkSSNIPjmKmA==/)

## Methodology

### Step1 Construct AND Gate

![AND-Gate-and-its-Truth-Table](https://user-images.githubusercontent.com/83152452/152642602-e71b7326-8b90-47f9-b701-4fd3e85c7e4a.jpg)


- Construct the "and gate" as shown in the figure below using eSim :

![and_gate-1](https://user-images.githubusercontent.com/83152452/152638739-4d6e875d-5744-4e22-9bd9-941ed6165030.png)

![and_gate-2](https://user-images.githubusercontent.com/83152452/152638743-ae860cb2-7ff7-40b1-8a0a-c74b658eb9a5.png)

- Follow the steps as shown in the video for making a subcircuit once the and gate is made or designed :
 
  Visit the YouTube link : https://youtu.be/o6dUXrv8EqY
 
- Once every step is followed perfectly open the Netlist that is generated and make the necessary changes to add the Sky130 models
- The Netlist generated initially is as shown below :

```

* C:\Users\priya\eSim-Workspace\and_gate\and_gate.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/2/2022 9:23:00 PM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
M1  Net-_M1-Pad1_ Net-_M1-Pad2_ Net-_M1-Pad3_ Net-_M1-Pad1_ mosfet_p		
M4  Net-_M1-Pad1_ Net-_M3-Pad2_ Net-_M1-Pad3_ Net-_M1-Pad1_ mosfet_p		
M6  Net-_M1-Pad1_ Net-_M1-Pad3_ Net-_M5-Pad1_ Net-_M1-Pad1_ mosfet_p		
M5  Net-_M5-Pad1_ Net-_M1-Pad3_ GND GND mosfet_n		
M3  Net-_M2-Pad3_ Net-_M3-Pad2_ GND GND mosfet_n		
M2  Net-_M1-Pad3_ Net-_M1-Pad2_ Net-_M2-Pad3_ Net-_M2-Pad3_ mosfet_n		
v1  Net-_M1-Pad1_ GND 3.3v		
U1  Net-_M1-Pad2_ Net-_M3-Pad2_ Net-_M5-Pad1_ PORT		

.end

```

- The Netlist generated after the subcircuit creation is as shown below :

```

* Subcircuit and_gate
.subckt and_gate net-_m1-pad2_ net-_m3-pad2_ net-_m5-pad1_ 
* c:\users\priya\esim-workspace\and_gate\and_gate.cir
m1  net-_m1-pad1_ net-_m1-pad2_ net-_m1-pad3_ net-_m1-pad1_ mosfet_p
m4  net-_m1-pad1_ net-_m3-pad2_ net-_m1-pad3_ net-_m1-pad1_ mosfet_p
m6  net-_m1-pad1_ net-_m1-pad3_ net-_m5-pad1_ net-_m1-pad1_ mosfet_p
m5  net-_m5-pad1_ net-_m1-pad3_ gnd gnd mosfet_n
m3  net-_m2-pad3_ net-_m3-pad2_ gnd gnd mosfet_n
m2  net-_m1-pad3_ net-_m1-pad2_ net-_m2-pad3_ net-_m2-pad3_ mosfet_n
v1  net-_m1-pad1_ gnd 3.3v
* Control Statements

.ends and_gate

```

- After making the necessary changes to the subcircuit file to add Sky130 models here is how the Spice code looks like :

```

* Subcircuit and_gate

.subckt and_gate net-_m1-pad2_ net-_m3-pad2_ net-_m5-pad1_ 

* c:\users\priya\esim-workspace\and_gate\and_gate.cir

xm2  net-_m1-pad3_ net-_m1-pad2_ net-_m2-pad3_ net-_m2-pad3_ sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm3  net-_m2-pad3_ net-_m3-pad2_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm1  net-_m1-pad1_ net-_m1-pad2_ net-_m1-pad3_ net-_m1-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm4  net-_m1-pad1_ net-_m3-pad2_ net-_m1-pad3_ net-_m1-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm5  net-_m5-pad1_ net-_m1-pad3_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm6  net-_m1-pad1_ net-_m1-pad3_ net-_m5-pad1_ net-_m1-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
v1  net-_m1-pad1_ gnd 3.3v

* Control Statements

.ends and_gate

```

- Save the above ngspice subcircuit spice file in a folder where the Sky130 folder is present.

### Step2 Construct XOR Gate

![EXOR-gate-and-its-truth-table](https://user-images.githubusercontent.com/83152452/152642603-5df31382-d2ff-47ec-8d22-e0e81c7c032a.jpg)


- Construct the "and gate" as shown in the figure below using eSim :

![xor_gate-1](https://user-images.githubusercontent.com/83152452/152638759-c48cc548-f537-4c1a-a70e-63fbb26f5604.png)

![xor_gate-2](https://user-images.githubusercontent.com/83152452/152638762-25e4215c-e7ee-4c59-8d6b-a1c676773843.png)

- Follow the similar steps as shown for AND Gate to implement XOR Gate and generate subcircuit & Netlist for the same.

- Once every step is followed perfectly open the Netlist that is generated and make the necessary changes to add the Sky130 models.
- The Netlist generated initially is as shown below :

```

* C:\Users\priya\eSim-Workspace\xor_gate\xor_gate.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/2/2022 10:39:05 PM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
M2  Net-_M14-Pad1_ Net-_M1-Pad2_ Net-_M1-Pad1_ Net-_M14-Pad1_ mosfet_p		
M1  Net-_M1-Pad1_ Net-_M1-Pad2_ GND GND mosfet_n		
M4  Net-_M14-Pad1_ Net-_M3-Pad2_ Net-_M11-Pad2_ Net-_M14-Pad1_ mosfet_p		
M3  Net-_M11-Pad2_ Net-_M3-Pad2_ GND GND mosfet_n		
M14  Net-_M14-Pad1_ Net-_M10-Pad3_ Net-_M13-Pad1_ Net-_M14-Pad1_ mosfet_p		
M13  Net-_M13-Pad1_ Net-_M10-Pad3_ GND GND mosfet_n		
M7  Net-_M14-Pad1_ Net-_M3-Pad2_ Net-_M10-Pad1_ Net-_M14-Pad1_ mosfet_p		
M8  Net-_M10-Pad1_ Net-_M11-Pad2_ Net-_M10-Pad3_ Net-_M10-Pad1_ mosfet_p		
M9  Net-_M14-Pad1_ Net-_M1-Pad1_ Net-_M10-Pad1_ Net-_M14-Pad1_ mosfet_p		
M10  Net-_M10-Pad1_ Net-_M1-Pad2_ Net-_M10-Pad3_ Net-_M10-Pad1_ mosfet_p		
M5  Net-_M10-Pad3_ Net-_M3-Pad2_ Net-_M5-Pad3_ Net-_M5-Pad3_ mosfet_n		
M6  Net-_M5-Pad3_ Net-_M1-Pad1_ GND GND mosfet_n		
M11  Net-_M10-Pad3_ Net-_M11-Pad2_ Net-_M11-Pad3_ Net-_M11-Pad3_ mosfet_n		
M12  Net-_M11-Pad3_ Net-_M1-Pad2_ GND GND mosfet_n		
U1  Net-_M1-Pad2_ Net-_M3-Pad2_ Net-_M13-Pad1_ PORT		
v1  Net-_M14-Pad1_ GND 3.3v		

.end

```

- The Netlist generated after the subcircuit creation is as shown below :

```

* Subcircuit xor_gate
.subckt xor_gate net-_m1-pad2_ net-_m3-pad2_ net-_m13-pad1_ 
* c:\fossee\esim\library\subcircuitlibrary\xor_gate\xor_gate.cir
m2  net-_m14-pad1_ net-_m1-pad2_ net-_m1-pad1_ net-_m14-pad1_ mosfet_p
m1  net-_m1-pad1_ net-_m1-pad2_ gnd gnd mosfet_n
m4  net-_m14-pad1_ net-_m3-pad2_ net-_m11-pad2_ net-_m14-pad1_ mosfet_p
m3  net-_m11-pad2_ net-_m3-pad2_ gnd gnd mosfet_n
m14  net-_m14-pad1_ net-_m10-pad3_ net-_m13-pad1_ net-_m14-pad1_ mosfet_p
m13  net-_m13-pad1_ net-_m10-pad3_ gnd gnd mosfet_n
m7  net-_m14-pad1_ net-_m3-pad2_ net-_m10-pad1_ net-_m14-pad1_ mosfet_p
m8  net-_m10-pad1_ net-_m11-pad2_ net-_m10-pad3_ net-_m10-pad1_ mosfet_p
m9  net-_m14-pad1_ net-_m1-pad1_ net-_m10-pad1_ net-_m14-pad1_ mosfet_p
m10  net-_m10-pad1_ net-_m1-pad2_ net-_m10-pad3_ net-_m10-pad1_ mosfet_p
m5  net-_m10-pad3_ net-_m3-pad2_ net-_m5-pad3_ net-_m5-pad3_ mosfet_n
m6  net-_m5-pad3_ net-_m1-pad1_ gnd gnd mosfet_n
m11  net-_m10-pad3_ net-_m11-pad2_ net-_m11-pad3_ net-_m11-pad3_ mosfet_n
m12  net-_m11-pad3_ net-_m1-pad2_ gnd gnd mosfet_n
v1  net-_m14-pad1_ gnd 3.3v
* Control Statements

.ends xor_gate

```

- After making the necessary changes to the subcircuit file to add Sky130 models here is how the Spice code looks like :

```

* Subcircuit xor_gate

.subckt xor_gate net-_m1-pad2_ net-_m3-pad2_ net-_m13-pad1_ 

* c:\fossee\esim\library\subcircuitlibrary\xor_gate\xor_gate.cir

xm5  net-_m10-pad3_ net-_m3-pad2_ net-_m5-pad3_ net-_m5-pad3_ sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm8  net-_m10-pad1_ net-_m11-pad2_ net-_m10-pad3_ net-_m10-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm7  net-_m14-pad1_ net-_m3-pad2_ net-_m10-pad1_ net-_m14-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm10  net-_m10-pad1_ net-_m1-pad2_ net-_m10-pad3_ net-_m10-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm6  net-_m5-pad3_ net-_m1-pad1_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm11  net-_m10-pad3_ net-_m11-pad2_ net-_m11-pad3_ net-_m11-pad3_ sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm12  net-_m11-pad3_ net-_m1-pad2_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm3  net-_m11-pad2_ net-_m3-pad2_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm4  net-_m14-pad1_ net-_m3-pad2_ net-_m11-pad2_ net-_m14-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm1  net-_m1-pad1_ net-_m1-pad2_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm2  net-_m14-pad1_ net-_m1-pad2_ net-_m1-pad1_ net-_m14-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm13  net-_m13-pad1_ net-_m10-pad3_ gnd gnd sky130_fd_pr__nfet_01v8 w=1 l=0.5 m=1
xm14  net-_m14-pad1_ net-_m10-pad3_ net-_m13-pad1_ net-_m14-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
xm9  net-_m14-pad1_ net-_m1-pad1_ net-_m10-pad1_ net-_m14-pad1_ sky130_fd_pr__pfet_01v8 w=1 l=0.5 m=1
v1  net-_m14-pad1_ gnd 3.3v

* Control Statements

.ends xor_gate
```

- Save the above ngspice subcircuit spice file in a folder where the Sky130 folder is present.


### Step3 Construct Half Adder

![ha](https://user-images.githubusercontent.com/83152452/152642606-594963bd-71c2-4f8c-b205-6cc2ff07e0d9.jpg)


- Construct the "Half Adder" as shown in the figure below using eSim :

![halfadder-1](https://user-images.githubusercontent.com/83152452/152638772-ab49afa0-3c13-44b4-90a7-b26170c7a240.png)

![halfadder-2](https://user-images.githubusercontent.com/83152452/152638776-3a6ee1d2-0cf7-4239-ae57-316f9a040ebd.png)


- Follow the similar steps as shown for AND Gate and implement Half Adder using the subcircuits of And Gate, XOR Gate and then generate the subcircuit & Netlist for the same.

- Once every step is followed perfectly open the Netlist that is generated and make the necessary changes to add the Sky130 models.
- The Netlist generated initially is as shown below :

```

* C:\FOSSEE\eSim\library\SubcircuitLibrary\halfadder\halfadder.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/2/2022 11:29:00 PM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
x1  Net-_U1-Pad1_ Net-_U1-Pad2_ Net-_U1-Pad3_ xor_gate		
x2  Net-_U1-Pad1_ Net-_U1-Pad2_ Net-_U1-Pad4_ and_gate		
U1  Net-_U1-Pad1_ Net-_U1-Pad2_ Net-_U1-Pad3_ Net-_U1-Pad4_ PORT		

.end

```

- The Netlist generated after the subcircuit creation is as shown below :

```
* Subcircuit halfadder
.subckt halfadder net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ net-_u1-pad4_ 
* c:\fossee\esim\library\subcircuitlibrary\halfadder\halfadder.cir
.include xor_gate.sub
.include and_gate.sub
x1 net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ xor_gate
x2 net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad4_ and_gate
* Control Statements

.ends halfadder

```

- After making the necessary changes to the subcircuit file to add Sky130 models here is how the Spice code looks like :

```

* Subcircuit halfadder

.subckt halfadder net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ net-_u1-pad4_ 

* c:\fossee\esim\library\subcircuitlibrary\halfadder\halfadder.cir

.include xor_gate.sub
.include and_gate.sub
x2 net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad4_ and_gate
x1 net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ xor_gate

* Control Statements

.ends halfadder

```

- Save the above ngspice subcircuit spice file in a folder where the Sky130 folder is present.


### Step4 Construct Full Adder

![fa](https://user-images.githubusercontent.com/83152452/152642609-2ca4fb85-6d0a-4a9f-a455-2332c1929110.jpg)


- Construct the "Full Adder" as shown in the figure below using eSim :

![fulladder-1](https://user-images.githubusercontent.com/83152452/152640363-f16c7d9b-7b6d-405f-a733-f74a5af56050.png)

![fulladder-2](https://user-images.githubusercontent.com/83152452/152640364-b527fd68-5b37-41e7-8be9-aa8a4e7c7e40.png)


- Follow the similar steps as shown for AND Gate and implement Half Adder using the subcircuits of Half Adder, XOR Gate and then generate subcircuit & Netlist for the same.

- Once every step is followed perfectly open the Netlist that is generated and make the necessary changes to add the Sky130 models.
- The Netlist generated initially is as shown below :

```

* C:\Users\priya\eSim-Workspace\fulladder\fulladder.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/3/2022 12:16:16 AM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
x1  Net-_U1-Pad2_ Net-_U1-Pad3_ Net-_x1-Pad3_ Net-_x1-Pad4_ halfadder		
x2  Net-_U1-Pad1_ Net-_x1-Pad3_ Net-_U1-Pad4_ Net-_x2-Pad4_ halfadder		
x3  Net-_x2-Pad4_ Net-_x1-Pad4_ Net-_U1-Pad5_ xor_gate		
U1  Net-_U1-Pad1_ Net-_U1-Pad2_ Net-_U1-Pad3_ Net-_U1-Pad4_ Net-_U1-Pad5_ PORT		

.end

```

- The Netlist generated after the subcircuit creation is as shown below :

```
* Subcircuit fulladder
.subckt fulladder net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ net-_u1-pad4_ net-_u1-pad5_ 
* c:\users\priya\esim-workspace\fulladder\fulladder.cir
.include xor_gate.sub
.include halfadder.sub
x1 net-_u1-pad2_ net-_u1-pad3_ net-_x1-pad3_ net-_x1-pad4_ halfadder
x2 net-_u1-pad1_ net-_x1-pad3_ net-_u1-pad4_ net-_x2-pad4_ halfadder
x3 net-_x2-pad4_ net-_x1-pad4_ net-_u1-pad5_ xor_gate
* Control Statements

.ends fulladder

```

- After making the necessary changes to the subcircuit file to add Sky130 models here is how the Spice code looks like :

```

* Subcircuit fulladder

.subckt fulladder net-_u1-pad1_ net-_u1-pad2_ net-_u1-pad3_ net-_u1-pad4_ net-_u1-pad5_ 

* c:\users\priya\esim-workspace\fulladder\fulladder.cir

.include xor_gate.sub
.include halfadder.sub
x3 net-_x2-pad4_ net-_x1-pad4_ net-_u1-pad5_ xor_gate
x1 net-_u1-pad2_ net-_u1-pad3_ net-_x1-pad3_ net-_x1-pad4_ halfadder
x2 net-_u1-pad1_ net-_x1-pad3_ net-_u1-pad4_ net-_x2-pad4_ halfadder

* Control Statements

.ends fulladder

```

- Save the above ngspice subcircuit spice file in a folder where the Sky130 folder is present.


### Step5 Construct 3-Bit Wallace Multiplier

- Expected structure of a Wallace Multiplier :

![3bitwallace](https://user-images.githubusercontent.com/83152452/152640871-8db7ca4d-8bc3-4f7f-b7be-75217a8c2e30.png)

- Construct the "Wallace Multiplier" as shown in the figure below using eSim :

![wallacetree3-1](https://user-images.githubusercontent.com/83152452/152638799-8bdfe1ea-af0c-4ce4-bf94-bedbf8a5051c.png)

![wallacetree3-2](https://user-images.githubusercontent.com/83152452/152638803-8b09f1a9-db59-4b57-bfd2-68eb4ff275e1.png)

- Generate a Schematic and construct the Wallace Multiplier for a 3-bit date using the subcircuits of AND Gate, Half Adder and Full Adder & generate the Netlist for the same.

- Once every step is followed perfectly, open the Netlist that is generated and make the necessary changes to add the Sky130 models.
- The Netlist generated initially is as shown below :

```

* C:\Users\priya\eSim-Workspace\wallace3tree\wallace3tree.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/3/2022 9:49:49 AM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N
* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /
x2  /b0 /a0 /z0 and_gate		
x1  /b0 /a1 Net-_x1-Pad3_ and_gate		
x3  /b0 /a2 Net-_x3-Pad3_ and_gate		
x5  /b1 /a0 Net-_x5-Pad3_ and_gate		
x6  /b1 /a1 Net-_x6-Pad3_ and_gate		
x4  /b1 /a2 Net-_x4-Pad3_ and_gate		
x7  Net-_x5-Pad3_ Net-_x1-Pad3_ /z1 Net-_x7-Pad4_ halfadder		
x9  Net-_x8-Pad5_ Net-_x4-Pad3_ Net-_x14-Pad2_ Net-_x15-Pad2_ halfadder		
x10  /b2 /a0 Net-_x10-Pad3_ and_gate		
x11  /b2 /a1 Net-_x11-Pad3_ and_gate		
x12  /b2 /a2 Net-_x12-Pad3_ and_gate		
x13  Net-_x10-Pad3_ Net-_x13-Pad2_ /z2 Net-_x13-Pad4_ halfadder		
U1  /a1 /a2 /a0 /b0 /b1 /b2 /z0 /z1 /z2 /z3 /z4 /z5 PORT		
x8  Net-_x6-Pad3_ Net-_x3-Pad3_ Net-_x7-Pad4_ Net-_x13-Pad2_ Net-_x8-Pad5_ fulladder		
x15  Net-_x12-Pad3_ Net-_x15-Pad2_ Net-_x14-Pad5_ /z4 /z5 fulladder		
x14  Net-_x11-Pad3_ Net-_x14-Pad2_ Net-_x13-Pad4_ /z3 Net-_x14-Pad5_ fulladder		

.end

```

- After making necessary changes to the Netlist file to add Sky130 models here is how the Spice code looks like :

```

* C:\Users\priya\eSim-Workspace\wallace3tree\wallace3tree.cir

.lib "C:/Users/priya/Desktop/prelayout/sky130_fd_pr/models/sky130.lib.spice" tt

.include fulladder.sub
.include and_gate.sub
.include halfadder.sub
x2 b0 a0 z0 and_gate
x1 b0 a1 net-_x1-pad3_ and_gate
x5 b1 a0 net-_x5-pad3_ and_gate
x6 b1 a1 net-_x6-pad3_ and_gate
x7 net-_x5-pad3_ net-_x1-pad3_ z1 net-_x7-pad4_ halfadder
* u1  a1 a0 a2 b0 b1 b2 z0 z1 z2 z3 z4 z5 port
x3 b0 a2 net-_x3-pad3_ and_gate
x4 b1 a2 net-_x4-pad3_ and_gate
x8 net-_x6-pad3_ net-_x3-pad3_ net-_x7-pad4_ net-_x13-pad2_ net-_x8-pad5_ fulladder
x10 b2 a0 net-_x10-pad3_ and_gate
x11 b2 a1 net-_x11-pad3_ and_gate
x12 b2 a2 net-_x12-pad3_ and_gate
x13 net-_x10-pad3_ net-_x13-pad2_ z2 net-_x13-pad4_ halfadder
x14 net-_x11-pad3_ net-_x14-pad2_ net-_x13-pad4_ z3 net-_x14-pad5_ fulladder
x9 net-_x8-pad5_ net-_x4-pad3_ net-_x14-pad2_ net-_x15-pad2_ halfadder
x15 net-_x12-pad3_ net-_x15-pad2_ net-_x14-pad5_ z4 z5 fulladder

v1 a0 0 pulse 0 1.8 0 0 0 5m 10m
v2 a1 0 pulse 0 1.8 10m 0 0 5m 15m
v3 a2 0 pulse 0 1.8 0 0 0 5m 10m

v4 b0 0 pulse 0 1.8 5m 0 0 5m 10m
v5 b1 0 pulse 0 1.8 0 0 0 15m 30m
v6 b2 0 pulse 0 1.8 10m 0 0 5m 15m

.tran 0.1m 20m

* Control Statements 
.control
run
plot a0
plot a1
plot a2
plot b0
plot b1
plot b2

plot z0
plot z1
plot z2
plot z3
plot z4
plot z5

print allv > plot_data_v.txt
print alli > plot_data_i.txt
.endc
.end

```

- Save the above spice file in a folder where the Sky130 folder is present.


## Results

#### Command Window 

- Type the command as shown in the figure below :
Syntax for the command : [Go to the Location of the ngspice folder] followed by typing "ngspice" (Location where the wallace3multiplier.cir file is present)

![command pic](https://user-images.githubusercontent.com/83152452/152640668-6e868ef9-e342-4158-b18c-fa0518fe76a2.png)

#### Obtained Output Waveforms

1. a0, a1, a2 and b0, b1, b2 waveforms obtained are :

![waveforms-a-b](https://user-images.githubusercontent.com/83152452/152640673-a1bd6525-d1b3-4177-9cca-a9a148bd266a.png)

2. z0, z1, z2, z3, z4, z5 waveforms obtained are :

![waveforms-z0-z5](https://user-images.githubusercontent.com/83152452/152640672-6df5f70b-1604-4028-bbb0-0e46a542dad0.png)

## References

- [eSim](https://esim.fossee.in/home)
- [YouTube](https://www.youtube.com/watch?v=Da3kzKzzuLs)


## Author

- [Aakash K], Bachelor of Engineering in Electronics and Communication Engineering, Bangalore

    
