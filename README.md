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

internally, this circut will be made of **Half Adders and Full Adders** which will be repeated again and again and agian(16 times) to make a **HEXABIT**


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


![IMG_20251231_172354](https://github.com/user-attachments/assets/e3137fff-c3ac-4d58-92f3-50a7344629ec)

the AND gate is very simple in behavior.

it acts like two switches connected in series. Power reaches the output only when **both switches are ON**. If even one switch is OFF, nothing will pass through. In binary addition, this situation matters because adding `1` and `1` is the **only time** an extra bit is created (cuz binary is like counting numbers which end after zero and 1). The AND gate’s job is to notice exactly that case.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 1      |


### OR gate

![IMG_20251231_145225](https://github.com/user-attachments/assets/733643ba-5fe6-4671-b7d1-db91b55bae91)

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

---

### NOT gate


the NOT gate (also called the inverted gate cuz it inverts the output) does the work of giving an oupposite output

in other words ot flips the signal.

* If the input is ON, the output turns OFF
* If the input is OFF, the output turns ON

This flipping ability is required to build more complex gates.

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

---

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

---

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

![IMG_20251231_010206](https://github.com/user-attachments/assets/c35dfd2f-b728-435f-8f8b-b9839520868e)

this daigram shows a half adder made using NAND gate, OR gate, & AND gate

A 1 bit adder (half adder) handles the most basic possible addition.

It adds **two single binary digits**.

Binary addition works like this:

* `0 + 0` gives `0`
* `0 + 1` gives `1`
* `1 + 0` gives `1`
* `1 + 1` gives `10`

That last case is important.

The result has **two bits**. One bit stays in the current position, and the other bit moves to the next position.
and instead of treating this as one result, the circuit separates the task so..

* NAND gate and OR gate decides the bit that stays
* AND gate gives us the output


### n bit adder

![IMG-20251224-WA0005~2](https://github.com/user-attachments/assets/a56e4141-47dd-4a51-9bad-8b3882a05a9c)

this is a Nth bit adder. the black box that you see is nothing but the same combination of NAND gate, AND gate and OR gate.
this n bit adder takes the inputs x and y and the output is then later fed into another 1 bit adder thats adds the output from the first one.

sooo when these steps are repeated n times we get an nth bit adder.


### HEXABIT (what i am gonna build)

A hexabit is built by **repeating the same idea of a 1 bit adder (full adder) again and again** when its done 16 times we get a hexabit (the more bits thy wishes to add the more times you gotta repeat it).

* The first position starts the addition
* Each next position waits for the extra bit from the previous one
* The process moves from right to left (again and again and again)

each position only cares about:

* Its own two bits
* Whether an extra bit is arriving

by connecting many Full Adders in a chain, large numbers can be added to make processors with HUGE calculation power.
this design may look pookie, but it is exactly how all of the processors are made (it really blows my mind when i think about it)


## Materials Requested

to build and test this project, the following materials are required:

* Breadboards
* LEDs
* Resistors
* Jumper wires
* transistors
* 5V power source
