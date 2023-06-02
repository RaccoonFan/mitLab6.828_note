# Lab 1: Booting a PC
## Part 1: PC Bootstrap
### Getting Started with x86 assembly
Some Syntax of AT&T
* Register names are prefixed with "%".
* The source is always on the left, and the destination is always on the right.
* Prefix all constant/immediate values with "$".
* You must suffix the instruction with one of b, w, or l to specify the width of the destination register as a byte, word or longword. If you omit this, GAS (GNU assembler) will attempt to guess. You don't want GAS to guess, and guess wrong! Don't forget it.

### Simulating the x86
Use QEMU to emulate a x86 PC.

### The PC's Physical Address Space
![Physical Address Space](https://github.com/RaccoonFan/mitLab6.828_note/blob/main/images/lab1/Physical_Address_Space.png)

### The ROM BIOS
The first instruction of IBM PC
![first instruction](https://github.com/RaccoonFan/mitLab6.828_note/blob/main/images/lab1/firstinstruction.bmp)
[CS:IP] ljmp newCS,newIP  
Physical Address on real mode addressing is equal to $16 * CS + IP$.  

## Part 2: The Boot Loader
The Boot Loader performs two main functions:
* The boot loader switches the processor from real mode to 32-bit protected mode, because it is only in this mode that software can access all the memory above 1MB in the processor's physical address space.
* The boot loader reads the kernel from the hard disk by directly accessing the IDE disk device registers via the x86's special I/O instructions.

### Exercise 3
* At what point does the processor start executing 32-bit code? What exactly causes the switch from 16- to 32-bit mode?  
![boot.S](https://github.com/RaccoonFan/mitLab6.828_note/blob/main/images/lab1/boot.bmp)
The processor started executing 32-bit code at the 57th line ".code32".The 55th line causes the switch from 16- to 32-bit mode.
* What is the last instruction of the boot loader executed, and what is the first instruction of the kernel it just loaded?

* Where is the first instruction of the kernel?

* How does the boot loader decide how many sectors it must read in order to fetch the entire kernel from disk? Where does it find this information?
## gdb debug
* 'si' run next instruction.
* 'c' run to next breakpoint.
* 'b *addr' make a breakpoint at addr.
* 'x/i addr' display the instruction at addr.
* 'x/Ni addr' display N instructions starting at addr.
