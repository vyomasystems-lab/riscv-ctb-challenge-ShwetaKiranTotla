# Bug
The RV32I ISA is the base integer instruction set for RISC-V, and it does not include certain instructions like `divw`, `mulw`, and `remw`, which are 64 bit instructions and a part of the RV64M extension (integer multiplication and division).  

# Bug Screenshot
![c2_1_bug](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/b37535df-7e74-4d70-9bdb-fd1dec501db4)

# Explaination of the fix

To resolve these errors, the AAPG configuration file has to be modified to ensure that it generates only instructions that are part of the RV32I ISA.  
Specifically, the probabilities for instructions that belong to unsupported extensions, in this case RV64M, should be set to zero (or removed).  
Now, the program runs successfully!
![c2_1_bug_fixed](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/903d8e3f-2b3a-4b87-ba9d-a871beadbcda)
