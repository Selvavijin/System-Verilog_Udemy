![image](https://github.com/user-attachments/assets/ce1946a4-df1b-41fe-900e-3b37b1c4175f)# System-Verilog_Udemy

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

Here we are calculating the phase, ton and toff and developing the code.

![image](https://github.com/user-attachments/assets/7bbec5d3-f391-4ad9-a189-06e35dda2571)

![image](https://github.com/user-attachments/assets/dda1048b-24de-420e-b881-fea0637534d3)

Now, a small modification will make this run from the posedge of the clock.

![image](https://github.com/user-attachments/assets/afdd3b7d-f3c8-43e4-934e-4b584e25c5d1)

Section 3: Understanding SV Datatypes

Agenda

2 state means, only 0 and 1. 4 states means 0,1,x and z.

![image](https://github.com/user-attachments/assets/fbb2b065-85b5-451a-b18b-8ed1a563b3ad)

Datatypes P1

We divide the datatypes into 3 for our convenience. First is hardware datatypes(wire and reg). Then when we need to add some variables into the code, we use some datatypes. And the next is the datatypes for simulation. When we use wire datatype in the procedural block, it will throw an error similarly, if we use the reg data type in assign datatype, it will throw an error in verilog. To overcome this, we use a datatype 'logic' in SV, which automatically switches to reg or wire.

![image](https://github.com/user-attachments/assets/0ff37822-3024-4419-8dd5-1b157e857fe3)

Datatypes P2

real is 64 bit capable. Floating point has only 'real' data type. If the datatype is capable of working with 4-states(1,0,x,z), we call it 4-state. In 4-state also we have only one datatype 'integer' which is 32 bit. Also, generally the 2-state unsigned datatype is 32 bit.

![image](https://github.com/user-attachments/assets/192b22f1-4196-47f2-af3b-914f9e7f8a6f)

![image](https://github.com/user-attachments/assets/f78e27eb-b656-494e-945d-c3e159125104)

Datatypes P3

Let us assume that there is a connection between the variable type and hardware type, finally the variable will be mapped to wire or reg type.

![image](https://github.com/user-attachments/assets/79750619-eafb-4d59-b14f-6ee3043b1394)

![image](https://github.com/user-attachments/assets/8c9d5afc-f9a1-4a29-bea4-5e2a3ea5edf8)

Datatypes P4

In simulation datatypes, for fixed point, we use 'time'(64-bit) and for floating point, we use 'realtime'. Here everything we discussed is multibits. To use single bit, we use 'bit'. Here all the datatypes are summarized.

![image](https://github.com/user-attachments/assets/4b726bbc-76c3-46ae-a9e5-5b141fe80c3e)

Demonstration of Datatypes P1

Providing the initial value is not mandatory. But providing an initial value is a good option. Default value of 2 state variable is '0' and the default value of 4 state variable is 'x'.

![image](https://github.com/user-attachments/assets/2b2cec16-bf17-4aa9-a6d9-c26d5803ad4e)

Demonstration of Datatypes P2

If we give the values out of range, we will get unexpected results.

![image](https://github.com/user-attachments/assets/a5e3ac4d-77fd-469c-b21a-330de37fe318)

![image](https://github.com/user-attachments/assets/f46f4904-674b-4cf8-96cb-e9ae802a35cc)

Demonstration of Datatypes P3

Here we are trying to display the realtime which is a floating point in 'time' datatype. So, we don't get the expected result.

![image](https://github.com/user-attachments/assets/6e5577e5-5c65-40a0-82d6-fc738f20c611)

Here the realtime is printed in picoseconds.

![image](https://github.com/user-attachments/assets/1d09dd41-02a7-483e-aa3a-104ba2e9eb0e)

Demonstration of Datatypes P4

![image](https://github.com/user-attachments/assets/f275d123-1a34-40a6-b4e0-a81d808a518b)

Demonstration of Datatypes P6

![image](https://github.com/user-attachments/assets/99ca6b11-963f-4c71-bc48-c76cad1407e4)

The datatype 'logic' can be used instead on wire or reg. Eg: Let us say that in one place we are using the 'reg' and we are getting error. Because, we are supposed to use 'wire' there. But, instead of using 'wire', even if we are using 'logic', it is correct in system verilog.  
This 'logic' type is particularly useful in interfaces.

Using array P1

In fixed size array, we need to initialize the size of the array or we need to specify the initial values of the array(From that the size will be fixed).

![image](https://github.com/user-attachments/assets/3b415e3d-6fe6-4240-8122-86aa76145197)

Using array P2

![image](https://github.com/user-attachments/assets/8bba9876-8059-4b5d-a69f-8b1a60ad2f64)

Array Initialization Strategies

Note: The default value of 2 state variable is '0' and the default value of 4 state variable is 'x'.

![image](https://github.com/user-attachments/assets/0a87b8e6-41c5-4861-9353-ef4499a8eb99)

Demonstration

![image](https://github.com/user-attachments/assets/8312377c-3bce-47b8-9c68-9285fd7aa8e9)

![image](https://github.com/user-attachments/assets/c196e023-3152-4e0e-b169-a2124c5d7b3c)

Loops for repetitive array operation P1

![image](https://github.com/user-attachments/assets/c431f4ca-d7ca-4358-b13f-b7975cf6bad6)

Loops for repetitive array operation P2

![image](https://github.com/user-attachments/assets/4c54a602-83e3-47cd-b7f2-4dcf2e1d1440)

Loops for repetitive array operation P3

![image](https://github.com/user-attachments/assets/340cc878-92a0-4c38-b0f2-effa5ec51a60)

Array Operation P1 : COPY

To perform array operation between two arrays, the two arrays should have the same size and also the arrays should have same data type.

![image](https://github.com/user-attachments/assets/2f8981f5-099f-4164-a59d-91699daa29c7)

Array Operation P1 : COMPARE

![image](https://github.com/user-attachments/assets/c4c53bfd-5aff-4e63-b678-d6e8b07b3ada)

Dynamic Array P1

When we add a constructor to the class, we use paranthesis. When we specify the size of the dynamic array, we use square bracket.

![image](https://github.com/user-attachments/assets/aea7ca96-f4ea-42d5-a720-63c335565f5c)

Dynamic Array P2

Initially we have the size of 5 using the new method(arr=new[5]). The we have the size of 30 using the new method. We we initialize the size as 30, the previous data that are present will be removed(arr=new[30]). But, if we want the previous data that are already present, we need to use "arr = new[30] (arr)", here the first five positions is for the previous data and the rest 25 positions is for the new data.

![image](https://github.com/user-attachments/assets/d354cee5-b2ec-4823-b1ba-38c56ce60953)

Dynamic Array P3

We can also convert the dynamic array to the fixed array by assigning. It is possible only if the dynamic array has the same size and same datatype as fixed array.

![image](https://github.com/user-attachments/assets/b645abb7-1582-495d-a904-c11cae030480)

Queue P1

In queue, the memory is efficiently utilized as compared to the dynamic array. In fixed or dynamic array, we need to mention an apostraphe(') before declaring the values. But in the case of queue, we don't need to use apostraphe(').

![image](https://github.com/user-attachments/assets/41ed8b9b-a500-4c49-8dd0-186bba70c0e7)

Queue P2

![image](https://github.com/user-attachments/assets/f5007b50-e612-436b-8d62-48b605ae10da)

Fundamentals of System Verilog OOP Construct

Agenda

![image](https://github.com/user-attachments/assets/d8161a3c-a03a-4e03-87c1-8a461d6338a0)

Fundamentals of Class P1

![image](https://github.com/user-attachments/assets/0c3db4e4-c951-4129-805a-dc76e034e2c6)

Fundamentals of Class P2

As soon as we add a constructor to the handler, memory is allocated to the class.


