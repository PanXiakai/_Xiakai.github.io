---
layout: post
title: MIPS Assembly(5)
subtitle: Examples of MIPS
description: Several MIPS program from Internet
author: Xiakai
date: 2020-05-16
tags:
  - MIPS
---

## Example1: A C Sort Example to Put It All Together

- Swap procedure

  - Original C Program

    ```C
    void swap(int v[], int k) {
        int tmp;
        temp = v[k];
        v[k] = v[k+1];
        v[k+1] = v[k];
    }
    ```

  - Steps

    1. Allocate registers to program variables.
    2. Produce code for the body of the procedure.
    3. Preserve registers across the procedure invocation.

  - Register allocation for swap.

    - `$a0, $a1`: v, k
    - `$t0`: tmp

  - Code for the body of the procedure swap

    - v[k]: \$t1

      ```MIPS ASM
      sll $t1, $a1, 2
      add $t1, $t0, $t1
      ```

    - tmp = v[k]; v[k] = v[k+1]; v[k+1] = tmp

      ```MIPS ASM
      lw $t0, 0($t1)
      lw $t2, 4($t1)

      sw $t2, 0($t1)
      sw $t0, 4($t1)
      ```

- Sort procedure
