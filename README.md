# Samsung-VSD
## VSLI-Internship   

<details>
<summary><b>Task 1: </b> Installing all essential tools and compiling a 'C' code using gcc compiler.</summary>
<br>
1. A program, which counts from 1 to 'n' numbers, was coded in C language and was run using gcc compiler.

The code is as follows:
```
#include <stdio.h>
int main() {
    int i, sum = 0, n = 60;
    for (i = 1; i <= n; ++i) {
        sum += i;
    }
    printf("Sum of number from 1 to %d is %d\n", n, sum);
    return 0;
}
```

  The output was run using ./a.out

  ![1](https://github.com/user-attachments/assets/b9d66816-3355-4c27-9482-b0289abb2130)


2. Compiling using RISC-V gcc compiler and seeing the assembly code with O1.
    ![3](https://github.com/user-attachments/assets/be00753b-81fb-45fa-8980-6e46c1e5f026)

   ![4](https://github.com/user-attachments/assets/bf320e7e-6df6-43b2-9f4d-65f1ea0617d5)

    
3. Compiling using RISC-V gcc compiler and seeing the assembly code with Ofast.

   
    ![5 1](https://github.com/user-attachments/assets/88b7dd3e-ed59-48b6-85aa-3c09ec178233)
    ![5 2](https://github.com/user-attachments/assets/367d3f80-8321-4c6a-9a56-a39da75d3e46)
</details>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------
<details>
<summary><b>Task 2: </b>SPIKE Simulation.</summary> 
<br>
The instruction set (Object Dump) is given below.

![Task2 instruction set](https://github.com/user-attachments/assets/7a475392-69c3-498b-b270-47286a60c10c)

1. The 'C' program code (Sum of 1 to n numbers) was run using riscv architecture using a spike simulator and output was obtained.

   ![Task2 1](https://github.com/user-attachments/assets/318835d9-7191-4084-ac8d-b16bca51c9a9)

2. The object dump of the riscv architecture was opened and debugging was done using spike.
3. The program counter (pc) was run till a certain instruction and it was manually run after that for debugging. 
   Each instruction was run by clicking enter each time.

   ![Task2 2](https://github.com/user-attachments/assets/4dd6ebdf-8f68-420e-ba3f-90c29c1d5b24)
   ![Task2 2 2](https://github.com/user-attachments/assets/883e2368-142c-4c9e-9c80-d22d2ffd627d)

4. The contents of the Stack Pointer(SP) register was observed. The stack pointer register(SP) instruction was run and the contents of the SP were looked at again.

   ![Tas2 4](https://github.com/user-attachments/assets/59892309-a0c1-4657-a0c5-6d68c2220fc0)
</details>

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<details>
<summary><b>Task 3: </b>Understanding and identifying different instruction types (R, I, S, B, U, J).</summary> 
<br>

## Instructions:
Instructions are a set of machine language instructions that a particular processor understands and executes. A processor performs tasks on the basis of the instruction provided.
An instruction comprises of groups called fields. These fields include:
* The Operation code (Opcode) field which specifies the operation to be performed.
* The Address field which contains the location of the operand, i.e., register or memory location.
* The Mode field which specifies how the operand will be located.

  
The RISC-V instructions are categorized into **6** types based on their field organization. The types include:
- **R-type**: Register type
- **I-type**: Immediate type
- **S-type**: Store type
- **B-type**: Branch type
- **U-type**: Upper immediate type
- **J-type**: Jump type

![Screenshot 2025-01-22 102538](https://github.com/user-attachments/assets/8d9d17af-f2ea-46bb-889e-a1131d48b99b)

Lets discuss one by one:

-------------------------------------------------------------------------------------------------------
## 1. R-Type Instruction:

![R type](https://github.com/user-attachments/assets/7aefa71e-76ba-43c5-9e8c-b5dbb54559b4)

R-type instructions are one of the six types of instructions in RISC-V's RV32I instruction set.
It is a register-register instruction that uses registers for both the source and destination.
R-type instructions are used for arithmetic and logic operations.
It specifies the two operands and the destination of the result using register file locations.
The R-type instruction has multiple fields, including: 
* The opcode field : Tells the processor what operation to perform.
* The destination register operand (rd): The register which stores the result of the operation.
* Source register operands (rs1, rs2): The registers where the input is stored.
* 'funct3' field: It is the field after the destination register . This field is 3 – bit length     i.e. from bit 12 to bit 14 and it further tells about the operation, such as whether it is an     addition, subtraction, or a logical operation that is being performed.
* 'funct7' field: It is the last field of R -type instruction format . It describes the              operation, such as whether it is a shift or multiplication operation etc.

------------------------------------------------------------------------
## 2. I-Type Instruction:

![I type](https://github.com/user-attachments/assets/13229840-4f30-4c08-95e7-5b9096e90193)

An I-type instruction in RISC-V is an instruction that uses a 12-bit constant as one of its operands. This constant is also known as an immediate. I-type instructions are also known as Immediate instructions. The 12-bit constant is a signed 2's complement number that is sign extended to form a 32-bit operand. I-type instructions perform the same operations as R-type instructions, but use an immediate value instead of an rs2 index. I-type instructions can be used for loads, stores, branches, or immediate ALU operations. The immediate field in an I-type instruction holds an immediate value that can be interpreted as an unsigned integer or two's complement. 
The I-type instruction also has multiple fields, including: 
* Immediate field (20 to 31): The immediate field is a part of an instruction that holds a constant value. The immediate field is used for arithmetic operations.
* The opcode field : Tells the processor what operation to perform.
* The destination register operand (rd): The register which stores the result of the operation.
* 'funct3' field: It is the field after the destination register . This field is 3 – bit length     i.e. from bit 12 to bit 14 and it further tells about the operation, such as whether it is an     addition, subtraction, or a logical operation that is being performed.
* Source register operand (rs1): The register where one of the input is stored.

-------------------------------------------------------------------------------------------
## 3. S-Type Instruction:

![s type](https://github.com/user-attachments/assets/e345a066-5997-485a-bfbb-2f036df1fa5d)

S-type instructions are used to store data from registers into memory. The S-type instruction format is used exclusively for memory store instructions. The immediate value in S-type instructions is split up into different bits.
The multiple fields in a S-Type instruction are:
* The opcode field : Tells the processor what operation to perform.
* Immediate fields (One from 7 to 11 and another from 25 to 31): The immediate field in an S-type instruction is used to store the contents of a register to data memory.
* 'funct3' field: It is the field after the destination register . This field is 3 – bit length     i.e. from bit 12 to bit 14 and it further tells about the operation, such as whether it is an     addition, subtraction, or a logical operation that is being performed.
* Source register operands (rs1, rs2): The registers where the input is stored.

---------------------------------------------------------------------
## 4. B-Type Instruction:

![B type](https://github.com/user-attachments/assets/02a0ca26-53f3-4747-9112-baf0a155da6d)

A B-type instruction in RISC-V is a branch instruction that controls the flow of a program. It compares two values in registers and branches to a new address. B-type instructions are a variation of S-type instructions.  B-type instructions are used for conditional branches, which test two registers and branch if the test passes. The target address for a B-type instruction is calculated by adding a branch offset to the current program counter (PC) value. The branch offset is stored as an immediate in the instruction. The fields in the B-Type instruction are:
* The opcode field : Tells the processor what operation to perform.
* The immediate field: The immediate field in a B-type instruction in RISC-V is a 12-bit field that stores a branch offset. The branch offset is used to calculate the target address for an instruction.
* 'funct3' field: It is the field after the immediate field. This field is 3 – bit length i.e. from bit 12 to bit 14 and it further tells about the operation, such as whether it is an addition, subtraction, or a logical operation that is being performed.
* Source register operands (rs1, rs2): The registers where the input is stored.

--------------------------------------------------------------------------
## 5. U-Type Instruction:

![u type](https://github.com/user-attachments/assets/3825ff30-62a1-4c58-92d3-1bcfe92e7375)

A U-type instruction in RISC-V is a type of instruction that specifies the upper 20 bits of a register's immediate value. It's also known as an "Upper immediate" instruction. The U-type instruction loads a 20-bit immediate value into the upper 20 bits of a register. The instruction only requires the destination register index (rd) and the 20-bit immediate number. The immediate number can be used directly as an operand. U-type instructions are used for special data manipulation instructions. They can be used to form addresses within a register. The fields in the U-Type instruction are:
* The opcode field (0 to 6): Tells the processor what operation to perform.
* The destination register operand (rd) (7 to 11): The register index which stores the result of the operation.
* The immediate field (12 to 31) : The immediate field in a U-type instruction in RISC-V is a 20-bit value that specifies the upper 20 bits of a register.

------------------------------------------------------------------------
## 6. J-Type Instruction:

![J- Type](https://github.com/user-attachments/assets/0b5b80b9-2c25-48db-93ff-3365f1b44d4e)

A J-type instruction in RISC-V is a jump instruction that unconditionally transfers control to a new instruction address. They use all of the non-opcode space for a 26-bit jump destination field. J-type instructions are part of the PC updating instructions, along with B-type instructions.
* The opcode field (0 to 6): Tells the processor what operation to perform.
* The destination register operand (rd) (7 to 11): The register index which stores the result of the operation.
* The immediate fields (12 to 31) : The immediate field in J type is is a 20-bit value that specifies the upper 20 bits of a register, similar to U type but it is slightly different.

--------------------------------------------------------------------------------

# Identifying Instruction types in Object Dump of application code.

> 15 unique instructions with 32-bit pattern are given below.


1. `lui a0,0x2b`
   * LUI (load upper immediate) is a U-type instruction.
   * LUI places the U-immediate value in the top 20 bits of the destination register rd, filling in the lowest 12 bits with zeros.
   * This instruction will be executed and the immediate value 0x2b will be written in the MSB of the rd a0.

   * The 32-bit pattern is: ```0000 0000 0000 0010 1011 0101 0011 0111```.

2. `addi sp,sp,-80`
   * addi (Add immediate) is a I-type instruction.
   * It is done on the stack pointer registor (sp).

   * The 32-bit pattern is: ```1111 1011 0000 0001 0000 0001 0001 0011```.

3. `SUB r7, r1, r2`
   * All the arithmetic and logical operations are performed using R-type instruction format, hence this instruction belongs to R-type instruction set.
   * r7 is the destination register that will hold the difference of values stored in the register r1 and r2.

   * The 32-bit pattern is: ```0100 0000 0010 0000 1000 0011 1011 0011```.

4. `lw a5,12(sp)`
   * LW stands for Load Word. Word is equal to 32 bits or 4 bytes. Since there is an immediate value given in the instruction which helps to calculate the address of memory from where we have to fetch the data, hence this instruction belongs to I-type.
   * a5 is the destination register that will hold the value fetched from the memory location.

   * The 32-bit pattern is: ```0000 0000 1100 0001 0010 0111 1000 0011```.

5. `SLT r11, r2, r4`
   * Since the logical operation is performed on registers, hence this instruction belongs to R-type instruction set.
   * r1 is the destination register that sets to 1, if r2 is less than r4, else 0 if r2 is greater than r4.

   * The 32-bit pattern is: ```0000 0000 0100 0001 0010 0101 1011 0011```.

6. `jal ra, 10408`
   * It is a J-Type instruction.
   * The jal instruction jumps to the target address 10408 and stores the return address in register ra.

   * The 32-bit pattern is: ```0011 0100 0000 0000 0000 0000 1110 1111```.

7. `ret `
   * This is a J-Type instruction as it contains an immediate , destination register and an opcode.
   * ret is also an pseudo instruction , which is a short for jalr x0 , ra , 0 . This means that when the ret instruction is executed, it effectively jumps to the address stored in the return address register (ra, which is register x1) and sets the program counter (PC) to that address.

   * The 32-bit pattern is: ```0000 0000 0000 0000 1000 0000 0110 0111 ```.

8. `mv  a1,a0`
   * This is an I - Type instruction.
   * The mv (move) instruction is a pseudo-instruction in RISC-V used to copy the value of one register to another.
   * mv is addi with an immediate value of 0.

   * The 32-bit pattern is: ```0000 0000 0000  0101 0000 0101 1001 0011  ```.
  
9. `auipc a5,0xffff0`
   * This is an U-Type instruction.
   * RISC-V includes an instruction to help with position-independent code: auipc (add upper immediate to PC). auipc works just like lui (load upper immediate) but adds a 20-bit immediate value to the program counter.

   * The 32-bit pattern is: ```1111 1111 1111 1111 0000 0111 1001 0111```.

10. `ld ra,8(sp)`
   
    * This is I-Type instruction.
    * ld is used to load a 64-bit value from memory into a specific register.
    * 'ra' is the register where the value at address sp is at with offset of 8.
    
    * The 32-bit pattern is: ```0000 0000 1000 0001 0011 0000 1000 0011```.

11. `addiw a5,a5,-1`
    * This is an I-type instruction.
    * 'addiw' indicates add immediate word,which adds a sign-extended 12-bit immediate to a 32-bit register.
    * a5 is both the source and destination register.
    
    * The 32-bit pattern is: ```1111 1111 1111 0111 1000 0111 1001 1011```.
  
12. `li a5,60`
    * This is an I-Type instruction.
    * li is a pseudo-instruction used to load a constant value directly into a register.
    * a5 is a destination register where the immediate value is loaded.
    
    * The 32-bit pattern is: ```0000 0011 1100 0000 0000 0111 1001 0011```.

13. `beq a0, a1, target`
    * This is an B-Type instruction.
    * The conditional branch instructions in RISC-V are beq (branch if equal), bne (branch if not equal), blt (branch if less than), and bge (branch if greater than or equal to).
    * These instructions are used to control the flow of execution in a program based on certain conditions.
    
    * The 32-bit pattern is: ```0111 1011 1111 1111 0000 0111 1001 0111```.

14. `slli a0, a0, 1`
    * This is an R-Type instruction.
    * SLLI is a logical left shift (zeros are shifted into the lower bits); SRLI is a logical right shift (zeros are shifted into the upper bits); and SRAI is an arithmetic right shift (the original sign bit is copied into the vacated upper bits).
    
    * The 32-bit pattern is: ```0000 0111 1101 1101 0010 0111 1001 0101```.
  
15. `SW r3, r1, 2`
    * This is an S-type instruction.
    * In this instruction SW means store word.
    * r3 is the source register. This instruction will store the value located in register r3 at the address obtained by adding the immediate address 2 with the address located in register r1.
    
    * The 32-bit pattern is: ```0000 0000 0011 0000 1010 0001 0010 0011```.

--------------------------------------------------------------------------------------------

</details>


<details>
<summary><b>Task 4: </b>Functional Simulation using GTKWave.</summary> 
<br>
    

### ABOUT IVERILOG AND GTKWAWE 

 ***Icarus Verilog*** (Iverilog) and ***GTKWave*** are widely used open-source tools for Verilog-based digital design and simulation. Iverilog functions as a Verilog simulator, enabling users to compile and execute simulations of their Verilog code, including modules and testbenches. It produces simulation output in formats such as VCD (Value Change Dump), which can be viewed using GTKWave. GTKWave is a waveform viewer that presents simulation results in a graphical format, allowing users to analyze signal transitions, zoom into specific events, and debug their designs effectively. Together, these tools create a comprehensive simulation and verification setup, with Iverilog handling simulation and GTKWave facilitating result interpretation.
***
A Verilog Netlist is Used for simulation.
***
## VERILOG NETLIST:
``` module iiitb_rv32i(clk,RN,NPC,WB_OUT);
input clk;
input RN;
//input EN;
integer k;
wire  EX_MEM_COND ;

reg 
BR_EN;

//I_FETCH STAGE
reg[31:0] 
IF_ID_IR,
IF_ID_NPC;                                

//I_DECODE STAGE
reg[31:0] 
ID_EX_A,
ID_EX_B,
ID_EX_RD,
ID_EX_IMMEDIATE,
ID_EX_IR,ID_EX_NPC;      

//EXECUTION STAGE
reg[31:0] 
EX_MEM_ALUOUT,
EX_MEM_B,EX_MEM_IR;                        

parameter 
ADD=3'd0,
SUB=3'd1,
AND=3'd2,
OR=3'd3,
XOR=3'd4,
SLT=3'd5,

ADDI=3'd0,
SUBI=3'd1,
ANDI=3'd2,
ORI=3'd3,
XORI=3'd4,

LW=3'd0,
SW=3'd1,

BEQ=3'd0,
BNE=3'd1,

SLL=3'd0,
SRL=3'd1;


parameter 
AR_TYPE=7'd0,
M_TYPE=7'd1,
BR_TYPE=7'd2,
SH_TYPE=7'd3;


//MEMORY STAGE
reg[31:0] 
MEM_WB_IR,
MEM_WB_ALUOUT,
MEM_WB_LDM;                      


output reg [31:0]WB_OUT,NPC;

//REG FILE
reg [31:0]REG[0:31];                                               
//64*32 IMEM
reg [31:0]MEM[0:31];                                             
//64*32 DMEM
reg [31:0]DM[0:31];   


//assign EX_MEM_COND = (EX_MEM_IR[6:0]==BR_TYPE) ? 1'b1 : 1'b0;
                     //1'b1 ? (ID_EX_A!=ID_EX_RD) : 1'b0;

always @(posedge clk or posedge RN) begin
    if(RN) begin
    NPC<= 32'd0;
    //EX_MEM_COND <=1'd0;
    BR_EN<= 1'd0; 
    REG[0] <= 32'h00000000;
    REG[1] <= 32'd1;
    REG[2] <= 32'd2;
    REG[3] <= 32'd3;
    REG[4] <= 32'd4;
    REG[5] <= 32'd5;
    REG[6] <= 32'd6;
    end
    //else if(EX_MEM_COND)
    //NPC <= EX_MEM_ALUOUT;

    //else if (EX_MEM_COND)begin
    //NPC = EX_MEM_COND ? EX_MEM_ALUOUT : NPC +32'd1;
    //NPC <= EX_MEM_ALUOUT;
    //EX_MEM_COND = BR_EN;
    //NPC = BR_EN ? EX_MEM_ALUOUT : NPC +32'd1;
    //BR_EN = 1'd0;
    //EX_MEM_COND <= 1'd0;
    //end
    else begin
    NPC <= BR_EN ? EX_MEM_ALUOUT : NPC +32'd1;
    BR_EN <= 1'd0;
    //NPC <= NPC +32'd1;
    //EX_MEM_COND <=1'd0;
    IF_ID_IR <=MEM[NPC];
    IF_ID_NPC <=NPC+32'd1;
    end
end

always @(posedge RN) begin
    //NPC<= 32'd0;
MEM[0] <= 32'h02208300;         // add r6,r1,r2.(i1)
MEM[1] <= 32'h02209380;         //sub r7,r1,r2.(i2)
MEM[2] <= 32'h0230a400;         //and r8,r1,r3.(i3)
MEM[3] <= 32'h02513480;         //or r9,r2,r5.(i4)
MEM[4] <= 32'h0240c500;         //xor r10,r1,r4.(i5)
MEM[5] <= 32'h02415580;         //slt r11,r2,r4.(i6)
MEM[6] <= 32'h00520600;         //addi r12,r4,5.(i7)
MEM[7] <= 32'h00209181;         //sw r3,r1,2.(i8)
MEM[8] <= 32'h00208681;         //lw r13,r1,2.(i9)
MEM[9] <= 32'h00f00002;         //beq r0,r0,15.(i10)
MEM[25] <= 32'h00210700;         //add r14,r2,r2.(i11)
//MEM[27] <= 32'h01409002;         //bne r0,r1,20.(i12)
//MEM[49] <= 32'h00520601;         //addi r12,r4,5.(i13)
//MEM[50] <= 32'h00208783;         //sll r15,r1,r2(2).(i14)
//MEM[51] <= 32'h00271803;         //srl r16,r14,r2(2).(i15) */

//for(k=0;k<=31;k++)
//REG[k]<=k;
/*REG[0] <= 32'h00000000;
REG[1] <= 32'd1;
REG[2] <= 32'd2;
REG[3] <= 32'd3;
REG[4] <= 32'd4;
REG[5] <= 32'd5;
REG[6] <= 32'd6;
REG[7] = 32'd7;
REG[6] = 32'd6;
REG[7] = 32'd7;
REG[8] = 32'd8;
REG[9] = 32'd9;
REG[10] = 32'd10;
REG[11] = 32'd11;
REG[12] = 32'd12;
REG[13] = 32'd13;
REG[14] = 32'd14;
REG[15] = 32'd15;
REG[16] = 32'd16;
REG[17] = 32'd17;*/
/*end
else begin
    if(EX_MEM_COND==1 && EX_MEM_IR[6:0]==BR_TYPE) begin
    NPC=EX_MEM_ALUOUT;
    IF_ID=MEM[NPC];
    end

    else begin
    NPC<=NPC+32'd1;
    IF_ID<=MEM[NPC];
    IF_ID_NPC<=NPC+32'd1;
    end
end*/
end
//I_FECT STAGE

/*always @(posedge clk) begin

//NPC <= rst ? 32'd0 : NPC+32'd1;

if(EX_MEM_COND==1 && EX_MEM_IR[6:0]==BR_TYPE) begin
NPC=EX_MEM_ALUOUT;
IF_ID=MEM[NPC];
end

else begin
NPC<=NPC+32'd1;
IF_ID<=MEM[NPC];
IF_ID_NPC<=NPC+32'd1;
end
end*/


//FETCH STAGE END

//I_DECODE STAGE 
always @(posedge clk) begin

ID_EX_A <= REG[IF_ID_IR[19:15]];
ID_EX_B <= REG[IF_ID_IR[24:20]];
ID_EX_RD <= REG[IF_ID_IR[11:7]];
ID_EX_IR <= IF_ID_IR;
ID_EX_IMMEDIATE <= {{20{IF_ID_IR[31]}},IF_ID_IR[31:20]};
ID_EX_NPC<=IF_ID_NPC;
end
//DECODE STAGE END

/*always@(posedge clk) begin
if(ID_EX_IR[6:0]== BR_TYPE)
EX_MEM_COND <= EN;
else
EX_MEM_COND <= !EN;
end*/


//EXECUTION STAGE

always@(posedge clk) begin

EX_MEM_IR <=  ID_EX_IR;
//EX_MEM_COND <= (ID_EX_IR[6:0] == BR_TYPE) ? 1'd1 :1'd0;


case(ID_EX_IR[6:0])

AR_TYPE:begin
    if(ID_EX_IR[31:25]== 7'd1)begin
    case(ID_EX_IR[14:12])

    ADD:EX_MEM_ALUOUT <= ID_EX_A + ID_EX_B;
    SUB:EX_MEM_ALUOUT <= ID_EX_A - ID_EX_B;
    AND:EX_MEM_ALUOUT <= ID_EX_A & ID_EX_B;
    OR :EX_MEM_ALUOUT <= ID_EX_A | ID_EX_B;
    XOR:EX_MEM_ALUOUT <= ID_EX_A ^ ID_EX_B;
    SLT:EX_MEM_ALUOUT <= (ID_EX_A < ID_EX_B) ? 32'd1 : 32'd0;

    endcase
    end
    else begin
        case(ID_EX_IR[14:12])
        ADDI:EX_MEM_ALUOUT <= ID_EX_A + ID_EX_IMMEDIATE;
        SUBI:EX_MEM_ALUOUT <= ID_EX_A - ID_EX_IMMEDIATE;
        ANDI:EX_MEM_ALUOUT <= ID_EX_A & ID_EX_B;
        ORI:EX_MEM_ALUOUT  <= ID_EX_A | ID_EX_B;
        XORI:EX_MEM_ALUOUT <= ID_EX_A ^ ID_EX_B;
        endcase
    end

end

M_TYPE:begin
    case(ID_EX_IR[14:12])
    LW  :EX_MEM_ALUOUT <= ID_EX_A + ID_EX_IMMEDIATE;
    SW  :EX_MEM_ALUOUT <= ID_EX_IR[24:20] + ID_EX_IR[19:15];
    endcase
end

BR_TYPE:begin
    case(ID_EX_IR[14:12])
    BEQ:begin 
    EX_MEM_ALUOUT <= ID_EX_NPC+ID_EX_IMMEDIATE;
    BR_EN <= 1'd1 ? (ID_EX_IR[19:15] == ID_EX_IR[11:7]) : 1'd0;
    //BR_PC = EX_MEM_COND ? EX_MEM_ALUOUT : 1'd0; 
end
BNE:begin 
    EX_MEM_ALUOUT <= ID_EX_NPC+ID_EX_IMMEDIATE;
    BR_EN <= (ID_EX_IR[19:15] != ID_EX_IR[11:7]) ? 1'd1 : 1'd0;
end
endcase
end

SH_TYPE:begin
case(ID_EX_IR[14:12])
SLL:EX_MEM_ALUOUT <= ID_EX_A << ID_EX_B;
SRL:EX_MEM_ALUOUT <= ID_EX_A >> ID_EX_B;
endcase
end

endcase
end


//EXECUTION STAGE END
		
//MEMORY STAGE
always@(posedge clk) begin

MEM_WB_IR <= EX_MEM_IR;

case(EX_MEM_IR[6:0])

AR_TYPE:MEM_WB_ALUOUT <=  EX_MEM_ALUOUT;
SH_TYPE:MEM_WB_ALUOUT <=  EX_MEM_ALUOUT;

M_TYPE:begin
case(EX_MEM_IR[14:12])
LW:MEM_WB_LDM <= DM[EX_MEM_ALUOUT];
SW:DM[EX_MEM_ALUOUT]<=REG[EX_MEM_IR[11:7]];
endcase
end

endcase
end

// MEMORY STAGE END


//WRITE BACK STAGE
always@(posedge clk) begin

case(MEM_WB_IR[6:0])

AR_TYPE:begin 
WB_OUT<=MEM_WB_ALUOUT;
REG[MEM_WB_IR[11:7]]<=MEM_WB_ALUOUT;
end

SH_TYPE:begin
WB_OUT<=MEM_WB_ALUOUT;
REG[MEM_WB_IR[11:7]]<=MEM_WB_ALUOUT;
end

M_TYPE:begin
case(MEM_WB_IR[14:12])
LW:begin
WB_OUT<=MEM_WB_LDM;
REG[MEM_WB_IR[11:7]]<=MEM_WB_LDM;
end
endcase
end



endcase
end
//WRITE BACK STAGE END

endmodule
 ```
***

#### The Testbench Code is:

```  module iiitb_rv32i_tb;

reg clk,RN;
wire [31:0]WB_OUT,NPC;

iiitb_rv32i rv32(clk,RN,NPC,WB_OUT);


always #3 clk=!clk;

initial begin 
RN  = 1'b1;
clk = 1'b1;

$dumpfile ("iiitb_rv32i.vcd"); //by default vcd
$dumpvars (0, iiitb_rv32i_tb);
  
  #5 RN = 1'b0;
  
  #300 $finish;

end
endmodule
```
###### BOTH THE FILES ARE SAVED IN .v FORMAT
***
###### INSTALLATION STEPS  


###### (1)  Installing:
```
sudo apt-get update
sudo apt-get install iverilog gtkwave
```
###### (2) Generating files:
```
MAKE TWO FILES IN .v FORMAT AS SAID EARLIER FOR VERILOG NETLIST AND FOR THE TESTBENCH


```


###### (3) Compiling the iverilog:
```
iverilog -o my_simulation.vvp sv.v sbt.v
```
###### (4) To run the simulation:
```
vvp my_simulation.vvp

```
###### Waveform Using GTKWave:
```
gtkwave iiitb_rv32i.vcd
```

##### [it will give the simulation] 
###### [ if the vcd file is not found to be in directory then give commant : "ls -1" and see the .vcd file in the directory and run the command for GTKwave]
***
### SNAPSHOTS 

![Screenshot 2025-02-12 211158](https://github.com/user-attachments/assets/ac842293-0dab-4778-9fe5-2c8e9291489f)

![Screenshot 2025-02-12 211631](https://github.com/user-attachments/assets/05b28306-41da-4b5b-aff1-13bd624e796e)

![Screenshot 2025-02-12 211843](https://github.com/user-attachments/assets/99357a16-997e-4258-9943-cc0832796f5e)

***

#### ABOUT PIPELINE
###### This is typical 5-stage RISC pipeline, which consists of the following stages:

###### Instruction Fetch (IF): Signals: IF_ID_IR, IF_ID_NPC Instruction is fetched from memory and the next program counter (NPC) is calculated.
  
###### Instruction Decode (ID): Signals: ID_EX_A, ID_EX_B, ID_EX_IMMEDIATE, ID_EX_IR  .The fetched instruction is decoded, and the register values are read.

###### Execute (EX): Signals: EX_MEM_ALUOUT, EX_MEM_IR .The instruction is processed, and ALU operations are performed.
###### Memory Access (MEM): Signals: MEM_WB_ALUOUT, MEM_WB_LDM .Memory operations like loads and stores are performed.
###### Write Back (WB): Signals: WB_OUT .Results from the ALU or memory are written back to the register file.

</details>

--------------------------------------------------------------------------------------------

<details>
<summary><b>Task 5: </b>Smart Light Sensor.</summary> 
<br>

# Overview

#### The Smart Light Sensor is an intelligent lighting system that automates lighting control based on ambient light levels and motion detection. It utilizes an LDR to measure brightness and a PIR sensor for motion detection, running on the VSDSquadron Mini (CH32V003F4U6) microcontroller. This project enhances energy efficiency by ensuring lights are only active when needed and reduces the manual intervention of turning the light on or off.

***
## Components Required To Build a Light Sensor:

* VSD SQUADRON MINI (CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set)
* 3 LDR's
* LED / Light source
* PIR Sensor
* Optional: Relay or MOSFET for controlling external lights

* Bread Board
* Jumper Wires


***
## CIRCUIT DIAGRAM

![Screenshot 2025-02-16 152539](https://github.com/user-attachments/assets/f5190f8d-064e-4900-8465-8fd48a363a5a)


## Table for Pin connection:


| CH32V003x Pins  | Peripherals |
|--------------|--------------|
| 5 volts      |  VCC For all Devices   |
| GND          | Ground For all Devices   |
|  PD5         | Ldr 1       |
|  PD4         | Ldr 2  |
|  PD3    |   Ldr 3  |
|  PD6    |   In built-Led   |
|  PD2    |   Output LED/ Light source  |
|  PC4    |   PIR Sensor input  |

## WORKING OF THE  CODE

The code checks the output of the PIR sensor (HIGH/LOW) and if the output is HIGH, it will check the ambient brightness using LDR's and accordingly light the LED (or any light) for optimum use. If there is enough brightness in the surroundings, the LED is turned off. If the PIR sensor's output is LOW then the LED is turned off for power saving.

## PROGRAMME CODE
```
#define ldrpin1 PD5
#define ldrpin2 PD4
#define ldrpin3 PD3
#define ledpin2 PD6
#define ledpin PD2
#define pir PC4


void setup() {
    pinMode(ledpin, OUTPUT);
    pinMode(ledpin2, OUTPUT);
    pinMode(ldrpin1, INPUT);
    pinMode(ldrpin2, INPUT);
    pinMode(ldrpin3, INPUT);
    pinMode(pir, INPUT);
}

void loop() {
    bool pir_val = digitalRead(pir);
    if (pir_val == HIGH){
      digitalWrite(ledpin2, HIGH);
    }
    else if (pir_val == LOW){
      digitalWrite(ledpin2, LOW);
    }
    bool ldr1 = digitalRead(ldrpin1);
    bool ldr2 = digitalRead(ldrpin2);
    bool ldr3 = digitalRead(ldrpin3);
    
    if (pir_val == HIGH){
      if (ldr1 == LOW && ldr2 == LOW && ldr3 == LOW){
        setPWMDuty(10000);
      }
      else if (ldr1 == HIGH && ldr2 == LOW && ldr3 == LOW){
        setPWMDuty(1000);
      }
      else if (ldr1 == HIGH && ldr2 == HIGH && ldr3 == LOW) {
        setPWMDuty(100);
      }
      else if (ldr1 == HIGH && ldr2 == HIGH && ldr3 == HIGH) {
        setPWMDuty(0);
      }
    }
    else {
      setPWMDuty(0);
    }
    
}
void setPWMDuty(int pulseWidth) {  
  if (pulseWidth == 0){
      digitalWrite(ledpin, LOW);
  }

  else{
    for (int i = 0; i < 50; i++) {
    
      digitalWrite(ledpin, HIGH);
      delayMicroseconds(pulseWidth);
      digitalWrite(ledpin, LOW);
      delay(20 - (pulseWidth / 1000)); 
    }
  }
}

```
</details>

-----------------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 6: </b>Smart Light Sensor, Working Video.</summary> 
<br>

https://drive.google.com/file/d/1cABiJjAcnGgZaSo86KzOUS1DdcsJkmaQ/view?usp=drive_link

</details>

-----------------------------------------------------------------------------------
