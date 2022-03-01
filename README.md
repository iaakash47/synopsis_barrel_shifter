# 8x4 Barrel Shifter using NMOS Pass Transistor Logic
* This project focuses on design of a 8x4 right Barrel Shifter using NMOS pass transistor logic using synopsis custom complierin 28nm Technology node with operating voltage of 1.8V .The project is build using commercial Tools like Synopsis custom complier . Refer following website for more details on Barrel Shifter:https://en.wikipedia.org/wiki/Barrel_shifter
 
# Table of Contents

1. [Introduction](#introduction)
2. [Creation of project](#creation-of-project)
    * [custom Complier](#custom-Complier)
    * [custom complier Schematic Window](#custom-complier-Schematic-Window)
4. [Reference Circuit](#reference-circuit)
5. [Reference Waveform](#reference-waveform)
6. [Methodology](#methodology) 
7. [Schematic](#schematic)
8. [Circuit Schematic](#circuit-schematic)
9. [Netlist](#netlist)
10. [Initial Transitent Analysis](#initial-transitent-analysis)
11. [Waveforms](#waveforms)
12. [References](#references)
13. [Contributor](#contributor)
14. [Acknowledgments](#acknowledgments)


## Introduction 
#### Barrel Shifter 
* Barrel Shifter is a digital circuit that can shift a data word by a specified number of bits without the use of any sequential logic, only pure combinational logic, i.e. it inherently provides a binary operation important function to optimize the RISC processor, so it is used for rotating and transferring the data either in left or right direction. This shifter is useful in lots of signal processing ICs. The Arithmetic and the Logical Shifters additionally can be changed by the Barrel Shifter Because with the rotation of the data it also supply the utility the data right, left change all mathemetically or logically.A purpose of this project is to design CMOS using NMOS Pass Transistor logic.CMOS based 8 bit barrel shifter has implemented in this project using eSim and Ngspice tools using skywater 130nm PDKs Tech lib files 


 
 ## Creation of project 
 * Click on the New Project and save the file name without any space 
 * Project will be created 
 
 
 ## eSim Window 
 
 
 
 ## synopsis Schematic Window 
 
 

To Run the ckt using ngspice:
1. Replace with sky130nm cells and save this .cir file.
2. Paste the .cir file in gedit document where the sky130_fd_pr folder is present  
3. To Run the ngspice waveform,save the .cir file and replace with filename.spice  
4. Open Terminal in the saved Directory 
5. And run the following command(ngspice filename.spice)
- For reference to download the tools and get an exposure to simulation using eSim, ngspice and Sky130, you may want to check the course : [Link](https://www.udemy.com/share/104Ie63@EAkZWPY9P8VxMdqx7DK4NzA2SwmLzfA1pfjL_MLTmkTV9O283uXSWpJkSSNIPjmKmA==/)

# Reference Circuit 

CMOS transmission gates may be used in place of the simple pass transistor switches.In this project, a 8x4 right barrel shifter circuit using NMOS pass transistor logic is implemented in eSim with skywater 130nm technology. The shifter circuit takes 8 inputs bits and shifts them according to 5 control shift bits and generates 4 output bits
* Reference Circuit of Barrel Shifter is as shown below 
![IMG_20220208_081335](https://user-images.githubusercontent.com/88897605/152908383-16142e3f-ff9e-43f1-a74d-daa38e236ca8.jpg)

# Reference Waveform
* Reference Waveform of Barrel Shifter is as shown below
![IMG_20220208_080218](https://user-images.githubusercontent.com/88897605/152909514-24875fbc-b2d1-4c3b-b07e-6ff87d665af7.jpg)


## Methodology

# Prelayout Simulation in eSim and Ngspice
Refer following manual to know how to operate eSim:
https://static.fossee.in/esim/manuals/eSim_Manual_2020_August.pdf

## Schematic 
- Construct the "8 * 4 Barrel Shifter using NMOS" as shown in the figure below using eSim 
![Barrel_Shifter_Schematic](https://user-images.githubusercontent.com/88897605/152915643-128d7179-5bb5-40e9-8096-07b7ff87ee1b.png)

# Circuit Schematic
* 8 * 4 Barrel Shifter using NMOS
![IMG_20220208_093228](https://user-images.githubusercontent.com/88897605/152916106-d471380d-1381-4beb-9add-bffccb4442fd.jpg)

- Once every step is followed perfectly open the Netlist that is generated and make the necessary changes to add the Sky130 models
- The Netlist generated initially is as shown below and replace the components with skywater130nm cells

#### Editing the Netlist
```

a) To execute the .cir file, follow these steps:
Step 1: Open the .cir file (barrel_shifter.cir in my case) with notepad 
Step 2: Make sure the path .lib "sky130_fd_pr/models/sky130.lib.spice" tt at the top.
Step 3: Make sure that all mosfets are replace with sky130_fd_pr__nfet_01v8
Step 4: Delete any / added if any 
Step 5: Prefix x with all Transistors starting with M. Do this for all transistors 
e.g Before M1, after xM1
Step 6: Comment with * if any ports are added by defaults 
e.g *U1  /input_In0 PORT	
*U9  /Out_0 PORT	
Step 7: Next Start adding Inputs sources, supply voltage, etc (Vdd was considered as 1.8V)
Step 8: Add .tran statement with initial step time and final stop time 
eg. .tran 0.4ns 40ns 
Step8: Add .control command and run command to run the plot 
Step9: Add the voltage or current input or output quantities to be plotted 
eg. plot V(input_In0) 
plot V(Out_0) 
Step 10: Last step is to add .endc followed by .end command 

```
* Now Run the circuit with ngspice.

To Run the ckt using ngspice:
1. Replace with sky130nm cells and save this .cir file.
2. Paste the .cir file in gedit document where the sky130_fd_pr folder is present  
3. To Run the ngspice waveform,save the .cir file and replace with filename.spice  
4. Open Terminal in the saved Directory 
5. And run the following command(ngspice filename.spice)
- For reference to download the tools and get an exposure to simulation using eSim, ngspice and Sky130, you may want to check the course : [Link](https://www.udemy.com/share/104Ie63@EAkZWPY9P8VxMdqx7DK4NzA2SwmLzfA1pfjL_MLTmkTV9O283uXSWpJkSSNIPjmKmA==/)


# Netlist 
 
```
* /home/user/eSim-Workspace/Barrel_shifter/bareelshifter.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: Mon Jan 31 16:56:06 2022

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

* Sheet Name: /
xM16 Out_4 GND input_in3 GND sky130_fd_pr__nfet_01v8 
xM17 Out_4 GND input_in4 GND sky130_fd_pr__nfet_01v8 	
xM18 Out_4 GND input_in5 GND sky130_fd_pr__nfet_01v8 			
xM19 Out_4 GND input_in6 GND sky130_fd_pr__nfet_01v8 	  
xM20 Out_4 Vdd input_in7 GND sky130_fd_pr__nfet_01v8 	
xM11 Out_3 GND input_in2 GND sky130_fd_pr__nfet_01v8 		
xM12 Out_3 GND input_in3 GND sky130_fd_pr__nfet_01v8 		
xM13 Out_3 GND input_in4 GND sky130_fd_pr__nfet_01v8 		
xM14 Out_3 GND input_in5 GND sky130_fd_pr__nfet_01v8 	
xM15 Out_3 Vdd input_in6 GND sky130_fd_pr__nfet_01v8 		
xM6  Out_2 GND input_in1 GND sky130_fd_pr__nfet_01v8 		
xM7  Out_2 GND input_in2 GND sky130_fd_pr__nfet_01v8 
xM8  Out_2 GND input_in3 GND sky130_fd_pr__nfet_01v8 
xM9  Out_2 GND input_in4 GND sky130_fd_pr__nfet_01v8 
xM10 Out_2 Vdd input_in5 GND sky130_fd_pr__nfet_01v8		
xM1  Out_1 GND input_in0 GND sky130_fd_pr__nfet_01v8 	
xM2  Out_1 GND input_in1 GND sky130_fd_pr__nfet_01v8 			
xM3  Out_1 GND input_in2 GND sky130_fd_pr__nfet_01v8 		
xM4  Out_1 GND input_in3 GND sky130_fd_pr__nfet_01v8 	
xM5  Out_1 Vdd input_in4 GND sky130_fd_pr__nfet_01v8 			
*U1 input_in0 PORT
*U2 input_in1 PORT
*U3 input_in2 PORT
*U4 input_in3 PORT
*U5 Vdd PORT
*U6 input_in4 PORT
*U7 input_in5 PORT
*U8 input_in6 PORT
*U9 input_in7 PORT
*U10 Out_3 PORT
*U11 Out_2 PORT
*U12 Out_1 PORT
*U13 Out_4 PORT		

V1 input_in4 0 PULSE(0 1.8 1n 10p 10p 10n 20n)
V2 input_in5 0 PULSE(0 1.8 7n 10p 10p 10n 20n)
V3 input_in6 0 PULSE(0 1.8 3n 10p 10p 10n 20n)
V4 input_in7 0 PULSE(0 1.8 9n 10p 10p 10n 20n)
VDD Vdd 0 1.5V
V6 input_in0 0 PULSE(0 1.8 4n 10p 10p 10n 20n)
V7 input_in1 0 PULSE(0 1.8 8n 10p 10p 10n 20n)
V8 input_in2 0 PULSE(0 1.8 12n 10p 10p 10n 20n)
V9 input_in3 0 PULSE(0 1.8 16n 10p 10p 10n 20n)

.tran 0.4ns 40ns 

.control
run
plot V(input_in0)
plot V(input_in1) 
plot V(input_in2) 
plot V(input_in3) 
plot V(input_in4) 
plot V(input_in5) 
plot V(input_in6) 
plot V(input_in7)
plot V(Out_1)   
plot V(Out_2)
plot V(Out_3) 
plot V(Out_4)  


.endc
.end


```


* Save the above ngspice subcircuit spice file in a folder where the sky_fd_pr_ folder is present

![sky130_fd_pr](https://user-images.githubusercontent.com/88897605/152917186-7c4c159a-60f4-4542-9786-ccf0d56f2d8e.png)

* Run the spice file with following Terminal Command as shown 

![terminal_command](https://user-images.githubusercontent.com/88897605/152917510-dd98597e-ec33-44fb-94c1-68c6b5c2328d.png)

## Initial Transitent Analysis
![IMG_20220208_095310](https://user-images.githubusercontent.com/88897605/152917940-d0fe923f-dc7f-499b-a4c3-5805c97c00b5.jpg)


# Waveforms 
* Input Waveforms (8 Inputs)
* Output Waveforms (4 Outputs)

# Input Waveforms 
![IMG_20220208_100727](https://user-images.githubusercontent.com/88897605/152919187-7b0681c7-d53e-4f83-9dec-1adf9ca3a55a.jpg)

# Output Waveforms 
![outputwaveform](https://user-images.githubusercontent.com/88897605/152919496-e5d81c89-8ff1-479d-8d8a-c3d52409649d.png)

# References
- Realization of 8 x 4 barrel shifter with 4-bit binary to gray
- Design of Various 4 Bit Shifters using CMOS


# Contributor
Aakash.K</br>
Contact:iaakashkrish@gmail.com</br>

Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com

# Acknowledgments
Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com









