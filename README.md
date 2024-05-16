EXP-3

date:

                                 SIMULATION AND IMPLEMENTATION OF MULTIPLIER
AIM: 
 To simulate and synthesis multiplier using STEP:1 Launch the Vivado 2023.2. 

APPARATUS REQUIRED:

VIVADO 2023.2
  
PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

Logic Diagram
2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

Verilog code
```
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
```

Output

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-3/assets/161432255/e08ffd69-3dc5-432b-960f-05d8def8b7d1)

Logic Diagram
2 bit Multiplier

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-3/assets/161432255/8381c0eb-8694-43d1-a56d-ce2c8b813adc)


Verilog code
```
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
endmodule
Output Waveform
```
OUTPUT


![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-3/assets/161432255/12637e2a-c11f-4143-a475-e45bb29443a6)

Result:
       Hence the 2 bit multiplier and 4 bit multiplier are simulated and synthesised using Vivado 2023.2.



