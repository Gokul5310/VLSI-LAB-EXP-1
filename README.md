# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado 2023.2.

SOFTWARE REQUIRED: Vivado 2023.2

PROCEDURE: 1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

----Type Verilog Code
#VERILOG CODE:
```
Program
Logic Gates:
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
Full Adder:
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```

# 4 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
OUTPUT:

-----Place a Waveform Generated from Xilinx ISE
# OR gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/4b503d63-b2c0-4255-a581-b6b273081b5c)
# NOT gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/3f6a703e-3557-40d3-8934-f6fda5d413c4)
# AND gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/15897bb4-d7d3-48d8-ba32-0ca3b6fb188e)
# NAND gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/0753d13c-aeae-4f34-a0ad-c3f18b783204)
# NOR gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/f728e8e9-d8c5-4985-9270-cd5998745696)
# XNOR gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/439a0925-ff55-406a-acb6-3bcb28fe9b80)
# XOR gate:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/870121a2-8dc6-4f59-a1cc-ce04c2235b78)
# Half Adder:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/8de4e914-6118-4ccf-868e-88dd08a09d7d)
# Half Subtracter:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/d335eb66-f012-4d35-9a14-35157d8b3129)
# Full Adder:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/b41468a2-d700-40ee-8666-e1033a1ee614)
# Full Subtracter:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/35839a9b-53a8-43ed-8b3b-cc889a1c6ea6)
# 4 Bit Ripple Carry Adder:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/67b67b05-3429-4a0e-abda-e1c1305a4f82)
# 8 Bit Ripple Carry Adder:
![image](https://github.com/Sairam1034/VLSI-LAB-EXP-1/assets/161026996/6cf32583-d6ca-4bd2-890e-6948b0cd67a4)
RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Vivado 2023.2.

