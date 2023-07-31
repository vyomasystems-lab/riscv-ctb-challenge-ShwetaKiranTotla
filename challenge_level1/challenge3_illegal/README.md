![c1_3_bug_fixed](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/2675b564-a394-4d7c-a3d2-a2bd6525ef03)# Bug
The test runs without exiting in spike.  
The reason the code runs into an infinte loop is due the presence of an undefined instruction (.word 0) and the absence of an exception handler.  
Hence, the code does not handle this situation, and instead, it enters an infinite loop as there is no instruction to exit or recover from the exception.  

# Bug Screenshot
![c1_3_bug](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/dd3ea166-1fe5-4018-a5a8-3192610039e9)

# Explaination of the fix
First let's analyze the code:

1. The code starts with the test header `RVTEST_RV64M`.
2. The code defines an exception handler called `mtvec_handler` using the `.global` directive. This handler is meant to handle an illegal instruction exception.
3. The `mtvec_handler` loads the value of the `mcause` CSR (Cause Register) into `t0` and checks if the cause is an illegal instruction exception (`CAUSE_ILLEGAL_INSTRUCTION`).
4. If the cause is not an illegal instruction, the code jumps to the `fail` label, signaling a test failure.
5. If the cause is an illegal instruction, the code retrieves the value of the `mepc` CSR (Exception Program Counter) into `t0` and then returns from the exception using the `mret` instruction.

When the .word 0 command is removed or replaced with any legal instruction, the code runs successfully!  
Or in the exception handler (riscv_test.h) code, a graceful termination method can be defined in the exception handler.  

Like the exception handler can calculate the next instruction's address, load it into the `mepc` register, and then branch to `continue_test` (created label).  
The `continue_test` label can be used to perform further test instructions or additional handling before branching to the `next_instruction` (created label).  
The test can then continue running normally, and in case of a failure, it can be handled in the `fail` section.

The `illegal_instruction` label must be replaced with a legal instruction or a sequence of instructions that will not cause an illegal exception.
![c1_3_bug_fixed](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/c1b62ee3-24f1-4936-9d00-de8817e613c4)
