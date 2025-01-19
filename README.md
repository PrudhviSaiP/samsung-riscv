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
