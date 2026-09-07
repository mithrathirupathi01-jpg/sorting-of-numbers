# sorting-of-numbers
## Aim
To write and execute an Assembly Language Program for sorting data in Ascending and  descending order using 8051 microcontroller on Keil software.
---

## Apparatus Required
- Personal Computer  
- Keil µVision software  
---

## Algorithm(ASCENDING ORDER)
1. Initialize the register **R7** with count (number of elements).  
2. Get the first two elements into two registers.  
3. Compare the two elements:  
   - If the value in register **R0** is lower, exchange **A** and **R0** data.  
   - Otherwise, increment pointer and decrement register **R7**.  
4. Check if **R7 = 0** → if yes, move the register **R0 & A**.  
5. Increment pointer and decrement **R7**.  
6. If **R7 ≠ 0**, repeat from Step 2.  
7. Otherwise, stop the program.  
---

## Program (Ascending order)

```
ORG 0000H
MOV R4,#04H        ; Number of passes (N-1)
OUTER: MOV R3,#04H ; Inner loop counter
MOV R0,#50H        ; Array starting address
INNER: MOV A,@R0
MOV B,A
INC R0
CLR C
SUBB A,@R0         ; Compare adjacent elements
JC NO_SWAP         ; If A < @R0 (Carry), no swap
; Exchange elements
MOV A,@R0
XCH A,B
MOV @R0,A
DEC R0
MOV A,B
XCH A,B
MOV @R0,A
INC R0
NO_SWAP: DJNZ R3,INNER
DJNZ R4,OUTER
END


```
## OUTPUT(Ascending order)
