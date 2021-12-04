---
title: GDB note
date: 2021-12-03 15:37:39
tags: linux
categories: coding
---

# GDB Usage

## Breakpoint

Use **info breakpoints** to view all breakpoints. There are various way to setup breakpoints

- using line number, **b 9**
- using function name, **b func**
- set the breakpoints if some conditions are satisfied. **break test.c:23 if b==0**, and use **condition** to set the variables
- set the breakpoints according to some custom rules. **rbreak**
- temporary breakpoints. **tbreak**
- ignore breakpoints for sometimes. **ignore 1 30**, ignore breakpoint 1 for 30 times.
- **disable**, **enable**, **clear**, **delete** breakpoints.

## Watch Variables

After we setup breakpoints and run the program, we need to watch the values of variables to locate the bugs and debug. When we reach certain breakpoints, we can check the variables as follows

- **print**: print ordinary variables such as scalars, arrays or strings. We can also print out variables that belong to certain functions or source code files via **p 'testGdb.h'::a**
- for pointer, **p d** will output the address only, **p *d** will give us the value. However, for array, it will output the first element only, please use **p *d@n** to print out **n** elements.
- **display**: print out certain variables everytime breakpoint is encountered. 
- **info display**: show variables that are be marked with **display**. 
