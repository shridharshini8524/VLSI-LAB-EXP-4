 # VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS


AIM: 


 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.



APPARATUS REQUIRED:



Xilinx 14.7
Spartan6 FPGA



**LOGIC DIAGRAM**



SR FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


JK FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)



T FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)




D FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)




COUNTER



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  
PROCEDURE:


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



VERILOG CODE:


DEVELOPED BY:S.SHRIDHARSHINI.


REGISTER NUMBER:212222060240.


SR FLIPFLOP:
~~~
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
~~~
JK FLIPFLOP:
~~~
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
~~~
T FLIPFLOP:
~~~
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
~~~
D FLIPFLOP:
~~~
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
~~~
UP DOWN COUNTER:
~~~
module updown(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
~~~
MOD 10 COUNTER:
~~~
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
~~~
RIPPLE COUNTER:
~~~
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
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
~~~


OUTPUT WAVEFORM:

SR FLIPFLOP:


![WhatsApp Image 2024-04-14 at 21 33 51_da485061](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/b59ca965-f3d4-485c-b542-ba1ca7e6bc26)


JK FLIPFLOP:


![WhatsApp Image 2024-04-14 at 21 36 33_34459828](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/ddf635e3-d22f-49ce-9870-20c6a530e18d)



T FLIPFLOP:


![WhatsApp Image 2024-04-14 at 21 38 04_7cf60d55](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/22d57407-a01a-470e-8458-689b8a0db24f)



D FLIPFLOP:



![image](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/6f09bff8-8902-42c7-9698-53c3ef28b946)



UP DOWN COUTER:


![WhatsApp Image 2024-04-14 at 21 41 41_b08dd8c8](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/6a27cbfe-46d1-4347-b9d2-12deaa5803e0)



MODULE 10 COUNTER:


![WhatsApp Image 2024-04-14 at 21 44 56_3c89508a](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/70fb740d-b88e-4404-92ce-f46750a4372e)



RIPPLE COUNTER:


![image](https://github.com/shridharshini8524/VLSI-LAB-EXP-4/assets/148639799/454eaf5c-d439-44f8-8bae-72c82ee3eaee)


RESULT:


Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGNS are simulated and synthesised using Xilinx ISE.


