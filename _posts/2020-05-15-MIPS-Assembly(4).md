---
layout: post
title: MIPS Assembly(4)
subtitle: MIPS Stack(2)
author: Xiakai
date: 2020-05-14
description: SP and Nested Procedure
tags:
  - Assembly
  - Stack
  - Nested Procedure
---

## An example of leaf procedure(continuation)

![stack-of-leaf_example](leaf_example.png "Stack")

- Procedures that not call others are called leaf procedures.
- MarkDown 图片插入语法：`![Alt text](图片链接 "optional title")`

### **Original C program**

```C
int leaf_example (int g, int h, int i, int j)
{
    int f;
    f = (g + h) – (i + j);
    return f;
}
```

- _The parameter variables `g, h, i, j` corresponds to the argument registers `$a0, $a1, $a2, $a3`; `f` corresponds to `$s0`; the compiled program starts with the label of the procedure:_

### Body of procedure

```MIPS ASM
add $t0, $a0, $a1   # $t0 contains g + h
add $t1, $a2, $a3   # $t1 contains i + j
sub $s0, $t0, $t1   # $f = $t0 - $t1
```

### Store the return value

```MIPS ASM
add $v0, $s0, 0    # returns f ($s0 = $s0 + 0)
```

### Restore the arguments by popping them from stack

```MIPS ASM
lw $s0, 0($sp)
lw $t0, 4($sp)
lw $t1, 8($sp)
addi $sp, $sp, 12     # adjust stack to delete 3 items
```

### End procedure

```MIPS ASM
jr $ra    # jump back to calling routine
```

### _All MIPS Code_

```MIPS ASM
  leaf_example:
              addi    $sp, $sp, -12       # adjust stack to make room for 3 items
              sw      $t1, 8($sp)         # save register $t1 for use afterwards
              sw      $t0, 4($sp)         # save register $t0 for use afterwards
              sw      $s0, 0($sp)

              add $t0, $a0, $a1           # $t0 contains g + h
              add $t1, $a2, $a3           # $t1 contains i + j
              sub $s0, $t0, $t1           # $f = $t0 - $t1

              add $v0, $s0, 0             # returns f ($s0 = $s0 + 0)

              lw $s0, 0($sp)
              lw $t0, 4($sp)
              lw $t1, 8($sp)
              addi $sp, $sp, 12           # adjust stack to delete 3 items

              jr $ra                      # jump back to calling routine
```

## An Example of Nested Procedure

> Recursive procedures invoke other procedures including itself

### Original C program

```C
int fact (int n)
{
  if (n < 1) return (1);
  else return (n * fact(n – 1));
}
```

### MIPS Codes

- Use stack to reserve return-address and argument

  ```MIPS ASM
  fact:
        addi  $sp, $sp, -8        # adjust stack for 2 items
        sw    $ra, 4($sp)         # save the return address
        sw    $a0, 0($sp)         # save the argument n
  ```

- Compare and execute

  > The first time fact is called, sw saves an address in the program that called fact. Th e next two instructions test whether n is less than 1, going to L1 if n ≥ 1.

  ```MIPS ASM
        slti  $t0, $a0, 1       # test for n < 1: if $n < 1, $t0 = 1, if n >= 1, $t0 = 0
        beq   $t0, $zero, L1    # if n >= 1, goto L1
  ```

- Base condition

  > If n is less than 1, fact returns 1 by putting 1 into a value register: it adds 1 to 0 and places that sum in `$v0`. It then pops the two saved values off the stack and jumps to the return address:

  ```MIPS ASM
        addi  $v0, $zero, 1   # return 1
        addi  $sp, $sp, 8     # pop 2 items off stack
        jr    $ra             # return to caller
  ```

  > Before popping two items off the stack, we could have loaded \$a0 and `$ra`. Since `$a0` and `$ra` don’t change when n is less than 1, we skip those instructions

- L1

  > If n is not less than 1, the argument n is decremented and then fact is called again with the decremented value:

  ```MIPS ASM
  L1:   addi    $a0, $a0, -1    # n >= 1, n := n - 1
        jal     fact            # call fact with n - 1
  ```

  > The next instruction is where fact returns. Now the old return address and old argument are restored, along with the stack pointer:

  ```MIPS ASM
        lw      $a0, 0($sp)     # return from jal: restore argument n
        lw      $ra, 4($sp)     # restore the return address
        addi    $sp, $sp, 8     # adjust stack pointer to pop items
  ```

  > Next, the value register $v0 gets the product of old argument $a0 and the current value of the value register.

  ```MIPS ASM
        mul     $v0, $a0, $v0   # return n * fact(n - 1)
  ```

  > Finally, fact jumps again to the return address:

  ```MIPS ASM
        jr      $ra
  ```
