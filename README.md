# Parallel-8-Tap-FIR-Filter-VHDL
2 INPUT/OUTPUT Parallel 8 Tap FIR Filter written in VHDL , compiled, simulated and synthesized using Xilinx Vivado.

One 8 tap FIR filter mathematical expression:
![mathematics](https://user-images.githubusercontent.com/56197365/118289924-85797100-b4de-11eb-9389-8c332af9b622.JPG)
and two *4 tap* (for simplicity) parallel FIR filters:
![parallel mathematics](https://user-images.githubusercontent.com/56197365/118290145-c4a7c200-b4de-11eb-835b-3c583ccf3f43.JPG)

### Implementation and Design Concerns
1. We wanted the design to be pipelined (1 cycle latency) and the critical path to be as small as possible (Great Clock frequency)
2. As few filp flops as possible used.
3. When valid_in=0, current state of the system must remain stable: Idea: "gated clock" --> chip enable.

Implementation was done following a "structural" methodology and using behavioral VHDL. More specifically the modules constructed were:

1. Input Module 2.Multiplier Module and 3. Adder Module. The idea is shown in the image below (for 4 Tap filter but the same logic is applied for 8 tap).
![3modules](https://user-images.githubusercontent.com/56197365/118286353-09315e80-b4db-11eb-94b7-b0286fbedd7a.jpg)

### Construction of one 1 I/O FIR filter.
By compining the above modules, one is able to implement one 1 I/O FIR filter. In order to add pipeline to the filter, extra flip flops must be added as shown in the "lines" and "dots" in the schematics below.
![CamScanner 05-14-2021 16 42 - Page 3](https://user-images.githubusercontent.com/56197365/118289524-1c91f900-b4de-11eb-94eb-9e6ca7018d56.jpg)

![CamScanner 05-14-2021 16 42 - Page 5](https://user-images.githubusercontent.com/56197365/118289528-1dc32600-b4de-11eb-804b-40c55e429d4c.jpg)


### Compining 2 FIR Filters
We can construct the 2-Parallel pipelined FIR Filter by compining 2 identical FIR module above. Only difference is , we have to give the correct inputs, so the only module that needs to be changed in the (now common for both Filters) input module. 

Input module:

![parallelINPUT](https://user-images.githubusercontent.com/56197365/118294002-f15dd880-b4e2-11eb-9149-f584b193ec44.jpg)

![IO paralell](https://user-images.githubusercontent.com/56197365/118294014-f3279c00-b4e2-11eb-9a2f-7097a8c9904d.jpg)






## Below it is presented in the following order:
1. RTL produced by Vivado
2. Behavioral Simulation
3. Utilisation
4. Critical Path 




![RTL](https://user-images.githubusercontent.com/56197365/118295099-261e5f80-b4e4-11eb-861c-6789224ae5f7.jpg)

![simulation](https://user-images.githubusercontent.com/56197365/118295101-26b6f600-b4e4-11eb-95bd-af5cf0e6aee4.png)

![util](https://user-images.githubusercontent.com/56197365/118295095-24ed3280-b4e4-11eb-83f2-6047947a76ff.jpg)

![critical path](https://user-images.githubusercontent.com/56197365/118295097-2585c900-b4e4-11eb-90ba-f2d85842bf86.jpg)




> Note that pipeline produces correct results after 10 Clock Cycles and initial reg values are 0.Also, utilisation and critical path are result of synthesis and not implementation
> 


# Board and Software
- Board Used: Zybo (xc7z010clg400-1) , Zynq-7000 product family.
- Xilinx Vivado 2018.2.1



# VHDL Code
Available only upon request.


# Author:
Dimitrios Lampros
