---
layout: post
author: Xiakai
date: 2020-05-12
title: MIPS Assembly(2)
subtitle: mipsProcedure
description: MIPS Procedure/Function
header-img: img/first-post.jpg
catalog:true
tags:
    - Assembly
    - procedure/function
---

## CS61C MIPS-Assembly-Language

## Computer organization and Design

> 2.8 Supporting Procedures in Computer Hardware

### Process of a program's execution

> _In the executin of a procedure, the program must follow these six steps_

1. Put parameters in a place where the procedure can access them.
2. ransfer control to the procedure.
3. Acquire the storage resources needed for the procedure.
4. Perform the desired task.
5. Put the result value in a place where the calling program can access it.
6. Return control to the point of origin, since a procedure can be called from several points in a program.

### Register Assignment convention

> _MIPS software follows the following convention for procedure calling in allocating its 32 registers_

1. `$a0-$a3`: four argument registers in which to pass parameters
2. `$v0-$v1`: two value register in whiVisualch to return values
3. `$ra`: one return address register to return to the point of origin.

### Address of Program/Procedure

In addition to allocating these registers, MIPS assembly language includes an instruction just for the procedures and simutaneously saves the address of the following instruction in register `$ra`, the jump-and-link instrcution(jal) is simply written as: **_jal ProcedureAddress_**, the link is stored in register `$ra`(register 31), is called the return address. The return address is needed because the same procedure counld be called from several parts of the program.
To support this situation, computers like MIPS use jump register instruction (jr), introduced above to help
with case statements, meaning an unconditional jump to the address specified in a register: jr \$ra.

### A Procedure Calling

- The calling program or _caller_, puts the parameter values in `$a0-$a3`.
- The caller uses `jal` to jump `X` to prcedure `X`(callee).
- The callee performs the calculations, place the results in `$v0` and `$v1`.
- Return control of the caller using jr \$jr.

### Instruction Address Register (Program Counter)

> The `jal` instruction actually saves `PC+4` in register `$ra` to a link to the following instruction to set up the procedure return.

## TODO

1. 将此文档添加到博客，以 CS61C 为主题。**_DONE_**
2. 将 Code 添加到文件夹打开方。**_DONE_**
   1. 解决方法：
      1. 打开注册表：`Win+R`,`Enter`,输入`regedit`,`Enter`
      2. 新建项：在`HKEY_CLASSES_ROOT\*\shell`(for file)或`HKEY_CLASSES_ROOT\Directory\shell`(for directory)下新建`VisualStudioCode`项（鼠标右键，新建项）
      3. 设定项：双击右侧窗口首行`默认`，输入`用首行打开`；新建`可扩充字符串值`，命名为`Icon`，双击，填入`code.exe`的绝对路径`path`。
      4. 新建`Command`项，双击右侧窗口，填入路径和打开方式-`"path" "%1"`(for file)或`"path" "%V"`(for directory)。
   2. Tip: 在命令行获取可执行文件(.exe)路径的命令，`_where *.exe_`。
