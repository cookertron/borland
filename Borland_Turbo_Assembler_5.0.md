# Turbo Assembler User's Guide

**Borland® Turbo Assembler®**

Borland International, Inc.  
100 Borland Way  
P.O. Box 660001, Scotts Valley, CA 95067-0001

---

**COPYRIGHT © 1988, 1996 Borland International. All rights reserved.**

All Borland product names are trademarks or registered trademarks of Borland International, Inc. Other brand and product names are trademarks or registered trademarks of their respective holders.

---

## Table of Contents

- [Introduction](#introduction)
- [Chapter 1: Getting Started with Turbo Assembler](#chapter-1-getting-started-with-turbo-assembler)
- [Chapter 2: Using Directives and Switches](#chapter-2-using-directives-and-switches)
- [Chapter 3: General Programming Concepts](#chapter-3-general-programming-concepts)
- [Chapter 4: Creating Object-Oriented Programs](#chapter-4-creating-object-oriented-programs)
- [Chapter 5: Using Expressions and Symbol Values](#chapter-5-using-expressions-and-symbol-values)
- [Chapter 6: Choosing Processor Directives and Symbols](#chapter-6-choosing-processor-directives-and-symbols)
- [Chapter 7: Using Program Models and Segmentation](#chapter-7-using-program-models-and-segmentation)
- [Chapter 8: Defining Data Types](#chapter-8-defining-data-types)
- [Chapter 9: Setting and Using the Location Counter](#chapter-9-setting-and-using-the-location-counter)
- [Chapter 10: Declaring Procedures](#chapter-10-declaring-procedures)
- [Chapter 11: Controlling the Scope of Symbols](#chapter-11-controlling-the-scope-of-symbols)
- [Chapter 12: Allocating Data](#chapter-12-allocating-data)
- [Chapter 13: Advanced Coding Instructions](#chapter-13-advanced-coding-instructions)
- [Chapter 14: Using Macros](#chapter-14-using-macros)
- [Chapter 15: Using Conditional Directives](#chapter-15-using-conditional-directives)
- [Chapter 16: Interfacing with the Linker](#chapter-16-interfacing-with-the-linker)
- [Chapter 17: Generating a Listing](#chapter-17-generating-a-listing)
- [Chapter 18: Interfacing Turbo Assembler with Borland C++](#chapter-18-interfacing-turbo-assembler-with-borland-c)
- [Appendix A: Program Blueprints](#appendix-a-program-blueprints)
- [Appendix B: Turbo Assembler Syntax Summary](#appendix-b-turbo-assembler-syntax-summary)
- [Appendix C: MASM 6.1 Compatibility](#appendix-c-masm-61-compatibility)
- [Appendix D: Error Messages](#appendix-d-error-messages)

---

## Introduction

Welcome to Borland's Turbo Assembler, a multi-pass assembler with forward-reference resolution, assembly speeds of up to 48,000 lines per minute (on an IBM PS/2 model 60), Microsoft Macro Assembler (MASM) compatibility, and an optional Ideal mode extended syntax. Whether you're a novice or an experienced programmer, you'll appreciate these features and others we've provided to make programming in assembly language easier.

### Key Features

- Object-oriented programming capabilities
- 32-bit model and stack frame support
- Full 386, i486, and Pentium support
- Simplified segmentation directives
- Table support
- Enumerations
- Smart flag instructions
- Fast immediate multiply operation
- Multiline definition support
- VERSION specification directive
- Nested directives
- Quirks mode to emulate MASM
- Full source debugging output
- Cross-reference utility (TCREF)
- Configuration and command files
- File converter utility (converts C `.h` files to TASM `.ash` files)
- Procedure prototyping and argument checking capabilities
- Alias support
- Windows 95 flat thunking support

Turbo Assembler is a powerful command-line assembler that takes your source (`.ASM`) files and produces object (`.OBJ`) modules. You then use `TLINK.EXE`, Borland's high-speed linker program, to link your object modules and create executable (`.EXE`) files.

### New Features in Version 5.0

Turbo Assembler version 5.0 incorporates the following new feature enhancements:

- Enhanced MASM compatibility, as described in "MASM 6.1 compatibility"
- Windows 95 flat thunking support with the `/utthk` command-line option

### Hardware and Software Requirements

Turbo Assembler generates instructions for the 8086, 80186, 80286, 80386, i486, Pentium, and Pentium Pro, and compatible processors. Turbo Assembler runs on all Intel-processor based computers, including all true compatibles. Turbo Assembler also generates floating-point instructions for the 8087, 80287, and 80387 numeric coprocessors.

### About the Manuals

Turbo Assembler comes with the *Turbo Assembler User's Guide* (this book) and the *Turbo Assembler Quick Reference Guide*. The User's Guide provides basic instructions for using Turbo Assembler, explores how to interface Turbo Assembler with other languages, and describes in detail the operators, predefined symbols, and directives Turbo Assembler uses.

### Typographic Conventions

| Typeface | Usage |
|----------|-------|
| *Italics* | Labels, placeholders, variables, and arrays. In syntax expressions, placeholders indicate user-defined items. |
| **Boldface** | Directives, instructions, symbols, operators, and command-line options. |
| CAPITALS | Instructions, directives, registers, and operators in text. |
| `Monospace` | Sample code, screen output, and text you must type. |
| Keycaps | Keys on your keyboard (e.g., "Press Enter"). |

### Software Registration and Technical Support

The Borland Assist program offers a range of technical support plans to fit the different needs of individuals, consultants, large corporations, and developers. North American customers can register by phone 24 hours a day by calling 1-800-845-0147.

---

## Chapter 1: Getting Started with Turbo Assembler

You might have heard that programming in assembly language is a black art suited only to hackers and wizards. However, assembly language is nothing more than the human form of the language of the computer. And, as you'd expect, the computer's language is highly logical. Assembly language is very powerful—in fact, assembly language is the only way to tap the full power of the Intel 80x86 family, the processors at the heart of the IBM PC family and compatibles.

You can write whole programs using nothing but assembly language or you can mix assembly language with programs written in high-level languages such as Borland C++ and Borland Pascal. Either way, assembly language lets you write small and blindingly fast programs.

### Installing Turbo Assembler

The Turbo Assembler package consists of a set of executable programs, utilities, and example programs. For instructions on installing Turbo Assembler, refer to the `TSM_INST.TXT` file on your installation disk:

1. Insert the TASM Install disk in drive A of your computer.
2. Use your text editor to open `TSM_INST.TXT`, or issue the following command at the command line:
   ```
   TYPE A:TSM_INST.TXT | MORE
   ```

### The Turbo Assemblers

| Assembler | Description |
|-----------|-------------|
| `TASM.EXE` | Real mode assembler |
| `TASM32.EXE` | Protected mode assembler |

### Writing Your First Turbo Assembler Program

Here's a sample program (`HELLO.ASM`) that demonstrates basic assembly language programming:

```asm
; HELLO.ASM - A "Greetings, World!" program

        DOSSEG
        .MODEL small
        .STACK 100h
        .DATA

GoodMorningMessage    DB 'Good morning, World!',13,10,'$'
GoodAfternoonMessage  DB 'Good afternoon, World!',13,10,'$'
DefaultMessage        DB 'Greetings, World!',13,10,'$'
TimePrompt            DB 'Is it after noon (Y/N)?$'

        .CODE
start:
        mov ax,@data
        mov ds,ax

        ; Display time prompt
        mov ah,9
        mov dx,OFFSET TimePrompt
        int 21h

        ; Get a single-character response
        mov ah,1
        int 21h

        ; Force character to lowercase
        or al,20h

        ; Check response
        cmp al,'y'
        je IsAfternoon
        cmp al,'n'
        je IsMorning

        mov dx,OFFSET DefaultMessage
        jmp DisplayGreeting

IsAfternoon:
        mov dx,OFFSET GoodAfternoonMessage
        jmp DisplayGreeting

IsMorning:
        mov dx,OFFSET GoodMorningMessage

DisplayGreeting:
        mov ah,9
        int 21h
        mov ah,4ch
        mov al,0
        int 21h

        END start
```

### Assembling Your First Program

To assemble `HELLO.ASM`, type the following at the command line:

```
TASM hello
```

If you entered the program correctly, you'll see output similar to:

```
Turbo Assembler Version 5.0 Copyright (c) 1988, 1996 by Borland International, Inc.
Assembling file: HELLO.ASM
Error messages: None
Warning messages: None
Passes: 1
Remaining memory: 439K
```

### Linking Your First Program

After successfully assembling, link the program using TLINK:

```
TLINK hello
```

If no errors are reported, an executable file `HELLO.EXE` is created. To run the program, enter `HELLO` at the command line.

### Recommended Reading

- Hummel, Robert L. *Programmers Technical Reference: Processor and coprocessor.* Emeryville, CA: Ziff Davis Press, 1992.
- Mischel, Jim. *Macro Magic with Turbo Assembler.* New York, NY: John Wiley & Sons, 1993.
- Swan, Tom. *Mastering Turbo Assembler, Second Edition.* Indianapolis, IN: Sams Publishing, 1995.
- Yao, Paul. *Borland C++ 4.0 Programming for Windows.* New York, NY: Random House, Inc., 1994.

Intel Corporation offers fact sheets and reference manuals:

> Intel Literature Sales  
> P.O. Box 7641  
> Mount Prospect, IL 60056-7641  
> 1 (800) 548-4725

---

## Chapter 2: Using Directives and Switches

This chapter describes Turbo Assembler's command-line options and how to control the assembler's behavior.

### Starting Turbo Assembler

If you start Turbo Assembler without arguments:

```
TASM
```

You'll see a help screen describing command-line options and syntax.

### Command-Line Syntax

The general form of the command line:

```
TASM [options] source [,object] [,listing] [,xref]
```

You can assemble multiple file groups by separating them with semicolons:

```
TASM /e FILE1; /a FILE2
```

### Wildcard Support

To assemble all `.ASM` files in the current directory:

```
TASM *
```

To assemble multiple specific files:

```
TASM MYFILE1 + MYFILE2
```

### Command-Line Options

#### `/a` — Alphabetical Segment Ordering

Tells Turbo Assembler to place segments in the object file in alphabetical order. Same as the `.ALPHA` directive.

```
TASM /a TEST1
```

#### `/c` — Cross-Reference in Listing

Enables cross-reference information in the listing file.

```
TASM /l /c TEST1
```

#### `/d` — Define Symbol

Defines a symbol for your source file:

```
TASM /dMAX=10 /dMIN=2 TEST1
```

#### `/e` — Floating-Point Emulator Instructions

Generates floating-point instructions for software emulation:

```
TASM /e SECANT
```

#### `/h` or `/?` — Help Screen

Displays the help screen.

#### `/i` — Include Path

Specifies directories to search for include files:

```
TASM /iC:\INCLUDE TEST1
```

#### `/j` — Jam Directive

Inserts an assembler directive at the start of assembly:

```
TASM /jIDEAL TEST1
```

#### `/kh#` — Hash Table Capacity

Sets the hash table capacity for symbols.

#### `/l` — Generate Listing

Creates a listing file:

```
TASM /l TEST1
```

#### `/la` — Expanded Listing

Creates an expanded listing with additional detail.

#### `/m#` — Multiple Passes

Allows multiple passes to resolve forward references:

```
TASM /m2 TEST1
```

#### `/ml` — Case Sensitivity (All Symbols)

Treats all symbol names as case-sensitive:

```
TASM /ml TEST1
```

#### `/mu` — Convert to Uppercase

Converts all symbols to uppercase (default behavior).

#### `/mv#` — Maximum Symbol Length

Sets the maximum distinguishable symbol length:

```
TASM /mv12 TEST1
```

#### `/mx` — Case Sensitivity (Externals Only)

Treats only external and public symbols as case-sensitive:

```
TASM /mx TEST1
```

#### `/n` — Suppress Symbol Table

Suppresses the symbol table in listing files:

```
TASM /l /n TEST1
```

#### `/o` — Overlay Code for TLINK

Generates overlay-compatible fixups for TLINK.

#### `/oi` — Overlay Code for IBM Linker

Generates overlay-compatible fixups for the IBM linker.

#### `/op` — Overlay Code for Phar Lap

Generates overlay-compatible fixups for the Phar Lap linker.

#### `/os` — Standard Objects (Default)

Outputs TLINK-compatible objects without overlay support.

#### `/p` — Protected Mode Check

Warns about impure code in protected mode:

```
TASM /p TEST1
```

#### `/q` — Suppress OBJ Records

Removes copyright and file dependency records from `.OBJ` files.

#### `/r` — Real Floating-Point Instructions

Generates real floating-point instructions (for 80x87 coprocessors):

```
TASM /r SECANT
```

#### `/s` — Sequential Segment Ordering

Specifies sequential segment ordering (default).

#### `/t` — Suppress Messages

Suppresses messages if assembly is successful.

#### `/u` — Version Emulation

Sets version emulation mode:

```
TASM /uM510 TEST1
```

#### `/w` — Warning Level

Controls warning message display:
- `/w0` — No warnings
- `/w1`, `/w2` — Warnings enabled
- `/w-xxx` — Disable specific warning
- `/w+xxx` — Enable specific warning

#### `/x` — Include False Conditionals

Includes false conditionals in the listing file.

#### `/z` — Display Source with Errors

Displays source lines with error messages.

#### `/zi` — Full Debug Info

Generates full debug information.

#### `/zd` — Line Numbers Only

Generates line number debug information only.

#### `/zn` — No Debug Info

Suppresses debug information.

### Indirect Command Files

You can place command-line options in a file and reference it with `@`:

```
TASM @MYOPTS.CFG TEST1
```

### The Configuration File

Turbo Assembler automatically reads `TASM.CFG` from the current directory or the directory containing `TASM.EXE`.

---

## Chapter 3: General Programming Concepts

This chapter discusses the differences between Ideal and MASM modes, predefined symbols, comment characters, and more.

### Turbo Assembler Ideal Mode

Ideal mode provides enhanced syntax with better type checking and clearer expression handling.

#### Why Use Ideal Mode?

- Stricter type checking catches errors at assembly time
- Clearer syntax for expressions and operands
- More consistent bracket notation
- Better handling of segments and groups

#### Entering and Leaving Ideal Mode

```asm
IDEAL           ; Switch to Ideal mode
; ... Ideal mode code ...
MASM            ; Switch back to MASM mode
```

### MASM and Ideal Mode Differences

#### Expressions and Operands

In Ideal mode, square brackets always refer to the contents of the enclosed quantity:

```asm
; MASM mode
mov ax,wordptr          ; Loads offset

; Ideal mode
mov ax,[wordptr]        ; Loads contents
mov ax,OFFSET wordptr   ; Loads offset
```

#### Operators

The period (`.`) structure member operator is stricter in Ideal mode:

```asm
; Declare variables using structure types
S_Stuff SomeStuff <>
O_Stuff OtherStuff <>

mov ax,[S_Stuff.Amount]   ; Load word value
mov bl,[O_Stuff.Amount]   ; Load byte value
```

### Commenting the Program

#### End-of-Line Comments

Use a semicolon (`;`) to start a comment that extends to the end of the line:

```asm
mov ax,bx    ; Copy BX to AX
```

#### The COMMENT Directive

For multi-line comments:

```asm
COMMENT *
This is a multi-line comment.
It can span several lines.
*
```

### Extending the Line

Use the backslash (`\`) to continue a line:

```asm
ARG a1:word, \    ; First argument
    a2:word, \    ; Second argument
    a3:word       ; Final argument
```

### Using INCLUDE Files

Include files let you reuse code across multiple modules:

**Ideal mode:**
```asm
INCLUDE "filename"
```

**MASM mode:**
```asm
INCLUDE filename
```

Include files can be nested to any depth.

### Predefined Symbols

Turbo Assembler provides predefined symbols:

| Symbol | Type | Description |
|--------|------|-------------|
| `??date` | String | Current date |
| `??time` | String | Current time |
| `??filename` | String | Current file name (8 characters) |
| `??version` | Numeric | Assembler version |
| `@code` | Alias | Current code segment |
| `@data` | Alias | Current data segment |
| `@curseg` | Alias | Current segment |
| `@FileName` | Alias | Current file name |

### Assigning Values to Symbols

#### The EQU Directive

Defines string, alias, or numeric equates:

```asm
name EQU expression
```

#### The = Directive

Defines numeric equates (can be redefined):

```asm
name = expression
```

### The VERSION Directive

Specifies assembler version compatibility:

```asm
VERSION T500    ; Turbo Assembler 5.0
```

Valid version IDs:

| ID | Version |
|----|---------|
| M400 | MASM 4.0 |
| M500 | MASM 5.0 |
| M510 | MASM 5.1 |
| M520 | MASM 5.2 (Quick ASM) |
| T100 | Turbo Assembler 1.0 |
| T200 | Turbo Assembler 2.0 |
| T300 | Turbo Assembler 3.0 |
| T400 | Turbo Assembler 4.0 |
| T500 | Turbo Assembler 5.0 |

### The NAME Directive

Sets the object file's module name (Ideal mode only):

```asm
NAME modulename
```

### The END Directive

Marks the end of the source file:

```asm
END [startaddress]
```

### Displaying Messages During Assembly

Use the `DISPLAY` or `%OUT` directives:

```asm
DISPLAY "Assembling main module..."
%OUT Assembling main module...
```

### Warning Messages

Control warning messages with the `WARN` and `NOWARN` directives:

```asm
WARN            ; Enable all warnings
NOWARN          ; Disable all warnings
WARN PRO        ; Enable specific warning
NOWARN PRO      ; Disable specific warning
```

---

## Chapter 4: Creating Object-Oriented Programs

This chapter describes how to use object-oriented programming techniques in assembly language.

### Terminology

| Term | Description |
|------|-------------|
| Object | A data type combining data and methods |
| Method | A procedure associated with an object |
| Instance | A specific occurrence of an object |
| Static method | Method resolved at compile time |
| Virtual method | Method resolved at run time |
| VMT | Virtual Method Table |
| Ancestor | Parent object in inheritance hierarchy |
| Descendant | Child object derived from another |

### Why Use Objects in Turbo Assembler?

- Better code organization
- Code reuse through inheritance
- Polymorphism through virtual methods
- Encapsulation of data and behavior

### What Is an Object?

An object combines:
- Data members (variables)
- Methods (procedures)
- Inheritance from ancestor objects

### Declaring Objects

#### Declaring a Base Object

```asm
list STRUC GLOBAL METHOD {
    construct:dword = list_construct    ; Constructor
    destroy:dword = list_destroy        ; Destructor
    init:dword = list_init              ; Initialization
    virtual insert:word = list_insert   ; Virtual method
    virtual delete:word = list_delete   ; Virtual method
}
list_head   dd ?    ; Head pointer
list_tail   dd ?    ; Tail pointer
ENDS
```

#### Declaring a Derived Object

```asm
queue STRUC GLOBAL list METHOD {
    virtual insert:word = queue_insert  ; Override
}
ENDS
```

### The Virtual Method Table

The VMT is a table of addresses for virtual method procedures. Create an instance with `TBLINST`:

```asm
INCLUDE list.aso
DATASEG
TBLINST         ; Create VMT instance
```

### Initializing the Virtual Method Table

Use `TBLINIT` in the initialization method:

```asm
list_init PROC PASCAL FAR
    ARG @@list:dword
    USES ds,bx

    lds bx,@@list
    TBLINIT ds:bx       ; Initialize VMT pointer
    ; ... initialize data ...
    ret
ENDP
```

### Calling Object Methods

#### Calling a Static Method

```asm
CALL foolist METHOD list:init pascal, ds offset foolist
```

#### Calling a Virtual Method

```asm
CALL es:di METHOD list:insert USES ds:bx pascal, es di, es dx, es cx
```

### Creating an Instance of an Object

```asm
foolist  list {}                                    ; Default instance
fooqueue queue {list_head=mynode,list_tail=mynode}  ; With overrides
```

### Programming Form for Objects

Recommended file organization:

- `<object>.ASO` — Object declaration with `INCLUDE` of parent, `GLOBAL` object declaration
- `<object>.ASM` — Method implementations with `INCLUDE` of `.ASO`, `TBLINST`, and method procedures

---

## Chapter 5: Using Expressions and Symbol Values

### Constants

#### Numeric Constants

A numeric constant starts with a digit (0-9). The radix determines its value:

| Radix | Valid Digits |
|-------|--------------|
| Binary | 0, 1 |
| Octal | 0-7 |
| Decimal | 0-9 |
| Hexadecimal | 0-9, A-F |

Suffix characters determine radix:

| Suffix | Radix |
|--------|-------|
| B | Binary |
| O, Q | Octal |
| D | Decimal |
| H | Hexadecimal |

Examples:
```asm
77d     ; 77 decimal
77h     ; 77 hexadecimal (119 decimal)
0FFFFh  ; FFFF hexadecimal
1010b   ; Binary (10 decimal)
```

#### Changing the Default Radix

**Ideal mode:**
```asm
RADIX expression
```

**MASM mode:**
```asm
.RADIX expression
```

#### String Constants

Strings are enclosed in single or double quotes:

```asm
DB 'Hello, World!'
DB "It's a test"
DB 'It''s a test'   ; Escaped quote
```

### Symbols

Symbols represent values: variables, labels, or operands.

#### Symbol Names

- Must start with a letter, underscore, `@`, or `?`
- Can contain letters, digits, underscores, `@`, `$`, `?`
- Maximum length depends on `/mv#` option

#### Symbol Types

| Type | Description |
|------|-------------|
| BYTE | 8-bit value |
| WORD | 16-bit value |
| DWORD | 32-bit value |
| FWORD | 48-bit value |
| QWORD | 64-bit value |
| TBYTE | 80-bit value |
| NEAR | Near pointer |
| FAR | Far pointer |

### Expressions

Expressions combine constants, symbols, and operators to produce values.

#### Unary Operators

| Operator | Description |
|----------|-------------|
| `LENGTH` | Number of elements |
| `SIZE` | Size in bytes |
| `WIDTH` | Width of record field |
| `MASK` | Bit mask for record field |
| `OFFSET` | Offset of symbol |
| `SEG` | Segment of symbol |
| `TYPE` | Type of expression |
| `HIGH` | High byte of word |
| `LOW` | Low byte of word |

#### Arithmetic Operators

| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `MOD` | Modulus |

#### Logical Operators

| Operator | Description |
|----------|-------------|
| `AND` | Bitwise AND |
| `OR` | Bitwise OR |
| `XOR` | Bitwise XOR |
| `NOT` | Bitwise NOT |

#### Shift Operators

| Operator | Description |
|----------|-------------|
| `SHL` | Shift left |
| `SHR` | Shift right |

#### Comparison Operators

| Operator | Description |
|----------|-------------|
| `EQ` | Equal |
| `NE` | Not equal |
| `LT` | Less than |
| `LE` | Less than or equal |
| `GT` | Greater than |
| `GE` | Greater than or equal |

---

## Chapter 6: Choosing Processor Directives and Symbols

### Processor Directives

| Directive | Processor |
|-----------|-----------|
| `.8086` | 8086/8088 |
| `.186` | 80186 |
| `.286` | 80286 |
| `.286P` | 80286 privileged |
| `.386` | 80386 |
| `.386P` | 80386 privileged |
| `.486` | i486 |
| `.486P` | i486 privileged |
| `.586` | Pentium |
| `.586P` | Pentium privileged |

### Predefined Symbols

| Symbol | Description |
|--------|-------------|
| `@Cpu` | Current processor type |
| `@WordSize` | Current word size (2 or 4) |

### Coprocessor Directives

| Directive | Coprocessor |
|-----------|-------------|
| `.8087` | 8087 |
| `.287` | 80287 |
| `.387` | 80387 |

### Coprocessor Emulation Directives

| Directive | Description |
|-----------|-------------|
| `EMUL` | Generate emulated FP instructions |
| `NOEMUL` | Generate real FP instructions |

---

## Chapter 7: Using Program Models and Segmentation

### The MODEL Directive

```asm
MODEL memory_model [, language] [, modifier]
```

#### Standard Memory Models

| Model | Code | Data | Description |
|-------|------|------|-------------|
| TINY | Near | Near | All in one segment (COM files) |
| SMALL | Near | Near | One code, one data segment |
| MEDIUM | Far | Near | Multiple code segments |
| COMPACT | Near | Far | Multiple data segments |
| LARGE | Far | Far | Multiple code and data |
| HUGE | Far | Far | Like LARGE with huge arrays |
| FLAT | Near | Near | 32-bit flat model |

### Symbols Created by MODEL

| Symbol | Description |
|--------|-------------|
| `@Model` | Current model type |
| `@32Bit` | Non-zero if 32-bit model |
| `@CodeSize` | 0=near, 1=far code |
| `@DataSize` | 0=near, 1=far data |
| `@Interface` | Language interface value |

### Simplified Segment Directives

| Directive | Creates |
|-----------|---------|
| `.CODE` | Code segment |
| `.DATA` | Initialized data segment |
| `.DATA?` | Uninitialized data segment |
| `.FARDATA` | Far initialized data |
| `.FARDATA?` | Far uninitialized data |
| `.CONST` | Constant data segment |
| `.STACK` | Stack segment |

### The SEGMENT Directive

```asm
name SEGMENT [align] [combine] [use] [class]
    ; ... segment contents ...
name ENDS
```

#### Alignment Attributes

| Attribute | Boundary |
|-----------|----------|
| BYTE | Any |
| WORD | 2-byte |
| DWORD | 4-byte |
| PARA | 16-byte (paragraph) |
| PAGE | 256-byte |

#### Combine Attributes

| Attribute | Description |
|-----------|-------------|
| PRIVATE | Not combined |
| PUBLIC | Combined with same-named segments |
| COMMON | Overlaid |
| STACK | Combined into stack segment |
| AT address | Placed at specific address |

### The GROUP Directive

```asm
name GROUP segment [, segment ...]
```

### The ASSUME Directive

```asm
ASSUME segreg:name [, segreg:name ...]
ASSUME NOTHING
```

### Segment Ordering

| Directive | Description |
|-----------|-------------|
| `.ALPHA` | Alphabetical order |
| `.SEQ` | Sequential order (default) |
| `DOSSEG` | DOS standard ordering |

---

## Chapter 8: Defining Data Types

### Defining Enumerated Data Types

```asm
name ENUM [size] {value [, value ...]}
```

Example:
```asm
colors ENUM {red, green, blue}
status ENUM byte {ok=0, error=1, warning=2}
```

### Defining Bit-Field Records

```asm
name RECORD field:width [=default] [, field:width [=default] ...]
```

Example:
```asm
fileflags RECORD readonly:1, hidden:1, system:1, reserved:5
```

### Defining Structures and Unions

#### Structure Definition

```asm
name STRUC
    member1  type  value
    member2  type  value
name ENDS
```

#### Union Definition

```asm
name UNION
    member1  type  value
    member2  type  value
name ENDS
```

#### Example

```asm
point STRUC
    x_coord  DW  0
    y_coord  DW  0
point ENDS

; Create instance
mypoint point <10, 20>
```

### Defining Tables

```asm
name TABLE [modifier] {
    [VIRTUAL] member:type = value
}
```

### Defining a Named Type

```asm
name TYPEDEF type
```

Example:
```asm
PBYTE TYPEDEF PTR BYTE
PWORD TYPEDEF PTR WORD
```

### The TBLPTR Directive

Places a virtual table pointer in a structure.

---

## Chapter 9: Setting and Using the Location Counter

### The `$` Location Counter Symbol

The `$` symbol represents the current location in the segment:

```asm
message  DB  'Hello, World!'
msglen   EQU $ - message    ; Calculate length
```

### The ORG Directive

Sets the location counter:

```asm
ORG 100h        ; For COM files
ORG $ + 10      ; Skip 10 bytes
```

### The EVEN and EVENDATA Directives

Align to word boundary:

```asm
EVEN            ; Align in code segment
EVENDATA        ; Align in data segment
```

### The ALIGN Directive

Align to specified boundary:

```asm
ALIGN 4         ; Align to DWORD
ALIGN 16        ; Align to paragraph
```

### Defining Labels

#### The `:` Operator

```asm
label:          ; Near label
label::         ; Global near label
```

#### The LABEL Directive

```asm
name LABEL type
```

Example:
```asm
bytevar  LABEL BYTE
wordvar  DW    1234h
```

---

## Chapter 10: Declaring Procedures

### Procedure Definition Syntax

```asm
name PROC [distance] [language] [visibility] [USES regs] [arguments]
    ; ... procedure body ...
    RET
name ENDP
```

### Declaring NEAR or FAR Procedures

```asm
myproc PROC NEAR
    ; Near procedure
    ret
myproc ENDP

myproc PROC FAR
    ; Far procedure
    ret
myproc ENDP
```

### Declaring a Procedure Language

```asm
myproc PROC PASCAL FAR
myproc PROC C NEAR
myproc PROC STDCALL
```

### Defining Arguments and Local Variables

```asm
myproc PROC NEAR
    ARG x:WORD, y:WORD
    LOCAL temp:WORD

    mov ax, x
    add ax, y
    mov temp, ax
    ret
myproc ENDP
```

### Preserving Registers

```asm
myproc PROC NEAR
    USES si, di, bx
    ; Registers automatically saved/restored
    ret
myproc ENDP
```

### Using Procedure Prototypes

```asm
PROCDESC name distance language [arguments]
```

---

## Chapter 11: Controlling the Scope of Symbols

### Redefinable Symbols

Use `=` to create symbols that can be redefined:

```asm
count = 0
count = count + 1
```

### Block Scoping

The `LOCALS` and `NOLOCALS` directives control local label scope:

```asm
LOCALS @@
; @@labels are local to current procedure

NOLOCALS
; Local labels disabled
```

### MASM Block Scoping

```asm
LOCALS          ; Enable local labels
label1:         ; Global label
@@temp:         ; Local label
```

---

## Chapter 12: Allocating Data

### Simple Data Directives

| Directive | Size | Description |
|-----------|------|-------------|
| `DB` | 1 | Define byte |
| `DW` | 2 | Define word |
| `DD` | 4 | Define doubleword |
| `DF` | 6 | Define fword |
| `DQ` | 8 | Define quadword |
| `DT` | 10 | Define tenbytes |

Examples:
```asm
byte1    DB    0
word1    DW    1234h
dword1   DD    12345678h
buffer   DB    100 DUP(0)
string   DB    'Hello', 0
```

### Creating Structure Instances

```asm
point1   point <10, 20>
point2   point {x_coord=5, y_coord=15}
point3   point {}        ; Use defaults
```

### Creating Record Instances

```asm
flags1   fileflags <1, 0, 0, 0>
flags2   fileflags {readonly=1}
```

---

## Chapter 13: Advanced Coding Instructions

### Intelligent Code Generation

```asm
SMART           ; Enable intelligent code generation
NOSMART         ; Disable
```

### Extended Jumps

SMART mode automatically extends conditional jumps beyond 128 bytes.

### Extended PUSH and POP

```asm
PUSH ax, bx, cx         ; Multiple pushes
POP cx, bx, ax          ; Multiple pops
```

### PUSHSTATE and POPSTATE

Save and restore assembler state:

```asm
PUSHSTATE
; ... change settings ...
POPSTATE
```

### Smart Flag Instructions

| Instruction | Description |
|-------------|-------------|
| `SETFLAG` | Set flag bits |
| `TESTFLAG` | Test flag bits |
| `FLIPFLAG` | Toggle flag bits |

### Field Value Instructions

| Instruction | Description |
|-------------|-------------|
| `SETFIELD` | Set record field value |
| `GETFIELD` | Get record field value |

### Calling Procedures with Stack Frames

```asm
CALL myproc C, arg1, arg2
CALL myproc PASCAL, arg1, arg2
```

---

## Chapter 14: Using Macros

### Text Macros

```asm
name EQU <text>
name TEXTEQU <text>
```

### String Macro Manipulation

| Directive | Description |
|-----------|-------------|
| `CATSTR` | Concatenate strings |
| `SUBSTR` | Extract substring |
| `INSTR` | Find substring |
| `SIZESTR` | Get string length |

### Multiline Macros

```asm
name MACRO [parameters]
    ; Macro body
ENDM
```

Example:
```asm
PUSHALL MACRO
    push ax
    push bx
    push cx
    push dx
ENDM
```

### Macro Parameters

```asm
ADD_VALUES MACRO val1, val2
    mov ax, val1
    add ax, val2
ENDM
```

### Local Labels in Macros

```asm
COMPARE MACRO val
    LOCAL done
    cmp ax, val
    je done
    ; ... code ...
done:
ENDM
```

### Repeat Macros

```asm
REPT count
    ; Repeated code
ENDM

IRP parameter, <list>
    ; Repeated for each item
ENDM

IRPC parameter, string
    ; Repeated for each character
ENDM
```

### The WHILE Directive

```asm
count = 0
WHILE count LT 10
    DB count
    count = count + 1
ENDM
```

---

## Chapter 15: Using Conditional Directives

### IF Directives

| Directive | Condition |
|-----------|-----------|
| `IF` | Expression is true (non-zero) |
| `IFE` | Expression is false (zero) |
| `IFDEF` | Symbol is defined |
| `IFNDEF` | Symbol is not defined |
| `IFB` | Argument is blank |
| `IFNB` | Argument is not blank |
| `IFIDN` | Strings are identical |
| `IFDIF` | Strings are different |

### Syntax

```asm
IF expression
    ; Assembled if true
ELSEIF expression
    ; Assembled if this is true
ELSE
    ; Assembled otherwise
ENDIF
```

### Error Generation Directives

| Directive | Description |
|-----------|-------------|
| `.ERR` | Generate error |
| `.ERRE` | Error if false |
| `.ERRNZ` | Error if true |
| `.ERRDEF` | Error if defined |
| `.ERRNDEF` | Error if not defined |
| `.ERRB` | Error if blank |
| `.ERRNB` | Error if not blank |
| `.ERRIDN` | Error if identical |
| `.ERRDIF` | Error if different |

---

## Chapter 16: Interfacing with the Linker

### Declaring Public Symbols

```asm
PUBLIC symbol [, symbol ...]
```

### Declaring External Symbols

```asm
EXTRN name:type [, name:type ...]
EXTERNDEF name:type [, name:type ...]
```

### Declaring Global Symbols

```asm
GLOBAL name:type [, name:type ...]
```

### Communal Variables

```asm
COMM [distance] name:type [:count] [, ...]
```

### Including Libraries

```asm
INCLUDELIB libraryname
```

### The ALIAS Directive

```asm
ALIAS <alias> = <actual>
```

---

## Chapter 17: Generating a Listing

### Listing Format

The listing file contains:
- Source lines with generated code
- Symbol table
- Cross-reference (if enabled)

### List Directives

| Directive | Description |
|-----------|-------------|
| `.LIST` | Enable listing |
| `.XLIST` | Disable listing |
| `.LFCOND` | List false conditionals |
| `.SFCOND` | Suppress false conditionals |
| `.TFCOND` | Toggle false conditional listing |

### Include File Listing

| Directive | Description |
|-----------|-------------|
| `.LALL` | List all macro lines |
| `.SALL` | Suppress macro listing |
| `.XALL` | List only code-generating lines |

### Cross-Reference Directives

| Directive | Description |
|-----------|-------------|
| `.CREF` | Enable cross-reference |
| `.XCREF` | Disable cross-reference |

### Format Parameters

| Directive | Description |
|-----------|-------------|
| `%TITLE` | Set listing title |
| `%SUBTTL` | Set listing subtitle |
| `%PAGE` | Start new page |
| `%PAGESIZE` | Set page dimensions |
| `%TABSIZE` | Set tab size |

---

## Chapter 18: Interfacing Turbo Assembler with Borland C++

### Calling Assembly Functions from C++

#### Basic Framework

**C++ code:**
```cpp
extern "C" int AsmFunction(int param);

int main() {
    int result = AsmFunction(42);
    return 0;
}
```

**Assembly code:**
```asm
.MODEL small, C
.CODE

PUBLIC AsmFunction
AsmFunction PROC C param:WORD
    mov ax, param
    ; ... processing ...
    ret
AsmFunction ENDP

END
```

### Memory Models and Segments

Match the memory model in assembly with the C++ compilation model.

### Underscore Convention

C functions have underscore prefixes. Use `/mx` to preserve case sensitivity.

### Parameter Passing

| Type | Size | Location |
|------|------|----------|
| char | 1 byte | On stack (word-aligned) |
| int | 2 bytes | On stack |
| long | 4 bytes | On stack |
| pointer | 2 or 4 bytes | Depends on model |

### Return Values

| Type | Register |
|------|----------|
| char, int | AX |
| long | DX:AX |
| pointer | AX (near) or DX:AX (far) |

### Preserving Registers

Preserve these registers: SI, DI, BP, DS, SS, SP.

### Pascal Calling Convention

```asm
myproc PROC PASCAL FAR
    ARG param1:WORD, param2:WORD
    ; Parameters pushed left-to-right
    ; Callee cleans stack
    ret
myproc ENDP
```

---

## Appendix A: Program Blueprints

### DOS Program Blueprint

```asm
DOSSEG
.MODEL small
.STACK 100h
.DATA
    ; Data declarations
.CODE
start:
    mov ax, @data
    mov ds, ax

    ; Program code

    mov ah, 4Ch
    int 21h

END start
```

### Windows Program Blueprint (16-bit)

```asm
.MODEL small, PASCAL
.286
.STACK 4096
.DATA
    ; Data
.CODE
    ; Windows code
END
```

### Windows Program Blueprint (32-bit)

```asm
.386
.MODEL flat, STDCALL
.STACK 4096
.DATA
    ; Data
.CODE
start:
    ; 32-bit Windows code
END start
```

---

## Appendix B: Turbo Assembler Syntax Summary

### Lexical Grammar

- Identifiers: Start with letter, `_`, `@`, or `?`
- Numbers: Digit followed by alphanumerics with optional radix suffix
- Strings: Enclosed in single or double quotes

### Expression Operators (by precedence)

**Highest precedence:**
- `()`, `[]`, `.`
- `LENGTH`, `SIZE`, `WIDTH`, `MASK`, `OFFSET`, `SEG`
- `PTR`, `HIGH`, `LOW`, `TYPE`

**Arithmetic:**
- `*`, `/`, `MOD`, `SHL`, `SHR`
- `+`, `-`

**Relational:**
- `EQ`, `NE`, `LT`, `LE`, `GT`, `GE`

**Logical:**
- `NOT`
- `AND`
- `OR`, `XOR`

---

## Appendix C: MASM 6.1 Compatibility

### New Data Types

| Type | Size | Description |
|------|------|-------------|
| `SBYTE` | 1 | Signed byte |
| `SWORD` | 2 | Signed word |
| `SDWORD` | 4 | Signed doubleword |
| `REAL4` | 4 | Single-precision float |
| `REAL8` | 8 | Double-precision float |
| `REAL10` | 10 | Extended-precision float |

### Decision and Looping Directives

```asm
.IF condition
.ELSEIF condition
.ELSE
.ENDIF

.WHILE condition
.ENDW

.REPEAT
.UNTIL condition
.UNTILCXZ

.BREAK
.CONTINUE
```

### New Directives

| Directive | Description |
|-----------|-------------|
| `ECHO` | Display message |
| `EXTERNDEF` | External definition |
| `OPTION` | Set assembler options |

---

## Appendix D: Error Messages

### Information Messages

Informational messages display status but don't indicate errors.

### Warning Messages

Warning messages indicate potential problems. Common warnings:

- "Pass-dependent construction encountered"
- "Segment alignment changed"
- "Symbol redefinition"

### Error Messages

Errors prevent successful assembly. Common errors:

- "Undefined symbol"
- "Syntax error"
- "Operand types do not match"
- "Illegal instruction for processor"
- "Phase error between passes"

---

## Index

### A
- ALIGN directive, 112
- ALPHA directive, 93
- ARG directive, 120-122
- ASSUME directive, 91-92

### B
- Binary constants, 57-58
- Block scoping, 130-131

### C
- CALL..METHOD instruction, 157
- Case sensitivity, 18-19
- CODESEG directive, 86
- COMMENT directive, 35
- Conditional assembly, 175-182
- Constants, 57-58
- Cross-reference, 13-14

### D
- Data directives, 134
- DATASEG directive, 86
- DB directive, 134
- DD directive, 134
- DOSSEG directive, 93
- DQ directive, 134
- DT directive, 134
- DW directive, 134

### E
- END directive, 40
- ENDP directive, 115
- ENDS directive, 90, 99
- ENUM directive, 95-96
- EQU directive, 38, 159
- Expressions, 61-72
- EXTRN directive, 185

### F
- Floating-point emulation, 79

### G
- GLOBAL directive, 185
- GROUP directive, 91

### I
- IDEAL directive, 30
- IF directives, 175-179
- INCLUDE directive, 37
- INCLUDELIB directive, 187

### L
- LABEL directive, 113
- Labels, 113-114
- LOCAL directive, 120-122
- LOCALS directive, 130
- Location counter, 109-112

### M
- Macros, 159-172
- MASM directive, 30
- Memory models, 82-84
- MODEL directive, 82-84

### O
- Objects, 43-56
- ORG directive, 110-112

### P
- PROC directive, 115-126
- PUBLIC directive, 184
- PUSHSTATE/POPSTATE, 149

### R
- RADIX directive, 58
- Records, 96-97
- REPT directive, 169

### S
- SEGMENT directive, 88-90
- Simplified segments, 86-87
- SMART/NOSMART, 145
- Stack frame, 155
- Structures, 98-102
- Symbols, 59-60

### T
- TBLINIT directive, 50
- TBLINST directive, 49
- TBLPTR directive, 106
- Tables, 102-104
- TYPE operator, 68
- TYPEDEF directive, 104

### U
- UNION directive, 98

### V
- VERSION directive, 39-40
- Virtual methods, 49-54

### W
- WARN directive, 41
- WHILE directive, 170

---

*Turbo Assembler User's Guide*  
*Copyright © 1988, 1996 Borland International, Inc.*
