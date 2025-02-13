# System-Verilog_Udemy

![image](https://github.com/user-attachments/assets/e5cb240e-9ca9-412c-9a5a-3a6e24fa5641)

Section 2: Fundamentals: Procedural Constructs

Agenda

Global signal - reset, clock
Control signal - It controls the operation of our design. Eg: read enable in the memory
Data signal - Eg: databus in memory
These three signals will present in every design.

![image](https://github.com/user-attachments/assets/c4f693cc-a24b-4c5d-9de5-ba36ef812822)

Type of signals in TB

For these categories of signals, we need to use the random stimulus or data to verify this.

![image](https://github.com/user-attachments/assets/10b8cfdd-74fe-45ab-a596-7e3d237f87f7)

Format of Initial Block in Testbench

reg - it is the verilog datatype which is used here and later we will use the SV datatypes.
The initial block starts execution at the start of simulation, which means they starts execution at '0ns'. Here, since we used the reg datatype, it will hold the data, even after the span of the initial block gets over. ie) a=0 will be stored till the end of simulation.

![image](https://github.com/user-attachments/assets/94a0d71d-9e92-47ec-b163-48adf2010dba)

Usage of Initial Block

Usually the signal that we initialize in the testbench top is a global signal. The uses of initial block is shown below. But we will not be using it for generating random values for data and control signals because we will use other verification techniques to do this. It is done here to show its usage.

![image](https://github.com/user-attachments/assets/8e958536-fa5f-497c-98eb-ade7090fc778)

![image](https://github.com/user-attachments/assets/8a67a876-909c-46ed-b15d-dab7ef38d832)


