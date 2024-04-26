# SIMULATION AND IMPLEMENTATION OF MULTIPLIER

# AIM:

 To simulate and synthesis multiplier using Xilinx ISE.

# APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
  
# PROCEDURE:

STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

![image](https://github.com/venkatesh2634/VLSI-LAB-EXP-3/assets/168212451/988fa9ab-2a84-4208-a37f-efbcac17473e)

# 4 Bit Multiplier

![image](https://github.com/venkatesh2634/VLSI-LAB-EXP-3/assets/168212451/e199c86e-300e-4836-8ddd-081ab5847d5c)

# Verilog code

# 2 bit multiplier:

module ha(a,b,sum,c);

input a,b;

output sum,c;

xor g1(sum,a,b);

and g2(c,a,b);

endmodule

module bitmultiplier(a,b,c);

input [1:0]a,b;

output[3:0]c;

wire w1;

and g1(c[0],b[0],a[0]);

ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);

ha ha2(a[1] &b[1],w1,c[2],c[3]);

endmodule

# 4 bit multipler:

module ha(a,b,c,s);

input a,b;

output s,c;

xor g1(s,a,b);

and g2(c,a,b);

endmodule

module fa(a,b,c,s,carry);

input a,b,c;

output s,carry;

wire w1,w2,w3;

xor g1(w1,a,b);

and g2(w2,a,b);

xor g3(s,w1,c);

and g4(w3,w1,c);

or g5(carry,w3,w2);

endmodule

module bitmultiplier(x,y,z);

input[3:0]x,y;

output[7:0]z;

wire [17:1]w;

and g1(z[0],x[0],y[0]);

ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);

fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);

fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);

ha ha2(x[3]&y[1],w[3],w[7],w[4]);

ha ha3(w[5],x[0]&y[2],z[2],w[8]);

fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);

fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);

fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);

ha ha4(w[12],x[0]&y[3],z[3],w[15]);

fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);

fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);

fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);

endmodule Output Waveform

# 2 bit multiplier:

![image](https://github.com/venkatesh2634/VLSI-LAB-EXP-3/assets/168212451/a8ce2bef-c294-497a-8042-7e3e44430e58)

# 4 bit multiplier:


![image](https://github.com/venkatesh2634/VLSI-LAB-EXP-3/assets/168212451/66bf19f7-c94f-46af-b5e4-0c8354c919e4)

# Result

Thus,the simulation and synthesis of multipliers by using vivado has been successfully excecuted and verified.












