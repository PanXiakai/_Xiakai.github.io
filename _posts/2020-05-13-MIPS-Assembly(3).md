---
title: MIPS Assembly(3)
subtitle:mipsStack(1)
author: Xiakai
date: 2020-05-13
description: MIPS Stack and Heap
---

> CS61C Notes  
> Computer Organization and Design 5th-edition  
> Chapter 2 Instruction:Language of the Computer  
> 2.8 Supporting Procedure in Computer Hardware

## Using More registers

- Necessity: For a program or a procedure, four argument registers and two return registers are not enough.

### Stack

- **Description**: After a procedure's mission is done, we must cover our tracks, any registers needed by the caller must be restored to the values that they contained before the procedure was invoked.
- **Solution**: Spill registers to memory using a stack--a last-in-first-out queue with a stack pointer.
- **Stack pointer**: sp was adjusted by one word for each register that is saved or stored, MIPS software reserves register 29 for it, giving it the obvious name `$sp`.
- **Stack operation**: push; pop.
- **Stack address**: stacks "grow from higher addresses to lower addresses. This convention means that you push values onto the stack by subtracting from the stack pointer. Adding to the stack pointer shrinks the stack, thereby popping values off the stack.

### Example

> Compiling a C Procedure That Doesn't Call Another Procedure

```C
int leaf_example (int g, int h, int i, int j)
{
    int f;
    f = (g + h) + (i + j);
    return f;
}
```

- The parameter variables `g, h, i, j` corresponds to the argument registers `$a0, $a1, $a2, $a3`; `f` corresponds to `$s0`; the compiled program starts with the label of the procedure:

```MIPS ASM
leaf_example:
```

- The next step is to save the registers used by the procedure. We "push"the old values onto the stacks by creating space for three words(12 bytes) on the stack and then store them:

```MIPS ASM
addi    $sp, $sp, -12       # adjust stack to make room for 3 items
sw      $t1, 8($sp)         # save register $t1 for use afterwards
sw      $t0, 4($sp)         # save register $t0 for use afterwards
sw      $s0, 0($sp)         # save register $s0 for use afterwards
```

- **All Assembly Code**

```MIPS ASM
leaf_example:
            addi    $sp, $sp, -12       # adjust stack to make room for 3 items
            sw      $t1, 8($sp)         # save register $t1 for use afterwards
            sw      $t0, 4($sp)         # save register $t0 for use afterwards
            sw      $s0, 0($sp)         # save register $s0 for use afterwards
```
