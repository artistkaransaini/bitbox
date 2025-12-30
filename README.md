bitbox

# Logic Gates and Hexabit
## Project Summary

This project dives straight into the heart of digital electronics: **binary addition at the hardware level**. Instead of treating addition as something that magically happens inside a CPU, this project breaks it down into its rawest form: voltages, logic gates, and wires.

The goal is to **physically build and test a Hexabit** on a breadboard using logic gate ICs and LEDs, and to understand exactly how simple gates cooperate to perform meaningful computation.


---

## Why I Chose This Project?

Binary addition is the foundation of *everything* in computing. Every calculation performed by a CPU, from adding two numbers to rendering graphics, eventually reduces to this.

By building a multi-bit adder physically, I want to understand:

* How extremely simple gates combine into powerful systems
* How numbers are added **without software**
* How CPUs actually perform calculations at the lowest possible level

---

## What I Am Building

I am building a **Hexabit** that:

* Takes **two 16-bit binary numbers** as input
* Produces the correct **16-bit sum and carry output** using only logic gates
* Displays outputs using **LEDs** for direct visual feedback
* Is fully built and tested on a **breadboard**

Internally, this circuit is constructed by chaining together **Half Adders and Full Adders**, exactly the same conceptual structure used inside real processors.

---

## Concepts Covered

This project includes explanation and physical implementation of:

* AND Gate
* OR Gate
* NOT Gate
* NAND Gate
* NOR Gate
* Half Adder
* Full Adder
* Hexabit

---

## Logic Gates Used

### AND Gate
![IMG_20251231_000532](https://github.com/user-attachments/assets/01a31d50-4e48-4427-aef8-76c57c6c922a)



The AND gate is very simple in behavior.

Think of it like two switches connected in series. Power reaches the output only when **both switches are ON**. If even one switch is OFF, nothing passes through.

In binary addition, this situation matters because adding `1` and `1` is the **only time** an extra bit is created. The AND gate’s job is to notice exactly that case.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 1      |

---

### OR Gate
![IMG20251230235929~2](https://github.com/user-attachments/assets/65d22a02-efe3-4b59-a1a9-cc2fb4540952)



The OR gate behaves like switches connected in parallel.

If **any one** input is ON, the output turns ON. It does not care how many inputs are ON, even one is enough.

In adders, extra bits can be created in more than one place. The OR gate is used to **collect all those possibilities** and turn them into one clean signal.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 1      |

---

### NOT Gate
![IMG20251230235929~3](https://github.com/user-attachments/assets/ae13f163-746f-42b4-bbd8-0715d4823b98)

The NOT gate does only one thing, but that one thing is essential.

It flips the signal.

* If the input is ON, the output turns OFF
* If the input is OFF, the output turns ON

This flipping ability is required to build more complex gates. Without NOT, gates like NAND and NOR would not exist.

**Truth Table**

| A | Output |
| - | ------ |
| 0 | 1      |
| 1 | 0      |

---

### NAND Gate
![IMG_20251231_000500](https://github.com/user-attachments/assets/6efece2f-e66a-4c5d-98f9-abada6cd28ac)

The NAND gate is an AND gate followed immediately by a NOT gate.

It behaves normally for most inputs, but when **both inputs are ON**, it does the opposite and turns OFF.

This gate is extremely popular in real electronics because it is:

* Easy to manufacture
* Fast
* Flexible

Entire computers can be built using only NAND gates.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 1      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 0      |

---

### NOR Gate
![IMG_20251231_000551](https://github.com/user-attachments/assets/17d8a245-7d4e-4e71-a87f-698b9f633293)

The NOR gate is an OR gate followed by a NOT gate.

The output turns ON **only when all inputs are OFF**. The moment even one input turns ON, the output shuts off.

NOR gates are commonly used in control logic and memory circuits.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 1      |
| 0 | 1 | 0      |
| 1 | 0 | 0      |
| 1 | 1 | 0      |

---

### XOR Gate

![IMG_20251231_010206](https://github.com/user-attachments/assets/f93a6afb-0712-4b61-9b66-9b53d61573e6)


The XOR gate outputs ON when the two inputs are **different**.

If both inputs are the same, the output stays OFF.

This behavior matches exactly how binary addition works when no extra bit is produced.

**Truth Table**

| A | B | Output |
| - | - | ------ |
| 0 | 0 | 0      |
| 0 | 1 | 1      |
| 1 | 0 | 1      |
| 1 | 1 | 0      |

---

## How Binary Addition Is Implemented

### Half Adder

![IMG_20251231_010206](https://github.com/user-attachments/assets/c35dfd2f-b728-435f-8f8b-b9839520868e)


A Half Adder handles the most basic possible addition.

It adds **two single binary digits**.

Binary addition works like this:

* `0 + 0` gives `0`
* `0 + 1` gives `1`
* `1 + 0` gives `1`
* `1 + 1` gives `10`

That last case is important.

The result has **two bits**. One bit stays in the current position, and the other bit moves to the next position.

Instead of treating this as one result, the circuit separates the job:

* One gate decides the bit that stays
* One gate checks if an extra bit needs to move forward

This is why a Half Adder uses:

* XOR gate for the main output bit
* AND gate to detect when both inputs are `1`

---

### Full Adder

![IMG-20251224-WA0005~2](https://github.com/user-attachments/assets/a56e4141-47dd-4a51-9bad-8b3882a05a9c)

A Full Adder is used when addition is already in progress.

At this point, there may already be **an extra bit coming in** from the previous position.

So a Full Adder adds:

* The two current bits
* The incoming extra bit

Instead of adding all three at once, the circuit breaks it into simple steps:

1. Add the two main bits
2. Add the incoming bit to that result
3. Check if any step produces an extra bit

Different gates handle each of these checks, and the results are combined carefully.

This is what allows addition to continue smoothly across many bit positions.

---

### Hexabit

A hexabit is built by **repeating the same idea of a full adder again and again**.

* The first position starts the addition
* Each next position waits for the extra bit from the previous one
* The process moves from right to left

Each position only cares about:

* Its own two bits
* Whether an extra bit is arriving

By connecting many Full Adders in a chain, large numbers can be added reliably.

This design may look simple, but it is exactly how real processors are made as well.

---

## Materials Requested

To build and test this project physically, the following materials are required:

* Breadboards
* LEDs
* Resistors
* Jumper wires
* transistors
* 5V power source
