# Samsung-VSD
## VSLI-Internship   
----------------------------------------------------------------------------------------------------------------------------------------------------------
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


 
</details>
