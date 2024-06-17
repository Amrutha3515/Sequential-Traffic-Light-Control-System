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
$ sudo apt install gcc
```
you can verify gcc installation as shown below
![2-2](https://github.com/Amrutha3515/vsdmini/assets/150571663/30a02b54-cb24-4ea6-b147-f85c85bcbf03)

## Steps to install Iverilog


```
$ sudo apt-get update
$ sudo apt-get -y install iverilog
```
![image](https://github.com/Amrutha3515/vsdmini/assets/150571663/8aa6bf8d-359f-47d8-be9d-ae0f808a5fbc)

The installation can be verified as shown below

![3-1](https://github.com/Amrutha3515/vsdmini/assets/150571663/3a485b68-6db4-4aff-aa47-f13193f454fb)


## Steps to install gtkwave

```
$ sudo apt update
$ sudo apt install gtkwave
```
![3-2](https://github.com/Amrutha3515/vsdmini/assets/150571663/55a2e7d5-f7e5-4a3f-ab1f-7cf1b3fef9e9)
