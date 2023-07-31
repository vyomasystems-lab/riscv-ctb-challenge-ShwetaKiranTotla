# Bug
The test runs without exiting in spike.  
The reason the code runs into an infinte loop is due to the absence of a logic that ends the code after completion of the 3 test cases.  
This test performs addition operations and self checks for 3 set of test cases.  

# Bug Screenshots
![c2_1_bug](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/398eaea8-b6a2-4909-aad4-436c944261c3)

# Explaination of the fix
In order to finish the code after the completion of the test cases so that the code does not run infinitely in the loop, the following fixes are implemented:
*   After completion of each test case, the test case count (stored in t5) is decremented by 1.
    (using the command ``addi t5, t5, -1``)
*   The code ends as soon as all the test cases are exhausted.  (using the command ``beqz t5, test_end``)

Now, the test runs successfully!
![c2_1_bug_fixed](https://github.com/vyomasystems-lab/riscv-ctb-challenge-ShwetaKiranTotla/assets/109335487/66f6c2f6-c8e0-4d95-a2ad-1629a690cb35)
