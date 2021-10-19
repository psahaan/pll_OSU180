# On Chip Clock Multiplier (PLL) on OSU 180 


 ![Screenshot 2021-10-19 110609](https://user-images.githubusercontent.com/64180927/137849917-61ecb4f1-148b-48bd-a001-a5b2c4fae571.png)
 
 ## About the Workshop 
This course will be an in-depth introduction to On-Chip Clock Multiplier (PLL) design and layout using open-source EDA tools (ngspice & Magic) on OSU180nm. This course starts with fundamentals (from CMOS inverter & basic semiconductor physics) to Advanced IP design Process, issues & ways to deal with them (by live demo of entire IP from Design to Layout).

##   Instructors 
###  Mr.Kunal Ghosh and Mr.Paras Gidd 


## INTRODUCTION 
###  What I have Learnt in the Workshop  

1) What , Why and How a PLL is used to achieve frequency multiplication ?
2) How to obtain a netlist from circuit and do a pre-layout simulation?
3) How to perfrom layout and extract parasitic information and obtain postlayout netlist and again perform simulation? 
4) The most important know how i learned through this workshop is learning how to obtain a larger block (here PLL) by connecting the smaller blocks (here Phase-   detector,chargepump,low-pass filter,VCO,frequency-divider) 

### 1)Design-specifications 
This is the starting point of the design , this we usually get from client (here VSD pvt-ltd) 

### 2)Architectural Design 
Based on the specifications required we do literature survey and come to an architecture. Here the architecture is selected as shown below

![Screenshot 2021-10-19 115403](https://user-images.githubusercontent.com/64180927/137855012-270feb3f-0daa-43f7-8957-79c0f0c76d04.png)
