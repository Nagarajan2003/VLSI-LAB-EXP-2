# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado Software

APPARATUS REQUIRED : Vivado™ ML 2023.2

PROCEDURE :

Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)



VERILOG CODE

 #1 DECODER_3TO8:-

Code:
```
module decoder_struct(  
  input [2:0] a,    
  output [7:0] d    
   );
wire x,y,z;
not g1(z,a[0]);
not g2(y,a[1]);
not g3(x,a[2]);
and g4(d[0],x,y,z);
and g5(d[1],x,y,a[0]);
and g6(d[2],x,a[1],z);
and g7(d[3],x,a[1],a[0]);
and g8(d[4],a[2],y,z);
and g9(d[5],a[2],y,a[0]);
and g10(d[6],a[2],a[1],z);
and g11(d[7],a[2],a[1],a[0]);
endmodule
```
OUTPUT:

 Simulation:
 ![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/3fc6dd17-f3c9-48ef-b0ab-97114fcbe077)
Elaborated Design:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/d80ec41e-50bf-422e-9701-9eecebb1bf26)

#2 DEMULTIPLEXER_1TO8:-

Code:
```
module demux_1_8(y,s,a);
output reg [7:0]y;
input [2:0]s;
input a;

always @(*)
begin 
y=0;
case(s)
3'd0: y[0]=a;
3'd1: y[1]=a;
3'd2: y[2]=a;
3'd3: y[3]=a;
3'd4: y[4]=a;
3'd5: y[5]=a;
3'd6: y[6]=a;
3'd7: y[7]=a;
endcase
end
endmodule
```
OUTPUT:-

Simulation:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/f3b0c5b1-cf8b-4f10-a6ae-8e9aee9bb69e)

Elaborated Design:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/8954b058-fde6-4cca-8baa-c98269179bb6)

#3 ENCODER_8to3:-

Code:
```
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);
input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
OUTPUT:-

Simulation:
![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/50e87c80-62c8-4969-9dba-fc8d414034fb)

Elaborated Design:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/c4e5d779-ede7-41bf-a8b1-24b7772dfa41)

#4 MAGNITUDE_COMPARATOR:-

Code:

```

module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT:-

Simulation:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/a5c3ca25-367e-4213-b726-31689dbc348e)

Elaborated Design:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/54be1f89-55b5-43ac-9294-9190fbc162ab)


#5 MULTIPLEXER_8TO1:-

Code:

```
module mux_8tol (in, sel, out);
    input [7:0] in;
    input [2:0] sel;
    output reg out;
    always @(*)
       begin
          case (sel)
              3'b000: out = in [0];
              3'b001: out = in [1];
              3'b010: out = in [2];
              3'b011: out = in [3];
              3'b100: out = in [4];
              3'b101: out = in [5];
              3'b110: out = in [6];
              3'b111: out = in [7];
              default: out = 1'bx;
          endcase
       end
endmodule
```
OUTPUT:-

Simulation:

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/0ad17c17-efd8-4eaa-85df-9307792368ea)

Elaborated Design: 

![image](https://github.com/Nagarajan2003/VLSI-LAB-EXP-2/assets/164840481/d23e8c25-1e3a-4b8e-9ccc-6bc374320058)

RESULT:The Simulation and Synthesis Logic Gates,Adders and Subtractor is successfully verified using Vivado Software .


