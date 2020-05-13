# Mantiq
Light weight operating system developed from scratch. 

### Objective 
To develop a light wieght operating system from scratch. This operating system compiler will be build for X64_64 for ARM. This is not a genral purpose Operating system. GNU targeting 32-bit Arm Cortex-A, Arm Cortex-M and Cortex-R family of processors for embedded systems. This operating system will be for raspberry pi bare bones. Some of the starting code is taking from wkik.osdev.org/Raspberry_pi_BareBones but later on I will modify, change and improve the operating system as I see fits.

### Download the compiler 
**Link:**
https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads



** Note : Download Number 4 on the list: **
gcc-arm-none-eabi-9-2019-q4-major-aarch64-linux.tar.bz2
There is a downloaded version in this github repo.



Once the file downloaded if you are working in linux create new folder for the project and copy and paste the download there. 


navigate to your newly created folder using the terminal and unzip the file using this command:


`tar -xf gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2`


**Note: The file name might be diffrent mine was the following change yours to match the download.:**

`gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2`


Compiler should be located at 
`gcc-arm-none-eabi-9-2019-q4-major/bin/arm-none-eabi-gcc`

installing a virutal machine for debugging is a great thing to do:

I installed qemu on this project.

For qemu you will need to install pixman-devel before hand. 

To install pixman-devel: 

`yum install pixman-devel`

if you don't have yum installed run this command:

`sudo-apt install yum`

or 

`sudo apt install pixman-devel`

after installing the virutal machine quem check if it is working: 

`qemu-system-arm --version`

*Note: Installing virutal machine within your virutal machine is not recommended but best practice for debugging*

*note there is arm assembly language cheat sheets in this repo*
## Files description:

### boot.S:

Contain the assembly code for the first thing that the hardware executes in our kernel. A language which the hardware can understand. 





