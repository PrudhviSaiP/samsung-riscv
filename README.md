# samsung-riscv
# VSD-VSLI-Internship   
# Task 1   
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
