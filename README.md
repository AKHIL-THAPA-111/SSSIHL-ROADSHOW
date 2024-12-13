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

#### v)We then change the directory to the openlane using following command which is an open-source framework used for the automated physical design of ICs.
    cd Desktop/work/tools/openlane_working_dir/openlane
Which after succesful completion should look like the following image:
![Screenshot 2024-12-13 121210](https://github.com/user-attachments/assets/f97fc1c1-8eb4-4067-bc30-91fc3340da1c)


#### vi)Then we specify the version to 0.9 by the following command 
        package require openlane 0.9

#### vii)Then we prepare the design workspace for a specific project which in our case is picorv32a using the following command
         prep -design picorv32a
After successful compilation it the output should be as follows
![Screenshot 2024-12-13 121803](https://github.com/user-attachments/assets/0ab8962c-e3f6-434a-923c-3aea009e4880)

#### viii)Then we trigger the synthesis stage of the digital IC design flow by using the following command
           run_synthesis
After successful compilation it the output should be as follows
![Screenshot 2024-12-13 122526](https://github.com/user-attachments/assets/bdeb24ce-b318-46bf-8cf4-b9735d939a50)

#### ix)Then we execute the floorplanning state of the IC design flow .It is a crucial step in translating the synthesized gate-level netlist into a physical design by defining the chip's layout structure and preparing it for placement and routing.This was done by executing the following command
        run_floorplan
After successful compilation it the output should be as follows
![Screenshot 2024-12-13 123658](https://github.com/user-attachments/assets/0326ff3b-b080-4575-8434-4c72c189e929)

#### x)Then we open a new terminal and type the following command to display the floorplan image(some changes in command is required) :
       eog designs/picorv32a/runs/{press tab as it varies from device to device}/results/floorplan/picorv32a.floorplan.def.png
The .png file is as follows
![Screenshot 2024-12-13 124009](https://github.com/user-attachments/assets/aa4d7457-d604-4e1a-8984-f86317b5e79b)

####  xi)For the placement stage of the digital ASIC design flow we use the following command 
          run_placement
After successful compilation it the output should be as follows
![Screenshot 2024-12-13 140631](https://github.com/user-attachments/assets/827edf90-fa8a-4922-96a9-33ee3aaecd52)


#### xii)Then we open a new terminal and type the following command to display the placement image(some changes in command is required)
        eog designs/picorv32a/runs/{press tab as it varies from device to device}/results/placement/picorv32a.placement.def.png
The .png file is as follows
![Screenshot 2024-12-13 140740](https://github.com/user-attachments/assets/369b6298-c4c9-4636-bbf7-a4955839fece)

#### xiii)Then we run the command n the OpenLane flow stands for Clock Tree Synthesis (CTS), and its purpose is to create a clock distribution network for your design.
          run_cts
After successful compilation it the output should be as follows
![Screenshot 2024-12-13 141938](https://github.com/user-attachments/assets/9352cb35-c83e-4c02-942e-1b14e79411b5)

#### xiv)Once CTS is complete, the next step is routing. This is where the tool connects all the cells using metal layers, creating the physical interconnections that make up the logic and clock paths of the design.We do this by running the following code:
                                          run_route
![Screenshot 2024-12-13 145414](https://github.com/user-attachments/assets/8290646b-c6fc-471b-b668-8fa568dd4539)

       
