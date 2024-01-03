# Name: DHANWANTH A
# Register number: 23006796
## Experiment:06 Synchornous counters up counter
## AIM: To implement 3 bit up and down counters and validate  functionality.
## HARDWARE REQUIRED:  
PC, Cyclone II , USB flasher
## SOFTWARE REQUIRED:  
Quartus prime
## THEORY 
## UP COUNTER 
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this 3-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 

## 3-bit Up Counter:

![Screenshot 2024-01-03 162218](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/f3369722-0468-4c3b-8275-0c1bdca57e8f)

## 3-bit Down counter:
![Screenshot 2024-01-03 161930](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/52da4525-3c91-4aee-b706-4dd767e229fe)

### Procedure
1. Create a New Project:
   - Open Quartus and create a new project by selecting "File" > "New Project Wizard."
   - Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).

2. Create a New Design File:
   - Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
   - Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.

3. Write the Combinational Logic Code:
   - Open the newly created Verilog or VHDL file and write the code for your combinational logic.
     
4. Compile the Project:
   - To compile the project, click on "Processing" > "Start Compilation" in the menu.
   - Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.

5. Analyze and Fix Errors: 
   - If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
   - Review and fix any issues in your code if necessary.
   - View the RTL diagram.

6. Verification:
   - Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
   - Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.
   - Give the Input Combinations according to the Truth Table amd then simulate the Output Waveform.

Program for flipflops  and verify its truth table in quartus using Verilog programming.

### PROGRAM:
## UP COUNTER
~~~
module upCounters(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
	A[2]=(((A[0])&(A[1]))^A[2]);
	A[1]=(A[0])^A[1];
	A[0]=A[0]^1;
end
endmodule
~~~
## DOWN COUNTER:
~~~
module downCounters(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
	A[2]=(((~A[0])&(~A[1]))^A[2]);
	A[1]=(~A[0])^A[1];
	A[0]=1^A[0];
end 
endmodule
~~~
### RTL LOGIC UP COUNTER 

![Screenshot 2024-01-03 161055](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/c5802cda-eb0d-4c0a-90af-efc3d3058c71)

## RTL LOGIC DOWN COUNTER:
![Screenshot 2024-01-03 161106](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/ba1f05f9-5b60-4392-b377-0d60bb7360c6)


### TIMING DIGRAMS:

## UP COUNTER:

![Screenshot 2024-01-03 161556](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/c3a999a7-d27b-4dc5-9ea1-84e7beee45b5)

## DOWN COUNTER:
![Screenshot 2024-01-03 161607](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/fc34c2e5-0280-43c2-a27e-49e078adc89b)


### TRUTH TABLE:

## UP COUNTER:

![Screenshot 2024-01-03 161414](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/4890b4a6-ea50-4baa-a370-98df778119e7)

## DOWN COUNTER:

![Screenshot 2024-01-03 161429](https://github.com/dhanwanth07/Exp-7-Synchornous-counters-/assets/152170135/6e9a2726-67d6-44fa-b874-7683cc7523a9)

### RESULTS 
By this we have verified the truth table of 4-bit up-counter using verilog.
