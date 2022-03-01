# 8x4 Barrel Shifter using NMOS Pass Transistor Logic in 28nm Technology node
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


 ## Synopsis Window 
 ![window](https://user-images.githubusercontent.com/88897605/156105077-980595cf-342d-4d9b-9757-0eadfab05f24.png)

 ## Creation of project 
 * Click on the New Project and save the file name without any space 
 * Project will be created
 
 
# Reference Circuit 

CMOS transmission gates may be used in place of the simple pass transistor switches.In this project, a 8x4 right barrel shifter circuit using NMOS pass transistor logic is implemented synopsis tool.The shifter circuit takes 8 inputs bits and shifts them according to 5 control shift bits and generates 4 output bits
* Reference Circuit of Barrel Shifter is as shown below 
![MI9RISf](https://user-images.githubusercontent.com/88897605/156105295-53c13902-46ae-44d4-b738-94893a2c2460.png)

# Reference Waveform
* Reference Waveform of Barrel Shifter is as shown below
![IMG_20220208_080218](https://user-images.githubusercontent.com/88897605/152909514-24875fbc-b2d1-4c3b-b07e-6ff87d665af7.jpg)


## Methodology

 ## synopsis Schematic Window 
 ![schematic window](https://user-images.githubusercontent.com/88897605/156105487-22871bf2-2215-4d02-9ac0-118ac516609b.png)


## Schematic 
- Construct the "8 * 4 Barrel Shifter using NMOS" as shown in the figure below using synopsis tool
![barrel_shifter_synopsis](https://user-images.githubusercontent.com/88897605/156105519-1ad51a0d-5444-4195-9ab2-288693f915d6.png)


# Circuit Schematic
* 8 * 4 Barrel Shifter using NMOS
![final_test_bench](https://user-images.githubusercontent.com/88897605/156105574-0433a515-2305-4752-ad0c-3ae4f182643b.png)

# Model files
![modelfiles](https://user-images.githubusercontent.com/88897605/156105681-95fc28ea-c87f-42a2-b6dc-9917a71b48d5.png)

# Analyses
![analyses](https://user-images.githubusercontent.com/88897605/156105734-c878f25e-101e-468c-b1dd-3480eecee226.png)


# Netlist  
![netlist](https://user-images.githubusercontent.com/88897605/156105781-9f06e66d-de01-474b-a4e2-97ac5c3ca8ad.png)


## Initial Transitent Analysis
![analyses](https://user-images.githubusercontent.com/88897605/156105836-3b8410c5-b328-4e85-8b10-273fe22d028d.png)

# Plot ecpressions
![plot_expression](https://user-images.githubusercontent.com/88897605/156106757-76410da2-82b3-4b3d-a262-abf85ba7df24.png)


# Waveforms 
![IMG_20220301_100930](https://user-images.githubusercontent.com/88897605/156105987-7d1cf0b9-170e-460d-845b-9b7d6378481a.jpg)


# References
- Realization of 8 x 4 barrel shifter with 4-bit binary to gray
- Design of Various 4 Bit Shifters using CMOS


# Contributor
Aakash.K</br>
Contact:iaakashkrish@gmail.com</br>

Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com

# Acknowledgments
Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com

Synopsys team









