# Bug 1
The error encountered, "illegal operand" for the command "and s7, ra, z4," is due to an incorrect destination register in the RISC-V assembly code.  

The destination register for the "and" instruction should be a general-purpose register (x0 to x31). The register "z4" is not a valid destination register name in the RISC-V ISA.  

# Bug 2
The error encountered for the RISC-V assembly code command "andi s5, t1, s0" is due to an incorrect syntax.  

The correct syntax for the "andi" instruction is :  
			andi rd, rs, imm  
	 
Where:  
"rd" is the destination register (a general-purpose register) where the result will be stored.  
"rs" is the source register (a general-purpose register) whose value will be ANDed with the immediate value.  
"imm" is the immediate value, which is a constant used in the AND operation.

## Bug Screenshots
![c1_1bug1](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/2814a13b-9a72-4c77-827d-40a9995492d4)
![c1_1_bug2](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/0dd0c833-9f76-4b92-b46f-db2451d5ae27)

# How to fix? (Explaination of the fix)

## Bug 1
To perform a bitwise AND operation and store the result in register s7, the correct instruction is: and s7, s7, ra  
This instruction will bitwise AND the values in register s7 and register ra, and store the result in register s7.  
Instead of using s7 as a destination address to store the result, any other register (x0 to x31) can be used.  
![c1_1_bug_fixed1](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/d206bbf7-7d87-4a76-8c66-2e90ee64a3bf)

## Bug 2
Instead of using the s0 register as an argument, any constant will fix the bug and the test runs successfully.
![c1_1_bug_fixed2](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/7b4598a6-dfba-416c-bfcf-cded50da7504)
