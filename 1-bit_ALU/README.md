# 1-Bit ALU

A 1-bit Arithmetic Logic Unit designed using 74HC logic chips. It supports ADD, AND, OR and XOR, with two control inputs selecting the result.

## Components

* **74HC00** — NAND gates for XOR operations and multiplexers
* **74HC08** — AND gates
* **74HC32** — OR gates

>[!NOTE]
>    Dedicated XOR gates, such as the **74HC86**, would simplify the circuit and reduce wiring. I did not have any available, so each XOR was built using four NAND gates.

## Operation Selection

| S1 | S0 | Operation | Result               |
| -: | -: | --------- | -------------------- |
|  0 |  0 | AND       | A AND B              |
|  0 |  1 | ADD       | A XOR B XOR Carry-in |
|  1 |  0 | OR        | A OR B               |
|  1 |  1 | XOR       | A XOR B              |

Carry-out comes directly from the full adder and is only relevant when using ADD.

## Truth Table

Results with **Carry-in = 0**:

|  A |  B | AND | ADD result | OR | XOR | Carry-out |
| -: | -: | --: | ---------: | -: | --: | --------: |
|  0 |  0 |   0 |          0 |  0 |   0 |         0 |
|  0 |  1 |   0 |          1 |  1 |   1 |         0 |
|  1 |  0 |   0 |          1 |  1 |   1 |         0 |
|  1 |  1 |   1 |          0 |  1 |   0 |         1 |

Setting Carry-in to 1 flips the ADD result and recalculates Carry-out. The logic operations remain unchanged.

## Schematic

![1-bit ALU schematic](Schematics.png)

## Breadboard Test

Both input buttons are pressed: **A = 1, B = 1**, with **Carry-in = 0**.
The yellow LEDs show **S1** (left) and **S0** (right). The upper red LED shows the result; the lower red LED shows Carry-out.

| AND — S1 S0 = 00, Result = 1 | ADD — S1 S0 = 01, Result = 0 |
|---|---|
| ![AND operation](alu-and-00.png) | ![ADD operation](alu-add-01.png) |

| OR — S1 S0 = 10, Result = 1 | XOR — S1 S0 = 11, Result = 0 |
|---|---|
| ![OR operation](alu-or-10.png) | ![XOR operation](alu-xor-11.png) |

**Carry-out stays HIGH in all four photos** because the full adder runs independently of the operation selector. It is used as an arithmetic result only in ADD mode.
