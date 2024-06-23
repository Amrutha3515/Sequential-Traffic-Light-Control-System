# vsdmini

<details>
<summary>Task-1</summary>

+ In this program we will be using **RISC-V GNU Compiler Toolchain** to compile our c programs into risc v instructions. 
+ Then we will be using **Iverilog** to compile & simulate our verilog files. 
+ We will be using **GTKwave** to view the relevant waveforms obtained from verilog simulation.
+ Also we will be using **Yosys** to synthesis our RTL.
### Steps to install git

```
 sudo apt-get install git
 git clone https://github.com/kunalg123/vsdflow.git
 cd vsdflow
 chmod 777 opensource_eda_tool_install.sh
 ./opensource_eda_tool_install.sh
 ./vsdflow spi_slave_design_details.csv
 ./vsdflow picorv32_design_details.csv

```
![1](https://github.com/Amrutha3515/vsdmini/assets/150571663/7d1db528-055d-4aa6-a059-d648f1e5b220)

  ### steps to install RISC-V GNU-TOOL CHAIN
  
   + For installing the riscv-gnu tool chain on ubuntu computer first clone the following repository 
```
git clone https://github.com/riscv/riscv-gnu-toolchain   _where_u_want_to_clone_repo
  ```
```
sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bczlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
 ``` 
#### The above code shows error : unable to locate the libslirp then use
```
sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat1-dev ninja-build git cmake libglib2.0-dev
cd directory_where_u_want_to_clone_repo
mkdir build
cd build
../configure --prefix=/absolute/path/where/u/want/to/keep/the/tools --enable-multilib
make
```
![4-1](https://github.com/Amrutha3515/vsdmini/assets/150571663/8cf8fb5a-3187-49ff-a44b-7a0ec1092150)

![5](https://github.com/Amrutha3515/vsdmini/assets/150571663/804ccf2e-e71a-4c24-87b0-923e061f03ab)

![7](https://github.com/Amrutha3515/vsdmini/assets/150571663/5889341e-e22f-4f75-af98-3f3981ceaf8e)
### Steps to install Yosys

```
sudo apt install yosys
```

You can verify the installation of yosys as shown below
![2-1](https://github.com/Amrutha3515/vsdmini/assets/150571663/3d291f38-f933-476b-8445-59b6690d12d3)


### Steps to install gcc 

```
 sudo apt install gcc
```
you can verify gcc installation as shown below
![2-2](https://github.com/Amrutha3515/vsdmini/assets/150571663/30a02b54-cb24-4ea6-b147-f85c85bcbf03)

## Steps to install Iverilog


```
 sudo apt-get update
 sudo apt-get -y install iverilog
```
![image](https://github.com/Amrutha3515/vsdmini/assets/150571663/8aa6bf8d-359f-47d8-be9d-ae0f808a5fbc)

The installation can be verified as shown below

![3-1](https://github.com/Amrutha3515/vsdmini/assets/150571663/3a485b68-6db4-4aff-aa47-f13193f454fb)


## Steps to install gtkwave

```
 sudo apt update
 sudo apt install gtkwave
```
![3-2](https://github.com/Amrutha3515/vsdmini/assets/150571663/55a2e7d5-f7e5-4a3f-ab1f-7cf1b3fef9e9)

# Compile a `c` Program Using Riscv Compiler


## Installing Leafpad Text Editor:


We will be using `leafpad` text editor to write our `c` program. The text editor can be installed as shown below (applicable for ubuntu 22.04 version).


```
sudo snap install leafpad 
```
## The Program:

Navigate to the home directory and create a new `.c` file in leafpad as shown below,

```
 cd 
 leafpad sum1ton.c &
```
write a `c program` and use the `save button`or use `ctrl + s`  to save the file. 

```
#include <stdio.h>
int main(){
    int sum = 0, i, n = 5;
    for (i=1; i<=n; ++i){
        sum += i;
    }
    printf("Sum of numbers from 1 to %d is %d \n", n, sum);
    return 0;
}

```

![8](https://github.com/Amrutha3515/vsdmini/assets/150571663/f23f70a9-04bf-4588-9a1b-f1e94de60a76)

## Compilation & Execution


Compile and run the program as below

```
 gcc program_name.c 
 ./a.out 
```
in my case it is sum1ton.c
![9](https://github.com/Amrutha3515/vsdmini/assets/150571663/970bafec-bd71-4319-8cd2-d82b524bd43a)

To view the code you have written and compile the program in riscv gcc compiler follow the below instruction.

```
cat program_name.c
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o program_name.o program_name.c
```
in my case it is sum1ton.o sum1ton.c

![14](https://github.com/Amrutha3515/vsdmini/assets/150571663/5120c785-1a2b-46ad-b493-d79e0d6a3f45)

Now open a new tab in terminal using `ctrl + shift + T` and follow below instruction to open the assembly code for the c program we had executed earlier.

```
riscv64-unknown-elf-objdump -d program_name.o
```
to search for `main()` section of our program below the below step,

```
riscv64-unknown-elf-objdump -d program_name.o | less
: /main
```

press `n` key to scrolldown & press `q` to quit.

![t-1](https://github.com/Amrutha3515/vsdmini/assets/150571663/dbfee5f1-1518-4b72-94e0-233e53a7176c)

The above image shows the `main()` section of my program. And as we can see there are 15 instructions in the `main()`. Address of each instruction can be seen. The address of the next instruction is `current address + 4 bytes`. <br>
<br> 
**Total Number of Instructions = (Address of the first instruction of the next instruction block -  Address of the first instruction of the current instruction block) / 4**
<br>
<br>
Therefore, Total number of instructions in main() =  (101c0 - 10184)/4 = (3c/4)<sub>**16**</sub>=(F)<sub>**16**</sub> = (**15**)<sub>**10**</sub>


## Role of -O1 & -Ofast: 

**-O** is a flag which directs the compiler to what extent it needs to optimize a given program, the optimization may be in terms of reducing binary size of the program while compramizing of the speed of execution or optimize the speed of exceution while increasing the binary program size. There are various levels of optimization,
<br>
**-O1** : This flag offers basic optimization, balances binary code size as well as speed. <br>
**-Ofast** : This flag offers aggressive optimizations. It prioritizes speed of execution over the size of compiled binary program size. <br>

Let us compile the same program with **-Ofast** flag.


```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o program_name.o program_name.c
# In a new terminal tab
riscv64-unknown-elf-objdump -d program_name.o | less
: /main
```
![t](https://github.com/Amrutha3515/vsdmini/assets/150571663/a39fcea4-6911-48e9-9acb-e50e19db3a6c)

The above image shows the `main()` section of my program. And as we can see there are 12 instructions in the `main()`. Address of each instruction can be seen. The address of the next instruction is `current address + 4 bytes`. <br>
<br> 
**Total Number of Instructions = (Address of the first instruction of the next instruction block -  Address of the first instruction of the current instruction block) / 4**
<br>
<br>
Therefore, Total number of instructions in main() =  (101e0 - 101bo)/4 = (30/4)<sub>**16**</sub>=(C)<sub>**16**</sub> = (**12**)<sub>**10**</sub>

we can observe that the Number of instructions is reduced with -Ofast

# Reference:
+ https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/
+ https://github.com/riscv-collab/riscv-gnu-toolchain
+ https://photos.onedrive.com/share/E0E9B5EEF85B162E!105257?cid=E0E9B5EEF85B162E&resId=E0E9B5EEF85B162E!105257&authkey=!AFLC_zCyiQ0i1co&ithint=video&e=gdA9TW
+ https://photos.onedrive.com/share/E0E9B5EEF85B162E!56283?cid=E0E9B5EEF85B162E&resId=E0E9B5EEF85B162E!56283&authkey=!AKfV5WV4yZsaIAc&ithint=video&e=ycX4fO
