---
layout: post
title: Programming Environment
date: 2024-01-11 17:39 -0500
---

# Programming Environment Setup

## C Programming on macOS

### 1. Open Terminal:

   - Press `Cmd + Space` to open Spotlight Search.
   - Type `Terminal` and hit `Return` to open the Terminal.

### 2. Check for Existing Installation:

   ```bash
   gcc --version
   ```

![image-description](/Users/roshawnw/photoweb.jpeg)
_Example above for checking compiler version_

If `gcc` is not installed, the system will prompt you to install the Command Line Tools.

### 3. Install Command Line Tools:

   ```zsh
    ~ % xcode-select --install
   ```

`xcode-select --install` command will open a dialog window for installation of the command 
 line tools. 

 - Click 'Yes' and follow the on screen instructions to finish installing. 

 ### 4. Write and Compile a C Program:

 - Use any text editor to write a C program (e.g., hello.c).
 - Open Terminal and navigate to the file's directory.
 - Compile the program using:

   ```bash
   gcc -o hello hello.c
   ```

  - Execute the compiled program:

```bash
  ./hello
  ```
