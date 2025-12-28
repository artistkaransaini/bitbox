# bitbox







![IMG-20251227-WA0008~2](https://github.com/user-attachments/assets/426b7b84-5700-4ec1-91e0-65f831375d6a)







Digital electronics works on binary logic , only two states exist:

0 (FALSE)

1 (TRUE)



Logic gates are the basic building blocks that process these binary signals.

This document explains:
 
1.AND gate

2.OR gate

3.NAND gate

4.NOR gate

5.How AND, OR, and NAND gates combine to form a half bit and a full bit adder

________________________


2. AND Gate
Working Principle

An AND gate outputs 1 only if all inputs are 1.

Output Table
Input A	Input B	Output
0	0	0
0	1	0
1	0	0
1	1	1

Real Meaning:

Think of two switches in series. Current flows only when both are ON.



-----------------------

3. OR Gate
Working Principle

An OR gate outputs 1 if at least one input is 1.

Output Table
Input A	Input B	Output
0	0	0
0	1	1
1	0	1
1	1	1
Real Meaning

Two switches in parallel. If any one is ON, current flows.

-------------------

4. NOT Gate
Working Principle

A NOT gate (also called an inverter) has a single input and produces an inverted (opposite) output.

Output Table
Input	Output
0	1
1	0

Real Meaning:

Think of a switch that flips the state. If current is present, it blocks it; if no current is present, it allows it.

Importance:

The NOT gate is fundamental. Without inversion, gates like NAND and NOR cannot exist.

----------------------

5. NAND Gate

Working Principle

A NAND gate is an AND gate followed by a NOT gate.

It outputs 0 only when both inputs are 1.

Output Table
Input A	Input B	Output
0	0	1
0	1	1
1	0	1
1	1	0


6. NOR Gate

Working Principle

A NOR gate is an OR gate followed by a NOT gate.

It outputs 1 only when all inputs are 0.

output Table
Input A	Input B	Output
0	0	1
0	1	0
1	0	0
1	1	0

---------------------------

7. Half Adder 

A Half Adder is used to add two binary digits.
Inputs X and Y

Outputs One bit written at the same place One extra bit that moves to the next place

Explanation:
 When two bits are added, the result can be 0, 1, or 2. If the result is 0 or 1, that digit is written at the same place. If the result is 2, it is written as 10 in binary. The right digit stays at the current place. The left digit(overflow) moves to the next place.

-------------------------------

8. Full Adder

A Full Adder is used when an extra bit is already coming from a previous addition.

Inputs X Y Extra bit from the previous step

Outputs One bit written at the current place One extra bit passed to the next place

Explanation:
First, X and Y are added. Then the extra bit (overflow) from the previous step is added. If the final result fits in one bit, it is written at the current place. If the result becomes two bits, the right bit stays here and the left bit moves forward.

Gates used:
OR gates decide the written bit. AND gates detect when the result becomes too large for one bit. OR gate combines those cases and gives the output.
