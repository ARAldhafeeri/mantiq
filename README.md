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

### kernel.c:
Here we handle our basic I/O thorugh UART. Later on, forsure I want to implement more advanced I/O such TTL for a starter.

mmio method: mmio, stands for memory mapped IO, basic way that the hardware using the kenral communicate with memory in predefined memory addresses.


So all the UART_xxxx addresses is nothing but incrementing the base address which is in raspberry pi 0x0x3F000000 by a set of values so we have a unique address for each peripheral. They range from 0x00000000 to 0xBFFFFFFFFF

Both mmio_read and mmio_write read in a register from the memory address.

delay() is used to slow down the code for wirtting/ reading processes.

enum is predfined offsets for the GPIO and the UART. 

uart_init : gets the UART hardware ready for use.

uart_putc(), uartgetc(), uart_puts() for reading and writing text.

kernel_main:
where our bootloader hands over the control to our kenral. 
atags contain the atags pointer. Where information about the hardware is stored. 

### linker.ld :
  .  means the current address. 
  here we assign the current address and assign things to it. 
  .text >>> executable code
  .rodata >>> read only data
  .data >>>> global varibles intilized at compile time ad stored.
  .bss >>> uninitialized global variables. 
  
  ENTRY(_start ) 
  declares the _start from boot.S
  the rest assigning addresses and declaring( .text, .rodata, .data, .bss) all put to the nearest 4096 ( page alignment ALIGN(4096) )
  
  
  At this point the OS is ready to run and compile. 

before compiling OS we need to activate qemu Virtual machine:

5-19-2020 :

tomorrow starting point is compiling the OS

 ./gcc-arm-none-eabi-9-2019-q4-major/bin/arm-none-eabi-gcc -mcpu=cortex-a7 -fpic -ffreestanding -c boot.S -o boot.o
 
 this is hard..............................................



