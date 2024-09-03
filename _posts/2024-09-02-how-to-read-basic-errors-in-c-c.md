---
layout: post
title: How To Read Basic Errors In C/C++
date: 2024-09-02 20:56 -0400
---


```c++

#include <iostream>
using namespeace std;

int main()
{
	int val;
	cout<<"Enter a value:";
	cin>>val;
	cout<<"You have entered: "<<val;

	return 0;
}
```

The art of learning how to program is to be patient with yourself and to break down problems as simply as they need to be, but no simpler. The above code is a snippet a friend shared with me, asking why it is not working as it should. 

If one is using text editors like _**Sublime Text Editor**_, _**Visual Studio Code**_, _**Atom**_, _**Notepad++**_, or _**JetBrains IDEs**_, etc., and installs the necessary packages for syntax highlighting, formatting, and other tools, they will have everything they need.

What i'm referring to specifically is called a **_linter_**

>  Sublime Text: Use SublimeLinter and appropriate C++ linter plugins.

>  VS Code: Use the C/C++ extension by Microsoft.

>  JetBrains IDEs: Benefit from built-in error detection and suggestions.

>  Atom: Use linter with plugins like linter-clang.

I've got _**LSP-Clangd**_ installed on my _**Sublime Text Editor**_, and you might be wondering, 'What’s that?' Well, simply put, it gives me access to awesome features like real-time error detection, code completion, and other powerful tools for C and C++.

I actually started out using _**Vim**_ for programming, but as my projects grew larger, managing things in **Vim** became a bit tricky, especially as a beginner. That’s when my mentor suggested I switch to _**Sublime Text Editor**_, and it turned out to be a great move. After that, I installed **LSP-Clangd**, and it’s been a game changer.

Without _**LSP-Clangd**_, a beginner might not even notice if they accidentally misspell namespace as _**namespeace**_. And that’s when you run into those frustrating errors where **cout** and **cin** aren’t recognized.

What is the function of _**using namespace std**_   ?

We are keeping everything friendly. The _**using namespace std;**_ directive in C++ allows you to use all the elements in the **_standard namespace (such as cout, cin, and string)_** without having to prefix them with _**std::**_. 

It simplifies the code by eliminating the need to write std:: repeatedly, making it more readable, especially for beginners.

_However, in larger projects, it’s generally better to avoid using it at a global level to prevent naming conflicts and maintain clearer, more maintainable code._


# Code above errors when program is executed
![Program Error Displayed In Console](/images/ProgramError1.jpeg)

It is my belief that upon learning programming, one is taught or one should be taught the common names such as:

- Declaration
- Identifier
- Variable
- Function (or Method)
- Expression
- Statement
- Loop
- Condition (or Conditional Statement)
- Array
- Algorithm

Just by knowing the above you're very much on your journey. By looking at the Screenshot of the console where the program above was executed, we see a list of errors. lets attack them one by one.

First error reads:
> `test.cpp:2:7: error: using declaration requires a qualified name
using namespeace std;`

So, how do you read this? Well, for starters, we know that _**test.cpp**_ is our file name. Then, **2:7** is read as _**line two (2), column seven (7)**_. After that, we see _**error**_ plastered in red—definitely something to pay attention to!

Now, moving on to the second part of the statement: _'using declaration requires a qualified name.'_ There is a green arrow right under namespeace, where it's spelled incorrectly. If that error wasn’t clear enough, I don’t know what is or could be!

### 1) Understanding “Declaration”

**What does "Declaration" mean?**

- The process of defining a variable, function, or other identifier in a program, specifying its type and possibly initializing it.

Now, in my head, I would remind myself: "The only variable I've defined is an integer named `val`. There's no way `using namespeace std;` could be seen as a variable." This would prompt me to double-check and quickly realize the misspelling, which happens to everyone.

### 2) Second Error: `error: use of undeclared identifier ‘cout’; did you mean ‘std::cout’?`

**Well, what is an "identifier"?**

- The name you give to a variable, function, or other parts of your code so you can refer to them easily. It’s like a label that helps you uniquely recognize and use those parts in your program.

It immediately clicks: "`cout` is supposed to output the message to the user, not act as an identifier or variable." So, I would try the suggestion in green and see what happens.

# Summary

- **Patience and Problem-Solving**: Programming requires patience and the ability to break down problems into simple, manageable parts.

- **Using `namespace std;`:**
  - Simplifies code by avoiding `std::` prefixes.
  - Better to avoid at the global level in larger projects to prevent naming conflicts.

- **Basic Programming Concepts**: Important to learn terms like Declaration, Identifier, Variable, Function, Expression, Statement, Loop, Condition, Array, and Algorithm.

- **Analyzing Errors:**
  - **Disclaimer**: While reading the file name, line, and column can be helpful, what's really necessary is understanding everything from `error:` onwards. For simple problems, just by understanding basic terminology, you'll be able to solve the majority of beginner issues.
  
  - **First Error**: `test.cpp:2:7: error: using declaration requires a qualified name using namespeace std;`.
    - Understand the error by identifying the misspelling of `namespeace`.
    
  - **Second Error**: `error: use of undeclared identifier ‘cout’; did you mean ‘std::cout’?`.
    - Recognize `cout` should output the message, not act as an identifier, and try the suggested correction.