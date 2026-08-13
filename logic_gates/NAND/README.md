# Transistor NAND Gate

A two-input NAND gate built with NPN transistors. The LED displays the output state.

## Truth Table

| Input A | Input B | Output | LED |
| ------: | ------: | -----: | --- |
|       0 |       0 |      1 | ON  |
|       0 |       1 |      1 | ON  |
|       1 |       0 |      1 | ON  |
|       1 |       1 |      0 | OFF |

## Schematic

![NAND gate schematic](Schematics.png)

## Test

| A = 0, B = 0                           | A = 0, B = 1                           |
| -------------------------------------- | -------------------------------------- |
| ![Both buttons released](input-00.jpg) | ![Only button B pressed](input-01.jpg) |

| A = 1, B = 0                           | A = 1, B = 1                          |
| -------------------------------------- | ------------------------------------- |
| ![Only button A pressed](input-10.jpg) | ![Both buttons pressed](input-11.jpg) |
