# SSSIHL-ROADSHOW

Welcome to my **SSSIHL-ROADSHOW** project! This repository showcases the work I completed as part of the **SSSIHL-ROADSHOW** workshop. The project focuses on creating an **interactive experience** that highlights the events, achievements, and educational programs of **SSSIHL** through a **virtual platform**.

## Project Overview

In this project, I worked on building a **virtual roadshow** that showcases key aspects of **SSSIHL's events and programs**. The primary goal of the project is to create an **interactive** and **engaging experience** for users to explore, learn about, and interact with hand on activities

## STEPS
There were several steps which was to be followed to design a chip 

### 1) Steps to create a vdi to do the tasks required


#### i)We intsalled a .vdi file provided by the host 
#### ii)Virtual box was downloaded and installed using the following link : 
         https://www.virtualbox.org/wiki/Downloads
#### iii)The type of OS was Ubuntu 18.04 LTS(Bionic Beaver) using the existing virtual hard disk provided by the host

### 2)After doing the above steps we enter the actual chip making process:

#### i)First we open the ubuntu os and open terminal

#### ii)We then  run a simple c code by following the steps
#####    I)We use the command ### Example Commands
   To clone a Git repository and install `gedit`:
   
     sudo apt install gedit
#####    II)Then the password given by host was added to succesfully install.
#####    III)Then we enter gedit to open text terminal to add code.The code in my case was as below
      #include<stdio.h>
       int main(){
       int sum = 0, i, n;
    
    // Prompt user to enter a number n
       printf("Enter the value of n = ");
       scanf("%d", &n);  // Read the value of n from the user
    
    // Calculate the sum of numbers from 1 to n using a for loop
       for(i = 1; i <= n; i++){
        sum = sum + i;  // Add each value of i to sum
    }
    
    // Output the result
       printf("The Sum of numbers from 1 to %d is %d\n", n, sum);
    
       return 0;  // Return 0 to indicate successful execution
      }

##### IV)After saving the file (in my case ak.c) we write gcc {followed by the code file name} to compile the file
##### V)After that we use the following command to run the c code
         ./a.out
The following image depicts the process

![Screenshot 2024-12-13 105017](https://github.com/user-attachments/assets/0941d5eb-a96f-4d55-9144-f0a1363d4e4f)

#### iii)Then as we are using RISC-V architechture we will use the following command to do so :
       
        riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o {filename}.o {filename}.c
#### iv)Then we disassemble the file for the RISC-V architecture using the following command :
        riscv64-unknown-elf-objdump -d {filename}.o
Which after runing code looks something like the following image :

![Screenshot 2024-12-13 110821](https://github.com/user-attachments/assets/2f318c23-0cb6-4f29-ab0a-6d691867fa50)

#### v)We then change the directory to the openlane which is an open-source framework used for the automated physics
