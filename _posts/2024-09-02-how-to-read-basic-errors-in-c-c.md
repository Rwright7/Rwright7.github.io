---
layout: post
title: How to read basic errors in C/C++
date: 2024-09-02 20:56 -0400
---

# Errors Presented in the Console

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

The art of learning how to program is to be patient with yourself and breaking down the problem as simple as they need to be and no more simpler. The above code is a snippet a friend shared with me asking why is it not working as it should be. 

If one using text editors like _**Sublime Text Editor**_, _**Visual Studio Code**_, _**Atom**_, _**Notepad++**_, _**JetBrains IDEs**_ etc etc. And install the necessary packages for syntax highlighting, formatter the whole nine yards.

But what im referring to specifically is called a **_linter_**

> Sublime Text: Use SublimeLinter and appropriate C++ linter plugins.

> VS Code: Use the C/C++ extension by Microsoft.

> JetBrains IDEs: Built-in error detection and suggestions.

> Atom: Use linter and appropriate linter plugins like linter-clang.

what i have installed on my _**Sublime Text Editor**_  specifically is called  _**LSP-Clangd**_.  What is that you may ask? simply put it gives me access to powerful features like real-time error detection, code completion, and other language server functionalities for C and C++.

I initially started using  **_Vim_**  to program, but as projects got large and large somethings in  _**Vim**_  as a beginner was hard to manage, then my mentor advise me to use  _**Sublime Text Editor**_  which proved to be very good, then i installed  _**LSP-Clangd**_.

Without  _**LSP-Clangd**_  installed the beginner wouldn't realise that they misspelled  _**namespace**_  and instead they have  _**namespeace**_.  which led to the error of  _cout_  and  _cin_  not being recognize.

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
> test.cpp:2:7: error: using declaration requires a qualified name
using namespeace std;

how do you read it well. for starters, we know that _**test.cpp**_ is our file name. we know that _**2:7**_ is read as _**line two (2): column seven(7)**_, then we have _**error**_ plastered in _red_.

It reads _"using declaration requires a qualified name"_
then it points a green arrow right under _"namespeace"_ where it is spelt incorrectly. Now if that error was not clear enough, i dont know what is or could be. 

1) Once you knew what _"Declaration"_ meant it should hit right away.

What does _Declaration_ means ?

2) **The process of defining a variable, function, or other identifiers in a program, specifying its type and possibly initializing it.**

Now in my head what i would say to myself is the only variable, i have defined is an **_integer named val_**. so there's no way **_using namespeace std;_** could be see as a variable and instantly, i would just double check and realise the miss spelling, which happens. 

Second error reads:
error: use of undeclared identifer 'cout'; did you mean 'std:: cout'?

Well what is a _"identifier"_?

3) **The name you give to a variable, function, or other parts of your code so you can refer to them easily. It's like a label that helps you uniquely recognize and use those parts in your program.**

Instantly it clicks _"cout"_ is suppose to output the message to the user, not as an identifier nor variable. So let me try the suggesting in green and see what happens. 

# Sumamry

1) Read, Read, Read, Read; Never Stop!

2) Be Interested To Learn More!

3) Be Patient With Yourself And Try To Understand The Errors

4) Ask Yourself Why, Why, Why

5) Never Forget The Basics


_Post shall be revisted, till everything flows just right._

_It's okay for Now!!_



