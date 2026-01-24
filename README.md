bitbox

# Logic Gates and Hexabit
## Project Summary

i am making a hexabit processor with the help logic gates, ICs and leds and cosntructing differenret gates out of them such as and, or Nand etc and displaying the outbut on leds (blue ones cuz they are cool)


## Why I Chose This Project?

the goal for this project is to get a proper understanding of the working of binary addition (cuz my friend said they are the foundation of *everything* in computing)


by building a multi-bit adder physically, I want to understand:

* how extremely simple gates combine to very powerful processors
* how numbers are added without software
* how CPUs actually perform calculations at the lowest possible level


## What I Am Building

I am building a **Hexabit** that:

* will take **two 16-bit binary numbers** as input
* produces the correct **16-bit sum and carry output** using logic gates
* displays outputs using **leds**
* it will be fully built and tested on a **breadboard**

internally, this circut will be made of **Half Adders and Full Adders** which will be repeated again and again to make a **HEXABIT**


## concepts covered

this project includes explanation of:

* AND gate
* OR gate
* NOT gate
* NAND gate
* NOR gate
* 1 bit adder
* N bit adder
* HEXABIT (16 bit adder )

## Logic gates used

### AND gate


**AND gate made from relays**
![relay AND](https://github.com/user-attachments/assets/35b98ede-09b4-420a-884a-acc7a9e3b466)



**AND gate made from Transistors** 
![transistor and](https://github.com/user-attachments/assets/0b35fbe9-4799-49e3-b453-4165235e3690)



**lastly, this is the commonly used *symbol* of AND gate**
![AND](https://github.com/user-attachments/assets/57c133e6-cacc-4f6f-8b8b-8b5320622932)

*Note*: all three mean the same, its just that one is made from transistors, one from relay and the symbol is just for brevity.

WORKING OF AND GATE:

The AND gate is very simple in behavior.

it acts like two switches connected in series. Power reaches the output only when **both switches are ON**. if even one switch is OFF, nothing will pass through. in binary addition, this situation matters because adding `1` and `1` is the **only time** an extra bit is created (cuz binary is like counting numbers which end after zero and 1). The AND gate’s job is to notice exactly that case.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 1      |


### OR gate

**OR gate made from relays**
![relay or](https://github.com/user-attachments/assets/c891d698-ede9-4ae3-af08-089ddfd925d6)

**OR gate made from transistors**
![transistor or](https://github.com/user-attachments/assets/436552cb-100d-4b49-9a38-3cc678d02099)


**And this is the commonly used *symbol* of OR gate**
![OR gate](https://github.com/user-attachments/assets/49a5f7a6-f9d1-4955-befc-b33a74d116ca)

WORKING OF OR GATE:

the OR gate behaves like switches connected in parallel.

so if **any one** input is ON, the output turns ON

in adders, extra bits can be created in more than one place. The OR gate is used to **collect ALL those possibilities** and turn them into one clean signal.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 1      |


### NOT gate

**NOT gate made from relays**
![relay not](https://github.com/user-attachments/assets/bf0b098b-9faf-4fd9-9a36-92054ff680ea)

**NOT gate made from transistors**
![transistor not](https://github.com/user-attachments/assets/5ea121b9-1d2f-4322-a4b2-fd1db4890e7b)

**And this is the commonly used *symbol* of NOT gate**
![NOT](https://github.com/user-attachments/assets/39469561-9479-4e74-bfcd-f3197b976dc6)

WORKING OF NOT GATE:

the NOT gate (also called the inverted gate cuz it inverts the output) does the work of giving an oupposite output

in other words ot flips the signal.

* If the input is ON, the output turns OFF
* If the input is OFF, the output turns ON

This flipping ability is helps to build some really complex gates.

**Truth Table**

| A | Output |
| - | ------ |
| 0 | 1      |
| 1 | 0      |


### NAND Gate

The NAND gate is an AND gate followed immediately by a NOT gate.

it behaves normally for most inputs, but when **both inputs are ON**, it does the opposite and turns OFF.
this gate is extremely popular in real electronics because it is:

* very easy to manufactur
* Fast
* Flexible

fun fact: Entire computers can be built using only NAND gates.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 1      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 0      |


### NOR Gate

The NOR gate is an OR gate followed by a NOT gate.

The output turns ON **only when all inputs are OFF**. The moment even one input turns ON, the output shuts off.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 1      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 0      |


### XOR Gate


The XOR gate outputs ON when the two inputs are **different**.

If both inputs are the same, the output stays OFF. this behavior matches exactly how binary addition works when no extra bit is produced.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 0      |


## How Binary Addition Is Implemented

### 1 bit adder

![IMG_20260118_011318](https://github.com/user-attachments/assets/ce5e7a94-6d9d-4988-b945-28acfdad273d)
the above diagrams shows the construction of a 1 bit adder. The diagranm on the left adder uses a symbolic box in the ceneter for brivity and the one on the right shows the anatomy behind that 1 bit adder.

The following 1 bit adder is made from following gates:
AND gate
-it detects when both inputs are 1
OR gate
-it detects when at least one input is 1
NOT gate
-lastly it is used to remove the 1 + 1 case from the OR result

A 1 bit adder (half adder) handles the most basic possible addition.

It adds **two single binary digits**.

Binary addition works like this:

* `0 + 0` gives `0`
* `0 + 1` gives `1`
* `1 + 0` gives `1`
* `1 + 1` gives `10`

now observe the last case,
the result has **two bits**. One bit stays in the current position, and the other bit moves to the next position.
and instead of treating this as one result, the circuit separates the task so....

* NAND gate and OR gate decides the bit that stays
* AND gate gives us the output


### n bit adder

![Nth bit adder](https://github.com/user-attachments/assets/980e4fdd-37be-41ba-9635-75531e10d5ae)

this is a Nth bit adder. the black box that you see is nothing but the same combination of NAND gate, AND gate and OR gate( as explained in the half adder above).
this n bit adder takes the inputs x and y and the output is then later fed into another 1 bit adder thats adds the output from the first one.

sooo when these steps are *repeated n times* we get our Nth bit adder.


### HEXABIT (what i am gonna build)

![IMG20260118022829~2](https://github.com/user-attachments/assets/11cddaa5-d157-410b-9c92-e898c0c53abb)



A hexabit is built by **repeating the same idea of a 1 bit adder (full adder) again and again and again** (the more bits you wish to add the more times you gotta repeat it).

* The first position starts the addition
* Each next position waits for the extra bit from the previous one
* The process moves from right to left (again and again and again)

each position only cares about:

* Its own two bits
* Whether an extra bit is arriving

by connecting many Full Adders in a chain, large numbers can be added to make processors with HUGEEE calculation power.
this design may look simple, but it is exactly how all of the processors are made (it really blows my mind when i think about it)


## Materials Requested

to build and test this project, the following materials are required:

* Breadboards
* LEDs
* Resistors
* Jumper wires
* transistors
* 5V power source
