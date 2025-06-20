# TCL
## <center>TCL Workshop</center> 
In this workshop using Yosys and OpenTimer tools with TCL (for initial interface shell used) based programming.
Analyzed Timing reports in the dashboard after Synthesis and Timing checks on given design.


### Introduction
TCL (Tool Command Language) is a high-level, interpreted scripting language known for its simplicity and flexibility. It is widely used for rapid application development, automation, GUI creation (often with Tk), and embedding into C-based programs. Tcl is platform-independent and supports dynamic typing, making it easy to prototype and extend. It is especially popular in domains like electronic design automation (EDA) for scripting tasks in tools like Synopsys and Cadence. With a straightforward syntax and powerful string handling, Tcl enables quick development of control scripts and testing frameworks, making it a valuable tool for developers and engineers in various technical fields.

## Module 1: Creating global unix file using shell scripting and to call TCL file

- Starting Info: If no argv is there, it shoud provide info to use
![image](https://github.com/user-attachments/assets/28e41fd5-e951-4c5f-9886-aa2d0f61d99c)

- Providing nonexisting csv file and expecting error message
![image](https://github.com/user-attachments/assets/bb92fd91-ef76-48ab-b1f4-144ee38273cf)

- -help info message
![image](https://github.com/user-attachments/assets/f34134b8-1604-40b0-8e33-755a3b406dff)

- Checking for existence of collaterals
![image](https://github.com/user-attachments/assets/6bc408eb-405f-4920-a32b-5dcf75287db5)

- Printing Collaterals and Variable values info
![image](https://github.com/user-attachments/assets/af1695ae-ccca-49d3-8950-1b71c2ebd507)

- Collaterals and paths existence check
![image](https://github.com/user-attachments/assets/b95a7139-a65e-42d1-9c0b-dccbea766af6)

- Analysing input constraints CSV/.xls file.
  - This will help to understand where clocks, inputs, outputs sections are starting and their starting location (Getting Row & Column info properly)
![image](https://github.com/user-attachments/assets/b3a93d1a-65f4-42d8-88ce-613b97b6829c)


## Module 2: ********* SDC Formatting started ***********

 ### Clocks Section
 #### Main theme: Creation of SDC cons for all clocks in the design
- Strategy used for grepping clock info, uniquifying ports, duty cycle forming and printing info:
![image](https://github.com/user-attachments/assets/bf4edd3c-b5d8-489d-88a3-707885f936ab)


- Clocks SDC formatting info:
![image](https://github.com/user-attachments/assets/d9a39a37-1f01-4422-8638-25debd75672a)


### Input ports section 
#### Main theme: Segregation of bussed and non-bussed ports of the design, uniquifying ports and broadcasting respective input port values in SDC cons 

- Input ports formatting code: 
![image](https://github.com/user-attachments/assets/80911ca5-2201-4766-a772-1871b87f61ff)
![image](https://github.com/user-attachments/assets/e099e646-4d89-4978-8856-2224faafa06f)

![Screenshot 2025-06-04 113250](https://github.com/user-attachments/assets/2f1cf994-33d5-47a3-a6cf-8541c1c7d079)

- **Issue faced** - 
![image](https://github.com/user-attachments/assets/6e7802e1-655e-4a49-aea7-c0677226f78a)


- Opened sdc file again for writing in input and output sdc formating code, so faced above error.
![image](https://github.com/user-attachments/assets/45e08922-1e91-4bc8-9107-6d138282df23)

- **After fixing the code** : (Input ports)
![image](https://github.com/user-attachments/assets/eae17753-0719-4c44-92e5-fe7cc4fde992)


### Output ports section 
#### Main theme: Segregation of bussed and non-bussed ports of the design, uniquifying ports and broadcasting respective Output port values in SDC cons

- Output ports bussed and non-bussed identification as like input ports 
![image](https://github.com/user-attachments/assets/393d68fe-bfc0-426a-99f0-ff688e435e86)
![image](https://github.com/user-attachments/assets/05d6f1bd-03fd-4e3d-8b88-32e7385b4b65)
![image](https://github.com/user-attachments/assets/7c478e11-74b7-4c47-91d9-b869a1f15ad5)


- Output ports sdc formatting:
![image](https://github.com/user-attachments/assets/70a0d7b8-e343-43eb-b75c-e72edb65ef1d)

###             ********* SDC Formatting Completed ***********


## Module 3: ********* Design Hierarchy check using Yosys Tool ***********

- Yosys Tool Hierarchy Identification code:
![image](https://github.com/user-attachments/assets/240db06f-83f1-4963-8773-3c45ec651373)

- Yosys Hierarchy check status:
![image](https://github.com/user-attachments/assets/daeac574-9347-4489-97d3-5accb7488dea)


### ********* Design Hierarchy check using Yosys Tool completed ***********

## Module 4: ********* YOSYS: Main Synthesis starts **********

- Yosys Synthesis commands for given verilog code 
![image](https://github.com/user-attachments/assets/e173b772-8bbf-4555-adb8-6b824bc054fe)


- Hacking code for Output NETLIST manipulation for Opentimer tool compatability:
![image](https://github.com/user-attachments/assets/713623c5-1429-483f-b4e8-b47048c71c31)


- Synthesis Running:
![image](https://github.com/user-attachments/assets/fcf0cb93-c8d8-44ea-92f3-c4c1ff1d8c69)

### Synthesis completed successfully
![image](https://github.com/user-attachments/assets/8ffca41c-f284-451b-97c6-6607f59832f8)


###  ********* YOSYS: Main Synthesis Completed **********

## Module 5: ********* OpenTimer: Timing starts **********

- Calling multiple procs for usage:
![image](https://github.com/user-attachments/assets/83a26ef8-bcb3-488a-af20-aec98e4f92e9)


- Faced output ports open timing format issue creation, so updated proc to pick proper values 
  - **Reason for this failure:** I have dumped sdc in different order so based on that I created proc to pic proper values)
![image](https://github.com/user-attachments/assets/def90145-02e4-43c0-8efe-91af380a0b71)


- After proc update, sdc to .timing is proper
![image](https://github.com/user-attachments/assets/9eda5f2f-c206-4746-80c6-d4bd2aacdc23)


- Creation of .conf file for Timnig run and sourcing it
![image](https://github.com/user-attachments/assets/e69d9355-f8ce-43ce-b842-7ef3a53ad93b)


- Timing analysis started and results info:
![image](https://github.com/user-attachments/assets/0eca00d9-8767-4347-9b0d-967f4caf54c9)

![image](https://github.com/user-attachments/assets/b5f06b1c-2116-40f7-8458-d09ef9ae42ea)

### ********* Timnig analysis completed *********

## Module 6: ********* QOR Dash board creation *********

- Grepping different info like WNS, Wost_slack (hold, setup), instance count from Open-Timer STA reports
![image](https://github.com/user-attachments/assets/dc52e172-8644-4846-8238-62d16f96011f)

- Code for Dashboard creation:
![image](https://github.com/user-attachments/assets/0a145faf-c885-4db5-9fba-9c1cd83667a9)

### ********* QOR Dash board creation completed *********



## Result: QOR Prelayout Timing Summary 
![image](https://github.com/user-attachments/assets/3cc98f1f-4f3d-4066-b667-41a34a830e44)



