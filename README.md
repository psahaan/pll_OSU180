# On Chip Clock Multiplier (PLL) on OSU 180 

## THEORY
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

## Design-specifications 
This is the starting point of the design , this we usually get from client (here VSD pvt-ltd) 

## Architectural Design 
Based on the specifications required we do literature survey and come to an architecture. Here the architecture is selected as shown below

![Screenshot 2021-10-19 115403](https://user-images.githubusercontent.com/64180927/137855012-270feb3f-0daa-43f7-8957-79c0f0c76d04.png) 

 **Phase-detector** : Based on the feedback from the frequency divider it creates two signals ,up and down which are given to the charge-pump\
 **Charge pump**  : Charge-pump consists of power MOSFETS it helps in better charging of the capacitors present in the next stage which is a LPF\
 **LPF** : LPF is used for smoothning the waveform and get a dc value \
 **MUX** : Here MUX is used to select between VCO only mode or PLL \
 **VCO** : VCO is used to get the output frequency based on the input DC value \
 **Frequency divider** :Here a basic D-Filp-flop based counter is used to get frequency division 
 
 ### Operation of feedback-loop 
![control](https://user-images.githubusercontent.com/64180927/137863054-f5a5a0da-3443-4501-ba7a-92bc1f077879.png) \
As shown above we consider a second-order feed back systesm , the response can be as shown below based on location of  poles  

![control2](https://user-images.githubusercontent.com/64180927/137864295-6423c779-f8c2-40cd-afb0-53fd176795c8.png) 

For PLL we should obtain a critically damped response as it has less oscillations and its fast. 

## LABS 
## PRE-LAYOUT SIMULATIONS 

## INVERTER 

##### NETLIST FROM ESIM 
![1](https://user-images.githubusercontent.com/64180927/137866353-9127cbfe-92c7-4187-9a1b-9120bb284923.png) \ 

##### NETLIST FOR  NGSPICE 
![2](https://user-images.githubusercontent.com/64180927/137866440-22af5903-be15-4664-bf41-a0b553cc3799.png) \ 

##### RUNNING NGSPICE IN TERMINAL \
 
![3](https://user-images.githubusercontent.com/64180927/137866492-fb61304f-7787-433a-80cd-6b08fa057461.png) \

#### RESULT  

![4](https://user-images.githubusercontent.com/64180927/137866556-5c38e214-d259-44c4-a194-7eaad652361a.png) \ 

## PHASE DETECTOR 






