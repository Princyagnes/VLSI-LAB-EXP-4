# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using vivado.

# APPARATUS REQUIRED:

vivado 2023.1

# PROCEDURE:

STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.


# LOGIC DIAGRAM:

# SR FLIPFLOP:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


# JK FLIPFLOP:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# T FLIPFLOP:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


# D FLIPFLOP:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


# COUNTER:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


# VERILOG CODE:

# SR FLIPFLOP:

module srff(clk,rst,s,r,q);

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case ({s,r})

2'b00:q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule


# JK FLIPFLOP:

module jkff(clk,rst,j,k,q);

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case ({j,k})

2'b00:q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule


# T FLIPFLOP:

module tff(clk,rst,t,q);

input t,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

if(t==0)

q=q;

else

q=~q;

end

endmodule


# D FLIPFLOP:

module dff(clk,rst,d,q);

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule


# UPDOWN COUNTER:

module updown(clk,rst,updown,out);

input clk,rst,updown;

output reg [3:0]out;

always@(posedge clk)

begin

if(rst==1)

out=4'b0000;

else if(updown==1)

out=out+1;

else

out=out-1;

end

endmodule


# MOD 10 COUNTER:

module mod10(clk,rst,count);

input clk,rst;

output reg [3:0]count;

always@(posedge clk)

begin

if(rst==1 | count==4'b1001)

count<=4'b0000;

else

count<=count+1;

end

endmodule


# RIPPLE COUNTER:

module ripplecounter(clk,rst,q);

input clk,rst;

output [3:0]q;

tff tff1(q[0],clk,rst);

tff tff2(q[1],q[0],rst);

tff tff3(q[2],q[1],rst);

tff tff4(q[3],q[2],rst);

endmodule

module tff(q,clk,rst);

input clk,rst;

output q;

wire d;

dff df1(q,d,clk,rst);

not n1(d,q);

endmodule

module dff(q,d,clk,rst);

input d,clk,rst;

output q;

reg q;

always@(posedge clk or posedge rst)

begin

if(rst)

   q=1'b0;

else

   q=d;

end

endmodule


# OUTPUT WAVEFORM:

# SR FLIPFLOP:

![srff](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/f4956bc9-2a50-4e55-9ace-bb519cf1c230)


# JK FLIPFLOP:

![jkff](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/1bbb9b33-711c-4d4e-b583-db18df921e5a)


# T FLIPFLOP:

![tff](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/45df4bb0-6599-4b44-8bb2-de1a3d33e6fd)


# D FLIPFLOP:

![dff](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/d0756b05-f682-4856-aa63-45fab4ecee07)


# UPDOWN COUNTER:

![updown](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/c08779c0-1853-4973-9ef2-6572364477d8)



# MOD 10 COUNTER:

![mod 10](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/8c994767-0fca-43e6-9962-46218e3e24d7)


# RIPPLE COUNTER:

![ripple carry](https://github.com/Princyagnes/VLSI-LAB-EXP-4/assets/115100663/fe5aff7d-f9d3-473e-a131-1f578c025dd5)


# RESULT:

Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.

