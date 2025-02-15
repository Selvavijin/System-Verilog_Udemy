# System-Verilog_Udemy

![image](https://github.com/user-attachments/assets/e5cb240e-9ca9-412c-9a5a-3a6e24fa5641)

Section 2: Fundamentals: Procedural Constructs

Agenda

Global signal - reset, clock.
Control signal - It controls the operation of our design. Eg: read enable in the memory.
Data signal - Eg: databus in memory.
These three signals will present in every design.

![image](https://github.com/user-attachments/assets/c4f693cc-a24b-4c5d-9de5-ba36ef812822)

Type of signals in TB

For these categories of signals, we need to use the random stimulus or data to verify this.

![image](https://github.com/user-attachments/assets/10b8cfdd-74fe-45ab-a596-7e3d237f87f7)

Format of Initial Block in Testbench

reg - it is the verilog datatype which is used here and later we will use the SV datatypes.
The initial block starts execution at the start of simulation, which means they starts execution at '0ns'. Here, since we used the reg datatype, it will hold the data even after the span of the initial block gets over. ie) a=0 will be stored till the end of simulation.

![image](https://github.com/user-attachments/assets/94a0d71d-9e92-47ec-b163-48adf2010dba)

Usage of Initial Block

Usually the signal that we initialize in the testbench top is a global signal. The uses of initial block is shown below. But we will not be using it for generating random values for data and control signals because we will use other verification techniques to do this. It is done here to show its usage.

![image](https://github.com/user-attachments/assets/8e958536-fa5f-497c-98eb-ade7090fc778)

![image](https://github.com/user-attachments/assets/8a67a876-909c-46ed-b15d-dab7ef38d832)

Executing Code

Here we can observe that the last value of temp is hold till the end of the simulation.

![image](https://github.com/user-attachments/assets/1234a55e-184c-41d2-8a46-9961dcf2f04c)

Also here we can observe the use of monitor.

![image](https://github.com/user-attachments/assets/236f5343-af13-42e7-a715-5562e7b557d8)

Format of always Block

There are three kinds of always block in the system verilog. They are always_comb(for combinational circuit), always_ff(for sequential circuit), always_latch(for implementing latch). When we are using always block in the testbench, we don't need to use the sensitivity list because our objective in testbench is to generate a stimulus. In case of combinational circuit, the system is sensitive to all the inputs. And in case of sequential circuits, the system is sensitive to clock.

![image](https://github.com/user-attachments/assets/88fb718c-9001-4e5f-8b26-89026889a710)

Usage of always Block

Now let us understand how to generate single clock signal. And later we will understand how to generate multiple clock signal. If the time of clock is 10ns, then the dut which we are testing will be tested on 100Mhz frequency. When we are using 'always' to generate clock, it will run forever since there is no sensitivity list. So to stop this we use '$finish' at the end of simulation. It is necessory to initialize the clock because we need a stable value to complement. Otherwise it will take the default value of 'x'.

![image](https://github.com/user-attachments/assets/af2a5f62-c040-4874-a2b9-489804c112ac)

Aligning edges of the generated clock and reference clock

Here, the first edge of all three clock signals are not aligned. Let us see how to align it.

![image](https://github.com/user-attachments/assets/deb37f8b-9812-4d92-b141-214d03ef1a57)

So, we leave the 100Mhz clock as it is and do alteration for the 50Mhz and 25Mhz clocks.

![image](https://github.com/user-attachments/assets/1e25497c-1d9c-4f2d-8be9-2f26c1fa3c21)

![image](https://github.com/user-attachments/assets/2f7c5ff0-7faa-41cf-a049-8238c7017d8e)

Understanding `timescale directive

When we want to generate clock in decimal, at that time, timescale will come into account.

![image](https://github.com/user-attachments/assets/ff815056-3558-460a-b7bc-5543d086c8e8)

When we divide TU/TP when it is 1ns/1ns, we get 1 which is 10^0. So, the precision digit we have is 0. So, now we can't use the floating point number. So, when we have number like 10.2, it will be rounded to 10, and when we have 10.7, it will be rounded to 11.

![image](https://github.com/user-attachments/assets/abcd9ead-7434-44b5-8c60-38454d32bffe)

![image](https://github.com/user-attachments/assets/c52badc0-5637-41c5-a8ad-a39269ca65ad)

Demonstration

Initially we are setting it to 1ns/1ns and see what happens. Here, the value will rounded off and the graph is plotted.

![image](https://github.com/user-attachments/assets/ffaf489b-b054-4c95-a1f7-1386390b7f43)

![image](https://github.com/user-attachments/assets/4999326b-3415-4b70-80bd-1cce86ff9a81)

Now we are changing the timescale to 1ns/1ps and now it is accurate. This is how the timescale plays a crutial role here.

![image](https://github.com/user-attachments/assets/7f500a24-8460-4394-9ffb-f5eace894315)

![image](https://github.com/user-attachments/assets/ba5ae856-842c-43b9-85ff-e500be467853)

Understanding parameters for generating Clock

Let us understand how to generate the reconfigurable clock. To generate a new signal, we should have inputs frequency, duty cycle and phase difference w.r.to the reference signal. We are designing in such a way that the duty cycle is not is percentage as input, instead it should be 1 for 100%, 0.5 for 50%.

![image](https://github.com/user-attachments/assets/6865147b-c825-4dd8-8831-e9c512558fe7)

![image](https://github.com/user-attachments/assets/58425a63-1103-4de6-8efc-e49b3d4c2fb6)

Demonstration Part 1

![image](https://github.com/user-attachments/assets/5d3179f3-914d-4f1d-86e8-47c17ffebea7)

This code is for the fixed clock. Now let us see how to write code for generating various clocks using 'task'.

![image](https://github.com/user-attachments/assets/a4a98c5d-eb56-4c6a-ad35-d4c0170dab81)

Demonstration Part 2

