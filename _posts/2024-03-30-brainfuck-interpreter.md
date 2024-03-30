---
layout: post
title: BrainFuck Interpreter
date: 2024-03-30 13:39 -0400
---

# What is Brain-Fuck ?

  - Brainfuck is simply a language that uses only eight simple commands to perform operations. Despite its odd name and appearance, it's a fully-functional programming language. The commands consist of symbols like '>' , '<' , '+' , '-',  '[', ']' , '.' and ',' which manipulate memory cells and data pointers.

### Example of what each operator does
  - >: Move the memory pointer to the right.
  - <: Move the memory pointer to the left.
  - +: Increment the value at the memory cell pointed to.
  - -: Decrement the value at the memory cell pointed to.
  - [: Start of a loop (executes code inside the loop while the current cell is not zero).
  - ]: End of a loop (jumps back to the corresponding [ if the current cell is not zero).
  - ,: Read one character of input into the current cell.
  - .: Output the character at the current cell.