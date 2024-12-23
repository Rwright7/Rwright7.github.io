---
layout: post
title: BrainFuck Interpreter
date: 2024-03-30 13:39 -0400
---

# What is Brain-Fuck ?

  - Brainfuck is simply a language that uses only eight simple commands to perform operations. Despite its odd name and appearance, it's a fully-functional programming language. The commands consist of symbols like '>' , '<' , '+' , '-',  '[', ']' , '.' and ',' which manipulate memory cells and data pointers.

### Example of what each operator does
  - '>' : Move the memory pointer to the right.
  - '<' : Move the memory pointer to the left.
  - '+' : Increment the value at the memory cell pointed to.
  - '-' : Decrement the value at the memory cell pointed to.
  - '[' : Start of a loop (executes code inside the loop while the current cell is not zero).
  - ']' : End of a loop (jumps back to the corresponding [ if the current cell is not zero).
  - ',' : Read one character of input into the current cell.
  - '.' : Output the character at the current cell.

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
  ## Previous Code Before Corrected!
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


### Issues with my initial LOOP_START
  They're things to note in my initial _LOOP_START_ for example:

  - The Linear scanning through the tokens to find the corresponding _LOOP_END_.
  - Manual tracking _depth_ and updating the _stack_pointer_.
  - As the nested loops increase then by default the checking loop depths also increases.

### Addressing issues in their own right

 - Linear scanning we can think of that just like how we would for a linear search. We all know linear search as one of the most basic searching algorithms, where it involves a step by step checking of each elements in the array. The  _loop_start_  linearly checks until the  _loop_end_  is found. By using what we fundamentally know about **linear search** and what a **nested loop** is one can see how it was not the best option.

 - Scanning process is move through each token one by one until the matching **LOOP_END** is found.
 - Increasing a depth counter when another **LOOP_START** is found and decreasing it when a **LOOP_END** is found.

### Manual Tracking
 - It's as simply as the nesting is the problem. Nested loops can be cumbersome in the nature that as the level of nesting increases, the number of operations grows exponentially. which can then lead to an algorithm being  inefficient for large inputs. Each loop start ('[') requires pushing to the stack and each loop end (']') requires popping from the stack and updating the bracket map. These operations involve multiple checks. 

### Nested Loops
 - Nested loops and Manual Tracking goes hand in hand. Nevertheless i've chosen to separate them and just continue onwards about the potiential dangers of nested loops especially in regards to my brainfuck code.

 - Each level of nesting adds another layer of logic that one needs to understand and manage.
 - Off-by-one errors, incorrect stack management, and other logical errors are more likely to occur and harder to spot.