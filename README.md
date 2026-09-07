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

<img width="1052" height="455" alt="WhatsApp Image 2026-09-02 at 12 26 43 PM" src="https://github.com/user-attachments/assets/2f07f67a-917c-4a0c-978b-06f82ed09938" />


---

## Algorithm(Descending order)
1. Initialize the register **R7** with count.  
2. Get first two elements in two registers.  
3. Compare the two elements of data:  
   - If the value of **R0** register is high, then exchange **A** and **R0** data.  
   - Else, increment pointer and decrement register **R7**.  
4. Check if **R7 = 0**, then move the contents of **R0** and **A**.  
5. Again increment pointer and decrement **R7**.  
6. Check if **R7 = 0**:  
   - If **No**, repeat the process from Step 2.  
   - If **Yes**, stop the program.  
---
## Program (Descending order)

```
ORG 0000H
MOV R1,30H     ; Outer loop count = N
DEC R1

LOOP1: MOV R0,#40H
       MOV R6,30H
       DEC R6

LOOP:  MOV A,@R0
       INC R0
       MOV B,@R0
       CJNE A,B,NEXT
NEXT:  JNC DOWN

       MOV @R0,A
       DEC R0
       MOV @R0,B
       INC R0

DOWN:  DJNZ R6,LOOP
       DJNZ R1,LOOP1   ; Outer loop ends correctly

END




```
## OUTPUT(Descending order)

<img width="1043" height="560" alt="WhatsApp Image 2026-09-02 at 12 27 22 PM" src="https://github.com/user-attachments/assets/c1b948bf-5754-4c62-ab66-876a3f50c435" />


---
## RESULT:
Thus the sorting of given data was done using 8051 keil software.

