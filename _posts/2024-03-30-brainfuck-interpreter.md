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

### Brain-Fuck code showing two different approach for handling loops in an Brainfuck Interpreter
  Now the conventional way and conventional meaning the way i have seen a few persons do it. Few because i can't possibly view every brainfuck interpreter project on Github. But the way that i have seen is a **Loop Table** created using a stack. for example the code below:

  ```c
  void precomputeBrackets(const BrainfuckComm tokens[], int numTokens, int bracketMap[]) {
	int stack[MAX_CODE_LENGTH];
	int stackPointer = -1;

	for (int i = 0; i < numTokens; i++) {
		if (tokens[i] == LOOP_START) {
			stack[++stackPointer] = i;
		} else if (tokens[i] == LOOP_END) {
			if (stackPointer < 0) {
				fprintf(stderr, "Error: Unmatched closing bracket.\n");
				exit(EXIT_FAILURE);
			}
			int startIndex = stack[stackPointer--];
			bracketMap[startIndex] = i;
			bracketMap[i] = startIndex;
		}
	}
	if (stackPointer >= 0) {
		fprintf(stderr, "Error: Unmatched opening bracket.\n");
		exit(EXIT_FAILURE);
	}
}
```
  Above is how i did it after trying to get the code below to work, which is my initial code
  ```c
  case LOOP_START:
	  if (*ptr == 0) {
		  int depth = 1;
		  while (depth > 0) {
			  i++;
				if (i >= numTokens) {  // added check
				fprintf(stderr, "Error: Reached end of tokens array without finding matching LOOP_END.\n");
				exit(EXIT_FAILURE);
		  }
		  if (tokens[i] == LOOP_START) {
				depth++;
			  } else if (tokens[i] == LOOP_END) {
				depth--;
			  }
		  }
		} else {
		  loop_stack[++stack_pointer] = i;
		}
		break;
```

```c
case LOOP_END:
	if (stack_pointer < 0) {  //added check
		fprintf(stderr, "Error: LOOP_END encountered without matching LOOP_START.\n");
		exit(EXIT_FAILURE);
	  }
	  if (*ptr != 0) {
		  i = loop_stack[stack_pointer] - 1; // Set i to just before LOOP_START to re-evaluate the loop
	  } else {
		  stack_pointer--;
	  }
	  break;
	  default:
		  fprintf(stderr, "Error: Unknown command encountered.\n");
		   exit(EXIT_FAILURE);
			break;
```

### Issues with my initial code (LOOP_START and LOOP_END)
  They're things to note 
