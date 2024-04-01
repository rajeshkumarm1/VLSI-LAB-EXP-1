AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

![301405876-ee17970c-3ac9-4603-881b-88e2825f41a4](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/567b87e6-13f3-4abf-898d-f7943aa3e6fc)
Half Adder:
![301406331-0e1ecb96-0c25-4556-832b-aeeedfdfe7b9](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/9bd27cf5-9efa-4135-9de5-dd29001ba477)

Full adder:
![301406527-9bb3964c-438f-469d-a3de-c1cca6f323fb](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/a64ed39b-0751-499e-a857-f5d075813bd3)
Half Subtractor:

![301406051-731470b7-eb4e-49f8-8bb7-2994052a7184](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/d5881631-510c-4cbd-adc0-38cb82ab038b)
Full Subtractor:
![301406088-d66f874b-c1f2-44b3-a035-7149b56430c1](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/c90a7708-2024-4711-8473-e4862d01e20e)

8 Bit Ripple Carry Adder
![301406117-7385a408-40a5-4203-8050-b72818622d79](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/8e7571dd-189d-4044-986e-a3250f4700b4)

VERILOG CODE:
# Full Adder:
```
module fulladder (sum, cout, a,b,c);
input a,b,c;
output sum, cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and al(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,w2,w3); or o2(cout,w5,w4);
endmodule
```
# Full Subractor:
```
module full_subtractor(a, b, c,D, Bout);
input a, b, c;
output D, Bout;
assign D = a^b^c;
assign Bout = (a & b) | ((a^ b) & c);
endmodule
Half Adder:
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
or(sum,a,b);
and(carry,a,b);
endmodule
```
# Half Subractor:
```
module half_subtractor(D,Bo,A,B);
input A,B;
output D,Bo;

assign D=A^B;
assign Bo=(~A)&B;
endmodule
```
# Logic Gates:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Ripple Carry Adder 4Bit:
```
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
```
OUTPUT:
full adder
![WhatsApp Image 2024-04-01 at 14 06 40_bf0bcce7](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/0a976f22-c773-48cd-b3ce-d53aa590312f)
Full Subractor
![WhatsApp Image 2024-04-01 at 14 29 23_d373d46f](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/f0ba4be8-64ca-4487-817e-676dec3fbc2a)
Half Adder
![WhatsApp Image 2024-04-01 at 14 06 39_9e93a24f](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/1336ec39-cbc6-4f0a-9f5c-5e2b2ba0ff56)
Half Subractor
![WhatsApp Image 2024-04-01 at 14 06 39_a3ae1259](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/3a73f477-3033-4ab5-8785-b4e1bd592b3a)
Logic Gates
![WhatsApp Image 2024-04-01 at 14 06 39_bacd2040](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/2e9deaae-f82e-4757-a687-0e065b079034)
Ripple Carry Adder
![WhatsApp Image 2024-04-01 at 14 06 41_72720412](https://github.com/rajeshkumarm1/VLSI-LAB-EXP-1/assets/160701441/a130fc86-e925-448d-942a-9557171a4362)

result:
Thus the simulation and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.
