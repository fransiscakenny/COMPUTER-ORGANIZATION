Name: Fransisca K Larasati
E-mail: FKL1@pitt.edu

CS 447 Project 2: jrMIPS

INTRODUCTION
jrMIPS is a program that should several instructions of the actual MIPS. It is created by making a datapath, consisting of a program counter and fetch adder, ROM as the instruction memory, a register file, decoders, sign extenders, ALU, RAM as the data memory and LEDs, in my program one is for the output of $rs, and one is for the immediate for testing purposes, and also one more LED to indicate the program has been halted. 

The MIPS INSTRUCTIONS that has been implemented in jrMIPS, and has worked well when tested with the example programs are:
and, nor, addi, addui, add, sub, div, mul, sllv, srlv, bx, bz, bp, bn, lw, sw, li, jal, jr, j, put, and halt (a.k.a all of them).

The CONTROL SIGNALS used in order for the program to work are:
- OPER: Oper controls which output of the ALU Mux would be outputted.
- WriteEn: WriteEn controls whether the we allow any of the registers in the RegFile to be written on or not. 
- DIM: Stands for Data/Immediate, this control signals controls what would be the input of the RegFile. It could be Data from Data Memory, ALU, Immediate from the Field, or the PC+1 for the Jal instruction. 
- ARS: Stands for ALU/$rs, it controls what would be the input of the RAM, it could be from the ALU or the $rs. 
- addi: addi controls the input of the ALU other than the $rs, it chooses between the value of $rt for regular add, or the immediate for the addi and addui instruction. 
- UII: Stands for Unsigned Immediate/Immediate. UII will only matter if addi is activated. It decides whether we want to do addi or addui instruction, and sends the immediate to the correct bit extender (sign or zero). 
- DivMul: Stands for Division/Multiplication. It controls whether the data to be put in to the RegFile is a remainder or the upper half of the multiplication result. 
- HEXMux: HEXMux controls whether we transfer the value in the $rs to the HEX LED or not. Will be activated when put instruction is put in. 
- PCMux: PCMux controls what the input of the PC would be. It chooses between, PC+1, Immediate, and $rs. 
- Str: Str controls whether we allow data to be stored to Data Memory or not. 
- Ld: Ld controls whether we allow data to be loaded from Data Memory or not.
- DataMemory: DataMemory controls whether the DataMemory should be activated or not. 

These Control Signals are controlled using the Combinational Analysis feature in Logisim, in which I put the Control Signals as the output of the Truth Table, and:
Opcode (split into 4), Subop, Zero Detector, Larger-Than Detector, Smaller-Than Detector, and Halt Detector, as the input. 
