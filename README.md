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

##### RUNNING IN NGSPICE  

![5](https://user-images.githubusercontent.com/64180927/137888350-925fa14d-625a-4bcc-abf3-705eb71ce1db.png) 

#### RESULT \ 


![6](https://user-images.githubusercontent.com/64180927/137888425-70893178-20ca-42de-8cd2-535c71bceaed.png)

####  PHASE DETECTOR AND CHARGE PUMP OUTPUT  WITHOUT LPF  


![9](https://user-images.githubusercontent.com/64180927/137888762-45ec1f6f-13c6-43e3-a70b-182d2bc1fa8e.png) 

#### PHASE DETECTOR AND CHARGE PUMP OUTPUT WITH LPF 


![10](https://user-images.githubusercontent.com/64180927/137888957-26cdbf28-075b-4f62-a788-e98e33c07083.png)

#### VCO WITH INPUT VOLTAGE OF 0.5V  
#### NETLIST 

![13](https://user-images.githubusercontent.com/64180927/137889159-e2fe3f9a-0d7d-4456-8263-d0ba521930f7.png)

#### SIMULATION USING NGSPICE 
![11](https://user-images.githubusercontent.com/64180927/137889450-7fab236d-923d-4686-b80f-aaf953e3a71c.png)

#### RESULT 
![12](https://user-images.githubusercontent.com/64180927/137889545-17652d3f-b289-4afe-bab9-d57cad00634e.png)


#### VCO WITH INPUT VOLTAGE OF 0.6V  
#### NETLIST 

![15](https://user-images.githubusercontent.com/64180927/137889639-e23de1b8-25ce-4503-89e6-ed3e78dbb168.png)

#### RESULT 

![14](https://user-images.githubusercontent.com/64180927/137889722-86a4a1f7-6714-4013-ba63-0212494fad28.png) 

#### PLL SIMULATION 


![16](https://user-images.githubusercontent.com/64180927/137890029-5e5584c3-9409-4887-89f5-ecd1d53bed24.png)

#### RESULTS 

![17](https://user-images.githubusercontent.com/64180927/137890096-cf0ba1d7-d761-40a4-8e05-d031560a5204.png)

![18](https://user-images.githubusercontent.com/64180927/137890116-d43b0fdd-af94-43e9-91f6-153592311440.png)

From the above simualtion grah we can observe that the  ouptput frequency is 8 times the input frequency. So a frequency multiplication of 8 is achieved 
## POST-LAYOUT SIMULATIONS  
### BASIC STEPS

![21](https://user-images.githubusercontent.com/64180927/137895963-fe17935a-2bcd-4a9c-8f00-20a260b31bc7.png)

#### Opening MAGIC TOOL with the intended technology library

![19](https://user-images.githubusercontent.com/64180927/137894528-cd532396-23f3-4b9b-bbba-9c3e437debdb.png)

![20](https://user-images.githubusercontent.com/64180927/137894571-6a60cbee-0b1b-484f-9cc1-a6b2b61d24c0.png)

#### Opening layout of phase detector  
![22](https://user-images.githubusercontent.com/64180927/137900202-30a5873c-268d-49d8-9d22-da0d333a0555.png)

#### Phase detector layout 
![23](https://user-images.githubusercontent.com/64180927/137897705-37e33c06-d032-4c0e-b96d-7b2d79f9e073.png)

 ####  POST-LAYOUT SIMULATION 
![24](https://user-images.githubusercontent.com/64180927/137901090-a5fbe30d-3f47-40a9-a545-8f34ad3d84b8.png)

#### 2X1MUX LAYOUT 
![41](https://user-images.githubusercontent.com/64180927/137926333-88988a5d-0d96-4ee0-8175-bd9e7a99c985.png)

 ####  POST-LAYOUT SIMULATION OF MUX 
 ![42](https://user-images.githubusercontent.com/64180927/137926653-36d94c27-5c67-4e41-b5bf-601cdf9fbe01.png) 
 
 #### SIMULATION RESULTS 
 ![43](https://user-images.githubusercontent.com/64180927/137927183-bec2e637-d678-4887-af3e-70c4d974ffa5.png)

 #### VCO LAYOUT 

![25](https://user-images.githubusercontent.com/64180927/137908588-fa76e2bb-ec9f-4601-84cf-3945213427c1.png)

#### POST LAYOUT SIMULATION OF VCO FOR VIN = 0.545V 

![28](https://user-images.githubusercontent.com/64180927/137910807-c3993f48-45fd-4869-a527-014171048581.png)
![29](https://user-images.githubusercontent.com/64180927/137910828-a0519a06-d82d-4bf0-b175-6b8b5c1ec0ae.png)


#### POST LAYOUT SIMULATION OF VCO FOR VIN = 0.5V
![26](https://user-images.githubusercontent.com/64180927/137910889-77fbc32f-8b87-43cb-8a63-c3d1d7dc973a.png)
![27](https://user-images.githubusercontent.com/64180927/137910919-8d70482b-5246-47c7-90cd-bc2ba7603f9d.png)

#### FREQUENCY DIVIDER BY 2 LAYOUT 

![31](https://user-images.githubusercontent.com/64180927/137913335-9dd7d7ab-57f1-4f2d-901d-40d3f60760bd.png)
![30](https://user-images.githubusercontent.com/64180927/137913356-e4662538-fbce-48b2-b9cd-8a05e3bd2144.png)
 
 #### POST LAYOUT SIMULATIONS 
 
 ![33](https://user-images.githubusercontent.com/64180927/137914380-7ff72a22-4eb0-446e-b4da-cff98dd70646.png)

![32](https://user-images.githubusercontent.com/64180927/137914404-81168bb8-a26f-46a3-9cec-a3f34c8514f8.png)

#### FREQUENCY DIVIDER BY  8 
![34](https://user-images.githubusercontent.com/64180927/137915578-5c4b9378-4b9f-4a13-8f37-23dc5bdc38a8.png)

 #### POST LAYOUT SIMULATION OF FREQUENCY DIVIDER BY 8 
 
 ![35](https://user-images.githubusercontent.com/64180927/137916407-e5f986db-34b8-4cf2-8a09-db6aa22f5539.png)

#### PLL FINAL LAYOUT  

![36](https://user-images.githubusercontent.com/64180927/137920097-e85bc8be-e2bc-4515-beb6-50352e315f0d.png)

#### PLL POST LAYOUT SIMULATION  

![37](https://user-images.githubusercontent.com/64180927/137922256-bfc6c9a8-4a86-4a05-b103-ffc617361a15.png)
 
####  POST LAYOUT SIMULATION RESULTS
 

![39](https://user-images.githubusercontent.com/64180927/137922709-dea9e992-b7e5-424a-9ca4-f92aab05e264.png)
![40](https://user-images.githubusercontent.com/64180927/137925369-e04d7bfd-b18a-4cea-86d7-2f608a5b78af.png) 

## CONCLUSION 
I have learnt the flow of designing a PLL and how to design a system from lower block to higher blocks.

