# Turbo Assembler Version 5 Quick Reference

**Borland International, Inc.**
100 Borland Way, P.O. Box 660001, Scotts Valley, CA 95067-0001

---

Copyright (c) 1988, 1995 by Borland International. All rights reserved. All Borland products are trademarks or registered trademarks of Borland International, Inc. Other brand and product names are trademarks or registered trademarks of their respective holders.

The material in Chapter 3 and Chapter 4 is reprinted with permission of Intel Corporation, copyright (c) Intel Corporation 1987, 1995.

---

## Contents

- [Chapter 1: Predefined Symbols](#chapter-1-predefined-symbols)
- [Chapter 2: Operators](#chapter-2-operators)
  - [Ideal Mode Operator Precedence](#ideal-mode-operator-precedence)
  - [MASM Mode Operator Precedence](#masm-mode-operator-precedence)
  - [Operators](#operators)
  - [Macro Operators](#macro-operators)
  - [Run-time Operators](#run-time-operators)
- [Chapter 3: Directives](#chapter-3-directives)
- [Chapter 4: Processor Instructions](#chapter-4-processor-instructions)
  - [Instruction Set Reference](#instruction-set-reference)
- [Chapter 5: Coprocessor Instructions](#chapter-5-coprocessor-instructions)

---

## Chapter 1: Predefined Symbols

All the predefined symbols can be used in both MASM and Ideal mode.

### `$`

Represents the current location counter within the current segment.

### `@32Bit`

Numeric equate indicating whether segments in the current model are declared as 16 bit or 32 bit.

### `@code`

Alias equate for .CODE segment name.

### `@CodeSize`

Numeric equate that indicates code memory model (O=near, l=far).

### `@CPU`

Numeric equate that returns information about current processor directive.

### `@curseg`

Alias equate for current segment.

### `@data`

Alias equate for near data group name.

### `@DataSize`

Numeric equate that indicates the data memory model (O=near, l=far, 2=huge).

### `??date`

String equate for today's date.

### `@fardata`

Alias equate for initialized far data segment name.

### `@fardata?`

Alias equate for uninitialized far data segment name.

### `@FileName`

Alias equate for current assembly file name.

### `??filename`

String equate for current assembly file name.

### `@Interface`

Numeric equate indicating the language and operating system selected by MODEL.

### `@Model`

Numeric equate representing the model currently In effect.

### `@Object`

Text macro containing the name of the current object. = Alias equate for stack segment.

### `@Stack`

Alias equate for stack segment.

### `@Startup`

Label that marks the beginning of startup code.

### `@Table_<objectname>`

Data type containing the object's method table.

### `@TableAddr_<objectname>`

Label describing the address of the instance of the object's virtual method table.

### `??time`

String equate for the current time.

### `??version`

Numeric equate for current Turbo Assembler version number.

### `@WordSize`

Numeric equate that indicates 16- or 32-bit segments (2=16-bit, 4=32-bit).

## Chapter 2: Operators

This chapter covers the operators Turbo Assembler provides and their precedence.

### Ideal Mode Operator Precedence

The following table lists the operators in order of priority (highest is first, lowest

- 0, [], LENGTH, MASK, OFFSET, SEG, SIZE, WIDTH

- HIGH, LOW

- +, - (unary)

- *, I, MOD, SHL, SHR

- +, - (binary)

- EQ, GE, GT, LE, L T, NE

- NOT

- AND

- OR,XOR

- : (segment override)

- . (structure member selector)

- HIGH (before pointer), LARGE, LOW (before pointer), PTR, SHORT,

### MASM Mode Operator Precedence

- <, 0, [], LENGTH, MASK, SIZE, WIDTH

- . (structure member selector)

- HIGH,LOW

- +, - (unary)

- : (segment override)

- OFFSET, PTR, SEG, THIS, TYPE

- *,/, MOD, SHL, SHR

- +, - (binary)

- EQ, GE, GT, LE, LT, NE

- NOT

- AND

- OR,XOR

- LARGE, SHORT, SMALL, .TYPE

### Operators

#### `()`

**Mode:** Ideal,MASM

**Syntax:** `( expression)`

Marks expression for priority evaluation.

#### `*`

**Mode:** Ideal,MASM

**Syntax:** `expression 1 * expression2`

Multiplies two integer expressions. Also used with 80386 addressing modes where one expression is a register .

#### `+ (unary)`

**Mode:** Ideal,MASM

**Syntax:** `+ expression`

Indicates that expression is positive.

#### `- (binary)`

**Mode:** Ideal, MASM

**Syntax:** `expression 1 - expression2`

Subtracts two expressions.

#### `- (unary)`

**Mode:** Ideal, MASM

**Syntax:** `- expression`

Changes the sign of expression.

#### `.`

**Mode:** Ideal,MASM

**Syntax:** `memptr. fieldname`

Selects a structure member.

#### `/`

**Mode:** Ideal,MASM

**Syntax:** `expression1 / expression2`

Divides two integer expressions.

#### `:`

**Mode:** Ideal, MASM

**Syntax:** `segorgroup : expression`

Generates segment or group override.

#### `?`

**Mode:** Ideal, MASM

**Syntax:** `Ox?`

Initializes with indeterminate data (where Dx is DB, DD, DF, OP, DQ, DT, or DW).

#### `[]`

**Mode:** Ideal,MASM

**Syntax:** `[expression 1][ expression2j`

expression 1[ expression2j MASM mode: The [ ] operator can be used to specify addition or register indirect memory operands. Ideal mode: The [ ] operator specifies a memory reference.

#### `AND`

**Mode:** Ideal, MASM

**Syntax:** `expression1 AND expression2`

Performs a bit-by-bit logical AND of two expressions.

#### `BYTE`

**Mode:** Ideal

**Syntax:** `BYTE expression`

Forces address expression to be byte size.

#### `BYTE PTR`

**Mode:** Ideal,MASM

**Syntax:** `BYTE PTR expression`

Forces address expression to be byte size.

#### `CODEPTR`

**Mode:** Ideal,MASM

**Syntax:** `CODEPTR expression`

Returns the default procedure address size.

#### `DATAPTR`

**Mode:** Ideal

**Syntax:** `DATAPTR expression`

Forces address expression tomodel-dependent size.

#### `DUP`

**Mode:** Ideal, MASM

**Syntax:** `count DUP (expression [,expression] ... )`

Repeats a data allocation operation count times.

#### `DWORD`

**Mode:** Ideal

**Syntax:** `DWORD expression`

Forces address expression to be doubleword size.

#### `DWORDPTR`

**Mode:** Ideal,MASM

**Syntax:** `DWORD PTR expression`

,Forces address expression to be doubleword size.

#### `EQ`

**Mode:** Ideal,MASM

**Syntax:** `expression1 EO expression2`

Returns true if expressions are equal.

#### `FAR`

**Mode:** Ideal

**Syntax:** `FAR expression`

Forces an address expression to be a far code pointer.

#### `FARPTR`

**Mode:** Ideal,MASM

**Syntax:** `FAR PTR expression`

Forces an address expression to be a far code pointer.

#### `FWORD`

**Mode:** Ideal

**Syntax:** `FWORD expression`

Forces address expression to be 32-bit far pointer size.

#### `FWORDPTR`

**Mode:** Ideal,MASM

**Syntax:** `FWORD PTR expression`

Forces address expression to be 32-bit far pointer size.

#### `GE`

**Mode:** Ideal, MASM

**Syntax:** `expression 1 G E expression2`

Returns true if one expression is greater than or equal to the other.

#### `GT`

**Mode:** Ideal, MASM

**Syntax:** `expression 1 GT expression2`

Returns true if one expression is greater than the other.

#### `HIGH`

**Mode:** Ideal,MASM

**Syntax:** `HIGH expression`

Returns the high part (8 bits or type size) of expression.

#### `HIGH`

**Mode:** Ideal

**Syntax:** `type HIGH expression`

Returns the high part (8 bits or type size) of expression.

#### `LARGE`

**Mode:** Ideal,MASM

**Syntax:** `LARGE expression`

Sets expression's offset size to 32 bits. In Ideal mode, this operation is legal only if 386 code generation is enabled.

#### `LE`

**Mode:** Ideal, MASM

**Syntax:** `expression 1 LE expression2`

Returns true if one expression is less than or equal to the other.

#### `LENGTH`

**Mode:** Ideal, MASM

**Syntax:** `LENGTH name`

Returns number of data elements allocated as part of name.

#### `LOW`

**Mode:** Ideal,MASM

**Syntax:** `LOW expression`

Returns the low part (8 bits or type size) of expression.

#### `LOW`

**Mode:** Ideal

**Syntax:** `type LOW expression`

Returns the low part (8 bits or type size) of expression.

#### `LT`

**Mode:** Ideal,MASM

**Syntax:** `expression 1 L T expression2`

Returns true if one expression is less than the other.

#### `MASK`

**Mode:** Ideal,MASM

**Syntax:** `MASK recordfieldname`

Returns a bit mask for a record field or an entire record.

#### `MOD`

**Mode:** Ideal,MASM

**Syntax:** `expression 1 MOD expression2`

Returns remainder (modulus) from dividing two expressions.

#### `NEAR`

**Mode:** Ideal

**Syntax:** `NEAR expression`

Forces an address expression to be a near code pointer.

#### `NEARPTR`

**Mode:** Ideal,MASM

**Syntax:** `NEAR PTR expression`

Forces an address expression to be a near code pointer.

#### `NOT`

**Mode:** Ideal,MASM

**Syntax:** `NOT expression`

Performs a bit-by-bit complement (invert) of expression.

#### `OFFSET`

**Mode:** Ideal,MASM

**Syntax:** `OFFSET expression`

Returns the offset of expression within the current segment (or the group that the segment belongs to, if using simplified segmentation directives or Ideal mode).

#### `OR`

**Mode:** Ideal,MASM

**Syntax:** `expression 1 OR expression2`

Performs a bit-by-bit logical OR of two expressions.

#### `PRoe`

**Mode:** Ideal

**Syntax:** `PROC expression`

Forces an address expression to be a near or far code pointer.

#### `PRoe PTR`

**Mode:** Ideal,MASM

**Syntax:** `PROC PTR expression`

Forces an address expression to be a near or far code pointer.

#### `PTR`

**Mode:** Ideal, MASM

**Syntax:** `type PTR expression`

Forces address expression to have type size.

#### `PWORD`

**Mode:** Ideal

**Syntax:** `PWORD expression`

Forces address expression to be 32-bit far pointer size.

#### `PWORDPTR`

**Mode:** Ideal,MASM

**Syntax:** `PWORD PTR expression`

Forces address expression to be 32-bit far pointer size.

#### `aWORD`

**Mode:** Ideal

**Syntax:** `aWORD expression`

Forces address expression to be quadword size.

#### `aWORDPTR`

**Mode:** Ideal, MASM

**Syntax:** `aWORD PTR expression`

Forces address expression to be quadword size.

#### `SEG`

**Mode:** Ideal, MASM

**Syntax:** `SEG expression`

Returns the segment address of an expression that references memory.

#### `SHL`

**Mode:** Ideal, MASM

**Syntax:** `expressioQ SHL count`

Shifts the value of expression to the left count bits. A negative count causes the data to be shifted the opposite way.

#### `SHORT`

**Mode:** Ideal,MASM

**Syntax:** `SHORT expression`

Forces expression to be a short code pointer (within -128 to +127 bytes of the current code location).

#### `SHR`

**Mode:** Ideal,MASM

**Syntax:** `expression SHR count`

Shifts the value of expression to the right count bits. A negative count causes the data to be shifted the opposite way.

#### `SIZE`

**Mode:** Ideal,MASM

**Syntax:** `SIZE name`

Returns size of data item allocated with name. In MASM mode, SIZE returns the value of LENGTH name multiplied by TYPE name. In Ideal mode, SIZE returns the byte count within name's DUP.

#### `SMALL`

**Mode:** Ideal,MASM

**Syntax:** `SMALL expression`

Sets expression's offset size to 16 bits. In Ideal mode, this operation is legal only if 386 code generation is enabled. .

#### `SYMTYPE`

**Mode:** Ideal

**Syntax:** `SYMTYPE`

Returns a byte describing expression.

#### `TBVTE`

**Mode:** Ideal

**Syntax:** `TBYTE expression`

Forces address expression to be lO-byte size.

#### `TBVTE PTR`

**Mode:** Ideal,MASM

**Syntax:** `TBYTE PTR expression`

Forces address expression to be 10-byte size.

#### `THIS`

**Mode:** Ideal,MASM

**Syntax:** `THIS type`

Creates an operand whose address is the current segment and location counter. type describes the size of the operand and whether it refers to code or data.

#### `.TYPE`

**Mode:** MASM

**Syntax:** `.TYPE expression`

Returns a byte describing the mode and scope of expression.

#### `TYPE`

**Mode:** IDEAL

**Syntax:** `TYPE name1 name2`

Applies the type of an existing variable or structure member to another variable or structure member.

#### `TYPE`

**Mode:** MASM

**Syntax:** `TYPE expression`

Returns a number indicating the size or type of expression.

#### `UNKNOWN`

**Mode:** Ideal

**Syntax:** `UNKNOWN expression`

Removes type information from address expression.

#### `WIDTH`

**Mode:** Ideal, MASM

**Syntax:** `WIDTH recordfieldname`

Returns the width in bits of a field in a record, or of an entire record.

#### `WORD`

**Mode:** Ideal

**Syntax:** `WORD expression`

Forces address expression to be word size.

#### `WORDPTR`

**Mode:** Ideal,MASM

**Syntax:** `WORD PTR expression`

Forces address expression to be word size.

#### `XOR`

**Mode:** Ideal, MASM

**Syntax:** `expression1 XOR expression2`

Performs bit-by-bit logical exclusive OR of two expressions. Unconditional page break inserted for print formatting

### Macro Operators

#### `&`

**Mode:** Ideal,MASM

**Syntax:** `&name`

Substitutes actual value of macro parameter name.

#### `<>`

**Mode:** MASM

**Syntax:** `!character`

Treats text literally, regardless of any special characters it might contain. Treats character literally, regardless of any special meaning it might otherwise have.

#### `%`

**Mode:** Ideal,MASM

**Syntax:** `%text`

Treats text as an expression, computes its value and replaces text with the result. text may be either a numeric expression or a text equate.

#### `"`

**Mode:** MASM

**Syntax:** `Suppresses storage of a comment in a macro definition.`

;;comment

### Run-time Operators

The following operators are evaluated at run time, and can only be used inside

#### `!=`

**Mode:** MASM

**Syntax:** `expressionl != expression2`

Returns true when expressionl is not equal to expression2.

#### `>`

**Mode:** MASM

**Syntax:** `expressionl > expression2`

Returns true when expressionl is greater than expression2. Returns true when expressionl is greater than or equal to expression2.

#### `<`

**Mode:** MASM

**Syntax:** `expressionl < expression2`

Returns true when expressionl is less than expression2. Returns true when expressionl is less than or equal to expression2.

#### `II`

**Mode:** MASM

**Syntax:** `expressionl I I expression2`

Returns the logical ORed value of expressionl and expression2.

#### `&&`

**Mode:** MASM

**Syntax:** `expressionl && expression2`

Returns the logical ANDed value of expressionl and expression2.

#### `&`

**Mode:** MASM

**Syntax:** `express ion 1 & expression2`

Returns the bitwise ANDed value of expressionl and expression2. Returns the logical negation of expression.

#### `CARRY?`

**Mode:** MASM

**Syntax:** `Returns the status of the carry flag.`

#### `OVERFLOW?`

**Mode:** MASM

**Syntax:** `Returns the status of the overflow flag.`

#### `PARITY?`

**Mode:** MASM

**Syntax:** `Returns the status of the parity flag.`

#### `SIGN?`

**Mode:** MASM

**Syntax:** `Returns the status of the sign flag.`

#### `ZERO?`

**Mode:** MASM

**Syntax:** `Returns the status of the zero flag.`

## Chapter 3: Directives

### `.186`

**Mode:** MASM

```asm
.186
```

Enables assembly of 80186 processor instructions .

### `.286`

**Mode:** MASM

```asm
.286
```

Enables assembly of non-privileged (real mode) 80286 processor instructions and 80287 numeric coprocessor instructions .

### `.286C`

**Mode:** MASM

```asm
.286c
```

Enables assembly of non-privileged (real mode) 80286 processor instructions and 80287 numeric coprocessor instructions .

### `.286P`

**Mode:** MASM

```asm
.286P
```

Enables assembly of all 80286 (including protected mode) processor instructions and 80287 numeric coprocessor instructions .

### `.287`

**Mode:** MASM

```asm
.287
```

Enables assembly of 80287 numeric coprocessor instructions.

### `.386`

**Mode:** MASM

```asm
.386
```

Enables assembly of non-privileged (real mode) 80386 processor instructions and 80387 numeric coprocessor instructions .

### `.386C`

**Mode:** MASM

```asm
.386C
```

Enables assembly of non-privileged (real mode) 80386 processor instructions and 80387 numeric coprocessor instructions .

### `.386P`

**Mode:** MASM

```asm
.386P
```

Enables assembly of all 80386 (including protected mode) processor instructions and 80387 numeric coprocessor instructions .

### `.387`

**Mode:** MASM

```asm
.387
```

Enables assembly of 80387 numeric coprocessor instructions .

### `.486`

**Mode:** MASM

```asm
.486
```

Enables assembly of non-privileged (real mode) instructions for the i486 processor .

### `.486C`

**Mode:** MASM

```asm
.486C
```

Enables assembly of non-privileged (real mode) instructions for the i486 processor .

### `.486P`

**Mode:** MASM

```asm
.486P
```

Enables assembly of protected mode instructions for the i486 processor .

### `.487`

**Mode:** MASM

```asm
.487
```

Enables assembly of 80487 numeric processor instructions.

### `*586`

**Mode:** MASM

.586 Enables assembly of non-privileged (real mode) instructions for the Pentium processor .

### `.586e`

**Mode:** MASM

```asm
.586e
```

Enables assembly of non-privileged (real mode) instructions for the Pentium processor .

### `.586P`

**Mode:** MASM

```asm
.586P
```

Enables assembly of protected mode instructions for the Pentium processor .

### `.587`

**Mode:** MASM

```asm
.587
```

Enables assembly of Pentium numeric processor instructions .

### `..8086`

**Mode:** MASM

```asm
.8086
```

Enables assembly of 8086 processor instructions only. This is the default processor instruction mode used by Turbo Assembler .

### `.8087`

**Mode:** MASM

```asm
.8087
```

Enables assembly of 8087 numeric coprocessor instructions only. This is the default coprocessor instruction mode used by Turbo Assembler. name: Defines a near code label called name.

### `=`

**Mode:** Ideal,MASM

```asm
name = expression
```

Defin~s or redefines a numeric equate.

### `ALIGN`

**Mode:** Ideal,MASM

```asm
ALIGN boundary
```

Rounds up the location counter to a power-of-two address boundary (2,4,8, ... ).

### `.ALPHA`

**Mode:** MASM

```asm
.ALPHA
```

Sets alphanumeric segment-ordering. The fa command-line option performs the same function.

### `ALIAS`

**Mode:** Ideal,MASM

```asm
ALIAS <alias _ name>=<targeL name>
```

Allows the association of an alias name with a particular target name. When the linker encounters an alias name, it resolves the alias by referring to the target name. Note: The syntax for ALIAS is identical in both Ideal and MASM modes.

### `ARG`

**Mode:** Ideal,MASM

```asm
ARG argument [,argumen~ ... [=symbo~
```

[RETURNS argument [,argumenm Sets up arguments on the stack for procedures.'Each argument is assigned a positive offset from the BP register, presuming that both the return address of the procedure call and the caller's BP have been pushed onto the stack already. Each argument has the following syntax (boldface items are literal): argname [[cauntt]] [:[debug_size] [type] [:caunt2]] The optional debug_size has this syntax: [type] PTR

### `ASSUME`

**Mode:** Ideal,MASM

```asm
ASSUME segmentreg:name [,segmentreg:name) ...
```
```asm
ASSUME segmentreg:NOTHING
```
```asm
ASSUME NOTHING
```

Specifies the segment register (segmentreg) that will be used to calculate the effective addresses for all labels and variables defined under a given segment or group name (name). The NOTHING keyword cancels the association between the designated segment register and segment or group name. The ASSUME NOTHING statement removes all associations between segment registers and segment or group names. In addition, MASM mode supports the following syntax, which uses ASSUME to assign a data type to a data register: ASSUME datareg:type [,datareg:type)

### `%BIN`

**Mode:** Ideal,MASM

```asm
%BIN size
```

Sets the width of the object code field in the listing file to size columns.

### `.BREAK`

**Mode:** MASM

```asm
.BREAK [.IF expression]
```

This directive generates code that terminates a . WHILE or .REPEAT block if the expression evaluates true.

### `BYTE`

**Mode:** MASM

```asm
[name] BYTE expression [,expression] ...
```

Allocates and initializes a byte of storage. Synonymous with DB.

### `CALL`

**Mode:** Ideal,MASM

```asm
CALL<instance ytr>M ETHOD{ objeclname>:}
```

< method_ name>{USES{ segreg: }offsreg}{ <extended _ caILParameters>} Calls a method procedure.

### `CATSTR`

**Mode:** Ideal, MASM51

```asm
name CATSTR string [,string] ...
```

Concatenates several strings to form a single string name .

### `.CODE`

**Mode:** MASM

```asm
.CODE [nameJ
```

Synonymous with CODESEG. MASM mode only.

### `CODESEG`

**Mode:** Ideal, MASM

```asm
CODESEG [name]
```

Defines the start of a code segment when used with the .MODEL directive. If you have specified the medium or large memory model, you can follow the .CODE (or CODESEG) directive with an optional name that indicates the name of the segment.

### `COMM`

**Mode:** Ideal,MASM

```asm
COMM definition [,definition] ...
```

Defines a communal variable. Each definition describes a symbol and has the following format (boldface items are literal): [distance] [language] symbolname[ [ cauntt] ]:type [:count2J distance can be either NEAR or FAR and defaults to the size of the default data memory model if not specified. language is either C, PASCAL, BASIC, FORTRAN, PROLOG, or NOLANGUAGE and defines any language-specific conventions to be applied to symbolname. symbolname is the communal symbol (or symbols, separated by commas). If distance is NEAR, the linker uses countl to calculate the total size of the array. If distance is FAR, the linker uses count2 to indicate how many elements there are of size countl times the basic element size (determined by type). type can be one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, or a structure name. count2 specifies how many items this communal symbol defines. Both countl and count2 default to 1.

### `COMMENT`

**Mode:** MASM

```asm
COMMENT delimiter [tex~
```

[tex~ [tex~ delimiter [tex~ Starts a multiline comment. delimiter is the first non-blank character following COMMENT.

### `%CONDS`

**Mode:** Ideal,MASM

```asm
%CONDS
```

Shows all statements in conditional blocks in the listing .

### `.CONST`

**Mode:** MASM

```asm
.CONST
```

Defines the start of the constant data segment. Synonymous with CONST. MASM mode only.

### `CONST`

**Mode:** Ideal,MASM

CaNST Defines the start of the constant data segment.

### `.CONTINUE`

**Mode:** MASM

```asm
.CONTINUE [.IF expression]
```

This directive generates code that jumps to the top of a .WHILE or .REPEAT block if the expression evaluates true .

### `.CREF`

**Mode:** MASM

```asm
.CREF
```

Synonymous with %CREF. MASM mode only.

### `%CREF`

**Mode:** Ideal,MASM

```asm
%CREF
```

Allows cross-reference information to be accumulated for all symbols encountered from this point forward in the source file .. CREF reverses the effect of any O/OXCREF or .xCREF directives that inhibited the information collection. %CREFALL %CREFALL Causes all subsequent symbols in the source file to appear in the cross-reference listing. This is the default mode for Turbo Assembler. %CREF ALL reverses the effect of any previous %CREFREF or %CREFUREF directives that disabled the listing of unreferenced or referenced symbols. %CREFREF %CREFREF Disables listing of unreferenced symbols in cross-reference. %CREFUREF %CREFUREF Lists only the unreferenced symbols in cross-reference. %CTLS %CTLS Causes listing control directives (such as %LIST, %INCL, and so on) to be placed in the listing file .

### `.`

**Mode:** MASM

```asm
. DATA
```
Synonymous with DATASE6: MASM mode only.

```asm
DATASEG
```
```asm
DATASEG
```
Defines the start of the initialized data segment in your module. You must first

```asm
have used the .MODEL directive to specify a memory model. The data segment
```
```asm
is put in a group called DGROUP, which also contains the segments defined
```
```asm
with the .STACK, .CONST, and .DATA? directives .
```

### `.`

**Mode:** MASM

```asm
. DATA?
```
Defines the start of the uninitialized data segment in your module. You must

```asm
first have used the .MODEL directive to specify a memory model. The data
```
```asm
segment is put in a group called DGROUP, which also contains the segments
```
```asm
defined with the .STACK, .CONST, and .DATA directives.
```

### `DB`

**Mode:** Ideal,MASM

```asm
[name] DB expression [,expression] ...
```

Allocates and initializes a byte of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a question mark, a character string, or a DUPlicated expression.

### `DD`

**Mode:** Ideal, MASM

```asm
[name] DO [type PTR] expression [,expression] ...
```

Allocates and initializes 4 bytes (a doubleword) of storage. name is the symbol you'll subsequently use to refer to the data. type followed by PTR adds debug information to the symbol being defined, so that Turbo Debugger can display its contents properly. type is one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, SHORT, NEAR, FAR or a structure name. expression can be a constant expression, a 32-bit floating-point number, a question mark, an address expression, or a DUPlicated expression.

### `%DEPTH`

**Mode:** Ideal, MASM

```asm
%DEPTH width
```

Sets size of depth field in listing file to width columns. The default is 1 column.

### `DF`

**Mode:** Ideal,MASM

```asm
[name] OF [type PTR] expression [,expression] ...
```

Allocates and initializes 6 bytes (a far 48-bit pointer) of storage. name is the symbol you'll subsequently use to refer to the data. type followed by PTR adds debug information to the symbol being defined, so that Turbo Debugger can display its contents properly. type is one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, SHORT, NEAR, FAR or a structure name. exprespion can be a constant expression, a question mark, an address expression, or a DUPlicated expression.

### `DISPLAY`

**Mode:** Ideal,MASM

```asm
DISPLAY "text'
```

Outputs a quoted string (text) to the screen.

### `DOSSEG`

**Mode:** Ideal,MASM

```asm
DOSSEG
```

Enables DOS segment-ordering at link time. DOSSEG is included for backward compatibility only.

### `OP`

**Mode:** Ideal,MASM

```asm
[name] DP [type PTR] expression [,expression] ...
```

Allocates and initializes 6 bytes (a far 48-bit pointer) of storage. name is the symbol you'll subsequently use to refer to the data. type followed by PTR adds debug information to the symbol being defined, so that Turbo Debugger can display its contents properly. type is one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, SHORT, NEAR, FAR or a structure name. expression can be a constant expression, a question mark, an address expression, or a DUPlicated expression.

### `OQ`

**Mode:** Ideal,MASM

```asm
[name] DO expression [,expression] ...
```

Allocates and initializes 8 bytes (a quadword) of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a 64-bit floating-point number, a question mark, or a DUPlicated expression.

### `OT`

**Mode:** Ideal,MASM

```asm
[name] DT expression [,expression] ...
```

Allocates and initializes 10 bytes of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a packed decimal constant expression, a question mark, an 80-bit floating-point number, or a DUPlicated expression.

### `ow`

**Mode:** Ideal,MASM

```asm
[name] DW [type PTR] expression [,expression] ...
```

Allocates and initializes 2 bytes (a word) of storage. name is the symbol you'll subsequently use to refer to the data. type followed by PTR adds debug information to the symbol being defined, so that Turbo Debugger can display its contents properly. type is one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, SHORT, NEAR, FAR or a structure name. expression can be a constant expression, a question mark, an address expression, or a DUPlicated expression.

### `OWORO`

**Mode:** MASM

```asm
[name] DWORD [type PTR] expression [,expression] ...
```

Allocates and initializes a doubleword (4 bytes) of storage. Synonymous with DD.

### `ECHO`

**Mode:** MASM

```asm
ECHO text
```

Displays the message text to the standard output device (the screen, by default). Synonymous with %OUT and DISPLAY.

### `ELSE`

**Mode:** Ideal,MASM

```asm
IF condition
```

statements 1 [ELSE statements2j ENDIF Starts an alternative IF conditional assembly block. The statements introduced by ELSE (statements2) are assembled if condition evaluates to false .

### `.ELSE`

**Mode:** MASM

.1 F condition statements 1 [.ELSE statements2j .ENDIF Starts an alternative .IF conditional assembly block. The statements introduced by .ELSE (statements2) are executed if condition evaluates to false.

### `ELSEIF`

**Mode:** Ideal,MASM

```asm
IF condition1
```

statements 1 [ELSEIF condition2 statements2j ENDIF Starts nested conditional assembly block if condition2 is true. Several other forms of ELSEIF are supported: ELSEIF1, ELSEIF2, ELSEIFB, ELSEIFDEF, ELSEIFDIF, ELSEIFDIFI, ELSEIFE, ELSEIFIDN, ELSEIFIDNI, ELSEIFNB, and ELSEIFNDEF.

### `EMUL`

**Mode:** Ideal,MASM

```asm
EMUL
```

Causes all subsequent numeric coprocessor instructions to be generated as emulated instructions, instead of real instructions. When your program is executed, you must have a software floating-point emulation package installed or these instructions will not work properly.

### `END`

**Mode:** Ideal,MASM

```asm
END [stat1address]
```

. Marks the end of a source file. startaddress is a symbol or expression that specifies the address in your program where you want execution to begin. Turbo Assembler ignores any text that appears after the END directive.

### `ENDIF`

**Mode:** Ideal, MASM

IFx condition statements ENDIF Marks the end of a conditional assembly block started with one of the IF directives .

### `.ENDIF`

**Mode:** MASM

.IF condition statements .ENDIF Marks the end of a conditional assembly block started with the .IF directive.

### `ENDM`

**Mode:** Ideal,MASM

```asm
ENDM
```

Marks the end of a repeat block or a macro definition.

### `ENDP`

**Mode:** Ideal, MASM

```asm
ENDP [procname]
```

[procname] ENDP Marks the end of a procedure. If procname is supplied, it must match the procedure name specified with the PROC directive that started the procedure definition.

### `ENDS`

**Mode:** Ideal, MASM

```asm
ENDS [segmentname I strucname]
```

[segmentname I strucname] ENDS Marks end of current segment, structure or union. If you supply the optional name, it must match the name specified with the corresponding SEGMENT, STRUC, or UNION directive .

### `.ENDW`

**Mode:** MASM

.WHILE expression statements .ENDW Marks the end of a conditional assembly block started with the .WHILE directive.

### `ENUM`

**Mode:** Ideal,MASM

```asm
ENUM name[enum_va~,enum_var ... ]]
```
```asm
name ENUM [enum_va~,enum_var ... ]]
```

Declares an enumerated data type.

### `EQU`

**Mode:** Ideal,MASM

```asm
name EQU expression
```

Defines name to be a string, alias, or numeric equate containing the result of evaluating expression .

### `.ERR`

**Mode:** MASM

```asm
.ERR <string>
```

Synonymous with ERR. MASM mode only.

### `ERR`

**Mode:** Ideal, MASM

```asm
ERR <string>
```

Forces an error to occur at the line that this directive is encountered on in the source file. The optional string will display as part of the error message .

### `.ERR1`

**Mode:** MASM

```asm
.ERR1 <string>
```

Forces an error to occur on pass 1 of assembly. The optional string will display as part of the error message .

### `.ERR2`

**Mode:** MASM

```asm
.ERR2 <string>
```

Forces an error to occur on pass 2 of assembly if multiple-pass mode (controlled by 1m command-line option) is enabled. The optional string will display as part of the error message .

### `.ERRS`

**Mode:** MASM

```asm
.ERRS argument <string>
```

Forces an error to occur if argument is blank (empty). The optional string will appear as part of the error message .

### `.ERRDEF`

**Mode:** MASM

```asm
.ERRDEF symbol <string>
```

Forces an error to occur if symbol is defined. The optional string will appear as part of the error message.

### `.ERRDIF`

**Mode:** MASM

```asm
.ERRDIF argument1,argument2 <string>
```

Forces an error to occur if arguments are different. The comparison is case sensitive. The optional string will appear as part of the error message .

### `.ERRDIFI`

**Mode:** MASM

```asm
.ERRDIFI argument1,argument2 <string>
```

Forces an error to occur if arguments are different. The comparison is not case sensitive. The optional string will appear as part of the error message .

### `.ERRE`

**Mode:** MASM

```asm
.ERRE expression <string>
```

Forces an error to occur if expression is false (0). The optional string will appear as part of the error message .

### `.ERRIDN`

**Mode:** MASM

```asm
.ERRIDN argument1,argument2 <string>
```

Forces an error to occur if arguments are identical. The comparison is case sensitive. The optional string will appear as part of the error message .

### `.ERRIDNI`

**Mode:** MASM

```asm
.ERRIDNI argument1,argument2 <string>
```

Forces an error to occur if arguments are identical. The comparison is not case sensitive. The optional string will appear as part of the error message.

### `ERRIF`

**Mode:** Ideal, MASM

```asm
ERRIF expression <string>
```

Forces an error to occur if expression is true (nonzero). The optional string will appear as part of the error message.

### `ERRIF1`

**Mode:** Ideal, MASM

```asm
ERRIF1 <string>
```

Forces an error to oCcur on pass 1 of assembly. The optional string will appear as part of the error message.

### `ERRIF2`

**Mode:** Ideal,MASM

```asm
ERRIF2 <string>
```

Forces an error to occur on pass 2 of assembly if multiple-pass mode (controlled by 1m command-line option) is enabled. The optional string will appear as part of the error message.

### `ERRIFB`

**Mode:** Ideal, MASM

```asm
ERRIFB argument <string>
```

Forces an error to occur if argument is blank (empty). The optional string will appear as part of the error message.

### `ERRIFDEF`

**Mode:** Ideal,MASM

```asm
ERRIFDEF symbol <string>
```

Forces an error if symbol is defined. The optional string will appear as part of the error message.

### `ERRIFDIF`

**Mode:** Ideal,MASM

```asm
ERRIFDIF argumentt,argument2 <string>
```

Forces an error to occur if arguments are different. The comparison is case sensitive. The optional string will appear as part of the error message.

### `ERRIFDIFI`

**Mode:** Ideal,MASM

```asm
ERRIFDIFI argument1,argument2 <string>
```

Forces an error to occur if arguments are different. The comparison is not case sensitive. The optional string will appear as part of the error message.

### `ERRIFE`

**Mode:** Ideal,MASM

```asm
ERRIFE expression <string>
```

Forces an error if expression is false (0). The optional string will appear as part of the error message.

### `ERRIFIDN`

**Mode:** Ideal,MASM

```asm
ERRIFIDN argumentt,argument2 <string>
```

Forces an error to occur if arguments are identical. The comparison is case sensitive. The optional string will appear as part of the error message.

### `ERRIFIDNI`

**Mode:** Ideal,MASM

```asm
ERRIFIDNI argument1,argument2 <string>
```

Forces an error to occur if arguments are identical. The comparison is not case sensitive. The optional string will appear as part of the error message.

### `ERRIFNB`

**Mode:** Ideal,MASM

```asm
ERRIFNB argument <string>
```

Forces an error to occur if argument is not blank. The optional string will appear as part of the error message.

### `ERRIFNDEF`

**Mode:** Ideal, MASM

```asm
ERRIFNDEF symbol <string>
```

Forces an error to occur if symbol is not defined. The optional string will appear as part of the error message .

### `.ERRNB`

**Mode:** MASM

```asm
.ERRNB argument <string>
```

Forces an error to occur if argument is not blank. The optional string will appear as part of the error message .

### `.ERRNDEF`

**Mode:** MASM

```asm
.ERRNDEF symbol <string>
```

Forces an error to occur if symbol is not defined. The optional string will appear as part of the error message .

### `.ERRNZ`

**Mode:** MASM

```asm
.ERRNZ expression <string>
```

Forces an error to occur if expression is true (nonzero). The optional string will appear as part of the error message.

### `EVEN`

**Mode:** Ideal, MASM

```asm
EVEN
```

Rounds up the location counter to the next even address. EVEN DATA EVENDATA Rounds up the location counter to the next even address in a data segment.

### `.EXIT`

**Mode:** MASM

```asm
.EXIT [return_value_exp~
```

Produces termination code. MASM mode only. Synonymous with EXITCODE.

### `EXITCODE`

**Mode:** Ideal,MASM

```asm
EXITCODE [return_value_exp~
```

Produces termination code. You can use it for each desired exit point. return_value_expr is a number to be returned to the operating system. If you don't specify return_value_expr, the value in AX is returned.

### `EXITM`

**Mode:** Ideal,MASM

```asm
EXITM
```

TeI1l1lnates macro- or block-repeat expansion and returns control to the next statement following the macro or repeat-block call. .

### `EXTERN`

**Mode:** MASM

```asm
EXTREN definition [,definition] ...
```

Synonymous with EXTRN. MASM mode only.

### `EXTERNDEF`

**Mode:** MASM

```asm
EXTERNDEF [language] name:type [,[Ianguage] name: type] ...
```

This directive defines one or more external variables, labels, or symbols called name, of type type. name is treated as PUBLIC if it is defined in the current module; it is treated as EXTERN if it is referenced in the module. name is ignored if it is not referenced in the module. If type is ABS, name can be imported as a constant. This directive is normally used in include files.

### `EXTRN`

**Mode:** Ideal, MASM

```asm
EXTRN definition [,definition] ...
```

Indicates that a symbol is defined in another module. definition describes a symbol and has the following format: [language] name[count1]:type [:count2] language specifies that the naming conventions of C, PASCAL, BASIC, FORTRAN, ASSEMBLER, or PROLOG are to be applied to symbol name. name i$ the symbol that is defined in another module and can optionally be followed by countl, an array element multiplier that defaults to 1. type must match the type of the symbol where it's defined and must be one of the following: NEAR, FAR, PROC, BYTE, WORD, DWORD, DATAPTR, , CODEPTR, FWORD, PWORD, QWORD, TBYTE, ABS, or a structure name. count2 specifies how many items this external symbol defines and defaults to 1 if not specified .

### `.FARDATA`

**Mode:** MASM

```asm
.FARDATA [segmentname]
```

Synonymous with FARDATA. MASM mode only.

### `FARDATA`

**Mode:** Ideal

```asm
FARDATA [segmentname]
```

Defines the start of a far initialized data segment. segmentname, if present, overrides the default segment name.

### `•`

**Mode:** MASM

.FARDATA? [segmentname] Defines the start of a far uninitialized data segment. segmentname, if present, overrides the default segment name.

### `FASTIMUL`

**Mode:** Ideal,MASM

```asm
FASTIMUL<deslreg>,<source_rlm>,<value>
```

Generates code that multiplies source register or memory address by value, and puts it into destination register.

### `FLiPFLAG`

**Mode:** Ideal, MASM

f1agreg FLIPFLAG f1agreg] Optimized form of XOR that complements bits with shortest possible instruction. Use only if the resulting contents of the flags registers are unimportant.

### `FOR`

**Mode:** MASM

```asm
FOR parameter, arg 1[, arg2] ...
```

statements ENDM Synonymous with IRP. MASM mode only.

### `FORe`

**Mode:** MASM

```asm
FORe parameter,string
```

statements ENDM Synonymous with IRPC. MASM mode only.

### `FWORD`

**Mode:** MASM

```asm
[name] FWORD [type PTR] expression [,expression] ...
```

Allocates and initializes a 6 bytes (a far 48-bit pointer) of storage. Synonymous with DF. MASM mode only.

### `GETFIELD`

**Mode:** Ideal,MASM

```asm
GETFI ELD<field _ name><destination Jeg>, <source_rim>
```

Generates code that retrieves the value of a field found in the same source register or memory address, and sets the destination to that value.

### `GLOBAL`

Ideal,M~SM GLOBAL definition [,definition] ... Acts as a combination of the EXTRN and PUBLIC directives to define a global symbol. definition describes the symbol and has the following format (boldface items are literal): [language] name [[ countt ]] :type [:count2] language specifies that the naming conventions of C, PASCAL, BASIC, FORTRAN, NOLANGUAGE, or PROLOG are to be applied to symbol name. If name is defined in the current source file, it is made public exactly as if used in a PUBLIC directive. If not, it is declared as an external symbol of type type, as if the EXTRN directive had been used. name can be followed by an optional array count multiplier, countl, which defaults to 1. type must match the type of the symbol in the module where it is defined and must be one of the following: NEAR, FAR, PROC, BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, ABS, or a structure name. count2 specifies how many items this symbol defines (1 is the default).

### `GOTO`

**Mode:** Ideal,MASM

```asm
GOTO tag_symbol
```

Tells Turbo Assembler to resume execution at the specified macro tag (tag_symbol). GOTO terminates any conditional block that it is found in.

### `GROUP`

**Mode:** Ideal,MASM

```asm
GROUP groupname segmentname [,segmentname] .. .
```
```asm
groupname GROUP segmentname [,segmentname] .. .
```

Associates groupname with one or'more segments, so that all labels and variables defined in those segments have their offsets computed relative to the beginning of group groupname. segmentname can be either a segment name defined previously with SEGMENT or an expression starting with SEG. In MASM mode, you must use a group override whenever you access a symbol in a segment that is part of a group. In Ideal mode, Turbo Assembler automatically generates group overrides for such symbols.

### `IDEAL`

**Mode:** Ideal,MASM

```asm
IDEAL
```

Enters Ideal assembly mode. Ideal mode will stay in effect until it is overridden by a MASM or QUIRKS directive.

### `IF`

**Mode:** Ideal,MASM

```asm
I F expression
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statements1 up to the optional ELSE directive, provided that expression is true (nonzero). If expression is falso (zero), statements2 are assembled .

### `.IF`

**Mode:** MASM

.1 F expression statements 1 [.ELSE statements2J .ENDIF This directive generates code that executes statements1 if the expression evaluates true. If an .ELSE follows the .IF, statements2 are executed if the expression evaluates false. Because the expression is evaluated at run time, it can incorporate the run-time relational operators. MASM mode only.

### `IF1`

**Mode:** Ideal, MASM

```asm
IF1
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statements1 up to the optional ELSE directive, provided directive, provided that multiple-pass mode (controlled by the 1m command-line option) is enabled and that the current assembly pass is pass one.

### `IF2`

**Mode:** Ideal, MASM

```asm
IF2
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statements 1 up to the optional ELSE directive, provided that multiple-pass mode (controlled by the 1m command-line option) is enabled and the current assembly pass is pass two.

### `IFB`

**Mode:** Ideal, MASM

```asm
IFB argument
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that argument is blank (empty). If argument is is not blank, statements2 are assembled.

### `IFDEF`

**Mode:** Ideal,MASM

```asm
IFDEF symbol
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that symbol is defined. If symbol is undefined, statements2 are assembled.

### `IFDIF`

**Mode:** Ideal,MASM

```asm
IFDIF argument1,argument2
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the as'sembly of statementsl up to the optional ELSE directive, provided that the arguments are different. If the arguments are the same, statements2 are assembled. The comparison is case sensitive. .

### `IFDIFI`

**Mode:** Ideal,MASM

```asm
IFDIFI argument1,argument2
```

statements 1 [ELSE statements2] ENDIF Initiates a conditional block, causing the assembly of truestatements up to the optional ELSE directive, provided that the arguments are different. If the arguments are the same, statements2 are assembled. The comparison is not case sensitive.

### `IFE`

**Mode:** Ideal,MASM

```asm
IFE expression
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that expression is false. If expression is true, statements2 are assembled.

### `IFIDN`

**Mode:** Ideal,MASM

```asm
IFIDN argument 1 ,argument2
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that the arguments are identical. If the arguments are not identical, statements2 are assembled. The comparison is case sensitive.

### `IFIDNI`

**Mode:** Ideal,MASM

```asm
IFIDNI argument1,argument2
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statements 1 up to the optional ELSE directive, provided that the arguments are identical. If the arguments are not identical, statements2 are assembled. The comparison is not case sensitive.

### `IFNB`

**Mode:** Ideal,MASM

```asm
IFNB argument
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that argument is nonblank. If argument is blank, statements2 are assembled.

### `IFNDEF`

**Mode:** Ideal, MASM

```asm
IFNDEF symbol
```

statements 1 [ELSE statements2J ENDIF Initiates a conditional block, causing the assembly of statementsl up to the optional ELSE directive, provided that symbol is not defined. If symbol is not defined, statements2 are assembled.

### `%INCL`

**Mode:** Ideal,MASM

```asm
%INCL
```

Enables listing of include files. This is the default INCLUDE file listing mode.

### `INCLUDE`

**Mode:** MASM, Ideal

```asm
INCLUDE filename or INCLUDE "filename"
```
```asm
Includes source code from file filename at the current position in the module
```

being assembled. If no extension is specified, .ASM is assumed.

### `INCLUDELIB`

**Mode:** MASM, Ideal

```asm
INCLUDELIB filename or INCLUDELIB "filename"
```

Causes the linker to include library filename at link time. If no extension is specified, .LIB is assumed.

### `INSTR`

**Mode:** Ideal,MASM

```asm
name INSTR [start,]string1,string2
```
```asm
name is assigned the position of the first instance of string2 in stringl. Searching
```

begins at position start (position one if start not specified). If string2 does not appear anywhere-within stringl, name is set to zero.

### `IRP`

**Mode:** Ideal,MASM

```asm
IRP parameter,arg1[,arg2] ...
```

statements ENDM Repeats a block of statements with string substitution. statements are assembled once for each argument present. The arguments may be any text, such as symbols, strings, numbers, and so on. Each time the block is assembled, the next argument in the list is substituted for any instance of parameter in the statements.

### `IRPC`

**Mode:** Ideal,MASM

```asm
IRPC parameter,string
```

statements EN OM Repeats a block of statements with character substitution. statements are assembled once for each character in string. Each time the block is assembled, the next character in the string is substituted for any instances of parameter in statements.

### `JMP`

**Mode:** Ideal, MASM

```asm
JM P <instance ytr>METHOO{ <objecl name>:}
```

<method _ name>{USES{ segreg:} offsreg} Functions exactly like CALL..METHOD except that it generates a IMP instead of a CALL and it cleans up the stack if there are LOCAL or USES variables on the stack. Use primarily for tail recursion.

### `JUMPS`

**Mode:** Ideal,MASM

```asm
JUMPS
```

Causes Turbo Assembler to look at the destination address of a conditional jump instruction, and if it is too far away to reach with the short displacement that these instructions use, it generates a conditional jump of the opposite sense around an ordinary jump instruction to the desired target address. This directive has the same effect as using the IJJUMPS command-line option.

### `LABEL`

MASM,ldeal name LABEL type LABEL name type Defines a symbol name to be of type type. name must not have been defined previously in the source file. type must be one of the following: NEAR, FAR, PROC, BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, or a structure name .

### `.LALL`

**Mode:** MASM

```asm
.LALL
```

Enables listing of macro expansions.

### `LARGESTACK`

**Mode:** Ideal,MASM

```asm
LARGESTACK
```

Indicates that the stack is 32-bit.

### `.LFCOND`

**Mode:** MASM

```asm
.LFCOND
```

Shows all statements in conditional blocks in the listing.

### `%LlNUM`

**Mode:** Ideal,MASM

%L1NUM size Sets the width of the line-number field in listing file to size columns. The default is four columns.

### `%LlST`

**Mode:** Ideal,MASM

%L1ST Shows source ooes in the listing. This is the default listing mode .

### `.`

**Mode:** MASM

```asm
.L1ST
```
Synonymous with %LIST. MASM mode only .

### `.LlSTALL`

**Mode:** MASM

.L1STALL Begins the listing of all statements. Combines the directives .LIST, .LISTIF, and .LISTMACROALL.

### `.LlSTIF`

**Mode:** MASM

.L1STIF Lists all statements in conditional blocks, whether true or false. Synonymous with .LFCOND. MASM mode only .

### `.LlSTMACRO`

**Mode:** MASM

.L1STMACRO Enables the listing of macro expansions that generate code or data. Synonymous with .XALL. MASM mode only .

### `.LlSTMACROALL`

**Mode:** MASM

.L1STMACROALL Enables the listing of macro all macro expansions. Synonymous with .LALL. MASM mode only.

### `LOCAL`

**Mode:** Ideal, MASM

In macros: LOCAL symbol [,symbo~ ... In procedures: LOCAL element [,elemen~ ... [=symbo~ Defines local variables for macros and procedures. Within a macro definition, LOCAL defines temporary symbol names that are replaced by new unique symbol names each time the macro is expanded. LOCAL must appear before any other statements in the macro definition. Within a procedure, LOCAL defines names that access stack locations as negative offsets relative to the BP register. If you end the argument list with an equal sign (=) and a symbol, that symbol will be equated to the total size of the local symbol block in bytes. Each element has the following syntax (boldface brackets are literal): symname [[count1]] [:[debug_size] [:type] [:count2]] type is the data type of the argument. It can be one of the following: BYTE, WORD, DATAPTR, CODEPTR, DWORD, FWORD, PWORD, QWORD, TBYTE, NEAR, FAR, PROC, or a structure name. If you don't specify a type, WORD size is assumed. count2 specifies how many items of type the symbol defines. The default for count2 is 1 if it is not specified. countl is an array element size multiplier. The total space allocated for the symbol is count2 times the length specified by the type field times countl. The default for countl is 1 if it is not specified. The optional debug_size has this syntax: [type] PTR

### `LOCALS`

**Mode:** Ideal,MASM

```asm
LOCALS [prefix]
```

Enables local symbols, whose names will begin with two at-signs (@@) or the two-character prefix if it is specified. Local symbols are automatically enabled in Ideal mode.

### `MACRO`

**Mode:** Ideal, MASM

```asm
MACRO name [parameter [,parametetj ... ]
```
```asm
name MACRO [parameter [,parametetj ... ]
```

Defines a macro to be expanded later when name is encountered. parameter is a placeholder that you use in the the body of the macro definition wherever you want to substitute one of the actual arguments the macro is called with. &MACS Enables listing of macro expansions.

### `MASKFLAG`

**Mode:** Ideal,MASM

f/agsreg MASKFLAG f/agsreg Optimized form of AND that clears bits with the shortest possible instruction. Use only if the resulting contents of the flags registers are unimportant.

### `MASM`

**Mode:** Ideal, MASM

```asm
MASM
```

Enters MASM assembly mode. This is the default assembly mode for Turbo Assembler.

### `MASM51`

**Mode:** Ideal,MASM

```asm
MASM51
```

Enables assemblr of some MASM 5.1 enhancements.

### `MODEL`

**Mode:** Ideal, MASM

```asm
MODEL [model modifie~ memorymodel [module name]
```

[,[/anguage modifie1/anguage ] [,model modifie~ Sets the memory model for simplified segmentation directives. model modifier can come before memorymodel or at the end of the statement and must be either NEARSTACK or FARSTACK if present. memorymodel is TINY, SMALL, MEDIUM, COMPACT, LARGE, HUGE or TCHUGE. module name is used in the large models to declare the name of the code segment. language modifier is WINDOWS, ODDNEAR, ODDFAR, or NORMAL and specifies generation of MS-Windows procedure entry and exit code. language specifies which language you will be calling from to access the procedures in this module: C, PASCAL, BASIC, FORTRAN, PROLOG, or NOLANGUAGE. Turbo Assembler automatically generates the appropriate procedure entry and exit code when you use the PROC and ENDP directives. language also tells Turbo Assembler which naming conventions to use for public and external symbols, and in what order procedure arguments were pushed onto the stack by the calling module. Also, the appropriate form of the RET instruction is generated to remove the arguments from the stack before returning if required .

### `.MODEL`

**Mode:** MASM

```asm
.MODEL
```

Synonymous with MODEL. MASM mode only.

### `MULTERRS`

**Mode:** Ideal,MASM

```asm
MULTERRS
```

Allows multiple errors to be reported on a single source line. NAME NAME modulename Sets the object file's module name. This directive has no effect in MASM mode; it only works in Ideal mode. %NEWPAGE %NEWPAGE Starts a new page in the listing file. °kNOCONDS %NOCONDS Disables the placement of statements in conditional blocks in the listing file. °kNOCREF %NOCREF [symbol, ... ] , Disables cross-reference listing (CREF) information accumulation. If you supply one or more symbol names, cross-referencing is disabled only for those symbols. %NOCTLS %NOCTLS Disables placement of listing-control directives in the listing file. This is the default listing-control mode for Turbo Assembler. NOEMUL NOEMUL Causes all subsequent numeric coprocessor instructions to be generated as real instructions, instead of emulated instructions. When your program is executed, you must have an 80x87 coprocessor installed or these instructions will not work properly. This is the default floating-point assembly mode for Turbo Assembler. %NOINCL %NOINCL Disables listing of source lines from INCLUDE files. NOJUMPS NOJUMPS Disables stretching of conditional jumps enabled with JUMPS. This is the default mode for Turbo Assembler.

### `%NOLIST`

**Mode:** Ideal,MASM

```asm
%NOLIST
```

Disables output to the listing file .

### `.NOLIST`

**Mode:** MASM

```asm
.NOLIST
```

Disables output to the list file. Synonymous with .XLIST. MASM mode only .

### `.NOLISTIF`

**Mode:** MASM

```asm
.NOLISTIF
```

Prevents statements in false conditional blocks from appearing in the listing file. Synonymous with .SFCOND. MASM mode only .

### `.NOLISTMACRO`

**Mode:** MASM

```asm
.NOLISTMACRO
```

Suppresses the listing of all statements in macro expansions. Synonymous with .sALL. MASM mode only.

### `NOLOCALS`

**Mode:** Ideal,MASM

```asm
.NOLOCALS
```

Disables local symbols enabled with LOCALS. This is the default for Turbo Assembler's MASM mode.

### `%NOMACS`

**Mode:** Ideal,MASM

```asm
%NOMACS
```

Lists only macro expansions that generate code. This is the default macro listing mode for Turbo Assembler.

### `NOMASM51`

**Mode:** Ideal,MASM

```asm
NOMASM51
```

Disables assembly of certain MASM 5.1 enhancements enabled with MASM51. This is the default mode for Turbo Assembler.

### `NOMULTERRS`

**Mode:** Ideal,MASM

```asm
NOMULTERRS
```

Allows only a single error to be reported on a source line. This is the default error-reporting mode for Turbo Assembler.

### `NOSMART`

**Mode:** Ideal, MASM

```asm
NOS MART
```

Disables code optimizations that generate different code than MASM.

### `%NOSYMS`

**Mode:** Ideal, MASM

```asm
%NOSYMS
```

Disables placement of the symbol table in the listing file.

### `%NOTRUNC`

**Mode:** Ideal, MASM

```asm
%NOTRUNC
```

Prevents truncation of fields whose contents are longer than the corresponding field widths in the listing file.

### `NOWARN`

**Mode:** Ideal,MASM

```asm
NOWARN [warne/ass]
```

Disables warning messages with warning identifier warn class, or all warning messages if warnclass is not specified.

### `OPTION`

**Mode:** MASM

```asm
OPTION option
```

TASM supports the following MASM options: CASEMAP, DOTNAME, EMULATOR, EXPR16, EXPR32, L}MP, NOEMULATOR, NOKEYWORD, NOL}MP, NODOTNAME, NOSCOPED, PROC, SEGMENT, and SCOPED. Note that all other MASM options are recognized, but are ignored, by TASM.

### `ORG`

**Mode:** Ideal, MASM

```asm
ORG expression
```

Sets the location counter in the current segment to the address specified by expression. %OUT text Displays text on screen.

### `P186`

**Mode:** Ideal, MASM

```asm
P186
```

Enables assembly of 80186 processor instructions.

### `P286`

**Mode:** Ideal,MASM

```asm
P286
```

Enables assembly of all 80286 (including protected mode) processor instructions and 80287 numeric coprocessor instructions.

### `P286N`

**Mode:** Ideal,MASM

```asm
P286N
```

Enables assembly of non-privileged (real mode) 80286 processor instructions and 80287 numeric coprocessor instructions.

### `P286P`

**Mode:** Ideal,MASM

```asm
P286P
```

Enables assembly of all 80286 (including protected mode) processor instructions and 80287 numeric coprocessor instructions.

### `P287`

**Mode:** Ideal,MASM

```asm
P287
```

Enables assembly of 80287 numeric coprocessor instructions.

### `P386`

**Mode:** Ideal, MASM

```asm
P386
```

Enables assembly of a1180386 (including protected mode) processor instructions and 80387 numeric coprocessor instructions.

### `P386N`

**Mode:** Ideal,MASM

```asm
P386N
```

Enables assembly of non-privileged (real mode) 80386 processor instructions and 80387 numeric coprocessor instructions.

### `P386P`

**Mode:** Ideal,MASM

```asm
P386P
```

Enables assembly of a1180386 (including protected mode) processor instructions and 80387 numeric coprocessor instructions.

### `P387`

**Mode:** Ideal,MASM

```asm
P387
```

Enables assembly of 80387 numeric coprocessor instructions. I,MASM Ideal, MASM all i486 (including protected mode) processor instructions. e 'es the leaves Ideal, MASM gn (+), ber eona lon-privileged (real mode) i486 processor instructions. Ideal,MASM I,MASM 87 numeric processor instructions. 1t is 4 al,MASM Pentium (including protected mode) processor ulated). al,MAS~ l-privileged (real mode) Pentium processor CTL eal, MA~M Ideal,MASM ium numeric processor instructions . . eal, MASM Ideal, MASM . Drocessor instructions only. This is the default e for Turbo Assembler. umeric coprocessor instructions only. This is the ~on mode for Turbo Assembler. WSor is OLOG. HZE. MASM mode only.

### `%PAGESIZE`

```asm
I Ide~~1
```
```asm
%PAGESIZE [rows] [,cols]
```
```asm
I
```

Sets the listing page height and width, starts new pages. rows specifies t~:li number of lines that will appear on each listing page (10 .. 255). cols speci~ number of columns wide the page will be (59 .. 255). Omitting rows or cols the current setting unchanged. If you follow %PAGESIZE with a plus s111 11 a new page starts, the section number is incremented, and the page nun !, restarts at 1. %P A G ESIZE with no arguments forces the listing to reSUJ:l1 new page, with no change in section number.

### `%PCNT`

Idei' %PCNT width Sets segment:offset field width in listing file to width columns. The defal for 16-bit segments and 8 for 32-bit segments.

### `PN087`

Id~ PN087 I I Prevents the assembling of numeric coprocessor instructions (real or e~

### `%POPLCTL`

IdE %POPLCTL Resets the listing controls to the way they were when the last %PUSHI directive was issued.

### `POPSTATE`

```asm
POPSTATE
```

Returns to last saved state from Turbo Assembler's internal state stack

### `MOC`

~ ________________________ -1[1 PROC name [language modifie~ [language] [distance] [USES items,] [argument [,argumen~ ... ] [RETURNS argument [,argumen~ ... ] statements name ENDP name PROC [language modifie~ [language] [distance] [USES items,] [argument [,argumen~ ... ] [RETURNS argument [,argumen~ ... ] statements name ENDP Defines the start of procedure name. language modifier is either WINDt NOWINDOWS, to specify generation of MS-Windows entry/exit co language specifies which language you will be calling from to access t procedure: C, PASCAL, BASIC, FORTRAN, NOLANGUAGE, or P This determines symbol naming conventions, the order of any arguments on the stack, and whether the arguments will be left on the stack when the procedure returns. distance is NEAR or FAR and determines the type of RET instruction that will be assembled at the end of the procedure. items is a list of registers and/ or single-token data items to be pushed on entry and popped on exit from the procedure. argument describes an argument the procedure is called with. Each argument has the following syntax: argname[[count1]] [[:distance] [PTR] type] [:count2] argname is the name you'll use to refer to this argument throughout the procedure. distance is NEAR or FAR to indicate that the argument is a pointer of the indicated size. type is the data type of the argument and can be BYTE, WORD, DWORD, FWORD, PWORD, QWORD, TBYTE, or a structure name. WORD is assumed if none is specified. countl and count2 are the number of elements of type. PTR tells Turbo Assembler to emit debug information to let Turbo Debugger know that the argument is a pointer to a data item. Using PTR without distance causes the pointer size to be based on the current memory model and segment address size. RETURNS introduces one or more arguments that won't be popped from the stack when the procedure returns.

### `PROCDESC`

**Mode:** Ideal,MASM

```asm
PROCDESC name [language] [language modifie~ [distance] [arguments]
```
```asm
name PRODESC [[/anguage_modifie~ language] [distance] [arguments]
```

Declares a procedure prototype, which lets Turbo Assembler check the types and number of parameters to procedure calls and declarations, and specifies language and distance. Also serves to PUBLIC or EXTRN the procedure name.

### `PROCTYPE`

**Mode:** Ideal,MASM

```asm
PROCTYPE name [procedure_description]
```
```asm
name PROCTYPE [procedure_description]
```

procedure_description has the following syntax: [[language _ modifie~/anguage][ distance][ argumenLlis~ argument _list has the following syntax: argumen~,argumen~ ... where each argument has the following syntax: [argname][[ countC expressions]] :complex _ type[ :count2 _ expression] Declares a procedure type. Describes a procedure but does not create a prototype for it. Can be used in place of the language specifier in a call to allow argument type checking during compilation.

### `PROTO`

**Mode:** MASM

```asm
name PROTO [[/anguage_modifie~ language] [distance] [arguments]
```
```asm
Prototypes the function name. Synonymous with PROCDESC. MASM mode
```

only.

### `PUBLIC`

**Mode:** Ideal,MASM

```asm
PUBLIC [language] symbol [,[language] symbo~ ...
```

Declares symbol to be accessible from other modules. If language is specified (C, PASCAL, BASIC, FORTRAN, ASSEMBLER, or PROLOG), symbol is made public after having the naming conventions of the specified language applied to it.

### `PUBLlCDLL`

**Mode:** Ideal, MASM

```asm
PUBLlCDLL [language] symbol [,[language] symbo~ ...
```

Declares symbols to be accessible as dynamic link entry points from other modules. symbol (a PROC or program label, data variable name, or numeric constant defined with EQU) becomes accessible to other programs under Windows. If language is specified (C, PASCAL, BASIC, FORTRAN, PROLOG, or NOLANGUAGE), symbol is made public after having the naming conventions of the specified language applied to it.

### `PURGE`

**Mode:** Ideal,MASM

```asm
PURGE macroname [,macroname] ...
```

Removes macro definition macroname.

### `%PUSHLCTL`

**Mode:** Ideal,MASM

```asm
%PUSHLCTL
```

Saves current listing controls on a 16-level stack

### `PUSHSTATE`

**Mode:** Ideal,MASM

```asm
PUSHSTATE
```

Saves current operating state on an internal stack that is 16 levels deep.

### `QUIRKS`

**Mode:** Ideal, MASM

```asm
QUIRKS
```

Allows you to assemble a source file that makes use of one of the true MASM bugs.

### `QWORD`

**Mode:** MASM

```asm
[name] QWORD expression [,expression] ...
```

Allocates and initializes 8 bytes (a quadword) of storage. Synonymous with DQ. MASM mode only .

### `.RADIX`

**Mode:** MASM

```asm
.RADIX radix
```

Synonymous with RADIX. MASM mode only ..

### `RADIX`

**Mode:** Ideal,MASM

```asm
RADIX radix
```

Sets the default radix for integer constants in expressions to 2, 8, la, or 16.

### `REAL4`

**Mode:** MASM

```asm
REAL4
```

Allocates a short (32 bit) real number. MASM mode only.

### `REAL8`

**Mode:** MASM

```asm
REAL8
```

Allocates a long (64 bit) real number. MASM mode only.

### `REAL10`

**Mode:** MASM

```asm
REAL10
```

Allocates a la-byte (80 bit) real or BCD number. MASM mode only.

### `RECORD`

MASM,ldeal name RECORD field [,field] .. . RECORD name field [,field] .. . Defines record name that contains bit fields. Each field describes a group of bits in the record and has the following format (boldface items are literal): fieldname: width[=expression] fieldname is the name of a field in the record. width (1..16) specifies the number of bits in the field. If the total number of bits in all fields is 8 or less, the record will occupy 1 byte; 9 .. 16 bits will occupy 2 bytes; otherwise, it will occupy 4 bytes. expression provides a default value for the field.

### `REPEAT`

**Mode:** MASM

```asm
REPEAT expression
```

statements ENDM Synonymous with REPT. MASM mode only.

### `.REPEAT`

**Mode:** MASM

```asm
.REPEAT
```

statements .UNTIL expression .REPEAT statements .UNTILCXZ [expression] This directive generates code that repeats the execution of the block of statements until the expression evaluates true. The directive .UNTILC:XZ, which evaluates true when the register CX is zero, can be used with or without the conditional expression. Because the expression is evaluated at run time, it can incorporate the run-time relational operators. MASM mode only.

### `REPT`

**Mode:** Ideal, MASM

```asm
REPT expression
```

statements ENDM Repeats the statement block until expression evluates true.

### `RETCODE`

**Mode:** Ideal,MASM

```asm
RETCODE
```

Generates either a near return (2-byte displacement) or a far return (4-byte displacement) depending on the size of the memory model declared in the .MODULE directive. A tiny, small, or compact memory model results in a near return, while a medium, large, or huge memory model results in a far return. See the RET processor instruction in Chapter 4 for more information.

### `RETF`

**Mode:** Ideal,MASM

```asm
RETF
```

Generates a far return (4-byte displacement) from a procedure. See the RET processor instruction in Chapter 4 for more information.

### `RETN`

**Mode:** Ideal,MASM

```asm
RETN
```

Generates a near return (2-byte displacement) from a procedure. See the RET processor instruction in Chapter 4 for more information .

### `.SALL`

**Mode:** MASM

```asm
.SALL
```

Suppresses the listing of all statements in macro expansions. MASM mode only.

### `SBVTE`

**Mode:** MASM

```asm
[name] SBYTE expression [,expression] ...
```

Allocates and initializes a signed byte of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a question mark, a character string, or a DUPlicated expression.

### `SDWORD`

**Mode:** MASM

```asm
[name] SDWORD expression [,expression] ...
```

Allocates and initializes a signed doubleword (4 bytes) of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a question mark, a character string, or a DUPlicated expression.

### `SEGMENT`

MASM,ldeal SEGMENT name [align] [combine] [use] ['class'] name SEGMENT [align] [combine] [use]['class'] Defines segment name with full attribute control. If you have already defined a segment with the same name, this segment is treated as a continuation of the previous one. align specifies the type of memory boundary where the segment must start: BYTE, WORD, DWORD, PARA (default), or PAGE. combine specifies how segments from different modules but with the same name will be combined at link time: AT expression (locates segment at absolute paragraph address expression), COMMON (locates this segment and all other segments with the same name at the same address), MEMORY (concatenates all segments with the same name to form a single contiguous segment), PRIVATE (does not combine this segment with any other segments; this is the default used if none specified), PUBLIC (same as MEMORY above), STACK (concatenates all segments with the same name to form a single contiguous segment, then initializes SS to the beginning of the segment and SP to the length of the segment) or VIRTUAL (defines a special kind of segment that will be treated as a common area and attached to another segment at link time). use specifies the default word size for the segment if 386 code generation is enabled, and can be either USE16 or USE32. class controls the ordering of segments at link time: segments with the same class name are loaded into memory together, regardless of the order in which they appear in the source file .

### `.`

**Mode:** MASM

```asm
.SEQ
```
Sets sequential segment-ordering. This is the default ordering mode for Turbo

```asm
Assembler .. SEQ has the same function as the Is command-line option.
```

### `SETFIELD`

**Mode:** Ideal,MASM

```asm
SETFI ELD <field _ name><destination -,1m>, <source Jeg>
```

Generates code that sets a value in a record field. Sets the field in the destination register or memory address with the contents of a source register.

### `SETFLAG`

**Mode:** Ideal,MASM

f/agreg SETFLAG f/agreg Optimized form of OR that sets bits with shortest possible instruction. Use only if the resulting contents of the flags register is unimportant.

### `.SFCOND`

**Mode:** MASM

```asm
.SFCOND
```

Prevents statements in false conditional blocks from appearing in the listing file.

### `SIZESTR`

**Mode:** Ideal,MASM

```asm
name SIZESTR string
```

Assigns the number of characters in string to name. A null string has a length of zero.

### `SMALLSTACK`

**Mode:** Ideal,MASM

```asm
SMALLSTACK
```

Indicates that the stack is 16-bit.

### `SMART`

**Mode:** Ideal,MASM

```asm
SMART
```

Enables all code optimizations .

### `.STACK`

**Mode:** MASM

```asm
.STACK [size]
```

Synonymous with STACK. MASM mode only.

### `STACK`

**Mode:** Ideal,MASM

```asm
STACK [size]
```

Defines the start of the stack segment, allocating size bytes. 1024 bytes are allocated if size is not specified .

### `.STARTUP`

**Mode:** MASM

,STARTUP Provides initialization code. MASM mode only. Equivalent to STARTUPCODE.MASM mode only.

### `STARTUPCODE`

**Mode:** Ideal,MASM

```asm
STARTUPCODE
```

Provides initialization code and marks the beginning of the program.

### `STRUC`

**Mode:** Ideal,MASM

```asm
[name] STR UC{ <modifiers>}{ <parenLname>}{M ETHOD<method _list>}
```

<structure_data> ENDS [name] STRUC [name]{ <modifiers>}{ <parenLname>}{M ETHOD<method _list>} <structure_data> ENDS [name] parent_name is the name of the parent object's data structure. method_list is like that of TABLE. structure _data is any (additional) data present in an instance of the object. modifiers can be GLOBAL, NEAR, or FAR.

### `STRUCT`

**Mode:** MASM

```asm
[name] STRUCT{<modifiers>}{<parenLname>}{METHOD<method_list>}
```

<structure_data> ENDS [name] STRUCT [name]{<modifiers>}{<parenLname>}{METHOD<method_list>} <structure_data> ENDS [name] Synonymous with STRUC. MASM mode only.

### `SUBSTR`

**Mode:** Ideal, MASM51

```asm
name SUBSTR string,position[,size]
```

Defines a new string name consisting of characters from string starting at position, with a length of size. All the remaining characters in string, starting from position, are assigned to name if size is not specified.

### `SUBTITLE`

**Mode:** MASM

```asm
SUBTITLE text
```

Sets the subtitle in the listing file to text. Synonymous with %SUBTTL and .SFCOND. MASM mode only.

### `SUBTTL`

**Mode:** MASM

```asm
SUBTTL "text'
```

Synonymous with %SUBTTL. MASM mode only.

### `%SUBTIL`

**Mode:** Ideal, MASM

%SUBTTL "text' Sets subtitle in listing file to text.

### `SWORD`

**Mode:** MASM

```asm
[name] SWORD expression [,expression] ...
```

Allocates and initializes a signed word (2 bytes) of storage. name is the symbol you'll subsequently use to refer to the data. expression can be a constant expression, a question mark, a character string, or a DUPlicated expression.

### `%SYMS`

**Mode:** Ideal,MASM

```asm
O/OSYMS
```

Enables symbol table placement in listing file. This is the default symbol listing mode for Turbo Assembler.

### `TABLE`

**Mode:** Ideal,MASM

```asm
TABLE name [table_member [,table_member ... ]]
```

Constructs a table structure used to contaih method pointers for objects.

### `%TABSIZE`

**Mode:** Ideal,MASM

```asm
%TABSIZE width
```

Sets the number of columns between tabs in .the listing file to width. The default is 8 columns.

### `TBLINIT`

**Mode:** Ideal,MASM

```asm
TBLINIT
```

Initializes pointer in an object to the virtual method table.

### `TBLINST`

**Mode:** Ideal,MASM

```asm
TBLINST
```

Creates an instance of the virtual table for the current object and defines @TableAddr_<object>. Must be used after every object definition that includes virtual methods, so that the virtual table is allocated. You should use this directive in only one module of your program.

### `TBLPTR`

**Mode:** Ideal,MASM

```asm
TBLPTR
```

Places a virtual table pointer within the object data. Defines a structure member of the name @Mptr_<object>. This can only be used inside an object definition.

### `TBYlE`

**Mode:** MASM

```asm
[name] TBYTE expression [, expression] ...
```

Allocates and initializes 10 bytes of storage. Synonymous with DT.

### `TESTFLAG`

**Mode:** Ideal, MASM '

flagreg TESTFLAG flagreg Optimized form of TEST that tests bits with the shortest possible instruction. %TEXT %TEXT width Sets width of source field in listing file to width columns.

### `TEXTEQU`

**Mode:** MASM

```asm
name TEXTEQU [item]
```

Assigns item to name. The item can be either a literal string, a string returned by a macro function, or a string constant (must be preceded by a %) .

### `.TFCOND`

**Mode:** MASM

```asm
TFCOND
```

Toggles conditional block-listing mode. MASM mode only.

### `TITLE`

**Mode:** MASM

```asm
TITLE "text'
```

Synonymous with % TITLE. MASM mode only. %TITLE %TITLE "text' Sets title in listing file to text. %TRUNC Truncates listing fields that are too long.

### `TYPEDEF`

**Mode:** Ideal,MASM

```asm
TYPEDEF type_name complex_type
```

type_name TYPEDEF complex_type Defines named types.

### `UDATASEG`

**Mode:** Ideal,MASM

```asm
UDATASEG
```

Defines the start of an uninitialized data segment.

### `UFARDATA`

**Mode:** Ideal, MASM

```asm
UFARDATA
```

Defines the start'of an uninitialized far data segment.

### `UNION`

Ideal, MASM (disabled by QUIRKS) UNION name fields ENDS [name] name UNION fields [name] ENDS Defines a union called name. A union is just like a STRUC except that all its members have an offset of zero from the start of the union. This results in a set of fields that are overlayed, allowing you to refer to the memory area defined by the union vyith different names and different data sizes. The length of a union is the length of its largest member, not the sum of the lengths of its members as in a STRUC. fields define the fields that comprise the union. Each field uses the normal data allocation directives (DB, DW, and so on) to define its size .

### `.UNTIL`

**Mode:** MASM

.REPEAT statements .UNTIL expression Termination directive to a .REPEAT loop. When expression evaluates true, the loop started with the .REPEAT directive terminates .

### `.UNTILCXZ`

**Mode:** MASM

.REPEAT statements .UNTILCXZ [expression] Termination directive to a .REPEAT loop. The directive .UNTILCXZ, which evaluates true when the register ex is zero, can be used with or without the conditional expression.

### `USES`

**Mode:** Ideal,MASM

```asm
USES item Litem] ...
```

Indicates which registers or single-token data items you want to have pushed at the beginning of the enclosing procedure and which ones you want popped just before the procedure returns. You must use this directive before the first instruction that actually generates code in your procedure.

### `VERSION`

**Mode:** MASM, Ideal

```asm
VERSION <version_/D>
```

Places Turbo Assembler in the equivalent operating mode for the specified version.

### `WARN`

**Mode:** Ideal,MASM

```asm
WARN [warne/ass]
```

Enables the type of warning message specified with warnclass, or all warnings if warnclass is not specified. warnclass may be one of: ALN, ASS, BRK, ICG, LCO, OPI, OPP, OPS, OVF, PDC, PRO, PQK, RES, or TPI.

### `WHILE`

**Mode:** Ideal,MASM

```asm
WHILE while_expression
```

macro body ENDM Repeats a macro body until while_expression evaluates to 0 (false) .

### `.WHILE`

**Mode:** MASM

```asm
.WHILE expression
```

statements .ENDW This directive generates code that executes the block of statements while the expression evaluates true. Because the expression is evaluated at run time, it can incorporate the run-time relational operators. MASM mode only.

### `WORD`

**Mode:** MASM

```asm
[name] WORD [type PRT] expression [,expression] ...
```

Allocates and initializes 2 bytes (a word) of storage. Synonymous with DW .

### `.XALL`

**Mode:** MASM

```asm
.XALL
```

Causes only macro expansions that generate code or data to be listed .

### `.XCREF`

**Mode:** MASM

```asm
.XCREF
```

Disables cross-reference listing (CREF) information accumulation .

### `.XLlST`

**Mode:** MASM

```asm
.xLlST
```

Disables subsequent output to listing file. MASM mode only.

## Chapter 4: Processor Instructions

This chapter presents instructions for the 80x86 processor set in alphabetical order. For each instruction, the forms are given for each operand combination, including object code produced, operands required, execution time, and a description. For each instruction, there is an operational description and a summary of exceptions generated.

### Operand-size and address-size attributes

When executing instructions in a 16-bit application, 80x86 processors address memory using either 16- or 32-bit addresses. Consequently, each instruction that uses memory addresses has associated with it an address-size attribute of either 16 or 32 bits. Sixteen-bit addresses imply both the use of a 16-bit displacement in the instruction and the generation of a 16-bit address offset (segment relative address) as the result of the effective address calculation. Thirty-two-bit addresses imply the use of a 32-bit displacement and the generation of a 32-bit address offset. Similarly, an instruction that accesses words (16 bits) or doublewords (32 bits) has an operand-size attribute of either 16 or 32 bits. The attributes are determined by a combination of defaults, instruction prefixes, and (for programs executing in protected mode) size-specification bits in segment descriptors.

### Default segment attribute

For programs executed in protected mode, the D-bit in executable-segment descriptors determines the default attribute for both address size and operand size. These default attributes apply to the execution of all instructions in the segment. A value of zero in the D-bit sets the default address size and operand c size to 16 bits; a value of one, to 32 bits. Programs that execute in real mode or virtual-8086 mode have 16-bit addresses and operands by default.

### Operand-size and address-size instruction prefixes

The internal encoding of an instruction can include two byte-long prefixes: the address-size prefix, 67H, and the operand-size prefix, 66H. (A later section, "Instruction format," shows the position of the prefixes in an instruction's encoding.) These prefixes override the default segment attributes for the instruction that follows. Table 4.1 shows the effect of each possible combination of defaults and overrides.

**Table 4.1 Effective size attributes**

1 Segment default D= .. , 0 0 0 0 1 y y y y Operand-size prefix 66h N N N N y y y y Address-size prefix 6711 N N N N Effective operand size 16 16 16 16 32 32 32 32 Effective address size 16 16 16 16 32 32 32 32 Y = Yes, this instruction prefix is present. N = No, this instruction prefix is not present.

### Address-size attribute for stack

Instructions that use the stack implicitly (for example, POP EAX) also have a stack address-size attribute of either 16 or 32 bits. Instructions with a stack address-size attribute of 16 use the 16-bit SP stack pointer register; instructions with a stack address-size attribute of 32 bits use the 32-bit ESP register to form the address of the top of the stack . The stack address-size attribute is controlled by the B-bit of the data-segment descriptor in the SS register. A value of zero in the B-bit selects a stack address- size attribute of 16; a value of one selects a stack address-size attribute of 32.

### Instruction format

All instruction encodings are subsets of the general instruction format shown in

**Figure 4.1. Instructions consist of optional instruction prefixes, one or two**

primary opcode bytes, possibly an address specifier consisting of the ModR/M byte and the SIB (scale index base) byte, a displacement, if required, and an immediate data field, if required. Smaller encoding fields can be defined within the primary opcode or opcodes. These fields define the direction of the operation, the size of the displacements, the register encoding, or sign extension; encoding fields vary depending on the class of operation. Most instructions that can refer to a operand in memory have an addressing form byte following the primary opcode byte(s). This byte, called the ModR/M byte, specifies the address form to be used. Certain encodings of the ModR/M byte indicate a second addressing byte, the SIB byte, which follows the ModR/ M byte and is required to fully specify the addressing form.

**Figure 4.1 80386 instruction format**

Instruction I Address- I operand-I Segment prefix size prefix size prefix override o or 1 o or 1 o or 1 o or 1 Number of bytes oPcodelMOdr/MI SIB _I DisPlacementl Immediate 1 or 2 0 or 1 0 or 1 0, 1, 2, or 4 0, 1, 2, or 4 Number of bytes Addressing forms can include a displacement immediately following either the ModR/M or SIB byte. If a displacement is present, it can be 8, 16, or 32 bits. If the instruction specifies an immediate operand, the immediate operand always follows any displacement bytes. The immediate operand, if specified, is always the last field of the instruction. The following are the allowable instruction prefix codes:

- F3h: REP prefix (used only with string instructions)

- F3h: REPE/REPZ prefix (used only with string instructions)

- F2h: REPNE/REPNZ prefix (used only with string instructions)

- FOh: LOCK prefix

The following are the segment override prefixes:

- 2Eh: CS segment override prefix

- 36h: 55 segment override prefix

- 3Eh: DS segment override prefix

- 26h: ES segment override prefix

- 64h: FS segment override prefix (386 processors and greater)

- 65h: GS segment override prefix (386 processors and greater)

- 66h: Operand-size override

- 67h: Address-size operand

### ModR/M and SIB bytes

The ModR/M and SIB bytes follow the opcode byte(s) in many of the 80x86 instructions. They contain the following information: the indexing type or register number to be used in the instruction; the register to be used, or more information to select the instruction; and the base, index, and scale information. The ModR/M byte contains three fields of information:

- The mod field, which occupies the two most significant bits of the byte,

combines with the rim field to form 32 possible values: 8 registers and 24 indexing modes.

- The reg field, which occupies the next three bits following the mod field,

specifies either a register number or three more bits of opcode information. The meaning of the reg field is determined by the first (opcode) byte of the instruction.

- The rIm field, which occupies the three least-significant bits of the byte, can

specify a register as the location of an operand, or can form part of the addressing-mode encoding in combination with the mod field as described earlier.

- The based indexed and scaled indexed forms of 32-bit addressing require

the SIB byte. The presence of the SIB byte is indicated by certain encodings of the ModR/M byte. The SIB byte then includes the following fields: e The ss field, which occupies the 2 most-significant bits of the byte, specifies the scale factor. e The index field, which occupies the next 3 bits following the ss field specifies the register number of the index register.

- The base field, which occupies the 3 least-significant bits of the byte,

specifies the register number of the base register.

**Figure 4.2 shows the format of the ModR/M and SIB bytes.**

**Figure 4.2 Mod RIM and SIB byte formats**

Modr/M Byte 7 6 5 4 3 2 Reg/Opcode I Mod RIM SIB (Scale Index Base) Byte

### I

Index Base The values and corresponding addressing forms of the ModR/M and SIB bytes are shown in Tables 4.2, 4.3, and 4.4.

**Table 4.2 16-bit addressing forms with ModR/M byte**

r8(!r) AL CL DL BL AH CH DH BH r16(!r) AX CX DX BX 5P BP 51 DI r32(!r) EAX ECX EDX EBX E5P EBP E51 EDI / digit (opcode) 2 3 4 5 6 7 0 REG = 000 001 010 011 100 101 110 111 [BX+ 51] 000 00 08 10 18 20 28 30 38 [BX+ DI] 001 01 09 11 19 21 29 31 39 [BP+ 51] 010 02 OA 12 1A 22 2A 32 3A [BP+ DI] 00 011 03 OB 13 1B 23 2B 33 3B [51] 14 24 100 04 OC 1C 2C 34 3C [DI] 101 05 OD 15 1D 25 2D 35 3D disp16 16 26 2E 3E 110 06 OE IE 36 [BX] 111 07 OF 17 IF 27 2F 37 3F 78 [BX + 51] + disp8 000 40 48 50 58 60 68 70 [BX + DI] + disp8 001 41 49 51 59 61 69 71 79 [BP + 51] + disp8 010 42 4A 52 5A 62 6A 72 7A [BP + DI] + disp8 01 011 43 4B 53 5B 63 6B 73 7B [51] + disp8 100 44 4C 54 5C 64 6C 74 7C [DI] + disp8 101 45 4D 55 5D 65 6D 75 7D

**Table 4.2**

[BP] + disp8 110 46 4E 56 5E 66 6E 76 7E 111 [BX] +disp8 47 4F 57 SF 67 6F 77 7F [BX + SI] + disp16 000 80 88 90 98 AO A8 BO B8 [BX + DI] + disp16 001 81 89 91 99 Al A9 B1 B9 [BP + SI] + disp16 010 82 8A 92 9A B2 BA A2 AA 10 011 [BP + DI] + disp16 83 8B 93 9B A3 AB B3 BB AC B4 BC [SI] + disp16 100 84 8C 94 9C A4 [DI] + disp16 101 85 80 95 90 AS AO B5 BO 110 [BP] + disp 16 86 8E 96 9E A6 AE B6 BE 111 [BX] + disp16 87 8F 97 9F A7 B7 BF AF co EAX/ AX/ AL (386) 000 C8 DO 08 EO E8 Fa F8 ECX/CX/CL (386) 001 C1 C9 01 E1 E9 F1 F9 D9 EOX/OX/OL (386) 010 C2 CA 02 OA E2 EA F2 FA EBX/BX/BL (386) 11 011 C3 CB 03 OB E3 EB F3 FB ESP /SP / AH (386) 100 C4 CC 04 E4 EC F4 FC DC co 05 00 E5 EO F5 FO EBP /BP /CH (386) 101 C5 ESI/Sl/OH (386) 110 C6 CE 06 OE E6 EE F6 FE 111 C7 CF 07 OF E7 FF EDI/DI/BH (386) EF F7 disp8 denotes an 8-bit displacement following the ModR/M byte, to be sign-extended and added to the index. disp 16 denotes a 16-bit displacement following the ModR/M byte, to be added to the index. Default segment register is SS for the effective addresses containing a BP index, DS for other effective addresses.

**Table**

r8(!r) AL CL OL BL AH CH OH BH 'AX a m ~ ~ & r16(jr). DI ~ r32(jr) EAX ECX EOX EBX ESP EBP ESI EOI o 2 3 4 5 6 7 / digit( opeode) 1 REG = 000 001 010 all 100 101 110 111 [EAX] 00 08 10 18 20 28 30 38 000 [ECX] 001 01 09 11 19 21 29 31 39 22 [EOX] 010 02 OA 12 lA 2A 32 3A [EBX] 00 all 03 OB 13 1B 23 2B 33 3B [- -] [--] 100 04 DC 14 lC 24 2C 34 3C disp32 101 05 00 15 10 25 2D 35 30 [ESI] 110 06 OE 16 IE 26 2E 36 3E [EDI] 111 07 OF 17 IF 27 2F 37 3F disp8[EAX] 000 40 48 50 58 60 68 70 78 disp8[ECX] 001 41 49 51 59 61 69 79 71 disp8[EOX] 010 52 SA 62 6A 72 7A 42 4A disp8[EPX]; 01 6B 73 all 43 4B 53. 5B 63 7B disp8[- -] [--] 100 44 54 5C 6C 74 7C 4C 64 disp8[EBP] 4D 55 50 65 6D 75 101 45 7D disp8[ESI] 110 46 4E 56 5E 66 6E 76 7E 111 4F 6F 77 disp8[EOI] 47 57 67 7F 5~ disp32[EAX] 000 80 88 90 98 AO A8 BO B8

**Table 4.3 32-bit addressing forms with Mod RIM byte (80386 only) (continued)**

disp32[EOX] 010 82 8A 92 9A AA BA disp32[EBX] 10 all 8B 93 9B A3 AB B3 BB 83 disp32[- -] [--] 100 84 8C 94 9C A4 AC B4 BC disp32[EBP] 101 85 80 95 9D A5 AD B5 BD disp32[ESI] 110 86 8E 96 9E A6 AE B6 BE BF disp32[EOI] 111 87 8F 97 9F A7 AF B7 Fa CO EAX/AX/AL 000 C8 DO E8 D8 EO F8 ECX/CX/CL 001 C1 C9 D1 D9 E1 E9 F1 F9 EOX/OX/OL 010 C2 CA D2 OA E2 EA F2 FA EBX/BX/BL 11 all C3 CB D3 DB E3 EB F3 FB ESP/SP/AH 100 C4 CC 04 DC E4 EC F4 FC EBP/BP/CH 101 C5 CO D5 OD E5 ED F5 FD 110 C6 CE D6 DE E6 EE F6 FE ESI/SI/OH EOI/OI/BH 111 C7 CF D7 DF E7 EF F7 FF [- -] [- -] means a SIB follows ~!e ModR/Mbyte. disp8 denotes an 8-bit displacement following the SIB byte, to be sign-extended and added to the index. disp32 denotes a 32-bit displacement following the ModR/M byte, to be added to the index.

**Table 4.4 32-bit addressing forms with SIB byte (80386 only)**

r32 EAX ECX EOX EBX ESP [*] ESI EOI a Base = 2 3 4 5 6 7 Base = 000 001 010 all 100 101 110 111 [EAX] 06 07 000 00 01 02 03 04 05 OC 00 OE ,OF [ECX] 001 08 OA QB 09 [EOX] 010 10 11 12 14 15 16 17 13 1E [EBX] all 18 19 1A 1C 10 IF 00 1B none 100 20 21 22 23 24 25 26 27 [EBP] 101 28 29 2A 2B 2C 20 2E 2F [ESI] 110 30 31 32 33 34 35 36 37 [EOI] 3D 3E 3F 111 38 39 3A 3B 3C [EAX*2] 000 40 41 42 44 44 45 46 47 [ECX*2] 49 4A 4B 4C 40 4E 4F 001 48 [EDX*2] 010 50 51 52 55 54 55 56 57 [EBX*2] 01 011 58 59 5A 5B 5C 50 5E 5F none 100 60 61 62 63 65 66 67 64 [EBP*2] 101 68 69 6A 6B 6C 60 6E 6F [ESI*2] 110 70 73 74 75 76 77 71 72 [EOI*2] 111 78 79 7A 7B 7C 7D 7E 7F [EAX*4] 000 80 81 82 83 84 85 86 87 [ECX*4] 001 88 89 8A 8B 8C 80 8E 8F [EOX*4] 91 94 95 96 97 010 90 92 93 [EBX*4] 10 all 98 89 9A 9B 9C 90 9E 9F none Al 100 AO A2 A3 A4 A5 A6 A7 [EBP*4] 101 A8 A9 AA AB AC AD AE AF [ESI*4] 110 BO B1 B2 B3 B4 B5 B6 B7

**Table 4.4 32-bit addressing forms with SIB byte (80386 only) (continued)**

i .. **.*;J~~~9~*;;i **,;M9d~;¥~~~~,;i,~4~~~'~im.~! '*SC~~~.~~~x+ [EDI*4] 111 B8 B9 BA BB BC BO [EAX*8] 000 CO C1 C2 C3 C4 C5 C6 C7 [ECX*8] 001 C8 C9 CA CB CC CO CE CF [EOX*8] 010 DO 01 02 03 D4 05 06 07 [EBX*8] 11 011 08 09 OA DB DC DO DE OF none 100 EO El E2 E3 E4 E5 E6 E7 [EBP*8] 101 E8 E9 EA EB EC ED EE EF [ESI*8] F5 110 FO Fl F2 F3 F4 F6 F7 [EDI*8] 111 F8 F9 FA FB FC FE FF FD [*] means a disp32 with no base if MOD is 00; otherwise, [ESP]. This provides the following addressing modes: disp32[index ](MOD=OO) disp8[EBP] [index ](MOD=Ol) disp32[EBP] [index](MOD=10)

### How to read the instruction set pages

Here's a sample of the format of this chapter:

### Instruction

### name

a D ITS ZAP C Flag information goes here 386 286* 86 This table contains clock information *Because the 80186 processor is effectively a 80286 without protected mode instructions, the 80186 timings are identical to the timings listed for the 80286.

### Flags

Each entry in this section includes information on which flags in the 80x86' s flag register are changed and how. Each flag has a one-letter tag for its name. D = Overflow flag Z = Zero flag D = Direction flag A = Auxiliary flag P = Parity flag I = Interrupt flag C = Carry flag T = Trap flag S = Sign flag The following symbols indicate how the flag register has changed: ? = Undefined after the operation

o = Always cleared

### Opcode

The "Opcode" column gives the complete object code produced for each form of the instruction. When possible, the codes are given as hexadecimal bytes, in the same order in which they appear in memory. Definitions of entries other than hexadecimal bytes ate as follows: Idigit (digit is between 0 and 7.) Indicates that the ModR/Mbyte of the instruction uses only the rim (register or memory) operand. The reg field contains the digit that provides an extension to the instruction's opcode. Ir Indicates that the ModR/M byte of the mstruction contains both a register operand and an rim operand. cb, cw, cd, cp A I-byte (cb),2-byte (cw),4-byte (cd), or 6-byte (cp) value following the opcode that is used to specify a code offset and possibly a new value for the code segment register. ib, iw, id A I-byte (ib),2-byte (iw), or 4-byte (id) immediate operand to the instruction that follows the opcode, ModR/M byte$, or scale-indexing bytes. The opcode determines if the operand is a signed value. All words and doublewords are given with the low-order byte first. +rb, +rw, +rd A register code, from 0 through 7, added to the hexadecimal byte given at the left of the plus sign to form a single opcode byte. The codes are AL=O AX=O EAX=O CL=1 CX=1 ECX=1 DL=2 DX=2 EDX=2 BL=3 BX=3 EBX=3 AH=4 SP=4 ESP=4 AH=4 SP=4 ESP=4 CH=5 BP=5 EBP=5 DH=6 SI=6 ESI=6 BH=7 DI=7 EDI=7

### Instruction

The "Instruction" column gives the syntax of the instruction statement as it would appear in a TASM 80386 program. The following is a list of the symbols used to represent operands in the instruction statements: reiS A relative address in the range from 128 bytes before the end of the instruction to 127 bytes after the end of the instruction. reI16, reI32 A relative address within the same code segment as the instruction assembled. re116 applies to instructions with an operand-size attribute of 16 bits; reI32 applies to instructions with an operand-size attribute of 32 bits (386 only). ptr16:16, ptr16:32 A far pointer, typically in a code segment different from that of the instruction. The notation 16:16 indicates that the value of the pointer has two parts. The value to the right of the colon is a 16-bit selector or value destined for the code segment register. The value to the left corresponds to the offset within the destination segment. ptr16:16 is used when the instruction's operand-size attribute is 16 bits; ptr16:32 is used with the 32-bit attribute (80386 only). r8 One of the byte registers AL, CL, DL, BL, AH, CH, DH, or BH. r16 One of the word registers AX, CX, DX, BX, SP, BP, SI, or DI. r32 (386) One of the doubleword registers EAX, ECX, EDX, EBX, ESP, EBP, ESI, or ED!. imm8 An immediate byte value. imm8 is a signed number between -128 and +127 inclusive. For instructions in which imm8 is combined with a word or doubleword operand, the immediate value is sign-extended to form a word or doubleword. The upper byte of the word is filled with the topmost bit of the immediate value. imm16 An immediate word value used for instructions whose operand-size attribute is 16 bits. This is a number between -32,768 and +32,767 inclusive. imm32 (386) An immediate doubleword value used for instructions whose operand-size attribute is 32 bits. It allows the use of a number between +2,147,483,647 and -2,147,483,648. r/m8 A I-byte operand that is either the contents of a byte register (AL, BL, CL, DL, AH, BH, CH, DH), or a byte from memory. r/m16 A word register or memory operand used for instructions whose operand-size attribute is 16 bits. The word registers are AX, BX, CX, DX, SP, BP, SI, DI. The contents of memory are found at the address provided by the effective address computation. r/m32 A doubleword register or memory operand used for instructions whose operand-size attribute is 32 bits. The doubleword registers are EAX, EBX, ECX, EDX, ESP, EBP, ESI, ED!. The contents of memory are found at the address provided by the effective address computation. m8 A memory byte addressed by DS:SI or ES:DI (used only by string instructions on the 80386). m16 A memory word addressed by DS:SI or ES:DI (used only by string instructions). m32 A memory doubleword addressed by DS:SI or ES:DI (used only by string instructions). m16:16, m16:32 (80386) A memory operand containing a far pointer composed of two numbers. The number to the left of the colon corresponds to the pointer's segment selector. The number to the right corresponds to its offset. m16 & 32, m16 & 16 (80186/80286/80386), m32 & 32 (80386) A memory operand consisting of data item pairs whose sizes are indicated on the left and the rigli.t side of the ampersand. All memory addressing modes are allowed. m16 & 16 and m32 & 32 operands are used by the BOUND instruction to provide an operand containing an upper and lower bounds for array indices. m16 & 32 is used by LIDT and LGDT to provide a word with which to load the limit field, and a doubleword with which to load the base field of the corresponding Global and Interrupt Descriptor Table Registers. moffs8, moffs16, moffs32 (memory offset; 80386 only) A simple memory variable of type BYTE, WORD, or DWORD (80386) used by some variants of the MOV instruction. The actual address is given by a simple offset relative to the segment base. No ModRIM byte is used in the instruction. The number shown with moffs indicates its size, which is determined by the address-size attribute of the instruction. Sreg A segment register. The segment register bit assignments are ES = 0, CS = I, SS = 2, DS = 3, FS = 4 (80386), and GS = 5 (80386).

### Clocks

The "Clocks" column gives the number of clock cycles the instruction takes to execute. The clock count calculations make the following assumptions:

- The instruction has been prefetched and decoded and is ready for execution.

- Bus cycles do not require wait states.

- There are no local bus HOLD requests delaying processor access to the bus.

- No exceptions are detected during instruction execution.

- Memory operands are aligned.

Clock counts for instructions that have an rim (register or memory) operand are separated by a slash. The count to the left is used for a register operand; the count to the right is used for a memory operand. The following symbols are used in the clock count specifications:

- n, which represents a number of repetitions.

- m, which represents the number of components in the next instruction

executed, where the entire displacement (if any) counts as one component, the entire immediate data (if any) counts as one component, and every other byte of the instruction and prefix( es) each counts as one component.

- pm=, a clock count that applies when the instruction executes in protected

mode. pm= is not given when the clock counts are the same for protected and real address modes. When an exception occurs during the execution of an instruction and the exception handler is in another task, the instruction exception time is increased by the number of clocks to effect a task switch. This parameter depends on several factors:

- The type of TSS used to represent the current task (386 TSS or 286 TSS).

- The type of TSS used to represent the new task.

- Whether the current task is in V86 mode. .

- Whether the new task is in V86 mode.

### Instruction Set Reference

#### `AAA`

*ASCII adjust after addition*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 D | T | S | A Z | P C |  |
|  | AAA |  |  |  |  |  |
| 37 |  | 3 | 4 | 3 | 8 | ASCII adjust after addition |

Execute AAA only following an ADD instruction that leaves a byte result in the AL register. The lower nibbles of the operands of the ADD instruction should be in the range a through 9 (BCD digits). In this case, AAA adjusts AL to contain the correct decimal digit result. If the addition produced a decimal carry, the AH register is incremented, and the carry and auxiliary carry flags are set to 1. If there was no decimal carry, the carry and auxiliary flags are set to a and AH is unchanged. In either case, AL is left with its top nibble set to O. To convert AL to an ASCII result, follow the AAA instruction with OR AL, 30B.

#### `AAD`

*ASCII adjust before division*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| D50A | AAD | 14 | 19 | 14 | 60 | ASCII adjust before division |

* * AAD is used to prepare two unpacked BCD digits (the least-significant digit in AL, the most-significant digit in AH) for a division operation that will yield an unpacked result. This is accomplished by setting AL to AL + (10 * AH), and then setting AH to O. AX is then equal to the binary equivalent of the original unpacked two-digit number.

#### `AAM`

*ASCII adjust AX after multiply*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| D40A | AAM | 15 | 17 | 16 | 83 | ASCII adjust AX after multiply |

Execute AAM only after executing a MUL instruction between two unpacked BCD digits that leaves the result in the AX register. Because the result is less than lOa, it is contained entirely in the AL register. AAM unpacks the AL result by dividing AL by 10, leaving the quotient (most-significant digit) in AH and the remainder (least-significant digit) in AL.

#### `AAS`

*ASCII adjust AL after subtraction*

**Flags:** `o D ITS ZAP C`

3F AAS 343 8 ASCII adjust AL after subtraction Execute AAS only after a SUB instruction that leaves the byte result in the AL register. The lower nibbles of the operands of the SUB instruction must have been in the range a through 9 (BCD digits). In this case, AAS adjusts AL so it contains the correct decimal digit result. If the subtraction produced a decimal carry, the AH register is decremented, and the carry and auxiliary carry flags are set to 1. If no decimal carry occurred, the carry and auxiliary carry flags are . set to 0, and AH is unchanged. In either case, AL is left with its top nibble set to O. To convert AL to an ASCII result, follow the AAS with OR AL, 30H.

#### `ADC`

*Add with carry*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 10/r | ADCr/m8,r8 | 1/3 | 2/7 | 2/7 | 3/16+EA | Add with carry byte register to rim byte ' rim word rim word |
| 12/r | ADCr8,r/m8 | 1/2 | 2/6 | 2/7 | 3/9+EA | Add with carry rim byte to byte register |
| 13/r | ADC r16,r/m16 | 1/2 | 2/6 | 2/7 | 3/9+EA | Add with carry rim word to word register |
| 13/r | ADC r32,r / m32 | 1/2 | 2/6 |  |  | Add with CF rim dword to dword register |
| 14ib | ADCAL,imm8 |  | 2 | 3 | 4 | Add with carry immediate byte to AL |
| 15iw | ADC AX,imm16 | 1 | 2 | 3 | 4 | Add with carry immediate word to AX |
| 15id | ADC EAX,imm32 |  | 2 |  |  | Add with carry immediate dword toEAX |
| 80/2 ib | ADC r/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add with carry immediate byte to r/mbyte |
| 81 /2 iw | ADC r/m16,imm16 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add with carry immediate word tor/mword |
| 81/2 id | ADC r/m32,imm32 | 1/3 | 2/7 |  |  | Add with CF immediate dword to rim dword |
| 8312 ib | ADC r/m16,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add with CF sign-extended immediate byte to rim word |
| 83/2 ib | ADC r/rn32,imm8 | 1/3 | 2/7 |  |  | Add with CF sign-extended immediate byte into rim dword |

* * 11 Ir ADC r/m16,r16 2/7 3/16+EA Add with carry word register to 1/3 2/7 11 Ir ADC r/m32,r32 Add with CF dword register to 1/3 2/7 ADC performs an integer addition of the two operands DEST and SRC and the carry flag, CF. The result of the addition is assigned to the first operand (DEST), and the flags are set accordingly. ADC is usually executed as part of a multi-byte or multi-word addition operation. When an immediate byte value is added to a word or doubleword operand, the immediate value is first sign- extended to the size of the word or doubleword operand.

#### `ADD`

*Add*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 04ib | ADDAL,imm8 | 1 | 2 | 3 | 4 | Add immediate byte to AL |
| 05 iw | ADD AX,imm16 | 1 | 2 | 3 | 4 | Add immediate word to AX |
| 05 id | ADD EAX,imm32 | 1 | 2 |  |  | Add immediate dword to EAX |
| 8010ib | ADDr/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add immediate byte to rim byte |
| 8110 iw ADD | r/m16,imm16 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add immediate word to rim word |
| 81/0id | ADDr/m32,imm32 | 1/3 | 2/7 |  |  | Add immediate dword to rim dword |
| 83/0ib | ADQr/m16,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Add sign-extended immediate byte to rim word |
| 8310 ib | ADD r/m32,imm8 | 1/3 | 2/7 | . |  | Add sign-extended immediate byte to rim dword |
| 00 Ir | ADD r/m8,r8 | 1/3 | 2/7 | 2/7 | 3/16+EA | Add byte register to rim byte |
| 01 Ir | ADD r/m16,r16 | 1/3 | 2/7 | 2/7 | 3/16+EA | Add word register to rim word |
| 01/r | ADD r/m32,r32 | 1/3 | 2/7 |  |  | Add dword register to rim dword |
| 02/r | ADDr8,r/m8 | 1/2 | 2/6 | 2/7 | 3/9+EA | Add rim byte to byte register |
| 03/r | ADD r16,r/m16 | 1/2 | 2/6 | 2/7 | 3/9+EA | Add rim word to word register |
| 03/r | ADD r32,r 1m32 | 1/2 | 2/6 |  |  | Add rim dword to dword register |

* ADD performs an integer addition of the two operands (DEST and SRC). The result of the addition is assigned to the first operand (DEST), and the flags are set accordingly. When an immediate byte is added to a word or doubleword operand, the immediate value is sign-extended to the size of the word or doubleword operand.

#### `AND`

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  |  |  |  | 0 |  |
| 20/r | ANDr/m8,r8 | 1/3 | 2/7 | 2/7 | 3/16+EA | AND byte register into rim byte |
| 21/r | AND r/m16,r16 | 1/3 | 2/7 | 2/7 | 3/16+EA | AND word register into rim word |
| 21/r | AND r/m32,r32 | 1/3 | 2/7 |  |  | AND dword register to rim dword |
| 22 Ir | ANDr8,r/m8 | 1/2 | 2/6 | 2/7 | 3/9+EA | AND rim byte to byte register |
| 23/r | AND r16,r/m16 | 1/2 | 2/6 | 2/7 | 3/9+EA | AND rim word to word register |
| 23/r | AND r32,r Im32 | 1/2 | 2/6 |  |  | AND rim dword to dword register |
| 25 iw | AND AX~imm16 |  | 2 | 3 | 4 | AND immediate word to AX |
| 25 id | AND EAX,imm32 |  | 2 |  |  | AND immediate dword to EAX |
| 80/4ib | ANDr/m8,imm8 | 113 | 2/7 | 3/7 | 4/17+EA | ANDimmediatebytetor/m byte |
| 81 14iw | ANDr/ml6,imml6- | 113 | 2/7 | 3/7 | 4/17+EA | AND immediate word to r/m word |
| 81/4id | ANDr/m32,imm32 | 113 | 2/7 |  |  | ANDimmediatedword to rim word |
| 83/4ib | ANDr/m16,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | AND sign-extended immediate byte with rim word |
| 83 14 ib | AND r Im32,imm8 | 1/3 | 2/7 |  |  | AND sign-extended immediate byte with rim dword |

o * 24ib ANDAL,imm8 234 AND immediate byte to AL Each bit of the result of the AND instruction is a 1 if both corresponding bits of the operands are 1; otherwise, it becomes a O. The optimized form of AND is MASKFLAG (see Chapter 3).

#### `ARPL`

*Adjust RPL field of selector*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 63/r | ARPLrl | 9/9 | pm=20/21 | pm=lO/l1 | Adjust RPL of rlm16 to not less than |
|  | m16,r16 |  |  |  | RPLofr16 |

The ARPL instruction has two operands. The first operand is a 16-bit memory variable or word register that contains the value of a selector. The second operand is a word register. If the RPL field ("requested privilege level"- bottom two bits) of the first operand is less than the RPL field of the second operand, the zero flag is set to 1 and the RPL field of the first operand is increased to match the second operand. Otherwise, the zero flag is set to 0 and no change is made to the first operand. ARPL appears in operating system software, not in application program~. It is used to guarantee that a selector parameter to a subroutine does not request more privilege than the caller is allowed. The second operand of ARPL is normally a register that contains the CS selector value of the caller.

#### `BOUND`

*Check array index against bounds*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 62/r | BOUND r16, 7 | 7 | 10 | 13 | Check if r16 is within m16&16 bounds (passes test) |
| 62/r | BOUND r32, 7 | 7 | 10 |  | Check if r32 is within m32&32 bounds (passes test) |

BOUND ensures that a signed array index is within the limits specified by a block of memory consisting of an upper and a lower bound. Each bound uses one word for an operand-size attribute of 16 bits and a doubleword for an operand-size attribute of 32 bits. The first operand (a register) must be greater than or equal to the first bound in memory (lower bound), and less than or equal to the second bound in memory (upper bound). If the register is not within bounds, an Interrupt 5 occurs; the return ElP points to the BOUND instruction. The bounds limit data structure is usually placed just before the array itself, making the limits addressable via a constant offset from the beginning of the array.

#### `BSF`

*Bit scan forward*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFBC | BSF r16,r/m16 | 6--42/7-43 | 10+3n | Bit scan forward on rim word |
| OFBC | BSF r32,r/m32 |  | 10+3n | Bit scan forward on r / m dword |

BSF scans the bits in the second word or doubleword operand starting with bit o. The ZF flag is cleared if the bits are all 0; otherwise, the ZF flag is set and the destination register is loaded with the bit index of the first set bit.

#### `BSR`

*Bit scan reverse*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFBD | BSRr16,r/m16 | 6-103/7-104 | 10+3n | Bit scan reverse on r / m word |
| OFBD | BSRr32,r/m32 | 6-103/7-104 | 10+3n | Bit scan reverse on r / m dword |

BSR scans the bits in the second word or doubleword operand from the most significant bit to the least significant bit. The ZF flag is cleared if the bits are all 0; otherwise, ZF is set and the destination register is loaded with the bit index of the first set bit found when scanning in the reverse direction.

#### `BSWAP`

*i486 processors and greater*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
| OFC8/r | BSWAPr32 | 1 | Swap bytes to convert little/big endian data in a 32- bit register to big/little endian form. |

BSW AP reverses the byte order of a 32-bit register, converting a value in little/ big endian form to big/little endian form. When BSWAP is used with a 16-bit operand size, the result left in the destination register is undefined.

#### `BT`

*Bit test*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFA3 | BTr/m16,r16 | 3/8 | 3/12 | Save bit in carry flag |
| OFA3 | BTr/m32,r32 | 3/8 | 3/12 | Save bit in carry flag |
| OFBA /4ib | BTr/m16,imm8 | 3/3 | 3/6 | Save bit in carry flag |
| OFBA /4 | ib BT r/m32,imm8 | 3/3 | 3/6 | Save bit in carry flag |

BT saves the value of the bit indicated by the base (first operand) and the bit offset (second operand) into the carry flag.

#### `BTC`

*Bit test and complement*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFBB | BTC r/m16,r16 | 6/13 | 6/13 | Save bit in carry flag and complement |
| OFBB | BTC r / m32,r32 | 6/13 | 6/13 | Save bit in carry flag and complement |
| OFBA/7ib | BTC r/m16,imm8 | 6/8 | 6/8 | Save bit in carry flag and complement |
| OF BA /7ib | BTC r/m32,imm8 | 6/8 | 6/8 | Save bit in carry flag and complement |

BTC saves the value of the bit indicated by the base (first operand) and the bit offset (second operand) into the carry flag and then complements the bit.

#### `BTR`

*Bit test and reset*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFB3 | BTR r/m16,r16 | 6/13 | 6/13 | Save bit in carry flag and reset |
| OFB3 | BTR r / m32,r32 | 6/13 | 6/13 | Save bit in carry flag and reset |
| OFBA /6 | ib BTRr/m16,imm8 | 6/8 | 6/8 | Save bit in carry flag and reset |
| OFBA /6 | ib BTRr/m32,imm8 | 6/8 | 6/8 | Save bit in carry flag and reset |

BTR saves the value of the bit indicated by the base (first operand) and the bit offset (second operand) into the carry flag and then stores 0 in the bit.

#### `BTS`

*Bit test and set*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
|  |  | CIQ~ks |  | IJ~scripti()n • |
| OFAB | BTS r / m16,r16 | 6/13 | 6/13 | Save bit in carry flag and set |
| OFAB | BTS r / m32,r32 | 6/13 | 6/13 | Save bit in carry flag and set |
| OFBA /5ib | BTSr/m16,imm8 | 6/8 | 6/8 | Save bit in carry flag and set |
| OFBA /5ib | BTS r/m32,imm8 | 6/8 | 6/8 | Save bit in carry flag and set |

BTS saves the value of the bit indicated by the base (first operand) and the bit offset (second operand) into the carry flag and then stores 1 in the bit.

#### `CALL`

*Call Procedure*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 86 | Description |
|---|---|---|---|---|---|
| E8cw | CALLre116 | 3 | 7+m | 7 19 | Call near, displacement relative to next instruction |
| FF /2 | CALLr/m16 | 5/5 | 7+m/10+m | 16/21+EA Call near, 7/11 | re~ster in irect/ memory indirect |
| 9Acd | CALL ptr16:16 | 18,pm=20 | 17+m, | 13, 28 | Call |
|  |  |  | pm=34=m | pm=26 | intersegment, tc? full pointer gIVen |
| 9Acd | CALL ptr16:16 | pm=35 | pm=52+m | 41 | Call gate, same privilege |
|  |  | 486 | 386 | 286* 86 |  |
| 9Acd | CALL ptr16:16 | pm=69 | pm=86+m | 82 | Call gate, more privilege, no parameters |
| 9Acd | CALL ptr16:16 | pm=77+4x | pm=94+4x+m | 86+4x | Call gate, more privilege, x parameters |
| 9Acd | CALL ptr16:16 | pm=37+ts | ts | 177/182 | Call to task (via task state segment/task |
| FF /3 | CALL.m16:16 | 17,pm=20 | 22+m,pm38+m 16/29 | 37+EA | Call intersegment, address at r/mdword |
| FF /3 | CALLm16:16 | pm=35 | pm=56+m | 44 | Call gate, same privilege |
| FF /3 | CALLm16:16 | pm=69 | pm=90+m | 83 | Call gate, more privilege, no parameters |
| FF /3 | CALLm16:16 | pm=77+4x | pm=98+4x+m | 90+4x+m | Call gate, more privilege, x parameters |
| FF /3 | CALLm16:16 | pm=37+ts | 5 + ts | 180/185 | Call to task (via task state segment! task gate for 286) |
| E8cd | CALLre132 | 3 | 7+m |  | Call near, displacement relative to next instruction |
| FF /2 | CALLr/m32 | 5/5 | 7+m/10+m |  | Call near, indirect |
| 9Acp | CALL ptr16:32 | 18,pm=20 | 17+m,pm= |  | Call |
|  |  |  | 34+m |  | intersegment, t~ full pointer gIven |
| 9Acp | CALL ptr16:32 | pm=35 | pm=52+m |  | Call gate, same privilege |
| 9Acp | CALL ptr16:32 | pm=69 | pm=86+m |  | Call gate, more privilege, no parameters |
| 9Acp | CALL ptr32:32 | pm=77+4x | pm=94+4x+m |  | Call gate, more privilege,x parameters |
| 9Acp | CALL ptr16:32 | pm=37+ts | ts |  | Call to task |
| FF /3 | CALLm16:32 | 17,pm=20 | 22+m,pm=38+ |  | Call |
|  |  |  | m |  | intersegment, address at r/mdword |
| FF /3 | CALLm16:32 | pm=35 | pm=56+m |  | Call gate, same privilege |
| FF /3 | CALLm16:32 | pm=69 | pm=90+m |  | Call gate, more privilege, no parameters |
| FF /3 | CALLm16:32 | pm=77+4x | pm=98+4x+m |  | Call gate, more privilege, x parameters |
| FF /3 | CALLm16:32 | pm=37+ts | 5+ts |  | Call to task |

All flags are affected if a task switch occurs; no flags are affected if a task switch does not occur. Optode Iilstruction Clocks "Qescriptiort The CALL instruction causes the procedure named in the operand to be executed. When the procedure is complete (a return instruction is executed within the procedure), execution continues at the instruction that follows the CALL instruction. The action of the different forms of the instruction are described next. Near calls are those with destinations of type r I m16, r I m32, re116, rel32; changing or saving the segment register value is not necessary. The CALL re116 and CALL rel32 forms add a signed offset to the address of the instruction following CALL to determine the destination. The re116 form is used when the instruction's operand-size attribute is 16 bits; rel32 is used when the operand- size attribute is 32 bits. The result is stored in the 32-bit EIP register. With rel16, the upper 16 bits of EIP are cleared, resulting in an offset whose value does not exceed 16 bits. CALL r I m16 and CALL r I m32 specify a register or memory location from which the absolute segment offset is fetched. The offset fetched from rim is 32 bits for an operand-size attribute of 32 (r/m32), or 16 bits for an operand-size of 16 (r/m16). The offset of the instruction following CALL is pushed onto the stack. It will be popped by a near RET instruction within the procedure. The CS register is not changed by this form of CALL. The far calls, CALL ptr16:16 and CALL ptr16:32, use a 4-byte or 6-byte operand as a long pointer to the procedure called. The CALL m16:16 and m16:32 forms fetch the long pointer from the memory location specified (indirection). In real address mode or virtual 8086 mode, the long pointer provides 16 bits for the CS register and 16 or 32 bits for the EIP register (depending on the operand-size attribute). These forms of the instruction push both CS and IP or EIP as a return address. In protected mode, both long pointer forms consult the AR byte in the descriptor indexed by the selector part of the long pointer. Depending on the value of the AR byte, the call will perform one of the following types of control transfers: • a far call to the same protection level • an inter-protectioi1level far call • a task switch parameter passing to high-level language routines. See Chapter 7 of the Turbo Assember User's Guide for more details.

> * Add one clock for each byte in the next instruction executed (80286 only).
> Note: Turbo Assember extends the syntax of the CALL instruction to facilitate

#### `CBW`

*Convert byte to word*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 98 | CBW | 3 | 3 | 2 | 2 | AX sign-extend of AL |

CBW converts the signed byte in AL to a signed word in AX by extending the most significant bit of AL (the sign bit) into all of the bits of AB.

#### `CDQ`

*Convert doubleword to quadword*

**Flags:** `o 0 ITS ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| 99 | CDQ | 3 | 2 | EDX:EAX [(sign-extend ofEAX) |

CDQ converts the signed doubleword in EAX to a signed 64-bit integer in the register pair EDX:EAX by extending the most significant bit of EAX (the sign bit) into all the bits of EDX.

#### `CLC`

*Clear carry flag*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 0 |  | T | S Z | P A | C 0 |
| F8 | CLC | 2 | 2 | 2 | 2 |  |

CLC sets the carry flag to zero. It does not affect other flags or registers.

#### `CLD`

*Clear direction flag*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | 0 | T | S | Z A | P C |
|  |  | 0 |  |  |  |  |

c CLD 2 2 2 2 Clear direction flag CLD clears the direction flag. No other flags or registers are affected. After CLD is executed, string operations will increment the index registers (51 or Dl) that they use.

#### `CLI`

*Clear interrupt flag*

**Flags:** `o 0 ITS ZAP C`

o FA CLI 5 332 CLI clears the interrupt flag if the current privilege level is at least as privileged as lOPL. No other flags are affected. External interrupts are not recognized at the end of the CLI instruction or from that point on until the interrupt flag is set.

#### `CllS`

*Clear task switched flag*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 06 | CLTS | 7 | 5 | 2 |  |

TS = 0 (TS is in CRO, not the flag register) CLTS clears the task-switched (TS) flag in register CRO. This flag is set by the 386 every time a task switch occurs. The TS flag is used to manage processor extensions as follows: • Every execution of an ESC instruction is trapped if the TS flag if set. • Execution of aWAIT instruction is trapped if the MP flag and the TS flag are both set. Thus, if a task switch was made after an ESC instruction was begun, the processor extension's context may need to be saved before a new ESC instruction can be issued. The fault handler saves the context and resets the TS flag. CL TS appears in operating system software, not in application programs. It is a privileged instruction that can only be executed at privilege level O.

#### `CMC`

*Complement carry flag*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F5 | CMC | 2 | 2 | 2 | 2 | Complement carry flag |

CMC reverses the setting of the carry flag. No other flags are affected.

#### `CMP`

*Compare two operands*

**Flags:** `0 D I T S A P C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 3Cib | CMPAL,imm8 | 1 | 2 | 3 | 4 | Compare immediate byte to AL |
| 3Diw | CMP AX,imm16 | 1 | 2 | 3 | 4 | Compare immediate word from AX |
| 3Did | CMP EAX,imm32 |  | 2 |  |  | Compare immediate dword to EAX |
| 80/7ib | CMP r/m8,imm8 | 1/2 | 2/5 | 3/6 | 4/10+EA | Compare immediate byte to r / m byte |
| 81 /7 iw | CMP r/m16,imm16 | 1/2 | 2/5 | 3/6 | 4/10+EA | ComJ'are immediate word to r / m wor |
| 81 /7 id | CMP r/m32,imm32 | 1/2 | 2/5 |  |  | Compare immediate dword to r/maword |
| 83/7ib | CMP r/ml6,imm8 | 1/2 | 2/5 | 3/6 | 4/10+EA Compare sign extended immediate |  byte to r / m word |
| 83/7ib | CMP r /m32,imm8 | 1/2 | 2/5 |  |  | Compare sigtl extended immediate byte to r/mdword |
| 38/r | CMPr/m8,r8 | 1/2 | 2/5 | 2/7 | 3/9+EA | Compare byte register to r / m byte |
| 39/r | CMP r/mI6,r16 | 1/2 | 2/5 | 2/7 | 3/9+EA | Conrare word register to r / m wor |
| 39/r | CMP r /m32,r32 | 1/2 | 2/5 |  |  | Compare dword register to r/m dword |
| 3A/r | CMPr8,r/m8 | 1/2 | 2/6 | 2/6 | 3/9+EA | Compare r / m byte to byte register register register |

* 3B /r CMP r16,r/m8 1/2 2/6 2/6 3/9+EA Compare r / m word to word 3B /r CMP r32,r/m32 1/2 2/6 Compare r/m dword to dword CMP subtracts the second operand from the first but, unlike the SUB instruction, does not store the result; only the flags are changed. CMP is typically used in conjunction with conditional jumps and the SETcc instruction. If an operand greater than one byte is compared to an immediate byte, the byte value is first sign-extended.

#### `CMPS`

*Compare string operands*

#### `CMPSB`

*CMPSD 386 processors and greater*

#### `CMPSW`

#### `CMPSD`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| A6 | CMP5m8,m8 | 8 | 10 | 8 | 22 | Com~are b~tes E5:[(E)OI] (second operand) with (E)51 (first operand) |
| A7 | CMP5 m16,m16 | 8 | 10 | 8 | 22 | Compare words E5:[(E)DI] (second operand) with [(E)SI] (first operand) |
| A7 | CMP5m32,m32 | 8 | 10 |  |  | Compare dwords E5:[(E)OI] (second operand) with [(E)SI] (first operand) |
| A6 | CMP5B | 8 | 10 | 8 | 22 | Compare bytes E5:[(E)DI] with OS:[51] |
| A7 | CMP5W | 8 | 10 | 8 | 22 | Compare words E5:[(E)DI] with 05:[SI] |
| A7 | CMP50 | 8 | 10 |  |  | Compare dwords E5:[(E)DI] with 05:[SI] |

CMPS compares the byte, word, or doubleword pointed to by the source-index register with the byte, word, or doubleword pointed to by the destination-index register. If the address-size attribute of this instruction is 16 bits, SI and DI will be used for source- and destination-index registers; otherwise ESI and EDI will be used. Load the correct index values into SI and DI (or ESI and EDI) before executing CMPS. The comparison is done by subtracting the operand indexed by the destination- index register from the operand indexed by the source-index register. Note that the direction of subtraction for CMPS is [SI] - [DI] or [ESI] - [EDI]. The left operand (SI or ESI) is the source and the right operand (DI or EDI) is the destination. This is the reverse of the usual Intel convention in which the left operand is the destination and the right operand is the source. The result of the subtraction is not stored; only the flags reflect the change. The types of the operands determine whether bytes, words, or doublewords are compared. For the first operand (SI or ESI), the DS register is used, unless a segment override byte is present. The second operand (DI or EDI) must be addressable from the ES register; no segment override is possible. After the comparison is made, both the source-index register and destination- index register are automatically advanced. If the direction flag is 0 (CLD was executed), the registers increment; if the direction flag is 1 (STD was executed), the registers decrement. The registers increment or decrement by 1 if a byte is compared, by 2 if a word is compared, or by 4 if a doubleword is compared. CMPSB, CMPSW and CMPSD are synonyms for the byte, word, and doubleword CMPS instructions, respectively. CMPS can be preceded by the REPE or REPNE prefix for block comparison of CX or ECX bytes, words, or doublewords. Refer to the description of the REP instruction for more information on this operation.

#### `CMPXCHG`

*Compare and Exchange*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
|  |  | issuccessfUli6/10 if | ZF and load byte reg into rim byte. Else, |
|  |  | comparison fails | clear ZF and load r / m byte into AL. |
| OF B1/r | CMPXCHG r/m16,r16 | 6/7ifcomparison | Compare AX with rim word. If equal, set |
|  |  | issuccessfUli6/10if ZF | and load word reg into rim word. |
|  |  | comparison fails | Else, dear ZF and load rim word into AX. |
|  |  | is successfUli | 6/10 if set ZF and load dword reg into rim |
|  |  | comparison fails | dword. Else, clear ZF and load rim dword intoEAX. |
| Note: The | A-stepping of the i486 | used | the apcades OF A6 and OF A7. |

OF BO I r CMPXCHG r I m8,r8 617 if comparison Compare AL with rim byte. If equal, set OF B1 I r CMPXCHG r I m32,r32 617 if comparison Compare EAX with rim dword. If equal, The CMPXCHG instruction compares the accumulator (AL, AX, or EAX register) with DEST. If they are equal, SRC is loaded into DEST. Otherwise, DEST is loaded into the accumulator. DEST is the destination operand; SRC is the source operand. Protected mode exceptions: #GP(O) if the result is in a nonwritable segment; #GP(O) for an illegal memory operand effective address in the CS, DS, ES, FS, or GS segments; #5S(O) for an illegal address in the SS segment; #PF (fault code) for a page fault; #AC for an unaligned memory reference if the current privilege level is 3: Real mode exception: interrupt 13 if any part of the operand would lie outside the effective address space from 0 to OFFFFh. Virtual 8086 mode exceptions: interrupt 13, as in real mode; #PF and #AC, as in protected mode. interface to the processor's bus, the destination operand receives a write cycle without regard to the result of the comparison. DEST is written back if the comparison fails, and SRC is written into the destination otherwise. (The processor never produces a locked read without producing a locked write.)

> Note: This instruction can be used with a LOCK-prefix. In order to simplify

#### `CHPXCHG88`

*Compare and Exchange bytes*

**Flags:** `o D T S ZAP C`

The CMPXCHG8B instruction compares the 64-bit value in EDX:EAX with DEST. EDX contains the high-order 32 bits and EAX contains the low-order 32 bits of the 64-bit value. If they are equal, the 64-bit value in ECX:EBX is stored into DEST. ECX contains the high-order 32 bits and EBX contains the low-order 32 bits. Otherwise, DEST is loaded into EDX:EAX. The ZF flag is set if the destination operand and EDX:EAX are equal; otherwise it is cleared. The CF, PF, AF, SF, and OF flags are unaffected. Protected mode exceptions: #GP(O) if the result is ina nonwritable segment; #GP(O) for an illegal memory operand effective address in the CS, DS, ES, FS, or GS segments; #55(0) for an illegal address in the SS segment; #PF(fault code) for a page fault; #AC for unaligned memory reference if the current privilege level is 3. The destination operand must be a memory operand, not a register. If the CMPXCHG8B instruction is executed with a modr / m byte representing a register as the destination operand, #UD occurs. Real mode exception: interrupt 13 if any part of the operand would lie outside the effective address space from 0 to OFFFFh. Virtual 8086 mode exceptions: same exceptions as in real mode, plus #PF(fault code) for a page fault; #AC for unaligned memory reference if the current privilege level is 3. #UD if the modr / m byte represents a register as the destination. Notes: This instruction can be used with a LOCK prefix. In order to simplify interface to the processor's bus, the destination operand receives a write cycle without regard to the result of the comparison. DEST is written back if the comparison fails, and SRC is written into the destination otherwise. (The processor never produces a locked read without also producing a locked write.) The "r/m64" syntax had previously been used only in the context of floating point operations. It indicates a 64-bit value, in memory at an address determined by the modr / mbyte.

#### `CPUIO`

*CPU identification*

**Flags:** `o D ITS ZAP C`

The CPUID instruction provides information to software about the vendor, family, model, and stepping of microprocessor on which it is executing. An input value loaded into the EAX register for this instruction indicates what information should be returned by the CPUID instruction. Following execution of the CPUID instruction with a zero in EAX, the EAX register contains the highest input value understood by the CPUID instruction. For the Pentium processor, the value in EAX will be one. Also returned is a vender identification string contained in the EBX, EDX, and ECX registers. EBX contains the first four characters. For Intel processors, the vender identification string is "GenuineIntel" as follows: EBX-756e6547h (* "Genu", with 'G' in the low nibble of BL *) EDX-49656e69h (* "ine!", with 'i' in the low nibble of DL *) ECX-6c65746eh (* "ntel", with In' in the low nibble of CL *) Following execution of the CPUID instruction with an, input value of one loaded into the EAX register, bits 0-3 in EAX contain the stepping id of the microprocessor, bits 4-7 of EAX contain the model (the first model will be indicated by a 0001b in these bits) and bits 8-11 of EAX contain the family (5 for the Pentium processor family). Bits 12-31 of EAX are reserved, as well as EBX, and ECX. The Pentium processor sets the feature register, EDX, to 1bfh, indicating which features the Pentium processor supports. A feature flag set to one indicates that the corresponding feature is supported. The feature set is defined as follows: EDX (bit 0) FPU on chip EDX (bits 1-6) Nonessential, proprietary information (contactIntel for more information) EDX (bit 7) Machine Check Exception EDX (bit 8) CMPXCHG8B Instruction EDX (bits 9-31) Reserved Software should determine the vender identification in order to properly interpret the feature register flag bits. This function does not affect the CPU flags.

#### `cwo*`

*Convert word to doubleword*

**Flags:** `o D T S ZAP C`

cwo 99 3 2 2 5 DX:AX ~ sign-extend of AX CWD converts the signed word in AX to a signed doubleword in DX:AX by extending the most significant bit of AX into all the bits of DX. Note that CWD is different from CWDE. CWDE uses EAX as a destination, instead of DX:AX.

#### `CWDE`

*Convert word to doubleword*

**Flags:** `0 D T S Z A P C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 98 | CWDE | 3 | 3 |  |  | EAX f- sign-extend of AX |

CWDE converts the signed word in AX to a doubleword in EAX by extending the most significant bit of AX into the two most significant bytes of EAX. Note that CWDE is different from CWD. CWD uses DX:AX rather than EAX as a destination.

#### `DAA`

*Decimal adjust AL after addition*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 27 | DAA | 2 | 4 | 3 | 4 | Decimal adjust AL after addition |

* Execute DAA only after executing an ADD instruction that leaves a two-BCD- digit byte result in the AL register. The ADD operands should consist of two packed BCD digits. The DAA instruction adjusts AL to contain the correct two- digit packed decimal result.

#### `DAS`

*Decimal adjust AL after subtraction*

**Flags:** `D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 2F | DAS | 2 | 4 | 3 | 4 | Decimal adjust AL after subtraction |

o * Execute DAS only after a subtraction instruction that leaves a two-BCD-digit . byte result in the AL register. The operands should consist of two packed BCD digits. DAS adjusts AL to contain the correct packed two-digit decimal result.

#### `DEC`

*Decrement by*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | T I | S | Z A | P C |
| FE /1 | DECr/m8 | 1/3 | 2/6 | 2/7 | 3/15+EA | Decrement r / m byte by 1 |
| FF /1 | DECr/mI6 | 1/3 | 2/6 | 2/7 | 3/15+BA | Decrement r / m word by 1 |
|  | DEC r/rh32 | 1/3 | 2/6 |  |  | Decrement r / m dword by 1 |
| 48+rw | DECr16 |  | 2 | 2 | 3 | Decrement word register by 1 |
| 48+rW | DECr32 | 1 | 2 |  |  | Decrement dword register by 1 |

* DEC subtracts 1 from the operand. DEC does not change the carry flag. To affect the carry flag, use the SUB instruction with an immediate operand of 1.

#### `DIV`

*Unsigned divide*

**Flags:** `0 D T S Z A P C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| OpCO(l.e | InstrUction |  |  | Clocks |  | D~sCrlption |
| F6/6 | DIVr/m8 | 16/16 14/17 14/17 80/86+EA |  |  |  | UnsilS!led divide AX by r / m byte (AL=QUO, AH=REM) |
| F7/6 | DIVr/m16 | 24/24 22/25 22/25 144/154+EA |  |  |  | Uns~ed divide DX:AX bY' r /m wor (AX=QUO, DX=REM) |
| F7/6 | DIVr/m32 | 40/40 | 38/41 |  |  | Unsigned divide EDX:EAX ~ r /m dword (EAX=QUO, EDX= M) |
| byt~ | AX |  | r/m8 |  | AL | AH |
| word | DX:AX |  | r/ml6 |  | AX | DX |
| dword | EDX:EAX |  | r/m32 |  | EAX | EDX (386 only) |

DN performs an unsigned division. The dividend is implicit; only the divisor is given as an operand. The remainder is always less than the divisor. The type of the divisor determines which registers to use as follows: "Quotient Dl\i{derid ;t)~viso~ s~~: R4am~irid~ti '.

#### `ENTER`

*Make stack frame for procedure parameters*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| C8 iw 00 Enter | imm16,O | 14 | 10 | 11 | Make procedure stack frame |
| C8 iw 01 Enter imm16,1 |  | 17 | 12 | 15 | Make stack frame for procedure parameters |
| C8 iw ib Enter imm16,imm8 |  | 17+3n 15+4(n-l) 12+4(n-l) Make stack frame for procedure |  |  |  parameters |

ENTER creates the stack frame required by most block-structured high-level languages. The first operand specifies the number of bytes of dynamic storage allocated on the stack for the routine being entered. The second operand gives the lexical nesting level (0 to 31) of the routine within the high-level language source code. It determines the number of stack frame pointers copied into the new stack frame from the preceding frame. BP (or EBP, if the operand-size attribute is 32 bits) is the current stack frame pointer. If the operand-size attribute is 16 bits, the processor uses BP as the frame pointer and SP as the stack pointer. If the operand-size attribute is 32 bits, the processor uses EBP for the frame pointer and ESP for the stack pointer. If the second operand is 0, ENTER pushes the frame pointer (BP or EBP) onto the stack; ENTER then subtracts the first operand from the stack pointer and sets the frame pointer to the current stack-pointer value. For example, a procedure with 12 bytes of local variables would have an ENTER 12,0 instruction at its entry point and a LEAVE instruction before every RET. The 12 local bytes would be addressed as negative offsets from the frame pointer.

#### `HLT`

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F4 | HLT | 4 | 5 | 2 | 2 | Halt |

HLT stops instruction execution and places the x86 in a HALT state. An enabled interrupt, NMI, or a reset will resume execution. If an interrupt (including NMI) is used to resume execution after HLT, the saved CS:IP (or CS:EIP on an 386) value points to the instruction following HLT.

#### `IDIV`

*Signed divide*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F6/7 | IDIVr/m8 | 19/20 | 19 | 17/20 | 101-112/107-118+EA , | Srmed divide AX ~ r m ~e (AL=QU , AH= M) |
| F7/7 | IDIVr/m16 | 27/28 | 27 | 25/28 165-184/171-190+EA |  | Si~ed divide DX:AX EA word (AX=QUO, ~ X=REM) |
| F7/7 | IDIVr/m32 | 43/44 | 43 |  |  | S~eddivide E X:EMC by DWORD ~e (EAX=QUO, X=REM) |
| byte | r/m8 | AL |  | AH |  | AX |
| word | r/m16 | AX |  | DX |  | DX:AX |
| dword | r/m32 | EAX |  | EDX |  | EDX:EAX (386 only) |

IDIV performs a signed division. The dividend, quotient, and remainder are implicitly allocated to fixed registers. Only the divisor is given as an explicitr/ m operand. The type of the divisor determines which registers to use as follows: If the resulting quotient is too large to fit in the destination, or if the division is 0, an Interrupt 0 is generated. Non-integral quotients are truncated toward o. The remainder has the same sign as the dividend and the absolute value of the remainder is always less than the absolute value of the divisor.

#### `IMUL`

*Signed multiply*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F6/5 IMUL | r/m8 | 13-18/13-18 9-14/12-17 13/16 80-98/86- |  |  |  | AX ~AL * rim byte |
|  |  |  |  |  | 104+EA |  |
| F7/5 IMUL | r/m16 | 13-26/13-26 9-22/12-25 21/24 |  |  | 128-154/1~ | DX:AX ~AX * rim |
|  |  |  |  |  | 160+EA | word |
| F7/5 IMUL | r/m32 | 12-42/13-42 9-38/12-41 |  |  |  | EDX:EAX ~EAX* rim dword |
| r/m16 |  |  |  |  |  | register r / m word |
| r/m32 |  |  |  |  |  | ~dword register * r / m dword |
| 6B /rib IMULr16, |  | 13-26/13-26 9-14/12-17 21/24 |  |  |  | word register ~r/m16 |
| r/m16,imm8 |  |  |  |  |  | * sign-extended immediate byte |
| 6B / r ib IMUL r32, |  | 13-42 | 9-14/12-17 |  |  | dword register ~r / |
| r/m32,imm8 |  |  |  |  |  | m32 * sign-extended immediate byte |
| 6B / r ib IMUL |  | 13-26 | 9-14/12~17 | 21/24 |  | word re~ter ~word |
| r16,imm8 |  |  |  |  |  | register sign-extended immediate byte |
| 6B /rib IMUL |  | 13-42 | 9-14/12-17 |  |  | dword register |
| r32,imm8 |  |  |  |  |  | ~dword register * sign- extended immediate byte |
| 69/riw IMULr16, |  | 13-26/13-26 9-22/12-25 21/24 |  |  |  | word register ~r/m16 |
| r/m16,imm16 |  |  |  |  |  | immediate word |
| r/m32,imm32 |  |  |  |  |  | immediate dword |
| 69/riw IMUL |  | 13-26/13-26 9-22/12-25 |  |  |  | word register ~r/m16 |
| r16,imm16 |  |  |  |  |  | * immediate word |
| 69/rid IMUL |  | 13-42/ | 9-38/12-41 |  |  | dword ref:ter |
| r32,imm32 |  | 13-42 |  |  |  | ~r/m32 immediate dword |

OF AF /r IMUL r16, 13-26/13-26 9-22/12-25 word re~ster ~word OF AF /r IMUL r32, 13-42/13-42 9-38/12-41 dword register dword register r / m32 * 69 / r id IMUL r32, 13-42/13-42 9-38/12-41 IMUL performs signed multiplication. Some forms of the instruction use implicit register operands. The operand combinations for all forms of the instruction are shown in the "Description" column above. IMUL clears ilie overflow and carry flags under the following conditions: Instruction form Condition for clearing CF and OF AL = sign-extend of AL to 16 bits r/m8 AX = sign-extend of AX to 32 bits r/m16 EDX:EAX = sign-extend of EAX to 32 bits r/m32 r16,r/m16 Result exactly fits within r16 r32,r I m32 Result exactly fits within r32 r16,r I m16,imm16 Result exactly fits within r16 r32,r I m32,imm32 Result exactly fits within r32

#### `IN`

*Input from port*

**Flags:** `0 D T S Z A P C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| E4ib | INAL,immS | 14,pm=S* /2S**,vm=27 | 12,pm=6* /26** S | 10 Input byte from immedIate port intoAL |
| ESib | INAX,immS | 1,4,pm=S* /2S**,vm=27 | 12,pm=6* /26** S | 10 Input word from immediate port into AX |
| ESib | IN EAX,immS 14,pm=S* /2S**,vm=27 |  | 12,pm=6* /26** | Input dword from immediate port intoEAX |
| EC | INAL,OX | 14,pm=S* /2S**,vm=27 | 13,pm=7* /27** S | Input byte from S port OX into AL |
| EO | INAX,OX | 14,pm=S* /2S**,vm=27 | 13,pm=7* /27** S | S Input word from port OX into AX |
| EO | INEAX,OX | 14,pm=S* /2S**,vm=27 | 13,pm=7* /27** | Input dword from port OX into EAX |
| *I£ CPL | ::; IOPL |  |  |  |

**I£ CPL > IOPL or if in virtual 8086 mode IN transfers a data byte or data word from the port numbered by the second operand into the register (AL, AX, or EAX) specified by the first operand. Access any port from 0 to 65535 by placing the port number in the DX register and using an IN instruction with DX as the second parameter. These I/O instructions can be shortened by using an 8-bit port I/O in the instruction. The upper eight bits of the port address will be 0 when 8-bit port I/O is used.

#### `INC`

*Increment by*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  | 0 D | I T | S Z | P A | C |
| FE /0 | INCr/mS | 1/3 | 2/6 | 2/7 | 3/1S+EA | Increment r / m byte by 1 |
| FF /0 | INCr/m16 | 1/3 | 2/6 | 2/7 | 3/1S+EA | Increment r / m word by 1 |
| FF /6 | . INCr/m32 | 1/3 |  |  |  | Increment rim dword by 1 |
| 40+rw | INCr16 |  | 2 | 2 | 3 | Increment word register by 1 |
| 40+rd | INCr32 | 1 |  |  |  | Increment dword register by 1 |

* INC adds 1 to the operand. It does not change the carry flag. To affect the carry flag, use the ADD instruction with a second operand of 1.

#### `INS`

*Input from port to string*

#### `INSB`

*80186 processors and greater*

#### `INSW`

#### `INSD`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 6C INSr/m8,DX |  | 17,pm=1O* /32**,vm=30 15,pm=9* |  | /29** 5 | In~ut byte from rort D into ES:(E)D |
| 6D INS r/m16,DX 17,pm=10* /32**,vm=30 15,pm=9* |  |  |  | /29** 5 | In~ut word from port D into ES:(E)DI |
| 6D INS r/m32,DX |  | 17,pm=1O* /32**,vm=30 15,pm=9* |  | /29** | In~ut dword from port D into ES:(E)DI |
| 6C INSB |  | 17,pm=1O* /32**,vm=30 15,pm=9* |  | /29** 5 | In~ut byte from rort D into ES:(E)D |
| 6D INSW |  | 17,pm=10* /32**,vm=30 15,pm=9* |  | /29** 5 | In~ut word from port D into ES:(E)DI |
| 6D INSD |  | 17,pm=10* /32**,vm=30 15,pm=9* |  | /29** | In~ut dword from port D into ES:(E)DI |
| *If CPL ::; | IOPL |  |  |  |  |
| **If CPL > | IOPL or if in | virtual 8086 mode |  |  |  |

INS transfers data from the input port numbered by the DX register to the memory byte or word at ES:dest-index. The memory operand must be addressable from ES; no segment override is possible. The destination register is DI if the address-size attribute of the instruction is 16 bits, or EDI if the address-size attribute is 32 bits. INS does not allow the specification of the port number as an immediate value. The port must be addressed through the DX register value. Load the correct value into DX before executing the INS instruction. The destination address is determined by the contents of the destination index register. Load the correct index into the destination index register before executing INS. After the transfer is made, DI or EDI advances automatically. If the direction flag is 0 (CLD was executed), DI or EDI increments; if the direction flag is 1 (STD was executed), DI or EDI decrements. DI increments or decrements by 1 if a byte is input, by 2 if a word is input, or by 4 if a doubleword is input. INSB, INSW and INSD are synonyms of the byte, word, and doubleword INS instructions. INS can be preceded by the REP prefix for block input of CX bytes or words. Refer to the REP instruction for details of this operation.

#### `INT`

*Call to interrupt procedure*

#### `INTO`

| Opcode | Instruction | 86 | Description |
|---|---|---|---|
|  |  | 0 D | T I S Z A P C 0 0 |
| CC | INT3 | 26 | 33 23 52 Interrupt 3-trap to debugger |
| CC | INT3 | 44 | Interrupt 3-protected mode pm=59 40 |
| CC | INT3 | 71 | pm=99 78 Interrupt 3-protected mode |
| CC | INT3 | 82 | pm=119 Interrupt 3-from V86 mode to PLO |
| CC | INT3 | 37+ts | ts 167 Interrupt 3-protected mode |
| CDib | INTimm8 | 30 | 37 23 51 Interrupt numbered by immedIate byte |
| CDib | INTimm8 | 44 | pm=59 40 Interrupt-protected mode |
| CDib | INTimm8 | 77 | pm=99 78 Interrupt-protected mode |
| CDib | INTimm8 | 37+ts | ts 167 Interrupt-protected mode |
| CE | INTO | Pass:28, Fail:3, | Fail:3, Fail:4, Interrupt 4-if overflow flag is 1 |
|  |  | Fail:3 | Pass:24 Pass:53 ~m=3; ass:35 |
| CE | INTO | 46 | pm=59 41 Interrupt 4-Protected mode |
| CE | INTO | 73 | pm=99 79 Interrupt 4-Protected mode |
| CE | INTO | 84 | pm=119 Interrupt 4-from V86 mode to PLO |
| CE | INTO | 39+ts | ts 168 Interrupt 4-Protected mode |
| *Add one | clock for each | byte | of the next instruction executed (80286 only). |

The INT n instruction generates via software a call to an interrupt handler. The immediate operand, from a to 255, gives the index number into the interrupt descriptor table (IDT) of the interrupt routine to be called. In protected mode, the IDT consists of an array of eight-byte descriptors; the descriptor for the interrupt invoked must indicate an interrupt, trap, or task gate. In real address mode, the IDT is an array of four byte-long pointers. In protected and real address modes, the base linear address of the IDT is defined by the contents of theIDTR. The INTO conditional software instruction is identical to the !NT n interrupt instruction except that the interrupt number is implicitly 4, and the interrupt is made if the 86, 286, or 386 overflow flag is set. The first 32 interrupts are reserved by Intel for system use. Some of these interrupts are uSe for internally generated exceptions. !NT n generally behaves like a far call except that the flags register is pushed onto the stack before the return address. Interrupt procedures return via the lRET instruction, which pops the flags and return address from the stack. In real address mode, !NT n pushes the flags, CS and the return IP onto the stack, in that order, then jumps to the long pointer indexed by the interrupt number.

#### `INVD`

*Invalidate cache*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
| OF 08 | INVD | 4 | Invalidate entire cache |

The internal cache is flushed, and a special-function bus cycle is issued which indicates that external caches should also be flushed. Data held in write-back external caches is discarded. implemented differently on future Intel processors. It is the responsibility of hardware to respond to the external cache flush indication.

> Note: This instruction is implementation-dependent; its function might be

#### `INVLPG`

*Invalidate TLB entry*

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
|  |  | 0 D | T S Z P C A |
| OF 01/7 | INVLPGm | 12 for hit | Invalidate TLB entry |

Qpcode hlstructb.lll Clock DeScrl.i'ti~~ The INVLPG instruction is used to invalidate a single entry in the TLB, the cache used for table entries. If the TLB contains a valid entry that maps the address of the memory operand, that TLB entry is marked invalid. In both protected mode and virtual 8086 mode, an invalid opcode is g~nerated when used with a register operand. implemented differently on future Intel processors.

> Note: This instruction is implementation-dependent; its function might be

#### `IRET`

*Interrupt return*

#### `IRETD`

*IRETD 386 processors and greater*

#### `IRETW`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| CF | IRETW | 15 | 22,pm=38 17,pm=31 32 |  |  | Interrupt return (far return and pop flags) |
| CF | IRETW | 36 | pm=82 | 55 |  | Interrupt return |
| CF | IRETW | ts+32 | ts | 169 | Interrupt | return |
| CF | IREID | 15 | 22,pm=38 |  |  | Interrupt return (far return and pop flags) |
| CF | IRETD | 36 | pm=82 |  |  | Interrupt return to lesser privilege |
| CF | IREID | 15 | pm=60 |  | Interrupt | return to V86 mode |
| CF | IRETD | ts+32 | ts |  |  | Interrupt return |
| CF | IRET |  |  |  |  | Selects IRETW or IREID depen~ y on segment size of 16 or 32 bits. workS for VERSION T320 or higher. |
| *Add one | clock, for each | byte | in the | next instruction executed (80286 only). |  |  |

* * The flags register is popped from stack. In real address mode, lRET pops the instruction pointer, CS, and the flags register from the stack and resumes the interrupted routine. In protected mode, the action of IRET depends on the setting of the nested task flag (NT) bit in the flag register. When popping the new flag image from the stack, the IOPL bits in the flag register are changed only when CPL equals O. If NT equals 0, IRET returns from an interrupt procedure without a task switch. The code returned to must be equally or less privileged than the interrupt routine (as indicated by the RPL bits of the CS selector popped from the stack). If the destination code is less privileged, IRET also pops the stack pointer and SS from the stack. If NT equals 1, IRET reverses the operation of a CALL or INT that caused a task switch. The updated state of the task executing IRET is saved in its task state segment. If the task is re-entered later, the code that follows IRET is executed. IRETW pops WORD-style (if you use VERSION T320 or higher). If you're using VERSION T310 or less, use IRET; IRETW replaces old functionality of IRET.

#### `Jee`

*Jump if condition is met*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 77cb | JArel8 | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short if above | (CF=O and ZF=D) |
| 73cb | JAErel8 | 3/1 | 7+m+,3 | 7,3 | 16,4 | Jump short if above or equal (CF=O) |
| 72cb | JBrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if below (CF=l) |
| 76cb | JBErel8 | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if below or equal (CF=1 orZF=l) |
| 72cb | JC rel8 | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if carry (CF=1) |
| E3cb | JCXZrelS | 3/1 | 9+m,5 | S,4 | 1S,6 | Jump short if CX register is 0 |
| E3cb | JECXZrel8 | 3/1 | 9+m,5 |  |  | Jump short if ECX register is 0 |
| 74cb | JE relS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short if equal | (ZF=1) |
| 74cb | JZrelS | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if 0 (ZF=l) |
| 7Fcb | JGrelS | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if greater (ZF=O and SF=OF) |
| 7Dcb | JGErelS | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if greater or equal (SF=OF) |
| 7Ccb | JL relS | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short ifless (SF<>OF) |
| 7Ecb | JLErelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if less or equal (ZF=l andSF<>OF) |
| 76cb | JNArelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not above (CF=1 or ZF=l) |
| 72cb | JNAErelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not above or equal (CF=1) |
| 73cb | JNBreIS- | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not below (CF=O) |
| 77cb | JNBErelS | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not below or equal (CF=O and ZF=O) |
| 73cb | JNCrelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not carry (CF=O) |
| 75cb | JNErelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not equal (ZF=O) |
| 7Ecb | JNGrelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not greater (ZF=1 or SF<>OF) |
| 7Ccb | JNGErelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not greater or equal (SF<>OF) |
| 7Dcb | JNLrelS | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if not less (SF=OF) |
| 7Fcb | JNLErel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not less or equal (ZF=O and SF=OF) |
| 71cb | JNOrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not overflow (OF=O) |
| 7Bcb | JNPrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not parity (PF=O) |
| 79cb | JNSrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not sign (SF=O) |
| 75cb | JNZrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if not zero (ZF=O) |
| 70cb | JO rel8 | 3/1 | 7+m,3 | 7,3 | 16,4 Jump short | if overflow (OF=l) |
| 7Acb | JPrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if parity (PF=l) |
| 7Acb | JPE rel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if parity even (PF=l) |
| 7Bcb | JPOrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if parity odd (PF=O) |
| 78cb | JSrel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short if sign (SF=l) |
| 74cb | JZ rel8 | 3/1 | 7+m,3 | 7,3 | 16,4 | Jump short of zero (ZF=l) ZF= ) |
| OF 83 cw/cd | JAE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if above or equal (CF=O) |
| OF 82cw/cd | JB re116/32 | 3/1 | 7+m,3 |  |  | Jump near if below (CF=l) |
| OF 86cw/cd | JBE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if below or equal (CF=lor ZF=l) |
| OF 82cw/cd | JC re116/32 | 3/1 | 7+m,3 |  |  | Jump near if carry (CF=l) |
| OF 84cw/cd | JE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if equal (ZF=l) |
| OF 84cw/cd | JZ re116/32 | 3/1 | 7+m,3 |  |  | Jump near if 0 (ZF=l) |
| OF 8F cw/cd | JG re116/32 | 3/1 | 7+m,3 |  |  | Jumg near if greater (ZF=O and SF= F) |
| OF 8Dcw/cd | JGE re116/32 | 3/1 | 7+m,3 |  |  | JumJ> near if greater or equal (SF=OF) |
| OF 8C cw/cd | JL re116/32 | 3/1 | 7+m,3 |  |  | Jump near if less (SF<>OF) |
| OF 8E cw/cd | JLE re116/32 | 3/1 | 7+m,3 |  |  | Jum~ near if less or equal(ZF=l and F<>OF) |
| OF 86cw/cd | JNA re116/32 | 3/1 | 7+m,3 |  |  | Jumr near if not above (CF=l or ZF= ) |
| OF 82cw/cd | JNAE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not above or equal (CF=l) |
| OF 83cw/cd | JNB re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not below (CF=O) (CF=O and ZF=O |
| OF83cw/cd | JNC re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not carry and ZF=O) |
| OF 85 cw/cd | JNE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not equal (ZF=O) |
| OF 8E cw/cd | JNG re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not greater (ZF=l or SF<>OF) |
| OF8Ccw/cd | JNGE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not greater or equal (SF<>OF) |
| OF8Dcw/cd | JNL re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not less (SF=OF) |
| OF 8F cw/cd | JNLE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not less or equal (ZF=O and SF=OF) |
| OF 81 cw/cd | JNO re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not overflow (OF=O) |
| OF 8B cw/cd | JNP re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not parity (PF=O) |
| OF 89 cw/cd | JNS re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not sign (SF=O) |
| OF 85 cw/cd | JNZ re116/32 | 3/1 | 7+m,3 |  |  | Jump near if not zero (ZF=O) |
| OF 80 cw/cd | JOre116/32 | 3/1 | 7+m,3 |  |  | Jump near if overflow (OF=l) |
| OF 8Acw/cd | . JP re116/32 | 3/1 | 7+m,3 |  |  | Jump near if parity (PF=l) |
| OF8Acw/cd | JPE re116/32 | 3/1 | 7+m,3 |  |  | Jump near if parity even (PF=l) |
| OF 88 cw/cd | JSre116/32 | 3/1 | 7+m,3 |  |  | Jump near if sign (SF=l) |
| OF 84 cw/cd | JZre116/32 | 3/1 | 7+m,3 |  |  | Jump near if zero (ZF=l) |
| *When a | jump is taken, add one | clock for every byte |  |  | of the | next instruction executed (80286 |
| only). |  |  |  |  |  |  |
| JZ FARLABELi |  |  |  |  |  |  |
|  | JNZ BEYONDi |  |  |  |  |  |
|  | JMP FARLABELi |  |  |  |  |  |
| BEYOND: |  |  |  |  |  |  |

/;Oncks ;;Il\Sf:Nctlott JPO re116/32 7+m,3 Jump near if parity odd (PF=O) OF 8B cw/cd 3/1 clock count is for the false condition (branch not taken). re116/32 indicates that these instructions map to two; one with a 16-bit relative displacement, the other with a 32-bit relative displacement, depending on the operand-size attribute of the instruction. Conditional jumps (except JCXZ/JECXZ) test the flags which have been set by a previous instruction. The conditions for each mnemonic are given in parentheses after each description above. The terms "less" and "greater" are used for comparisons of signed integers; "above" and "below" are used for unsigned integers. If the given condition is true, a jump is made to the location provided as the operand. Instruction coding is most efficient when the target for the conditional jump is in the current code segment and within -128 to + 127 bytes of the next instruction's first byte. The jump can also target -32768 through +32767 (segment size attribute 16) or -2 to the 31st power +2 to the 31st power -1 (segment size attribute 32) relative to the next instruction's first byte. When the target for the conditional jump is in a different segment, use the opposite case of the jump instruction (that is, JE and JNE), and then access the target with an unconditional far jump to the other segment. For example, you cannot code You must instead code Because there can be several ways to interpret a particular state of the flags, TASM provides more than one mnemonic for mostof the conditional jump opcodes. For example, if you compared two characters in AX and want to jump if they are equal, use JE; or, if you ANDed AX with a bit field mask and only want to jump if the result is 0, use JZ, a synonym for JE. JCXZ/JECXZ differs from other conditional jumps because it tests the contents of the CX or ECX register for 0, not the flags. JCXZ/JECXZ is useful at the beginning of a conditional loop that terminates with a conditional loop instruction (such as LOOPNE TARGET LABEL). The JCXZ/JECXZ prevents entering the loop with ex or ECX equal to zero, which would cause the loop to execute 64K or 32G times instead of zero times.

> Note: The first clock count is for the true condition (branch taken); the second

#### `JMP`

*Jump*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | T S I Z | A C P |  |  |
| EBcb | JMPre18 | 3 | 7+m | 7 | 15 | Jump short |
| E9cw | JMPre116 | 3 | 7+m | 7 | 15 | Jump near |
| FF /4 | JMPr/ml6 | 5/5 | 7+m/l0+m | 7/11 | 1l/18+EA Jump near |  indiiect |
| EAcd | JMP ptr16:16 17pm=19 |  | 12+m, pm=27+m | ll,pm=23 | 15 | Jump intersegment, 4-bte munediate ad ress |
| EAcd | JMP ptr16:16 | 32 | pm=45+m | 38 |  | Jump to call gate, same privilege |
| EAcd | JMP ptr16:16 42+ts |  | ts | 175 |  | Jump via task state segment |
| EAcd | JMP ptr16:16 43+ts |  | ts | 180 | 24+EA | Jump via task gate |
| FF /5 | JMPm16:16 | 13,pm=18 | 43+m,pm=31 +m 15,pm=26 |  |  | Jump r/mI6:16 indiiect and intersegment |
| FF /5 | JMPm16:16 | 31 | pm=49+m | 41 |  | Jump to call gate, same privilege |
| FF /5 | JMPm16:16 | 41+ts | 5+ts | 178 |  | Jump via task state segment |
| FF /5 | JMPm16:16 | 42+ts | 5+ts | 183 |  | Jump via task gate |
| E9cd | JMPre132 | 3 | 7+m |  |  | Jump near |
| FF /4 | JMPr/m32 | 5/5 | 7+m,10+m |  |  | Jump near |
| EAcp | JMP ptr16:32 | 13,pm=18 | 12+m, pm=27+m |  |  | Jump intersegment, 6-b£e munediate ad ess ' |
| EAcp | JMP ptr16:32 | 31 | pm=45+m |  |  | Jump to call gate, same privilege |
| EAcp | JMP ptr16:32 | 42+ts | ts |  |  | Jump via task state segment |
| EAcp | JMP ptr16:32 | 43+ts | ts |  |  | Jump via task gate |
| FF /5 | JMPm16:32 | 13,pm=18 | 43+m, pm=31 +m |  |  | Jump intersegment address at r / m dword |
| FF /5 | JMPm16:32 | 31 | pm=49+m |  |  | Jump to call gate, same privilege |
| FF /5 | JMPm16:32 | 41+tsl0 | 5+ts |  |  | Jump via task state segment |
| FF /5 | JMPm16:32 | 42+ts | 5+ts |  |  | Jump via task gate |
| *Add one | clock for every | byte | of the next instruction executed (80286 only). |  |  |  |

All if a task switch takes place; none if no task switch occurs. The JMP instruction transfers control to a different point in the instruction stream without recording return information. The action of the various forms ofthe instruction are shown below. Jumps with destinations of type r/m16, r/m32, re116, and rel32 are near jumps and do not involve changing the segment register value. The JMP re116 and JMP rel32 forms oithe instruction add an offset to the address of the instruction following the JMP to determine the destination. The re116 form is used when the instruction's operand-size attribute is 16 bits (segment size attribute 16 only); rel32 is used when the operand-size attribute is 32 bits (segment size attribute 32 only). The result is stored in the 32-bit EIP register. With re116, the upper 16 bits of EIP are cleared, which results in an offset whose value does not exceed 16 bits. JMP r I m16 and JMP r I m32 specifies a register or memory location from which the absolute offset from the procedure is fetched. Theoffset fetched from rim is 32 bits for an operand-size attribute of 32 bits (r Im32), or 16 bits for an operand- size attribute of 16 bits (r/m16). The JMP ptr16:16 and ptr16:32 forms of the instruction use a four-byte or six- byte operand as a long pointer to the destination. The JMP m16:16 and m16:32 forms fetch the long pointer from the memory location specified (indirection). In real address mode or virtual 8086 mode, the long pointer provides 16 bits for the CS register and 16 or 32 bits for the EIP register (depending on the operand- size attribute). In protected mode, both long pointer forms consultthe access rights (AR) byte in the descriptor indexed by the selector part of the long pointer. Depending on the value of the AR byte, the jump will perform one of the following types of control transfers: • a jump to a code segment at the same privilege level • a task switch

#### `LAHF`

*Loads flags into AH register*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 9F | LAHF | 3 | 2 | 2 | 4 | Load: AH = flags SF ZF xx AF xx PF xx CF |

LAHF transfers the low byte of the flags word to AH. The bits, from MSB to LSB, are sign, zero, indeterminate, auxiliary carry, indeterminate, parity, indeterminate, and carry.

#### `LAR`

*Load access rights byte*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 02/r | LAR r16,r/m16 11/11 pm=15/16 14/16 |  |  |  | r16f-r/m16 masked by FFOO |

OF 02 /r LAR r32,r/m32 11/11 pm=15/16 r32f-r/m32 masked by OOFxFFOO The LAR instruction stores a marked form of the second doubleword of the descriptor for the source selector if the selector is visible at the CPL (modified by the selector's RPL) and is a valid descriptor type. The destination Tegister is loaded with the high-order doubleword of the descriptor masked by OOFxFFOO, and ZF is set to 1. The x indicates that the four bits corresponding to the upper four bits of the limit are undefined in the value loaded by LAR. If the selector is invisible or of the wrong type, ZF is cleared. If the 32-bit operand size is specified, the entire 32-bit value is loaded into the 32-bit destination register. If the 16-bit operand size is specified, the lower 16- bits of this value are stored in the 16-bit destination register. All code and data segment descriptors are valid for LAR. (See your Intel manual for valid segment and gate descriptor types for LAR.)

#### `LEA`

*Load effective address offset*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 8D/r | LEAr16,m 1 |  | 2 | 3 | 2+EA | Store effective address for m in register r16 |
| 8D / r | LEA r32,m 1 |  | 2 |  |  | Store effective address for m in register r32 |
| 8D/r | LEAr16,m 1 |  | 2 |  |  | Store effective address for m in register r16 |
| 8D / r | LEA r32,m 1 |  | 2 |  |  | Store effective address for m in register r32 |

()pc~~~;:ltisij!u.ctiQn ' LEA calculates the effective address (offset part) and stores it in the specified register. The operand-size attribute of the instruction is determined by the chosen register. The address-size attribute is determined by the USE attribute of the segment containing the second operand. The address-size and operand-size attributes affect the action performed by LEA, as follows: Operand size Address size Action performed 16 16 16-bit effective address is calculated and stored in requested 16-bit register destination. 16 32 32-bit effective address is calculated. The lower 16 bits of the address are stored in the requested 16-bit register destination. 32 16 16-bit effective address is calculated. The 16-bit address is zero-extended and stored in the requested 32-bit register destination. 32 32 32-bit effective address is calculated and stored in the requested 32-bit register destination.

#### `LEAVE`

*High-level procedure exit*

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
|  | 0 | D | T I | S | P C Z A |
| C9 | LEAVE | 5 | 4 | 5 | SetSPto BP |
| C9 | LEAVE | 5 | 4 |  | Set ESP to EBP |

LEAVE reverses the actions of the ENTER instruction. By copying the frame pointer to the stack pointer, LEAVE releases the stack space used by a procedure for its local variables. The old frame pointer is popped into BP or EBP, restoring the caller's frame. A subsequent RET nn instruction removes any arguments pushed onto the stack of the exiting procedure.

#### `LGOT/LIOT`

*Load globallinterrupt descriptor table register*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 01 /2 | LGDT m16&32 | 11 | 11 | 11 | Load m into global descriptor table register |
| OF 01 /3 | LIDT m16&32 | 11 | 11 | 12 | Load m into interrupt descriptor table register |

The LCDT and LIDT instructions load a linear base address and limit value from a six-byte data operand in memory into the CDTR or IDTR, respectively. If a 16-bit operand is used with LCDT or LIDT, the register is loaded with a 16- bit limit and a 24-bit base, and the high-order 8 bits of the 6-byte data operand are not used. If a 32-bit operand is used, a 16-bit limit and a 32-bit base is loaded; the high-order 8 bits of the 6-byte operand are used as high-order base address bits. The SCDT and SIDT instructions always store into all 48 bits of the 6-byte data operand. With the 80286, the upper 8 bits are undefined after SCDT or SIDT is executed. With the 386, the upper 8 bits are written with the high-order 8 address bits, for both a 16-bit operand and a 32-bit operand. If LCDT or LIDT is used with a 16-bit operand to load the register stored by SCDT or SIDT, the upper 8 bits are stored as zeros. LCDT and LIDT appear in operating system software; they are not used in application programs. They are the only instructions that directly load a linear address (i.e., not a segment relative address) in 386 protected mode.

#### `LGS`

*Load full pOinter*

#### `LSS`

*LGS/LSS/LFS 386 processors and greater*

#### `LFS`

**Flags:** `0 D I T S Z A P C`

#### `LOS`

#### `LES`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| C5/r | LDS r16,m16:16 | 6/12 | 7,pm=22 | 7,pm=21 | 16+EA Load DS:r16 | with pointer from memory |
| C5/r | LOS r32,m16:32 | 6/12 | 7,pm=22 |  |  | Load DS:r32 with pointer from memory |
| OFB2/r | LSS r16,m16:16 | 6/12 | 7,pm=22 |  |  | Load SS:r16 with pointer from memory |
| OF B2 /r | LSS r32,m16:32 | 6/12 | 7,pm=22 |  |  | Load SS:r32 with pointer from memory |
| C4/r | LES r16,m16:16 | 6/12 | 7,pm=22 | 7,pm=21 | 16+EA Load | ES:r16 with pointer from memory |
| C4/r | LES r32,m16:32 | 6/12 | 7,pm=22 |  |  | Load ES:r32 with pointer from memory |
| OFB4 /r | LFS r16,m16:16 | 6/12 | 7,pm=25 |  |  | Load FS:r16 with pointer from memory . frommemory |
| OFB5/r | LGS r16,m16:16 | 6/12 | 7,pm=25 |  |  | Load GS:r16 with pointer from memory from memory |

OFB4 /r LFS r32,m16:32 6/12 7,pm=25 Load FS:r32 with pointer OF B5 /r LGS r32,m16:32 6/12 7,pm=25 Load GS:r32 with pointer These instructions read a full pointer from memory and store it in the selected segment register: register pair. The full pointer loads 16 bits into the segment register 55, D5, E5, F5, or G5. The other register loads 32 bits if the operand-size attribute is 32 bits, or loads 16 bits if the operand-size attribute is 16 bits. The other 16- or 32-bit register to be loaded is determined by the r16 or r32 register operand specified. When an assignment is made to one of the segment registers, the descriptor is also loaded into the segment register. The data for the register is obtained from the descriptor table entry for the selector given. A null selector (values 0000-0003) can be loaded into D5, E5, F5, or G5 registers without causing a protection exception. (Any subsequent reference to a segment whose corresponding segment register is loaded with a null selector to address memory causes a #GP(O) exception. No memory reference to the segment occurs.)

#### `LLDT`

*Load local descriptor table register*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 00/2 | LLDT r/m 16 | 11/11 | 20 | 17/19 Load selector | r/m16 into LDTR |

LLDT loads the local descriptor table register (LDTR). The word operand (memory or register) to LLDT should contain a selector to the global descriptor table (GDT). The GDT entry should be a local descriptor table. If so, then the LDTR is loaded from the entry. The descriptor registers D5, E5, 55, F5, G5, and C5 are not affected. The LDT field in the task state segment does not change. The selector operand can be 0; if so, the LDTR is marked invalid. All descriptor references (except by the LAR, VERR, VERW or L5L instructions) cause a #GP fault. LLDT is used in operating system software; it is not used in application programs.

#### `LMSW`

*Load machine status word*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 01/6 | LMSW r/m 16 | 13/13 10/13 |  | 3/6 | Load r/m 16 into machine status word |

LMSW loads the machine status word (part of CRO) from the source operand. This instruction can be used to switch to protected mode; if so, it must be followed by an intrasegment jump to flush the instruction queue. LMSW will not switch back to real address mode. LMSW is used only in operating system software. It is not used in application programs.

#### `LOCK`

*Assert LOCK# signal prefix*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | LOCK |  |  |  | 2 | Assert LOCK# signal for the next instruction |

o FO 1 0 The LOCK prefix causes the LOCK# signal of the CPU to be asserted during execution of the instruction that follows it. In a multiprocessor environment, this signal can be used to ensure that the CPU has exclusive use of any shared memory while LOCK# is asserted. The read-modify-write sequence typically used to implement test-and-set on the 386 is the BTS instruction. On the 386 and i486, the LOCK prefix functions only with the following instructions: BT, BTS, BTR, BTC mem, reg/imm XCHG reg,mem XCHG mem,reg ADD, OR, ADC, SBB, mem, reg/imm AND, SUB, XOR NOT, NEG, INC, DEC mem An undefined opcode trap will be generated if a LOCK prefix is used with any instruction not listed above. XCHG always asserts LOCK # regardless of the presence or absence of the LOCK prefix. The integrity of the LOCK is not affected by the alignment of the memory field. Memory locking is observed for arbitrarily misaligned fields. Locked access is not assured if another CPU processor is executing an instruction concurrently that has one of the following characteristics: • Is not preceded by a LOCK prefix. • Is not one of the instructions in the preceding list. • Specifies a memory operand that does not exactly overlap the destination operand. Locking is not guaranteed for partial overlap, even if one memory operand is wholly contained within another.

#### `LOOS`

*Load string operand*

#### `LOOSe`

*LODSD 386 processors and greater*

#### `LOOSW`

#### `LOOSO`

| Opcode | Instruction | 286 | 86 | Description |
|---|---|---|---|---|
| AC | LODSm18 5 5 | 5 | 12 | Load byte [(E)SI] into AL |
| AD | LODSm16 5 5 | 5 | 12 | Load word [(E)SI] into AX |
| AD | LODSm32 5 5 |  |  | Load dword [(E)SI] into EAX |
| AC | LODSB 5 5 | 5 | 12 | Load byte DS:[(E)SI] into AL |
| AD | LODSW 5 5 | 5 | 12 | Load word DS:[(E)SI] into AX |
| AD | LODSD5 5 |  |  | Load dword DS:[(E)SI] into EAX |

LaDS loads the AL, AX, or EAX register with the memory byte, word, or doubleword at the location pointed to by the source-index register. After the transfer is made, the source-index register is automatically advanced. If the direction flag is 0 (CLD was executed), the source index increments; if the direction flag is 1 (STD was executed), it decrements. The increment or decrement is 1 if a byte is loaded, 2 if a word is loaded, or 4 if a doubleword is loaded. If the address-size attribute for this instruction is 16 bits, 51 is used for the source-index register; otherwise the address-size attribute is 32 bits, and the ESl register is used. The address of the source data is determined solely by the contents of ES1/S1. Load the correct index value into 51 before executing the LaDS instruction. LODSB, LODSW, LODSD are synonyms for the byte, word, and doubleword LaDS instructions. LaDS can be preceded by the REP prefix; however, LaDS is used more typically within a LOOP construct, because further processing of the data moved into EAX, AX, or AL is usually necessary.

#### `LOOP`

*Loop control with CX counter*

#### `LOOPcond`

*Loop control with CXlECX counter*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | T | Z S | A P C |  |
| E2cb | LOOPre18 | 2,6 | ll+m | 8,noj=4 | 17,noj=5 | DEC Count; jump short if Count a |
| El cb | LOOPEre18 | 9,6 | ll+m | 8,noj=4 | 18,noj=6 | DEC Count jump short if Count a an ZF=l |
| E1 cb | LOOPZre18 | 9,6 | ll+m | 8,noj=4 | 18,noj=6 | DEC Count jump short if Count a an ZF=l |
| Eacb | LOOPNEre18 | 9,6 | ll+m | 8,noj=4 | 19,noj=5 | DEC Count jump short if Count a an ZF=a |
| Ea'cb | LOOPNZre18 | 9,6 | ll+m | 8,noj=4 | 19,noj=5 | DEC Count jump short if Count a an ZF=a |

LOOP decrements the count register without changing any of the flags. Conditions are then checked for the form of LOOP being used. If the conditions are met, a short iumpis made to the label given by the operand to LOOP. If the address-size attribute is 16 bits, the CX register is used as the count register; otherwise the ECX register is used (386 only). The operand of LOOP must be in the range from 128 (decimal) bytes before the instruction to 127 bytes phead of the instruction. The LOOP instructions provide iteration control and combine loop index management with conditional branching. Use the LOOP instruction by10ading an unsigned iteration count into the count register, then code the LOOP at the end of a series of instructions to be iterated. The destination of LOOP is a label that points to the beginning of the iteration.

#### `LSL`

*Load segment limit*

**Flags:** `o D ITS ZAP C`

OF 03 /r LSL r16,r/m16 10/tO pm=20/21 14/16 Load: r16~segment limit, selector OF 03 /r LSL r32,r / m32 10/tO pm=20/21 Load: r32~segment limit, segment OF 03 /r LSL r16,r/m16 10/tO 14/16 Load: r16~segment limit, segment pm=25/26 OF 03 /r LSL r32,r/m32 10/tO pm=26/26 Load: r32~segment limit selector The LSL instruction loads a register with an unscrambled segment limit, and sets ZF to l, provided that the source selector is visible at the CPL weakened by RPL, and that the descriptor is a type accepted by LSL. Otherwise, ZF is cleared to 0, and the destination register is unchanged. The segment limit is loaded as a byte granular value. If the descriptor has a page granular segment limit, LSL will translate it to a byte limit before loading it in the destination register (shift left 12 the 20-bit "raw" limit from descriptor, then OR with OOOOOFFFH). The 32-bit forms of this instruction store the 32-bit byte granular limit in the 16-bit destination register. Code and data segment descriptors are valid for LSL.

#### `LTR`

*Load task register*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 00 /3 | LTRr/m16 | 20/20 | pm=23/27 | 17/19 | Load EA word into task register |

LTR loads the task register from the source register or memory location specified by the operand. The loaded task state segment is marked busy. A task switch does not occur. LTR is used only in operating system software; it is not used in application programs.

#### `MOV`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | I T S | A P C Z |  | n/~ster into r mbyte |
| B9/r | MOV r/m16,r16 |  | 2/2 | 2/3 | 2/9+EA | Move word rrrrster into r mword |
| B9/r | MOV r/m32,r32 |  | 2/2 |  |  | Movedword register to rim dword byte into byte register word into word register dwordinto dword register register to r / m register word to segment register |
| AO | MOV AL,moffsB | 1 | 4 | 5 | 10 | Move byte at ~:offset) to |
| Al | MOV AX,moffs16 |  | 4 | 5 | 10 | Move word at ~:offset) to |
| Al | MOV |  | 4 |  |  | Movedword |
|  | EAX,moffs32 |  |  |  |  | at (seg:offset) to EAX |
| A2 | MOV moffsB,AL |  | 4 | 3 | 10 | Move ALto (seg:offset) |
| A3 | MOV moffs16,AX |  | 2 | 3 | 10 | Move AX to (seg:offset) |
| A3 | MOV |  | 2 |  |  | MoveEAXto |
|  | moffs32,EAX |  |  |  |  | (seg:offset) |
| BO+rb | MOV regB,immB |  | 2 | 2 | 4 | Move immediate byte to register |
| B8+rw MOV |  | 1 | 2 | 2 | 4 | Move |
|  | regI6,imm16 |  |  |  |  | immediate word to register |
| B8+rd | MOV |  | 2 |  |  | Move |
|  | reg32,imm32 |  |  |  |  | immediate dwordto register |
| C6 | MOV r/m8,imm8 1 |  | 2/2 | 2/3 | 4/10+EA Move | immediate byte tor/mbyte |
| C7 | MOVrl | 1 | 2/2 | 2/3 | 4/l0+EA | Move |
|  | m16,imm16 |  |  |  |  | immediate word to rim word |
| C7 | MOVrl |  | 2/2 |  |  | Move |
|  | m32,imm32 |  |  |  |  | immediate dword to rim dword |

BB /r MOVr/mB,rB 2/2 2/3 2/9+EA Move byte BA /r MOVrB,r/mB 1 2/4 2/5 2/B+EA Mover/m BB /r MOV r16,r/m16 1 2/4 Mover/m 2/5 2/B+EA BB /r MOV r32,r /m32 1 2/4 Mover/m MOV r/m16,Sreg 3/3 Move segment BC /r 2/2 2/3 2/9+EA BD /r MOV Sreg,r /m16 3/9 Mover/m 2/5,pm=18/19 2/5,pm=17/19 2/B+EA MOV copies the second operand to the first operand. If the destination operand is a segment register (DS, ES, SS, etc.), then data from a descriptor is also loaded into the register. The data for the register is obtained from the descriptor table entry for the selector given. A null selector (values 0000-0003) can be loaded into DS and ES registers without causing an exception; however, use of DS or ES causes a #GP(O), and no memory reference occurs. A MOV into SS inhibits all interrupts until after the execution of the next instruction (which is presumably a MOV into eSP).

#### `MOV`

*Move to/from special registers*

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OF 22 Ir | MOV,CRO,r32 | 16 |  | Move (register) to (control register) |
| OF 22 Ir | MOV CRO/CR2/CR3/CR4,r32 | 4 | 1014/5 |  |
| OF 21 Ir | MOV r32,DRO - 3 | 10 | 22 | Move (debug register) to (register) |
| OF 21 Ir | MOV r32,DR6/DR7 | ' 10 | 14 | Move (debug register) to (register) |
| OF 23 Ir | MOV DRO -3,r32 | 11 | 22 | Move (register) to (debug register) |
| OF 23 Ir | MOV DR6/DR7,r32 | 11 | 16 | Move (register) to (debug register) |
| OF 24 Ir | MOV r32,TR6/TR7 | 4 | 12 | Move (test register) to (register) |
| OF 26 Ir | MOV TR6/TR7,r32 | 4 | 12 | Move (register) to (test register) |
| OF 24 Ir | MOVr32,TR3 |  | 3 | Move (registers) to (test register3) |

a D T S Z A P C OF 20 /r MOV r32,CROICR2/CR3/CR4 4 6 Move (control register) to (register) These forms of MOV store or load the following special registers in or from a general-purpose register: • Control Registers CRO, CR2, CR3, and CR4 (CR4 only on Pentium) • Debug Registers DRO, DR1, DR2, DR3, DR6, and DR7 • Test Registers TR3, TR4, TR5, TR6, and TR7 (not valid on Pentium) 32-bit operands are always used with these instructions, regardless of the operand-size attribute.

#### `MOVS`

*Move data from string to string*

#### `MOVSB`

*MOVSD 386 processors and greater*

#### `MOVSW`

#### `MOVSD`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| A4 | MOVSm8,m8 | 7 | 7 | 5 | 18 | Move byte [(E)SI] to ES:[(E)DI] |
| A5 | MOVS m16,m16 | 7 | 7 | 5 | 18 | Move word [(E)SI] to ES:[(E)DI] |
| A5 | MOVm32,m32 | 7 | 7 |  |  | Move dword [(E)SI] to ES:[(E)DI] |
| A4 | MOVSB | 7 | 7 | 5 | 18 | Move byte DS:[(E)SI] to ES:[(E)DI] |
| A5 | MOVSW | 7 | 7 | 5 | 18 | Move word DS:[(E)SI] to ES:[(E)DI] |
| A5 | MOVSD | 7 | 7 |  |  | Move dword DS:[(E)SI] to ES:[(E)DI] |

MOVS copies the byte or word at [(E)SI] to the byte or word at ES; [(E)DI]. The destination operand must be addressable from the ES register; no segment override is possible for the destination. A segment override can be used for the source operand; the default is DS. The addresses of the source and destination are determined solely by the contents of (E)SI and (E)DI. Load the correct index values into (E)SI and (E)DI before executing the MOVS instruction. MOVSB, MOVSW, and MOVSD are synonyms for the byte, word, and doubleword MOVS instructions. After the data is moved, both (E)SI and (E)DI are advanced automatically. If the direction flag is a (CLD was executed), the registers are incremented; if the direction flag is 1 (STD was executed), the registers are decremented. The registers are incremented or decremented by 1 if a byte was moved, 2 if a word was moved, or 4 if a doubleword was moved. MOVS can be preceded by the REP prefix for block movement of CX bytes or words. Refer to the REP instruction for details of this operation.

#### `MOVSX`

*Move with sign-extend*

**Flags:** `o D ITS ZAP C`

OF BE Ir MOVSXrI6,r/m8 3/3 3/6 Move byte to word with sign extend OF BE Ir MOVSX r32,r/m8 3/3 3/6 Move byte to dword OF BE Ir MOVSX r32,r/mI6 3/3 3/6 Move word to dword MOVSX reads the contents of the effective address or register as a byte or a word, sign-extends the value to the operand-size attribute of the instruction (16 or 32 bits), and stores the result in the destination register.

#### `MOVZX`

*Move with zero-extend*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFB6/r | MOVZX r32,r/m8 | 3/3 | 3/6 | Move byte to dword |
| OFB7/r | MOVZX r32,r/m16 | 3/3 | 3/6 | Move word to dword |

OF B6 /r MOVZX r16,r/m8 3/3 3/6 Move byte to word with zero extend MOVZX reads the contents of the effective address or register as a byte or a word, zero extends the value to the operand-size attribute of the instruction (16 or 32 bits), and stores the result in the destination register.

#### `MUL`

*Unsigned multiplication of AL or AX*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  | 0 D | I T | S Z A | P C |  |
| F6/4 | MULr/m8 | 13/18, | 9-14/12-17 | 13/16 70-77/76-83+EA |  | unsiffPed multiply |
|  |  | 13/18 |  |  |  | (AX (AL8r/m byte) |
| F7/4 | MUL,r/m16 13/26, |  | 9-22/12-25 | 21/24 118-113/124-139+EA |  | (DX:AX[AX |
|  |  | 13/26 |  |  |  | *r/m word) |
| F7/4 | MULr/m32 | 13/42, 9-38/12-41 |  |  |  | Uns~edm~ly |
|  |  | 13/42 |  |  |  | (ED :EAX[E *r/mdword) |

* MDL performs unsigned multiplication. Its actions depend on the size of its operand, as follows: • A byte operand is multiplied by AL; the result is left in AX. The carry and overflow flags are set to a if AH is 0; otherwise, they are set to 1. • A word operand is multiplied by AX; the result is left in DX: AX. DX contains the high-order 16 bits of the product. The carry and overflow flags are set to a if DX is 0; otherwise, they are set to 1. • A doubleword operand is multiplied by EAX and the result is left in EDX:EAX. EDX contains the high-order 32 bits of the product. The carry and overflow flags are set to a if EDX is 0; otherwise, they are set to 1 (386 only).

#### `NEG`

*Two's complement negation*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F6/3 | NEGr/m8 | 1/3 | 2/6 | 2/7 | 3/16+EA | Two'scomplementnegater/mbyte |
| F7/3 | NEG r/m16 | 1/3 | 2/6 | 2/7 | 3/16+EA | Two'scomplementnegater/mword |
| F7/3 | NEG r/m32 | 1/3 | 2/6 |  |  | Two's complement negate rim dword |

NEG replaces the value of a register or memory operand with its two's complement. The operand is subtracted from zero, and the result is placed in the operand. The carry flag is set to I, unless the operand is zero, in which case the carry flag is cleared to O.

#### `NOP`

*No operation*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  |  |  |  | A |  |
| 90 | NOP | 1 | 3 | 3 | 3 | No operation |

c 0 D I T S Z P Ol'cod.~ . IrtSttuctiotr . Clocks Description Nap performs no operation. Nap is a one-byte instruction that takes up space but affects none of the machine context except (E)IP. Nap is an alias mnemonic for the XCHG (E)AX, (E)AX instruction.

#### `NOT`

*One's complement negation*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  | 0 D | I | T S | Z A | P C |
| F6/2 | NOTr/m8 | 1/3 | 2/6 | 2/7 | 3/16+EA Reverse each bit of r / m byte |  |
| F7/2 | NOTr/m16 | 1/3 | 2/6 | 2/7 | 3/16+EA Reverse each bit of r / m | word |
| F7/2 | NOTr/m32 | 1/3 | 2/6 | 2/7 |  | Reverse each bit of r / m dword |

NOT inverts the operand; every 1 becomes a 0, and vice versa.

#### `OR`

*Logical inclusive OR*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| OCib | ORAL,imm8 | 1 | 2 | 3 | 4 | OR immediate byte to AL |
| ODiw | ORAX,immI6 | 1 | 2 I | 3 | 4 | OR immediate word to AX |
| ODid | OR EAX,imm32 | 1 | 2 |  |  | OR immediate dword to EAX |
| 80/1 ib | OR r/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA OR immediate byte to r / m byte |  |
| 81/1 iw OR | r/m16,immI6 | 1/3 | 2/7 | 3/7 | 4/17+EA OR immediate | word to r / m word |
| . 81/lid | OR r/m32,imm32 | 1/3 | 2/7 |  |  | OR immediate dword to rim dword |
| 83/1 ib | OR r/m16,imm8 | 1/3 | 2/7 |  |  | OR sign-extended immediate byte with rim word |
| 83/1 ib | OR r/rn32,imm8 | 1/3 | 2/7 |  |  | OR sign-extended immediate byte with rim dword |
| 08/r | ORr/m8,r8 | 1/3 | 2/6 | 2/7 | 3/16+EA OR byte register to r / m byte |  |
| 09/r | OR r/m16,rI6 | 1/3 | 2/6 | 2/7 | 3/16+EA OR | word register to r / m word |
| 09/r | ORr/m32,r32 | 1/3 | 2/6 |  |  | OR dword register to r / m dword |
| OA/r | ORr8,r/m8 | 1/2 | 2/7 | 2/7 | 3/9+EA | OR byte register to r / m byte |

o 0 OB /r OR r16,r/m16 1/2 2/7 2/7 3/9+EA OR word register to r/m word OB /r OR r32,r/m32 1/2 2/7 ORdword register to r/mword OR computes the inclusive OR of its two operands and places the result in the first operand. Each bit of the result is 0 if both corresponding bits of the operands are 0; otherwise, each bit is l. The optimized form of OR is SETFLAG (see Chapter 3).

#### `OUT`

*Output to port*

**Flags:** `D I T S Z A P C 0`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| E6ib | OUT | 16,pm=11 * | /31 **, 1O,pm==4* | /24** 3 | 10 | Output byte AL to |
|  | imm8,AL | vm==29 |  |  |  | immediate port number |
| E7ib | OUT | 16,pm==11 | * /31 **, 10,pm==4* | /24** 3 | 10 | Output word AX to |
|  | imm8,AX | vm==29 |  |  |  | immediate port number |
| E7ib | OUT | 16,pm==11 | * /31 **, 1O,pm==4* | /25** |  | Output dword EAX |
|  | imm8,EAX | vm=29 |  |  |  | to immediate port number |
| EE | OUT DX,AL | 16,pm==11 | * /31 **, 11,pm==5* | /25** 3 | 8 | Output b~e AL to |
|  |  | vm==29 |  |  |  | port num er in OX |
| EF | OUT DX,AX | 16,pm==11 | * /31**, 11,pm==5* | /25** 3 | 8 | Output word AX to |
|  |  | vm==29 |  |  |  | port number in OX |
| EF | OUT DX,EAX | 16,pm==11 | * /31 **, 11,pm==5* | /25** |  | Output dword EAX |
|  |  | vm==29 |  |  |  | to port number in OX |
| *I£ CPL | ~ lOPL. |  |  |  |  |  |

**I£ CPL > lOPL or if in virtual 8086 mode. OUT transfers a data byte or data word from the register (AL, AX, or EAX) given as the second operand to the output port numbered by the first operand. Output to any port from 0 to 65535 is performed by placing the port number in the DX register and then using an OUT instruction with DX as the first operand. If the instruction contains an eight-bit port ID, that value is zero-extended to 16 bits.

#### `OUTS`

*Output string to port*

#### `OUTSe`

*OUTS/OUTSB/OUTSW 80186 and greater*

#### `OUTSW`

*OUTSO 386 processors and greater*

#### `OUTSO`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 6E | OUTS DX,r/m8 | 17,pm=10* /32**, | 14,pm==8* | /28** 5 | Output byte [(E)5I] |
|  |  | vm==30 |  |  | to port in OX |
| 6F | OUTS DX,r/m16 | 17,pm==10* | /32**, 14,pm==8* | /28** 5 | Output word [(E)51] |
|  |  | vm==30 |  |  | to port in OX |
| 6F | OUTS DX,r/m32 | 17,pm==10* | /32**, 14,pm==8* | /28** | Ou~utdword |
|  |  | vm==30 |  |  | [(E) I] to port in DX |
| 6E | OUTSB | 17,pm=1O* /32**, | 14,pm=S* | /2S** 5 | Ouwutbt e in OX |
| 6F | OUTSW | 17,pm=10* /32**, | 14,pm=S* | /2S** 5 | Ouwutword |
|  |  | vm=30 |  |  | OS: (E)SI] to ~ort numberinO |
| 6F | OUTSO | 17,pm=10* /32**, | 14,pm=S* | /2S** | Ouwutdword |
|  |  | vm=30 |  |  | OS: (E)SI] to port in OX |

Op¢Qg~ ;; ,lnstritction' Clocks' ' D(!sctlption os: (E)SI to port vm=30 OUTS transfers data from the memory byte, word, or doubleword at the source-index register to the output port addressed by the DX register. If the address-size attribute for this instruction is 16 bits, SI is used for the source- index register; otherwise, the address-size attribute is 32 bits, and ESI is used for the source-index register. OUTS does not allow specification of the port number as an immediate value. The port must be addressed through the DX register value. Load the correct value into DX before executing the OUTS instruction. The address of the source data is determined by the contents of source-index register. Load the correct index value into SI or ESI before executing the OUTS instruction. After the transfer, source-index register is advanced automatically. If the direction flag is 0 (CLD was executed), the source-index register is incremented; if the direction flag is 1 (STD was executed), it is decremented. The amount of the increment or decrement is 1 if a byte is output, 2 if a word is output, or 4 if a doubleword is output. OUTSB, OUTSW, and OUTSD are synonyms for the byte, word, and doubleword OUTS instructions. OUTS can be preceded by the REP prefix for block output of CX bytes or words. Refer to the REP instruction for details on this operation.

#### `POP`

*word from the stack*

**Flags:** `D I T S Z A P C 0`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| SF /0 | POPm16 | 6 | 5 | 5 | 17+EA | Pop top of stack into memory word dwor |
| 5S+rw | POPr16 | 4 | 4 | 5 | S | Pop top of stack into word register |
| 5S+rd | POPr32 | 4 | 4 |  |  | Pop top of stack into dword register |
| IF | POP OS | 3 | 7,pm=21 | 5,pm=20 | S | Pop top of stack into OS |
| 07 | POPES | 3 | 7,pm=21 | 5,pm=20 | S | Pop top of stack into ES |
| 17 | POPSS | 3 | 7,pm=21 | 5,pm=20 | S | Pop top of stack into SS |
| OF Al | POPFS | 3 | 7,pm=21 |  |  | Pop top of stack into FS |
| OFA9 | POPGS | 3 | 7,pm=21 |  |  | Pop top of stack into GS |

POPm32 5 SF /0 6 Pop tJ' of stack into memory POP replaces the previous contents of the memory, the register, or the segment register operand with the word on the top of the stack, addressed by SS:SP (address-size attribute of 16 bits) or SS:ESP (address-size attribute of 32 bits). The stack pointer SP is incremented by 2 for an operand-size of 16 bits or by 4 for an operand-size of 32 bits. It then points to the new top of stack. POP CS is not an instruction. Popping from the stack into the CS register is accomplished with a RET instruction. If the destination operand is a segment register (DS, ES, FS, GS, or SS), the value popped must be a selector. In protected mode, loading the selector initiates automatic loading of the descriptor information associated with that selector into the hidden part of the segment register; loading also initiates validation of both the selector and the descriptor information. A null value (0000-0003) may be popped into the DS, ES, FS, or GS register without causing a protection exception. An attempt to reference a segment whose corresponding segment register is loaded with a null value causes a general protection fault. No memory reference occurs. The saved value of the segment register is null. A POP SS instruction inhibits all interrupts, including NMI, until after execution of the next instruction. This allows sequential execution of POP S5 and POP ESP instructions without danger of having an invalid stack during an interrupt. However, use of the LSS instruction is the preferred method of loading the SS and ESP registers. popping multiple items in sequence. The items popped can include any legal POP value, including registers, immediate values, and memory locations. This feature does not actually affect the code generated.

> Note: Turbo Assember extends the syntax of the POP instruction to facilitate

#### `POPA`

*Pop all general registers*

#### `POPAD`

*POPA 80186 processors and greater*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 61 | POPA | 9 | 24 | 19 | Pop DI / 51, BP, BX, OX, CX, AX |
| 61 | POPAO | 9 | 24 |  | Pop EOI, ESI, EBP, EBX, EOX, ECX, EAX |
| 61 | POPAW | 9 | 24 | 19 | Pop DI, 51, BP, BX, OX, CX, AX |

POPAD 386 processors and greater PO PAW POP A pops the yight 16- or 32-bit general registers depending on the segment size. However, the SP value is discarded instead of loaded into SP. paPA reverses a previous PUSHA, restoring the general registers to their values before PUSHA was executed. The first register popped is DI. POP AD pops the eight 32-bit general registers. The ESP value is discarded instead of loaded into ESP. POP AD reverses the previous PUSHAD, restoring the general registers to their values before PUSHAD was executed. The first register popped is ED!. paPAW pops WORD-sized registers. (Can only be used for VERSION T320 or higher.)

#### `POPF`

*Pop from stack into FLAGS or EFLAGS register*

#### `POPFD`

*POPFD 386 processors and greater*

#### `POPFW`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | I T | S Z | A P | C |
| 90 | POPF | 9,pm=6 | 5 | 5 | 8 | Pop top of stack into FLAGS |
| 90 | POPFD | 9,pm=6 | 5 |  |  | Pop top of stack into EFLAGS |
| 90 | POPFW | 9,pm=6 | 5 | 5 | 8 | Pop top of stack into FLAGS |

* POPF /POPFD pOpS the word or doubleword on the top of the stack and stores the value in the flags register. If the operand-size attribute of the instruction is 16 bits, then a word is popped and the value is stored in FLAGS. If the operand- size attribute is 32 bits, then a doubleword is popped and the value is stored in EFLAGS. Note that bits 16 and 17 of EFLAGS, called VM and RF, respectively, are not affected by POPF or POPFD. The I/O privilege level is altered only when executing at privilege level O. The interrupt flag is altered only when executing at a level at least as privileged as the I/O privilege level. (Real-address mode is equivalent to privilege level 0.) If a POPF instruction is executed with insufficient privilege, an exception does not occur, but the privileged bits do not change. POPFW always pops into FLAGS WORD-style. (Can only be used for VERSION T320 or higher.)

#### `PUSH`

*Push operand onto the stack*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| FF 16 | PUSHm16 | 4 | 5 | 5 | 16+EA | Push memory word |
| FF 16 | PUSHm32 | 4 | 5 |  |  | Push memory dword |
| 6A | PUSHimm8 | 1 | 2 | 3 |  | Push immediate byte |
| 68 | PUSHimm16 | 1 | 2 | 3 |  | Push immediate word |
| 68 | PUSHimm32 | 1 | 2 |  |  | Push immediate dword |
| DE | PUSHCS | 3 | 2 | 3 | 10 | PushCS |
| 16 | PUSHSS | 3 | 2 | 3 | 10 | PushSS |
| 1E | PUSH OS | 3 | 2 | 3 | 10 | PushDS |
| 06 | PUSHES | 3 | 2 |  | 10 | PushES |
| OF AD | PUSHFS | 3 | 2 |  |  | PushFS |
| OFA8 | PUSHGS | 3 | 2 |  |  | PushGS |

50+ Ir 11 Push register word PUSHr16 1 2 3 50+ Ir PUSHr32 1 2 Push register dword PUSH decrements the stack pointer by 2 if the operand-size attribute of the instruction is 16 bits; otherwise, it decrements the stack pointer by 4. PUSH then places the operand on the new top of stack, which is pointed to by the stack pointer. The 386 PUSH ESP instruction pushes the value of the ESP as it existed before the instruction. The 80286 PUSH SP instruction also pushes the value of SP as it existed before the instruction. This differs from the 8086, where PUSH SP pushes the new value (decremented by 2). pushing multiple items in sequence. The items pushed can include any legal PUSH value, including registers, immediate values, and memory locations. This feature does not actually affect the code generated. In addition, the PUSH instruction allows constant arguments even when generating code for the 8086 processor. Such instructions are replaced in the object code by a lO-byte sequence that simulates the 80186/286/386 PUSH immediate value instruction.

> Note: Turbo Assember extends the syntax of the PUSH instruction to facilitate

#### `PUSHA`

*Push all general registers*

#### `PUSHAD`

*PUSHA 80186 processors and greater*

#### `PUSHAW`

*PUSHAD 386 processors and greater*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| 60 | PUSHA | 11 | 18 | 17 | Push AX,CX,DX,BX,original SP,BP,SI |
| 60 | PUSHAD | 11 | 18 |  | Push EAX,ECX,EDX,EBX |
| 60 | PUSHAW | 11 | 18 | 17 | Push AX,CX,DX,BX,original SP,BP,SI |

PUSHA and PUSHAD save the 16-bit or 32-bit general registers, respectively, on the stack depending on the segment size. PUSHA decrements the stack pointer (SP) by 16 to hold the eight word values. PUSHAD decrements the stack pointer (ESP) by 32 to hold the eight doubleword values. Because the registers are pushed onto the stack in the order in which they were given, they appear in the 16 or 32 new stack bytes in reverse order. The last register pushed is DI or ED!. PUS HAW always pushes WORD-style. (Can only be used for VERSION T320 or higher.)

#### `PUSHF`

*Push flags register onto the stack*

#### `PUSHFD`

*PUSHFD 386 processors and greater*

#### `PUSHFW`

**Flags:** `0 D T S Z A P C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 9C | PUSHF | 4,pm=3. 4 |  | 3 | 10 | Push FLAGS |
| 9C | PUSHFD | 4,pm=3 4 |  |  |  | PushEFLAGS |
| 9C | PUSHFW | 4,pm=3 4 |  | 3 | 10 | Push FLAGS |

PUSHF decrements the stack pointer by 2 and copies the FLAGS register to the new top of stack; PUSHFD decrements the stack pointer by 4, and the 386 EFLAGS register is copied to the new top of stack which is pointed to by SS:ESP. PUSHFW always pops WORD-sized registers. (Can only be used for VERSION T320 or higher.)

#### `RCL`

*Rotate*

#### `RCR`

c

#### `ROL`

#### `ROR`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  |  |  |  | per it)+EA | (CF,r/m byte) left CL times |
| CO /2 ib | RCL r/m8,imm8 | 8-30/9-31 | 9/10 | 5/8 |  | Rotate 9 bits (CF,r/m byte) left imm8 times (CF,r/m word) left once |
|  |  |  |  |  | per it)+EA | r / m word) left CL times |
| C1 /2 ib | RCL r /m16, imm8 8-30/9-31 |  | 9/10 | 5/8 |  | Rotate 17bits (CF,r/m word)) left imm8 times (CF,r/m dword) left once (CF,r/m dword) left CL times |
| C1 /2 ib | RCL r /m32, imm8 8-30/9-31 |  | 9/10 |  |  | Rotate 33 bits (CF,r/m dword) left, imm8 times |
| DO/3 | RCRr/m8,1 | 3/4 | 9/10 | 2/7 | 2/15+EA | Rotate 9 bits (CF,r/m byte) right once |
| D2/3 | RCRr/m8,CL | 8-30/9-31 | 9/10 | 5/8 | 8+4 Eer | bit/ (20+4 Rotate 9 bits |
|  |  |  |  |  | per it)+EA | (CF,r/m byte) right CL times |
| CO /3ib | RCR r /m8,imm8 | 8-30/9-31 | 9/10 | 5/8 |  | Rotate 9 bits (CF,r/m bte) right imm times |
| D1/3 | RCRr/m16,1 | 3/4 | 9/10 | 2/7 | 2/15+EA | Rotate 17 bits (CF,r/m word) right once |
| D3/3 | RCRr/m16,CL | 8-30/9-31 | 9/10 | 5/8 | 8+4 Eer | bit/ (20+4 Rotate 17 bits |
|  |  |  |  |  | per it)+EA | (CF,r/m word) right CL times |
| C1/3ib | RCRr/m16,imm8 | 8-30/9-31 | 9/10 | 5/8 |  | Rotate 17 bits (CF,r/m word) right imm8 times |
| D1/3 | RCRr/m32,1 | 3/4 | 9/10 |  |  | Rotate 33 bits (CF,r/m dword) right once |
| D3/3 | RCR r /m32,CL | 8-30/9-31 | 9/10 |  |  | Rotate 33 bits (CF,r/mdword) right CL times |
| C1 /3 ib | RCR r /m32, imm8 8-30/9-31 |  | 9/10 |  |  | Rotate 33 bits (CF,r/m dWOl:d) right imm8 times byte left once |
|  |  |  |  |  | per it)+EA | byte left CL times |
| CO /Oib | ROLr/m8,imm8 | 2/4 | 3/7 | 5/8 |  | Rotate 8 bits r / m byte left imm8 times r / m word left once |
|  |  |  |  |  | per it)+EA | r / m word left CL times |
| C1/0ib | ROL r/m16, imm8 | 2/4 | 3/7 | 5/8 |  | Rotate 16 bit rim word left imm8 times r / m dword left once r / m dword left CLtimes |
| C1/0ib | ROL r/m32, imm8 | 2/4 | 3/7 |  |  | Rotate 32 bits r / m dword left imm8times |
| DO /1 | RORr/m8,1 | 3/4 | 3/7 | 2/7 | 2/15+EA | Rotate 8 bits rim byte right once |
| 02/1 | RORr/m8,CL | 3/4 | 3/7 | 5/8 | 8+4lJer | Rotate 8 bits rim bit/ (20+4 |
|  |  |  |  |  | per it)+EA | byte right CL times |
| CO /1 ib | RORr/m8,imm8 | 2/4 | 3/7 | 5/8 |  | Rotate 8 bits rim word right imm8 times |
| 01/1 | RORr/m16,1 | 3/4 | 3/7 | 2/7 | 2/15+EA | Rotate 16 bits r /m word right once |
| 03/1 | RORr/m16,CL | 3/4 | 3/7 | 5/8 | 8+4lJer | Rotate 16 bits bit/ (20+4 |
|  |  |  |  |  | per it)+EA | r /m word right CLtimes |
| C1 /1 ib | ROR r/m16, imm8 | 2/4 | 3/7 | 5/8 |  | Rotate 16 bit rim word right imm8 times ' |
| 01/1 | RORr/m32,1 | 3/4 | 3/7 |  |  | Rotate 32 bits r /m dword right once |
| 03/1 | ROR r/m32,CL | 3/4 | 3/7 |  |  | Rotate 32 bits rim dword right CLtimes |
| C1 /1 ib | ROR r/m32, imm8 | 2/4 | 3/7 |  |  | Rotate 32 bits r/mdwordright imm8times |
| Add 1 clock | to the times shown | for each | rotate | made | (80286 only). |  |

Opcode • "Insttltclion (nlod<s Description 00/2 RCLr/m8,1 2/7 2/15+EA Rotate 9 bits 3/4 9/10 02/2 RCLr/m8,CL 8-30/9-31 9/10 5/8 8+4 Eer bit/ (20+4 Rotate 9 bits 01/2 RCLr/m16,1 3/4 9/10 2/7 2/15+EA Rotate 17 bits 03/2 RCLr/m16,CL 8-30/9-31 9/10 5/8 8+4 Eer bit/ (20+4 Rotate 17bits (CF, 01/2 RCLr/m32,1 3/4 9/10 Rotate 33 bits 03/2 RCL r /m32,CL 8-30/9-31 9/10 Rotate 33 bits 00/0 ROLr/m8,1 3/4 3/7 2/7 2/15+EA Rotate 8 bits r / m 02/0 ROLr/m8,CL 3/4 3/7 5/8 8+4lJer bit/ (20+4 Rotate 8 bits r / m 01/0 ROLr/m16,1 3/4 3/7 2/7 2/15+EA Rotate 16 bits ROL r/m16,CL Rotate 16 bits 03/0 3/4 3/7 5/8 8+4lJer bit/ (20+4 01/0 ROLr/m32,1 3/4 3/7 Rotate 32 bits 03/0 ROL r /m32,CL Rotate 32 bits 3/4 3/7 Each rotate instruction shifts the bits of the register or memory operand given. The left rotate instructions shift all the bits upward, except for the top bit, which is returned to the bottom. The right rotate instructions do the reverse: The bits shift downward until the bottom bit arrives at the top. For the RCL and RCR instructions, the carry flag is part of the rotated quantity. RCL shifts the carry flag into the bottom bit and shifts the top bit into the carry flag; RCR shifts the carry flag into the top bit and shifts the bottom bit into the carry flag. For the ROL and ROR instructions, the original value of the carry flag is not a part of the result, but the carry flag receives a copy of the bit that was shifted from one end to the other. The rotate is repeated the number of times indicated by the second operand, which is either an immediate number or the contents of the CL register. To reduce the maximum instruction execution time, the 80286/386 does not allow rotation counts greater than 31. If a rotation count greater than 31 is attempted, only the bottom five bits of the rotation are "Used. The 8086 does not mask rotation counts. The 386 in virtual 8086 mode does mask rotation counts. The overflow flag is defined only for the single-rotate forms of the instructions (second operand = 1). It is undefined in all other cases. For left shifts/rotates, the CF bit after the shift is XORed with the high order result bit. For right shifts/rotates, the high-order two bits of the result are XORed to get OF.

#### `RDMSR`

*Read from Model Specific Register*

**Flags:** `o D ITS ZAP C`

The value in ECX specifies one of the 64-bit Model Specific Registers of the Pentium processor. The content of that Model Specific Register is copied into EDX:EAX. EDX is loaded with the high-order 32 bits, and EAX is loaded with the low-order 32 bits. The following values are used to select model specific registers on the Pentium processor: Other values used to preform cache, TLB and BTB testing and performance monitoring, are available under a non-disclosure agreement from Intel. Protected mode exceptions: #GP(O) if either the current privilege level is not 0 or the value in ECX does not specify a Model-Specific Register'that is implemented in the Pentium processor. Real mode exceptions: #GP if the value in ECX does not specify a Model- Specific Register that is implemented in the Pentium processor. Virtual 8086 mode exceptions: #GP(O) if instruction execution is attempted. Notes: This instruction must be executed at privilege level 0 or in real-address mode; otherwise a protection exception will be generated. If less than 64 bits are implemented in a model specific register, the value returned to EDX:EAX, inthe locations corresponding to the unimplemented bits, is unpredictable. RDMSR is used to read the content of Model-Specific Registers that control functions for testability, execution tracing, performance monitoring and machine check errors. Refer to the Pentium Processor Data Book for more information or contact Intel. The values 3h, OFh, and vailles above 13h are reserved. Do not execute RDMSR with reserved values in ECX.

#### `RDTSC`

*(Proprietary instruction. Contact Intel for more information.)*

#### `REP`

*Repeat following string operation*

#### `REPE`

#### `REPZ`

#### `REPNE`

#### `REPNZ`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| F36C | REP INS | I6+S(E)CX, | I3+6*(E)CX, | 5+4*CX |  | Input (E)CX |
|  | r/mS,DX | ~m=10+S(Eicx*1 | / ~m=7 +6*(E)CX/ |  |  | bytes from |
|  |  | O+S(E)CX* | 7+6*h(E)CX*2 ,VM== |  |  | EortDXinto |
|  |  | 29+8(E)CX |  |  |  | S:[(E)DI] |
| F36D | REP INS | I6+S(E)CX, | 13+6*(E)CX, | 5+4*CX |  | Input (E)CX |
|  | r/mI6,DX | ~m=lO+S(EiCx*l | / ~m=7+6*(E)CX/ |  |  | words from |
|  |  | O+S(E)CX* | ,VM= 7+6*h(E)CX*2 |  |  | EortDXinto |
|  |  | 29+S(E)CX |  |  |  | S:[(E)DI] |
| F36D | REP INS | I6+S(E)CX, | 13+6*(E)CX, |  |  | Input (E)CX |
|  | r/m32,DX | ~m=lO+S(EiCx*l | / ~m=7+6*(E)CX/ |  |  | dwordsfrom |
|  |  | O+S(E)CX* | 7 +6*1*(E)CX*2 ,VM= |  |  | EortDXinto |
|  |  | 29+S(E)CX |  |  |  | S:[(E)DI] |
| F3A4 | REP MOVS | 5..3,13 wi ,12+3(E) | 5+4*(E)CX | 5+4*CX 9+I7*CX |  | Move (E)CX |
|  | mS,mS | CX;.s |  |  |  | b&:esfrom [ )SI] to ES:[(E)DI] |
| F3A5 | REP MOVS | 5..3,13 wi ,12+3(E) | 5+4*(E)CX | 5+4*CX 9+I7*CX |  | Move (E)CX |
|  | m16,m16 | CX*5 |  |  |  | words from [(E)SI] to ES:[(E)DI] |
| F3A5 | REP MOVS | 5..3,13 wi ,12+3(E) | 5+4*(E)CX |  |  | Move (E)CX |
|  | m32,m32 | CX*5 |  |  |  | dwordsfrom [(E)SI] to ES:[(E)DI] |
|  | DX,r/mS |  |  |  |  | b&tesfrom |
|  |  | 3I+5(E)CX* | X/26+5* | *(E) |  | [ )SI] to port |
|  |  |  | CX*2 |  |  | DX |
|  | DX,r/mI6 |  |  |  |  | worasfrom |
|  |  | 1+5(E)CX* | X/26+5* | *(E) |  | [(E)SI] to port |
|  |  |  | CX*2 |  |  | DX |
|  | DX,r/m32 |  |  |  |  | dwordsfrom |
|  |  | 1+5(E)CX* | . X/26+5* | *(E) |  | [(E)SI] to port |
|  |  |  | CX*2 |  |  | DX |
| F2AC | REP LODS 5..3,7+4(E)CX..6 |  |  |  |  | Load (E)CX |
|  | m8 |  |  |  |  | b&:tes from [ )S1] toAL |
| F2AD | REP LODS 5..3,7 | +4(E)CX*6 |  |  |  | Load (E)CX |
|  | m16 |  |  |  |  | words from [(E)S1] to AX |
| F2AD | REP LODS 5..3,7 | +4(E)CX*6 |  |  |  | Load (E)CX |
|  | m32 |  |  |  |  | dwordsfrom [(E)S1] to EAX |
| F3AA | 5..3,7 REPSTOS | +4(E)CX*6 | 5+5*(E)CX | 4+3*CX | 9+ lO*CX | Fill (E)CX |
|  | m8 |  |  |  |  | ~esat :[(E)DI] withAL |
| F3AB | REPSTOS 5..3,7 | +4(E)CX*6 | 5+5*(E)CX | 4+3*CX | 9+ lO*CX | Fill (E)CX |
|  | m16 |  |  |  |  | words at ES:[(E)DI] with AX |
| F3AB | 5..3,7 REPSTOS | +4(E)CX*6 | 5+5*(E)CX |  |  | Fill (E)CX |
|  | m32 |  |  |  |  | dwordsat ES:[(E)DI] withEAX |
| F3A6 | 5..3,7+7(E)CX*6 REPE |  | 5+9*N | 5+9*N | 9+22*N | Find |
|  | CMPS |  |  |  |  | nonmatching |
|  | m8,mB |  |  |  |  | ~tesin S:[(E)DI] and [(E)S1] |
| F3A7 | REPE 5..3,7+7(E)CX*6 |  | 5+9*N | 5+9*N | 9+22*N | Find |
|  | CMPS |  |  |  |  | nonmatching |
|  | m16,m16 |  |  |  |  | words in ES:[(ElDI] and [(E)S1 |
| F3A7 | REPE 5..3,7+7(E)CX*6 |  | 5+9*N |  |  | Find |
|  | CMPS |  |  |  |  | nonmatching |
|  | m32,m32 |  |  |  |  | dwordsin ES:[(ElDI] and [(E)S1 |
| F3AE | 5..3,7 REPE | +5(E)CX..6 | 5+B*N | 5+8*N | 9+15*N | Findnon-AL |
|  | SCASmB |  |  |  |  | ~te starting at S:[(E)DI] |
| F3AF | 5..3,7+5(E)CX*6 EPESCAS |  | 5+B*N | 5+B*N | 9+15*N | Find non-AX |
|  | m16 |  |  |  |  | word starting at ES:[(E)DI] |
| F3AF | REPE 5..3,7 | +5(E)CX*6 | 5+B*N |  |  | Find non- |
|  | 5CA5m32 |  |  |  |  | EAXdword startin[,at E5:[(E) I] |
| F2A6 | 5..3,7+ REPNE | 7(E)CX*6 | 5+9*N | 5+9*N | 9+22*N | Find |
|  | CMPS |  |  |  |  | matching |
|  | mB,mB |  |  |  |  | ~tesin :[(ElDI] and [(E)51 |
| F2A7 | 5..3,7+7(E)CX*6 REPNE |  | 5+9*N | 5+9*N | 9+22*N | Find |
|  | CMPS |  |  |  |  | matching |
|  | m16,m16 |  |  |  |  | words in E5:[(E)D1] and [(E)51] |
| F2A7 | REPNE 5..3,7+7(E)CX..6 |  | 5+9*N |  |  | Find |
|  | CMP5 |  |  |  |  | matchin~ |
|  | m.32,m32 |  |  |  |  | dwordsm E5:[(ElDI] and [(E)51 |
| F2AE | REPNE 5..3,7 | +5(E)CX*6 | 5+B*N | 5+B*N | 9+15*N | FindAL |
|  | 5CASm8 |  |  |  |  |  |
| F2 AF | REPNE | 50+3,7+5(E)CX*6 | 5+8*N | 5+8*N | 9+15*N | Find AX |
|  | SCASrn16 |  |  |  |  |  |
| F2 AF | REPNE | 50+3,7+5(E)CX~ | 5+8*N |  |  | FindEAX |
|  | SCASrn32 |  |  |  |  |  |
| *3If(E)CX=O |  |  |  |  |  |  |
| *6If(E)CXO |  |  |  |  |  |  |

F36E REP OUTS pm=l1 I7+5(E)CX, +5(EiCX*1 / 5+ I2*(E)CX, t m=6+5*(£) 5+4*CX Output (E)CX 5+ I2*(E)CX, 5+4*CX Ouqmt (E)CX F36F REP OUTS ~m=l1 I7+5(E)CX, +5(EiCX*1 / t m=6+5*(£) F36F REP OUTS ~m=l1 I7+5(E)CX, +5(EiCX*1 / 5+ I2*(E)CX, t m =6+5*(£) Output(E)CX REP, REPE (repeat while equal), and REPNE (repeat while not equal) are prefixes that are applied to string operations. Each prefix causes the string instruction that follows to be repeated the number of times indicated in the count register or (for REPE and REPNE) until the indicated condition in the zero flag is no longer met. Synonymous forms of REPE and REPNE are REPZ and REPNZ, respectively. The REP prefixes apply only to one string instruction at a time. To repeat a block of instructions, use the LOOP instruction or another looping construct. The precise action for each iteration is as follows: 1 If the address-size attribute is 16 bits, use CX for the count register; if the address-size attribute is 32 bits, use ECX for the count register. 2 Check ex. If it is zero, exit the iteration, and move to the next instruction. 3 Acknowledge any pending interrupts. 4 Perform the string operation once. 5 Decrement CX or ECX by one; no flags are modified. 6 Check the zero flag if the string operation is SCAS or CMPS. If the repeat condition does not hold, exit the iteration and move to the next instruction. Exit the iteration if the prefix is REPE and ZF is 0 (the last comparison was not equal), or if the prefix is REPNE and ZF is one (the last comparison was equal). 7 Return to step 1 for the next iteration. Repeated CMPS and SCAS instructions can be exited if the count is exhausted or if the zero flag fails the repeat condition. These two cases can be distinguished by using either the JCXZ instruction, or by using the conditional jumps that test the zero flag aZ, JNZ~ and JNE).

> *1 If CPL ::; IOPL
> *2 If CPL > IOPL
> *4 If (E) CX = 1
> *5 If (E) CX 1

#### `RET`

*Return from procedure*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  | 0 D | T I S | Z A P | C |  |
| C3 | RET | 5 | lO+rn | 11 | 16 | Return (near) to caller |
| CB | RET | 13,prn=18 18+rn,prn=32+rn |  | 15,prn=25 | 26 | Return (far) to caller, same privilege |
| CB | RET | 13,prn=33 prn=68 |  | 55 |  | Return (far) |
| C2 iw | RET imm16 | 5 | 10+m | 11 | 20 | Return (near) |
| CA iw | RET imm16 | 14,pm=17 18+m,pm=32+m |  | 15,pm=25 | 25 | Return (far) pop imm16bytes |
| CA iw | RET imm16 | 14,pm=33 pm=68 |  | 55 |  | Return (far) |

RET transfers control to a return address located on the stack. The address is usually placed on the stack by a CALL instruction, and the return is made to the instruction that follows the CALL. The optional numeric parameter to RET gives the number of stack bytes (OperandMode = 16) or words (OperandMode = 32) to be released after the return address is popped. These items are typically used as input parameters to the procedure called. For the intrasegment (near) return, the address on the stack is a segment offset, which is popped into the instruction pointer. The CS register is unchanged. For theintersegment (far) return, the address on the stack is a long pointer. The offset is popped first, followed by the selector. In real mode, CS and IP are loaded directly. In protected mode, an intersegment return causes the processor to check the descriptor addressed by the return selector. The AR byte of the descriptor must indicate a code segment of equal or lesser privilege (or greater or equal numeric value) than the current privilege level. Returns to a lesser privilege level cause the stack to be reloaded from the value saved beyond the parameter block. ' The DS, ES, FS, and GS segment registers can be set to 0 by the RET instruction during an inter-level transfer. If these registers refer to segments that cannot be used by the new privilege level, they are set to 0 to prevent unauthorized access from the new privilege level.

#### `RSM`

*Resume from System Management Mode*

**Flags:** `o D T S ZAP C`

* * * Resume operation of a program by a System Management Mode (SMM) interrupt. The processor state is restored from the dump created upon entrance to SMM. Note, however, that the contents of the model-specific registers are not affected. The processor leaves SMM and returns control to the interrupted application or operating system. If the processor detects any invalid state information, it enters the shutdown state. This happens in any of the following situations: • The value stored in the State Dump Base field is not a 32 Kbyte aligned address. • Any reserved bit in CR4 is set to 1. • Any combination of bits in CRO is illegal; namely, (PG=l and PE=O) or (NW=l andCD=O). Protected mode, Real mode, and Virtual 8086 mode exception: #UD if an attempt is made to execute this instruction when the processor is not in SMM. Notes: for more information about SMM and the behavior of the RSM instruction, see the Pentium Processor User's Manual (available from Intel).

#### `SAHF`

*Store AH into Flags*

**Flags:** `o D T S ZAP C`

* * 4 9E SAHF 232 Store AH flags SF ZF xx AF xx PF xx CF SAHF loads the flags listed above with values from the AH register, from bits 7, 6,4, 2 and 0, respectively.

#### `SAL`

*Shift instructions*

#### `SAR`

**Flags:** `o D ITS ZAP C`

#### `SHL`

#### `SHR`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| DO/4 | SALr/m8,1 | 3/4 | 3/7 | 2/7 | 2/15+EA | Multiply rim byte by 2 |
| D2/4 | SALr/m8,CL | 3/4 | 3/7 | 5/8 | 8+4 | per bit/(20+4 per Multiplyr/m byte by 2, |
|  |  |  |  |  | bit)+nA | CLtimes |
| CO /4ib | SALr/m8,imm82/4 |  | 3/7 | 5/8 |  | Multiply rim byte by 2 |
| Dl/4 | SALr/m16,l | 3/4 | 3/7 | 2/7 | 2/15+EA | Multiply r /m word by 2 |
| D3/4 | SALr/m16,CL | 3/4 | 3/7 | 5/8 | 8+4 per bit | (20+4 per Multiply r /m word by 2, |
|  |  |  |  |  | bit)+nA | CLtimes |
|  | m16,imm8 |  |  |  |  |  |
| D3/4 | SALr/m32,CL | 3/4 | 3/7 |  |  | Multiply r /m dword by 2 |
| Cl/4ib | SALr/ | 2/4 | 3/7 |  |  | Multiply r /m dword by 2 |
|  | m32,imm8 |  |  |  |  |  |
| DO/7 | SARr/m8,l | 3/4 | 3/7 | 2/7 | 2/15+EA | Signed divide** rim byte by2 |
| D2/7 | SARr/m8,CL | 3/4 | 3/7 | 5/8 | 8+4per,bit(20+4per | Signed divide** rim byte |
|  |  |  |  |  | bit)+nA | by2 |
| CO /7ib | SARr/ | 2/4 | 3/7 | 5/8 |  | Signed divide** rim byte |
|  | m8,imm8 |  |  |  |  | by2 by2 |
| D3/7 | SARr/m16,CL | 3/4 | 3/7 | 5/8 | 8+4 per bit (20+4 per | Signed divide** r /m word |
|  |  |  |  |  | bit)+nA | by2 |
| Cl/7ib | SARr/ | 2/4 | 3/7 | 5/8 |  | Signed divide** r /m word |
|  | m16,imm8 |  |  |  |  | by2 dwordby2 , |
| D3/7 | SAR r / m32,CL | 3/4 3/7 |  |  |  | Signed divide** rim dword by 2, CLtimes |
|  | m32,imm8 |  |  |  |  | dwordby2 |
| DO/4 | SHLr/m8,1 | 3/4 | 3/7 | 2/7 | 2/15+EA | Multiply r / m byte by 2 |
| D2/4 | SHLr/m8,CL | 3/4 | 3/7 | 5/8 | 8+4 !1:r bit | (20+4 per Multiply rim byte by 2, |
|  |  |  |  |  | bit)+ A | CLtimes |
| CO /4 ib | SHLr/ | 2/4 | 3/7 | 5/8 |  | Multiply r / m byte by 2 |
|  | m8,imm8 |  |  |  |  |  |
| D3/4 | SHLr/m16,CL | 3/4 3/7 |  | 5/8 | 8+4 !1:r bit | (20+4 per Multiply rim word by 2, |
|  |  |  |  |  | bit)+ A | CLtimes |
| Cl /4 ib | SHLr/ | 2/4 | 3/7 | 5/8 |  | Multiply r / m word by 2 |
|  | m16,imm8 |  |  |  |  |  |
| D3/4 | SHL r /m32,CL | 3/4 3/7 |  |  |  | Multiply rim dword by 2 |
| Cl /4 ib | SHLr/ | 2/4 | 3/7 |  |  | Multiply rim dword by 2 |
|  | m32,imm8 |  |  |  |  |  |
| DO/5 | SHRr/m8,1 | 3/4 3/7 |  | 2/7 | 2/15+EA | Unsigned divide r / m byte by2 |
| D2/5 | SHRr/m8,CL | 3/4 | 3/7 | 5/8 | 8+4 !1:r bit | (20+4 per Unsigned divide r / m byte |
|  |  |  |  |  | bit)+ A | by2 |
| CO /5 ib | SHRr/ | 2/4 | 3/7 | 5/8 |  | Unsigned divide r / m byte |
|  | m8,imm8 |  |  |  |  | by2 wor by2 |
| D3/5 | SHRr/m16,CL | 3/4 | 3/7 | 5/8 | 8+4 ~ | bit (20+4 per Uns~ed divide r /m |
|  |  |  |  |  | bit)+ | wor by2 |
| Cl/5ib | SHRr/ | 2/4 | 3/7 | 5/8 |  | Uns~ed divide rim |
|  | m16,imm8 |  |  |  |  | wor by2 dwordby2 |
| D3/5 | SHR r /m32,CL | 3/4 | 3/7 |  |  | Unsis:!led divide r /m dwordby2 |
| C1 /5 ib | SHRr/ | 2/4 | 3/7 |  |  | Unsis:!led divide r / m |
|  | m32,imm8 |  |  |  |  | dwordby2 |
| **Not the | same division as | IDIV; | rounding |  | is toward | negative infinity. |

Cl /4 ib SALr/ 2/4 3/7 5/8 Multiply r /m word by 2 Dl/4 SALr/m32,l 3/4 3/7 Multiply rim dword by 2 Dl/7 SARr/m16,l 3/4. 3/7 2/7 2/15+EA Signed divide** r / m word Dl/7 SARr/m32,l 3/4 3/7 Signed divide** r / m Signed divide** rim Cl/7 SARr/ 2/4 3/7 Dl/4 SHLr/m16,1 3/4 3/7 2/7 2/15+EA Multiply r / m word by 2 SHLr/m32,1 Multiply rim dword by 2 Dl/4 3/4 3/7 Dl/5 SHRr/m16J 3/4 3/7 2/7 2/15+EA Uns~ed divide r /m Dl/5 SHRr/m32,1 3/4 3/7 Unsis:!led divide rim SAL (or its synonym, SHL) shifts the bits of the operand upward. The high- order bit is shifted into the carry flag, and the low-order bit is set to O. SAR and SHR shift the bits of the operand downward. The low-order bit is shifted into the carry flag. The effect is to divide the operand by 2. SAR performs a signed divide with rounding toward negative infinity (not the same as IDIV); the high-order bit remains the same. SHR performs an unsigned divide; the high-order bit is set to O. The shift is repeated the number of times indicated by the second operand, which is either an immediate number or the contents of the CL register. To reduce the maximum execution time, the 80286/386 does not allow shift counts greater than 31.1£ a shift count greater than 31 is attempted, only the bottom five bits of the shift count are used. (The 8086 uses all eight bits of the shift count.) The overflow flag is set only if the single-shift forms of the instructions are used. For left shifts, OF is set to 0 if the high bit of the answer is the same as the result of the carry flag (that is, the top two bits of the original operand were the same); OF is set to 1 if they are different. For SAR, OF is set to 0 for all single shifts. For SHR, OF is set to the high-order bit of the original operand.

#### `see`

*Integer subtraction with borrow*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 10 iw | SSB AX,imm16 |  | 2 | 3 | 4 | Subtract with borrow immediate word from AX |
| 10 id | SSB EAX,imm32 |  | 2 |  |  | Subtract with borrow immediate , dword from EAX |
| 80/3 ib | SEB r/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA Subtract with borrow immediate |  byte from r / m byte |
| 81 /3 iw | SEB r/ml6,imml6 | 1/3 | 2/7 | 3/7 | 4/17+EA Subtract | with borrow immediate word from r/m word |
| 81 /3 id | SEB r/m32,imm32 | 1/3 | 2/7 |  |  | Subtract with borrow immediate dword from r /m dword |
| 83/3 ib | SBB r/ml6,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA Subtract with borrow sign-extended |  |
| 83/3 ib | SBB r/m32,imm8 | 1/3 | 2/7 |  |  | Subtract with borrow sign-extended |
| 18/r | SBB r/m8,r8 | 1/3 | 2/6 | 2/7 | 3/16+EA Subtract with borrow byte register |  from r / m byte |

* Ie ib SSB AL,imm8 1 234 Subtract with borrow immediate immediate byte from rim word immediate byte from rim dword 19 /r SBB r/mI6,r16 1/3 2/6 2/7 3/16+EA Subtract with borrow word register from rim word 19 Ir SBB r/m32,r32 1/3 2/6 Subtract with borrow dword register from rim dword lA Ir SBBr8,r/m8 1/2 2/7 3/9+ EA Subtract with borrow byte register 2/7 from rim byte IB /r SBB r16,r/mI6 1/2 2/7 3/9+EA Subtract with borrow word register 2/7 from rim word 18 Ir SBB r32,r/m32 1/2 2/7 Subtract with borrow dword register from rim dword SBB adds the second operand (DEST) to the.carry flag (CF) and subtracts the result from the first operand (SRC). The result of the subtraction is assigned to the first operand (DEST), and the flags are set accordingly. When an immediate byte value is subtracted from a word operand, the immediate value is first sign-extended.

#### `SCAS`

*Compare string data*

#### `SCASe`

*SCASD 386 processors and greater*

#### `SCASW`

#### `SCASD`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| AE | SCASm8 | 6 | 7 | 7 | 15 | Compare bytes AL - ES:[OI] |
| AF | SCASm16 | 6 | 7 | 7 | 15 | Compare words AX - ES: [01] |
| AF | SCASm32 | 6 | 7 |  |  | Compare dwords EAX - ES: [01] |
| AE | SCASB | 6 | 7 | 7 | 15 | Compare bytes AL - ES:[OI] |
| AF | SCASW | 6 | 7 | 7 | 15 | Compare words AX - ES: [01] |
| AF | SCASD | 6 | 7 |  |  | Compare dwords EAX - ES: [01] |

SCAS subtracts the memory byte or word at the destination register from the AL, AX or EAX register. The result is discarded; only the flags are set. The operand must be addressable from the ES segment; no segment override is possible. If the address-size attribute for this instruction is 16 bits, DI is used as the destination register; otherwise, the address-size attribute is 32 bits and EDI is used. The address of the memory data being compared is determined solely by the contents of the destination register, not by the operand to SCAS. The operand validates ES segment addressability and determines the data type. Load the correct index value into DI or EDI before executing SCAS. After the comparison is made~ the destination register is automatically updated. If the direction flag is 0 (CLD was executed), the destination register is . incremented; if the direction flag is 1 (SID was executed), it is decremented. The increments or decrements are by 1 if bytes are compared, by 2 if words are compared, or by 4 if doublewords are compared. SCASB, SCASW, and SCASD are synonyms for the byte, word and doubleword SCAS instructions that don't require operands. They are simpler to code, but provide no type or segment checking. SCAS can be preceded by the REPE or REPNE prefix for a block search of CX or ECX bytes or words. Refer to the REP instruction for further details.

#### `SETcc`

*Byte set on condition*

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
|  | 0 D | I | T S | Z P C A |
| OF 97 | SETAr/m8 | 4/3 | 4/5 | Set byte if above (CF=O and ZF=O) |
| OF 93 | SETAEr/m8 | 4/3 | 4/5 | Set byte if above or equal (CF=O) |
| OF 92 | SETBr/m8 | 4/3 | 4/5 | Set byte if below (CF=l) |
| OF 96 | SETBEr/ro8 | 4/3 | 4/5 | Set byte if below or equal (CF=l or ZF=l) |
| OF 92 | SETCr/m8 | 4/3 | 4/5 | Set if carry (CF=l) |
| OF 94 | SETEr/m8 | 4/3 | 4/5 | Set byte if equal (ZF=l) |
| OF9F | SETGr/ro8 | 4/3 | 4/5 | Set byte if greater (ZF=O or SF=OF) . |
| OF9D | SETGEr/mB | 4/3 | 4/5 | Set byte if greater or equal (SF=OF) |
| OF9C | SETLr/mB | 4/3 | 4/5 | Set byte if less (SF<>OF) |
| OF9E | SETLEr/mB | 4/3 | 4/5 | Set byte if less or equal (ZF=1 and SF<>OF) |
| OF 96 | SETNAr/mB | 4/3 | 4/5 | Set byte if not above (CF=I) |
| OF 92 | SETNAEr/mB | 4/3 | 4/5 | Set byte if not above or equal (CF=I) |
| OF 93 | SETNBr/mB | 4/3 | 4/5 | Set byte if not below (CF=O) |
| OF 97 | SETNBE r/mB | 4/3 | 4/5 | Set byte if not below or equal (CF=O and ZF=O) |
| OF 93 | SETNC r/mB | 4/3 | 4/5 | Set byte if not carry (CF=O) |
| OF 95 | SElNEr/mB | 4/3 | 4/5 | Set byte if not equal (ZF=O) |
| OF 9E | SETNG r/mB | 4/3 | 4/5 | Set byte if not greater (ZF=1 or SF<>OF) |
| OF 9C | SETNGE r/mB | 4/3 | 4/5 | Set byte if not greater or equal (SF<>OF) |
| OF 9D | SETNL r/m8 | 4/3 | 4/5 | . Set byte if not less (SF=OF) |
| OF 9F | SETNLE r/mB | 4/3 | 4/5 | Set byte if not less or equal (ZF=1 and SF<>OF) |
| OF 91 | SETNO r/m8 | 4/3 | 4/5 | Set byte if not overflow (OF=O) |
| OF 9B | SETNP r/mB | 4/3 | 4/5 | Set byte if not parity (PF=O) |
| OF 99 | SETNS r/m8 | 4/3 | 4/5 | Set byte if not sign (SF=O) |
| OF 95 | SETNZr/m8 | 4/3 | 4/5 | Set byte if not zero (ZF=O) |
| OF 90 | SETOr/mB | 4/3 | 4/5 | Set byte if overflow (OF=I) |
| OF9A | SETPr/mB | 4/3 | 4/5 | Set byte if parity (PF=I) |
| OF 9A | SETPE r/mB | 4/3 | 4/5 | Set byte if parity even (PF=I) |
| OF 9B | SETPO r/mB | 4/3 | 4/5 | Set byte if parity odd (PF=O) |
| OF 98 | SETSr/mB | 4/3 | 4/5 | Set byte if sign (SF=I) |
| OF 94 | SETZ r/m8 | 4/3 | 4/5 | Set byte if zero (ZF=I) |

SETcc stores a byte containing 1 at the destination specified by the effective address or register if the condition is met, or a 0 byte if the condition is not met.

#### `SGDT`

*Store global/interrupt descriptor table*

#### `SlOT`

*80286 and greater protected mode only*

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
|  | 0 | D |  | T S | P C Z A |
| OF 01 10 | SGDTm | 10 | 9 | 11 | Store GUTR to m |

OF 01 II SIDTm 10 9 12 Store IDTR to m SGDT /SIDT copies the contents of the descriptor table register to the six bytes of memory indicated by the operand. The LIMIT field of the register is assigned to the first word at the effective address. If the operand-size attribute is 16 bits, the next three bytes are assigned the BASE field of the register, and the fourth byte is written with zero. The last byte is undefined. Otherwise, if the operand- size attribute is 32 bits, the next four bytes are assigned the 32-bit BASE field of the register . .sGDT and SIDT are used only in operating system software; they are not used in application programs.

#### `SHLD`

*Double precision shift left*

**Flags:** `o D ITS Z A C`

| Opcode | Instruction | 486 | 386 | Description |
|---|---|---|---|---|
| OFA4 | SHLD r /m16,r16,imm8 | 2/3 | 3/7 | r / m16 gets SHL of r / m16 concatenated withrl |
| OFA4 | SHLD r /m32,r32,imm8 | 2/3 | 3/7 | r / m32 ~ets SHL of r / m32 concatenated withr3 |
| OFA5 | SHLD r / m16,r16,CL | 2/3 | 3/7 | r/m16 gets SHL 6f r/m16 concatenated withrl |
| OFA5 | SHLD r /m32,r32,CL | 2/3 | 3/7 | r / m32 ~ets SHL of r / m32 co~catenated withr3 |

SHLD shifts the first operand provided by the rim field to the left as many bits as specified by the count operand. The second operand (r16 or r32) provides the bits to shift in from the right (starting with bit 0). The result is stored back into the rim operand. The register remains unaltered. The count operand is provided by either an immediate byte or the contents of the CL register. These operands are taken MODULO 32 to provide a number between 0 and 31 by which to shift. Because the bits to shift are provided by the specified registers, the operation is useful for multiprecision shifts (64 bits or more). The SF, ZF and PF flags are set according to the value of the result. CF is set to the value of the last bit shifted out. OF and AF are left undefined.

#### `SHRD`

*Double precision shift right*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
|  | 0 | D | T | S Z A | P C |
| OFAC | SHRD r /m16,r16,imm8 |  | 2/3 | 3/7 | r / m16 gets SHR of r / m16 concatenated withrl |
| OFAC | SHRD r /m32,r32,imm8 |  | 2/3 | 3/7 | r / m32 ~ets SHR of r / m32 concatenated withr3 |
| OF AD | SHRD r/m16,r16,CL |  | 3/4 | 3/7 | r / m16 gets SHR of r / m16 concatenated withrl |
| OF AD | SHRD r /m32,r32,CL |  | 3/4 | 3/7 | r/m32 ~ets SHRofr/m32 concatenated withr3 |
| OFOO/O | SLDTr/m16 | 2/3 | pm=2/2 | 2/3 | Store LDTR to EA word |

* SHRD shifts the first operand provided by the rim field to the right as many bits as specified by the count operand. The second operand (r16 or r32) provides the bits to shift in from the left (starting with bit 31). The result is stored back into the rim operand. The register remains unaltered. The count operand is provided by either an immediate byte or the contents of the CL register. These operands are taken MODULO 32 to provide a number between 0 and 31 by which to shift. Because the bits to shift are provided by the specified register, the operation is useful for multi-precision shifts (64 bits or more). The SF, ZF and PF flags are set according to the value of the result. CF is set to the value of the last bit shifted out. OF and AF are left undefined. SLDT stores the Local Descriptor Table Register (LDTR) in the two-byte register or memory location indicated by the effective address operand. This register is a selector that points into the global descriptor table. SLDT is used only in operating system software. It is not used in application programs.

#### `SMSW`

*Store machine status word*

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
|  | 0 | D | T S I | Z A P | C |
| OF 01 /4 | SMSWr/m16 | 2/3 | 2/3,pm=2/2 | 2/3 | Store machine status word to EA word |

SMSW stores the machine status word (part of CRO) in the two-byte register or memory location indicated by the effective address operand.

#### `STC`

*Set carry flag*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | I T | S | Z A | P C 1 |
| F9 | STC | 2 | 2 | 2 | 2 | Set carry flag |

STC sets the carry flag to 1.

#### `STO`

*Set direction flag*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | I | T S | Z A | P C |
|  |  | 1 |  |  |  |  |
| PO | SID | 2 | 2 | 2 | 2 | Set direction flag so (E)SI or (E)OI decrement |

SID sets the direction flag to I, causing all subsequent string operations to decrement the index registers, (E)Sland/ or (E)DI, on which they operate.

#### `STI`

*Set interrupt enable flag*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | T I | S | Z A | P C |
|  |  |  | 1 |  |  |  |
| FB | STI | 5 | 3 | 2 | 2 | Set interrupt flag |
| AA | STOSm8 | 5 | 4 | 3 | 11 | Store AL in byte ES:[(E)DI] |
| AB | STOSm16 | 5 | 4 | 3 | 11 | Store AX in word ES:[(E)DI] |
| AB | STOSm32 | 5 | 4 |  |  | Store EAX in dword ES:[(E)DI] |
| AA | STOSB | 5 | 4 | 3 | 11 | Store AL in byte ES:[(E)DI] |
| AB | STOSW | 5 | 4 | 3 | 11 | Store AX in word ES:[(E)DI] |
| AB | STOSD | 5 | 4 |  |  | Store EAX in dword ES:[(E)DI] |

STI sets the interrupt flag to 1. The CPU then responds to external interrupts after execlJ.ting the next instruction if the next instruction allows the interrupt flag to remain enabled. If external interrupts are disabled and you code STI, RET (such as at the end of a subroutine), the RET is allowed to execute before external interrupts are recognized. Also, if external interrupts are disabled and you code STI, CLI, then external interrupts are not recognized because the CLI instruction clears the interrupt flag during its execution. STOS transfers the contents of the AL, AX, or EAX register to the memory byte, word, or doubleword given by the destination register relative to the ES segment. The destination register is DI for an address-size attribute of 16 bits or EDI for an address-size attribute of 32 bits. The destination operand must be addressable from the ES register. A segment override is not possible. The address of the destination is determined by the contents of the destination register, not by the explicit operand of STOS. This operand is used only to validate ES segment address ability and to determine the data type. Load the correct index value into the destination register before executing STOS. After the transfer is made, DI is automatically updated. If the direction flag is 0 (CLD was executed), DI is incremented; if the direction flag is.1 (SID was executed), DI is decremented. DI is incremented or decremented by 1 if a byte is stored, by 2 if a word is stored, or by 4 if a doubleword is stored. STOSB, STOSW, and STOSD are synonyms for the byte, word, and double- word STOS instructions, that do not requir~ an operand. They are simpler to use, but provide no type or segment checking. STOS can be preceded by the REP prefix for a block fill of CX or ECX bytes, words, or doublewords. Refer to the REP instruction for further details.

#### `STR`

*Store task register*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OF 00 II | STRr/m16 | 2/3 | pm=23/272/3 |  | LoadEA word into task register |

The contents of the task register are copied to the two-byte register or memory location indicated by the effective address operand. STR is used only in operating system software. It is not used in application programs.

#### `SUB`

*Integer Subtraction*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 2Cib | SUBAL,imm8 | 1 | 2 | 3 | 4 | Subtract immediate byte fromAL |
| 2Diw | SUB AX,imm16 | 1 | 2 | 3 | 4 | Subtract immediate word from AX |
| 2Did | SUB EAX,imm32 |  | 2 |  |  | Subtract immediate dword fromEAX |
| 80/5ib | SUB r/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Subtract immediate byte from rim byte |
| 81/5iw | SUB r/ml6,imml6 | 1/3 | 2/7 | 3/7 | 4/17+EA | Subtract immediate word from rim word |
| 8115 id | SUB r Im32,imm32 | 1/3 | 2/7 |  |  | Subtract immediate dword from rim dword |
| 83/5ib | SUB r/m16,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Subtract si~-extended immediate yte from r / m word |
| 83/5ib | SUB r Im32,imm8 | 1/3 | 2/7 |  |  | Subtract si~-extended immediate yte from rim dword |
| 28/r | SUBr/m8,r8 | 1/3 | 2/6 | 2/7 | 3/16+EA | Subtract byte register from rim byte |
| 29/r | SUB r/m16,r16 | 1/3 | 2/6 | 2/7 | 3/16+EA | Subtract word register from rim word |
| 29/r | SUB r I m32,r32 | 1/3 | 2/6 |  |  | Subtract dword register from r/mdword |
| 2A/r | SUBr8,r/m8 | 1/2 | 2/7 | 2/7 | 3/9+EA | Subtract EA byte from byte register |
| 2B Ir | SUB r16,r/m32 | 1/2 | 2/7 | 2/7 | 3/9+EA | Subtract EA word from word register |
| 2B Ir | SUB r32,r I m32 | 1/2 | 2/7 |  |  | Subtract EA dword from dword register |

SUB subtracts the second operand (SRC) from the first operand (DEST). The first operand is assigned the result of the subtraction, and the flags are set accordingly. When an immediate byte value is subtracted from a word operand, the immediate value is first sign-extended to the size of the destination operand.

#### `TEST`

*Logical compare*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  |  |  |  |  | 0 |  |
| A8ib | TEST AL,imm8 | 1 | 2 | 3 | 4 | And immediate byte with AL |
| A9iw | TEST AX,imm16 | 1 | 2 | 3 | 4 | And immediate word with AX |
| A9id | TEST EAX,imm32 | 1 | 2 |  |  | And immediate dword withEAX |
| F6 /0 ib | TEST r/m8,imm8 | 1/2 | 2/5 | 3/6 | 5/11+EA | And immediate byte with r/mbyte |
| F7 /0 iw | TEST r/m16,imm16 | 1/2 | 2/5 | 3/6 | 5/11+EA | And immediate word with r/mword |
| F7 /0 id | TEST r/m32,imm32 | 1/2 | 2/5 |  |  | Andimmediatedword with r / m dword byte |
| 85 /r | TEST r/m16,r16 | 1/2 | 2/5 | 2/6 | 3/9+EA | Andwordregisterwith r/mword |
| 85/r | TEST r/m32,r32 | 1/2 | 2/5 |  |  | And dword register with r/mdword |

* o 84 /r TESTr/m8,r8 1/2 2/5 2/6 3/9+EA Andbyteregisterwithr/m TEST computes the bit-wise logical AND of its two operands. Each bit of the result is 1 if both of the corresponding bits of the operands are 1; otherwise, each bit is O. The result of the operation is discarded and only the flags are modified. The optimized form of TEST is TESTFLAG (see Chapter 3).

#### `VERR`

*Verify segment for reading or writing*

#### `VERW`

*80286 and greater protected mode only*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | Description |
|---|---|---|---|---|---|
| OFOO/4 | VERRr/m16 | 11/11 pm=10/11 |  | 14/16 | SetZF=lifsegmentcanberead |
| OFOO/5 | VERWr/m16 | 11/11 pm=15/16 |  | 14/16 | SetZF=lifsegmentcanbewritten |

The two-byte register or memory operand of VERR and VERW contains the value of a selector. VERR and VERW determine whether the segment denoted by the selector is reachable front the current privilege level and whether the segment is readable (VERR) or writable (VERW). If the segment is accessible, the zero flag is set to 1; if the segment is not accessible, the zero flag is set to O. To set ZF, the following conditions must be met: • The selector must denote a descriptor within the bounds of the table (GDT or LDT); the selector must be "defined." • The selector must denote the descriptor of a code or data segment (not that of a task state segment, LDT, or a gate). • For VERR, the segment must be readable. For VERW, the segment must be a writable data segment. • If the code segment is readable and conforming, the descriptor privilege level (DPL) can be any value for VERR. Otherwise, the DPL must be greater than or equal to (have less or the same privilege as) both the current privilege level and the selector's RPL. The validation performed is the same as if the segment were loaded into DS, ES, FS, or GS, and the indicated access (read or write) were performed. The zero flag receives the result of the validation. The selector's value cannot result in a protection exception, enabling the software to anticipate possible segment access problems.

#### `WAIT`

*Wait until BUSY# pin is inactive (HIGH)*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 9B | WAIT | 1-3 | 6 | 3 | 4+5n | Wait until BUSY pin is inactive (I-llGH) |

WAIT suspends execution of CPU instructions until the BUSY# pin is inactive (high). The BUSY# pin is driven by the 80x87 numeric processor extension.

#### `WBINVD`

*Write-back and Invalidate cache*

**Flags:** `o D ITS ZAP C`

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
| OF 09 | WBINVD | 5 | Write-back and invalidate entire cache |

The internal cache is flushed, and a special-function bus cycle is issued which indicates that the external cache should write-back its contents to main memory. Another special-function bus cycle follows, directing the external cache to flush itself. implemented differently on future Intel processors. It is the responsibility of the hardware to respond to the external cache write-back and flush indications.

> Note: This instruction is implementation-dependent; its function might be

#### `WRMSR`

*Write to Model Specific Register*

**Flags:** `o D ITS ZAP C`

The value in ECX specifies one of the 64-bit Model Specific Registers of the Pentium processor. The contents of EDX:EAX is copied into that Model Specific Register. The high-order 32 bits are copied from EDX and the low-order 32 bits are copied from EAX. ' The following values are used to select model specific registers on the Pentium processor: Other values used to preform cache, TLB and BTB testing and performance monitoring, are available under a non-disclosure agreement from Intel. Protected mode exceptions: #GP(O) if either the current privilege level is not 0 or the value in ECX does not specify a Model-Specific Register that is implemented in the Pentium processor. Real mode exceptions: #GP if the value in ECX does not specify a Model- Specific Register that is implemented in the Pentium processor. Virtual 8086 mode exceptions: #GP(O) if instruction execution is attempted. Notes: This instruction must be executed at privilege level 0 or in real-address mode; otherwise a protection exception will be generated. Always set undefined or reserved bits to the value previously read. WRMSR is used to write the content of Model-Specific Registers that control functions for testability, execution tracing, performance monitoring and machine check errors. Refer to the Pentium Processor Data Book for more information or contact Intel. The values 3h, OFh, and values above 13h are reserved. Do not execute WRMSR with reserved values in ECX.

#### `XADD`

*Exchange and add*

**Flags:** `o D ITS ZAP C`

* * * OFCO/r XADDr/m8,r8 3/4 Exchange byte register and rim byte; load sum into rim byte. OFCl/r XADDr/ml6,rl68 3/4 Exchange word register and rim word; load sum into rim word. OFCl/r XADDr/m32,r32 3/4 Exchange dword register and rim dword; load sum into rim dwora. The XADD instruction loads DEST into SRC, and then loads the sum of DEST and the original value of SRC into DEST. DEST is the destination operand; SRC is the source operand. Protected mode exceptions: #GP(O) if the result is in a nonwritable segment; #GP(O) for an illegal memory operand effective address in the CS, DS, ES, FS, or GS segments; #5S(O) for an illegal address in the SS segment; #PF (fault code) for a page fault; #NM if either EM or TS in CRO is set; #AC for an unaligned memory reference if the current privilege level is 3. Real address mode exceptions: interrupt 13 if any part of the operand would lie outside the effective address space from 0 to OFFFFh. Virtual 8086 mode exceptions: same exception as in real-address mode; same #PI! and #AC exceptions as in protected mode.

#### `XCHG`

*Exchange memory/register with register*

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
|  | 0 | D | T | S | Z A | P C |
| 86/r | XCHG r/m8,r8 | 3/5 | 3/5 | 3/5 | 4/17+EA | Exchange byte register with EA byte |
| 86/r | XCHG r8,r/m8 | 3/5 | 3/5 | 3/5 | 4/17+EA | Exchange byte with EA byte register |
| 87/r | XCHG r/m16,r16 | 3/5 | 3/5 | 3/5 | 4/17+EA Exchange | word register with EA word |
| 87/r | XCHG r16,r/m16 | 3/5 | 3/5 | 3/5 | 4/17+EA Exchange | word register with EA word |
| 87/r | XCHG r/m32,r32 | 3/5 | 3/5 |  |  | Exchange dword register with EA dword |
| 87/r | XCHGr32,r/m32 | 3/5 | 3/5 |  |  | Exchange dword register with EA dword |
| 90+r | XCHGAX,r16 | 3 | 3 | 3 | 3 | Exchange word register with AX |
| 90+r | XCHGr16,AX | 3 | 3 | 3 | 3 | Exchange word register with AX |
| 90+r | XCHG EAX,r32 | 3 | 3 |  |  | Exchange dword register with EAX |
| 90+r | XCHG r32,EAX | 3 | 3 |  |  | Exchange dword register with EAX |

XCHG exchanges two operands. The operands can be in either order. If a memory operand is involved, BUS LOCK is asserted for the duration of the exchange,regardless of the presence or absence of the LOCK prefix or of the value of the IOPL.

#### `XLAT`

*Table look-up translation*

#### `XLATB`

**Flags:** `0 D I T S Z A P C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 07 | XLATm8 | 4 | 5 | 5 | 11 | Set AL to memory byte OS:[(E)BX + unsigned AL] |
| 07 | XLATB | 4 | 5 | 5 | 11 | Set AL to memory byte OS:[(E)BX + unsigned AL] |

XLAT changes the AL register from the table index to the table entry. AL should be the unsigned index into a table addressed by DS:BX (for an address- size attribute of 16 bits) or DS:EBX (for an address-size attribute of 32 bits). The operand to XLAT allows for the possibility of a segment override. XLAT uses the contents of BX even if they differ from the offset of the operand. The offset of the operand should have been moved into BXjEBX with a previous instruction. The no-operand form, XLATB, can be used if the BXjEBX table will always reside in the DS segment.

#### `XOR`

*Logical exclusive OR*

**Flags:** `o D T S ZAP C`

| Opcode | Instruction | 486 | 386 | 286 | 86 | Description |
|---|---|---|---|---|---|---|
| 34ib | XORAL,imm8 | 1 | 2 | 3 | 4 | Exclusive-OR immediate byte toAL |
| 35iw | XOR AX,imm16 | 1 | 2 | 3 | 4 | Exclusive-OR immediate word to AX |
| 35id | XOR EAX,imm32 | 1 | 2 |  |  | Exclusive-OR immediate dword toEAX |
| 80/6ib | XORr/m8,imm8 | 1/3 | 2/7 | 3/7 | 4/17+EA | Exclusive-OR immediate byte to rim byte |
| 8116 iw | XORr/m16,imm16 | 1/3 | 2/7 | 3/7 | 4/17+EA | Exclusive-OR immediate word to rim word |
| 81/6id | XORr/m32,imm32 | 1/3 | 2/7 |  |  | Exclusive-OR immediate dword tor/mdword |
| 8316 ib | XOR r/m16,imm8 | 1/3 | 2/7 |  |  | XOR sign-extended immediate byte to rim word |
| 83/6ib | XORr/m32,imm8 | 1/3 | 2/7 |  |  | XORsign-extendedimmediate byte to rim dword |
| 30/r | XOR r/m,r8 | 1/3 | 2/6 | 2/7 | 3/16+EA | Exclusive-OR byte register to rim byte |
| 31/r | XORr/m16,r16 | 1/3 | 2/6 2/7 |  | 3/16+EA | Exclusive-OR word register into rim word |
| 31/r | XORr/m32,r32 | 1/3 | 2/6 |  |  | Exclusive-ORdword register to r/mdword |
| 32/r | XORr8,r/m8 | 1/2 | 2/7 2/7 |  | 3/9+EA | Exclusive-OR rim byte to byte register |
| 33/r | XOR r16,r/m16 | 1/2 | 2/7 | 2/7 | 3/9+EA | Exclusive-OR rim word to word register |
| 33/r | XOR r32,r/m32 | 1/2 | 2/7 |  |  | Exclusive-OR to rim dword to dword register |

o XOR computes the exclusive OR of the two operands. Each bit of the result is 1 if the corresponding bits of the operands are different; each bit is 0 if the corresponding bits are the same. The answer replaces the first operand. The optimized form of XOR is FLIPFLAG (see Chapter 3).

## Chapter 5: Coprocessor Instructions

This chapter lists the 80x87 instructions in alphabetical order. There is one entry for each combination of operand types that can be coded with the mnemonic. The following table explains the operand identifiers used in this section: ST Stack tOPi the register currently at the top of the stack. ST(l) A register in the stack i (0 ::; i ::; 7) stack elements from the top. ST(I) is the next-on-stack register, ST(2) is below ST(l), etc, m32real A short real (32 bits) number in memory. ' m64real A long real (64 bits) number in memory. m80real A temporary real (80 bits) number in memory. m80dec A packed decimal integer (18 digits, 10 bytes) in memory. m16int A word binary integer (16 bits) in memory. m32int A short binary integer (32 bits) in memory. m64int A long binary integer (64 bits) in memory. mxxbyte A memory area xx bytes long. Here is a summary of the possible exceptions each instruction can cause:

- IS = invalid operand due to stack overflow /underflow
- I = invalid operand due to other cause
- D = denormal operand
- Z = zero-divide
- a = Overflow
- U = Underflow
- P = Inexact result (precision)

#### `F2XM1`

*Compute x*

| Opcode | Instruction | 87 | 287 | 387 | 486 | 586 | Description |
|---|---|---|---|---|---|---|---|
| D9FO | F2XM1 |  | 211-476 | 211-476 | 242(140-279) | 13-57 |  |

Exceptions: p, U, 0, I, IS F2XM1 (no operands)

#### `FABS`

*Absolute value*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | IS |  |  |
| No operands |  | 10-17 | 10-17 | 22 | 3 | FABS 2 |

FABS (no operands)

#### `FADD`

*Add real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST,ST(i) |  | 70-100 | 70-100 | 23-34 | 10(8-20) | 2 FADDST,5T(4) |
| ST(i),ST |  |  |  |  |  | FADDST(2),ST |
| short real |  | 90-120+EA | 90-120 | 24-32 | 10(8-20) | 2-4 FADD AIR_TEMP[SI] |
| long real |  | 95--125+EA | 95-125 | 29-37 | 10(8-20) | 2-4 FADD [BX].MEAN |

Exceptions: I, 0, 0, U, P, IS FADD destination, source

#### `FADDP`

*Add real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),ST |  | 75-105 | 75-105 | 23-34 | 10(8-20) | 2 FADDP ST(2),ST |

FADDP destination, source

#### `FBLD`

*Packed decimal (BCD) load*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| Packed decimal |  | 290-310 | 290-310 | 5 | 75(70-103) | 2-4 FBLD YTD _SALES |

FBLDsource

#### `FBSTP`

*Packed decimal (BCD) store and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| Packed |  | 520-540+EA | 520-540+EA | 512-534 175(172-176) |  | 2-4 FBSTP |
| decimal |  |  |  |  |  | [BX].FORECAST |

FBSTP destination

#### `FCHS`

*I*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 10-17. | 10-17 | 24-25 | 6 | 2 FCHS |

Change sign FCHS (no operands)

#### `FCLEX`

*Clear exceptions*

#### `FNCLEX`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| No operands |  | 2--8 | 2--8 | 11 | 7 | FNCLEX |

FCLEX/FNCLEX (no operands)

#### `FCOM`

*Compare real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| / /ST(i) |  | 40-50 | 40-50 | 24 | 4 | FCOMST(l) |
| short real |  | 60-70+EA | 60-70 | 26 | 4 | 2-4 FCOM [BP].UPPER_LIMIT |
| long real |  | 65-75+EA | 65-75 | 31 | 4 | 2-4 . FCOM WAVELENGTH |

FCOM / / source

#### `FCOMP`

*Compare real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| / /St(i) |  | 42-52 | 45-52 | 26 | 4 | 2 FCOMPST(2) |
| short real |  | 63-73+EA | 63-73 | 26 | 4 | 2-4 FCOMP [BP+2].N_READINGS |
| long real |  | 67-77+EA | 67-77 | 31 | 4 | 2-4 FCOMP DENSITY |

FCOMP / / source

#### `FCOMPP`

*Compare real and pop twice*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 45-55 | 45-55 | 26 | 5 | 2 FCOMPP |

FCOMPP (no operands)

#### `FCOS`

*Cosine of 51(0)*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  |  |  | 123-772* | 241(193-279) | 2 FCOS |
| additional clocks |  | may | be needed | to reduce the operand. |  |  |

FCOS

> *These timings hold for operands in the range I x I /4. For operands not in this range, up to 76

#### `FDECSTP`

*Decrement stack pointer*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| No operands |  | 6-12 | 6-12 | 22 | 3 | 2 FDECSTP |

FDECSTP (no operands)

#### `FDISI`

*Disable interrupts*

#### `FNDISI`

FDISI (no operands)

#### `FDIV`

*Divide real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| I/ST(i),ST |  | 193-203 | 193-203 | 88-91 | 73 | 2 FDIV |
| short real |  | 215-225 | 215-225 | 89 | 73 | 2-4 FDIV DISTANCE |
| long real |  | 220-230 | 220-230 | 94 | 73 | 2-4 FDIV ARqDI] |
| IIST,ST(i) |  |  |  |  | 73 |  |

FDIV / /source/destination, source

#### `FDIVP`

*Divide real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| IIST(i),ST |  | 197-207 | 198-209 | 88-91 | 73 | 2 FDIVP ST(4),ST |

Exceptions: I, 0, Z, 0, U, P FDIVP destination, source

#### `FDIVR`

*Divide real reversed*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),ST |  |  |  |  | 73 |  |
| short real |  | 216-226+EA 215-225 |  | 89 | 73 | 2-4 FDIVR [BX].PULSE_RATE |
| long real |  | 221-231+EA 220-230 |  | 94 | 73 | 2-4 FDIVR RECORDER FREQUENCY |

Exceptions: I, 0, Z, 0, U, P FDIVR / / source/ destination, source - II 194-204 198-208 88-91 73 2 FDIVR ST(2),ST ST,ST(i) I

#### `FDIVRP`

*Divide real reversed and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),ST |  | 198-208 198-208 |  | 88-91 | 73 | 2 FDIVRP ST(1),ST |

Exceptions: I, 0, Z, 0, U, P FDIVRP destination, source

#### `FENI`

*Enable interrupts*

#### `FNENI`

| Opcode | Instruction | 87 | Description |
|---|---|---|---|
|  |  | Exceptions: | None |
| (no operands) |  | 5(2-8) | 2 FNENI |

FEN! (no operands)

#### `FFREE`

*Free register*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| ST(i) |  | 9-16 | 9-16 | 18 | 3 | 2 FFREEST(I) |

FFREE destination

#### `FIADD`

*0,0, P*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 102-137+EA | 102-137 71-85 |  | 22.5(19-32) | 2-4 FIADD |
| integer |  |  |  |  |  | DISTANCE_TRAVELLED |
| short |  | 108-143+EA | 108-143 57-72 |  | 24(20-35) | 2-4 FIADD PULSE_COUNT [SI] |
| integer |  |  |  |  |  |  |

FlADD source

#### `FICOM`

*Integer compare*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 72-86+EA | 72-86 71-75 |  | 18(16-20) | 2-4 FICOM TOOL.N] ASSES |
| integer |  |  |  |  |  |  |
| short |  | 78-91+EA | 78-91 56-63 |  | 16.5(15-17) | 2-4 FICOM [BP+4].PARM_COUNT |
| integer |  |  |  |  |  |  |

FlCOM source

#### `FICOMP`

*Integer compare and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 74-88+EA | 74-88 | 71-75 | 18(16-20) | 2-4 FICOMP [BP].LIMIT [SI] |
| integer |  |  |  |  |  |  |
| short |  | 80-93+EA | 80-93 | 56-63 | 16.5(15-17) | 2-4 FICOMP N_SAMPLES |
| integer |  |  |  |  |  |  |

FICOMP source

#### `FIDIV`

*Integer divide*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 224-238+EA 224-238 |  | 136-140 | 73 | 2-4 FIDIV SURVEY.OBSERVATIONS |
| integer |  |  |  |  |  |  |
| short |  | 230-243+EA 230-243 |  | 120-127 | 73 | 2-4 FIDIV RELATIVE_ANGLE [DI] |
| integer |  |  |  |  |  |  |

FIDIV source ;:<X<::i>de.* .; .......•.... < .... <Pyte!!J •.. l~xample

#### `FIDIVR`

*Integer divide reversed*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word integer 225-239+EA 224-238 135-141 |  |  |  |  | 73 2-4 | FIDIVR [BP].x_COORD |
| short integer 231-245+EA 230-243 121-128 |  |  |  |  | 73 2-4 | FIDIVR FREQUENCY |

FIDIVR source

#### `FILD`

*Integer load*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 46-54+EA | 46-54 | 61--65 | 11.5(9-12) | 2-4 FILD [BX].SEQUENCE |
| integer |  |  |  |  |  |  |
| short |  | 52--60+EA | 52--60 | 45-52 | 14.5(13-16) | 2-4 FILD STANDOFF [DI] |
| integer |  |  |  |  |  |  |
| long |  | 60--68+EA | 60--68 | 56--67 | 16.8(10-18) | 2-4 FILD RESPONSE.COUNT |
| integer |  |  |  |  |  |  |

FILD source

#### `FIMUL`

*Integer multiply*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word integer |  | 124-138+EA | 124-138 | 76-87 | 8 | 2-4 FIMUL BEARING |
| short integer |  | 130-144+ EA | 130-144 | 61-82 | 8 | 2-4 FIMUL POSmON.Z_AXIS |

FIMUL source

#### `FINCSTP`

*Increment stack pOinter*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  | Exceptions: |  | None |  |  |
| No operands |  | 6-12 | 6-12 | 21 | 3 | 2 FINCSTP |

FINCSTP (no operands)

#### `FINIT`

*Initialize processor*

#### `FNINIT`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 2-8 | 2-8 | 33 | 17 | 2 FINIT |

FINIT /FNINIT (no operands)

#### `FIST`

*Integer store*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 80-90+EA | 80-90 | 82-95 | 33.4(29-34) | 2-4 FIST OBS.COUNT [51] |
| integer |  |  |  |  |  |  |
| short |  | 82-92+EA | 82-92 | 79-93 | 32.4(28--34) | 2-4 FIST [BP;].FACTORED]ULSES |
| integer |  |  |  |  |  |  |

FIST destination

#### `FISTP`

*Integer store and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 82-92+EA | 82-92 | 82-95 33.4(29-34) |  | 2-4 FISTP[BX]. |
| integer |  |  |  |  |  | ALPHA_COUNT [51] |
| short |  | 84-94+EA | 84-94 | 79-93 33.4(29-34) |  | FISTP CORRECTED_TIME 2-4 |
| integer |  |  |  |  |  |  |
| long |  | 94-105+EA 94-105 80-97 33.4(29-34) |  |  |  | 2-4 FISTP PANEL. N_READINGS |
| integer |  |  |  |  |  |  |

FISTP destination

#### `FISUB`

*Integer subtract*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 102-137+EA 102-137 |  | 71--83 | 22.5(19-32) | 2-4 FISUB BASE_FREQUENCY |
| integer |  |  |  |  |  |  |
| short |  | 108-143+EA 108-143 |  | 57--82 | 24(20-35) | 2-4 FISUB TRAIN_SIZE [OI] |
| integer |  |  |  |  |  |  |

Exceptions: \, D, 0, P FISUB source

#### `FISUBR`

*Integer subtract reversed*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| word |  | 103-139+EA | 102-137 | 72--84 | 22.5(19-32) | 2-4 FISUBR FLOOR [BX][SI] |
| integer |  |  |  |  |  |  |
| short |  | 109-144+EA | 108-143 | 58-83 | 24(20-35) | 2-4 FISUBR BALANCE |
| integer |  |  |  |  |  |  |

Exceptions: I, D, 0, P FISUBR source

#### `FLO`

*Load real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i) |  | 17-22 | 17-22 | 14 | 4 | 2 FLDST(O) |
| short real |  | 38-56+EA | 38-56 | 20 | 3 | 2-4 FLO READING [SI].PRESSURE |
| long real |  | 40--60+EA | 40--60 | 25 | 3 | 2-4 FLO [BP].TEMPERATURE |
| Temp real |  | 53-65+EA | 53-65 | 44 | 6 | 2-4 FLO SA VEREADING |

Exceptions: \, D FLDsource

#### `FLOCW`

*Load control word*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| 2 bytes |  | 7-14+EA | 7-14 | 19 | 4 | 2-4 FLDCW CONTROL_WORD |

FLDCW source

#### `FLDENV`

*Load environment*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| 14 bytes |  | 35-45+EA | 35-45 | 71 | 44 real or virtual | 34 2-4 FLDENV [BP+6] |
|  |  |  |  |  | protected |  |

FLDENV source

#### `FLDLG2`

*Load 109102*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 18--24 | 18--24 | 41 | 8 | 2 FLDLG2 |

FLDLG2 (no operands)

#### `FLDLN2`

*Load 109e2*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 17-23 | 17-23 | 41 | 8 | 2 FLDLN2 |

FLDLN2 (no operands)

#### `FLDL2E`

*I*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 15-21 | 15-21 | 40 | 8 | 2 FLDL2E |

Loadl092 e FLDL2E (no operands)

#### `FLDL2T`

*I*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 16-22 | 16-22 | 40 | 8 | 2 FLDL2T |

Load 109210 FLDL2T (no operands)

#### `FLOPI`

*Load (pi)*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 16-22 | 16-22 | 40 | 8 | 2 FLDPI |

FLDPI (no operands)

#### `FLOZ`

*Load +0.0*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 11-17 | 11-17 | 20 | 4 | 2 FLDZ |

FLDZ (no operands)

#### `FL01`

*Load +1.0*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 15-21 | 15-21 | 24 | 4 | 2 FLD1 |

FLD1 (no operands)

#### `FMUL`

*Multiply real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| I IST(i),ST 1ST, |  | 90-105 | 90-145 . | 29-57 | 16 | 2 FMUL ST,ST(3) |
| 90-105,ST(1)* |  |  |  |  |  |  |
| I IST(i),ST | 1ST, | 130-145 | 90-145 | 29-57 | 16 | 2 FMUL ST,ST(3) |
| ST,ST(l) |  |  |  |  |  |  |
| short real |  | 110-125+EA | 110-125 | 27-35 | 11 | 2-4 FMUL SPEED_FACTOR |
| long real* |  | 112-126+EA | 112-168 | 32-57 |  | 2-4 FMUL [BP].HEIGHT |
| long real |  | 154-168+EA | 112-168 | 32-57 | 14 | 2-4 FMUL [BP].HEIGHT |
| example, | it was | loaded from | a short-real | memory | operand). |  |

Exceptions: I, 0, 0, U, P FMUL / / source/ destination, source

> *Occurs when one or both operands is "short" -it has 40 trailing zeros in its fraction (for

#### `FMULP`

*Multiply real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),ST* |  | 94-108 | 198-208 | 29-57 |  | 2 FMULP ST(l),ST |
| ST(i),ST |  | 134-148 198-208 |  | 29-57 | 16 | 2 FMULP ST(l),ST |
| example, it | was | loaded from a short-real |  |  | memory | operand). |

FMULP destination, source

> *Occurs when one or both operands is "short" -it has 40 trailing zeros in its fraction (for

#### `FNOP`

*No operation*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| No operands |  | 10-16 | 10-16 | 12 | 3 | 2 FNOP |

FNOP (no operands)

#### `FPATAN`

*Partial arctangent*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 250-800 | 250-800 | 314-487 | 5(2-17) | 2 FPATAN |

FPATAN (no operands)

#### `FPREM`

*Partial remainder*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 15-190 | 15-190 | 74-155 | 2(2-8) | 2 FPREM |

FPREM (no operands)

#### `FPREM1`

*Partial remainder*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  |  |  | 95-185 | 94.5(72-167) | 2 FPREM1 |

FPREM (no operands)

#### `FPTAN`

*Partial tangent*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands 30-540 |  |  | 30-540 | 191-573 | 244(200-273) | 2 FPTAN |

FPTAN (no operands)

#### `FRNDINT`

*Round to integer*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 16-50 | 16-50 | 66-80 | 29.1(21-30) | 2 FRNDINT |

FRNDINT (no operands)

#### `FRSTOR`

*Restore saved state*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| 94 bytes |  | 197-207+EA | 205-215 | 308 | 131 real | FRSTOR or virtual 120 2-4 |
|  |  |  |  |  | protected | [BP] |
| Note: The 80287 execution clock |  |  |  | count for | this instruction | is not meaningful in determining |
| overall instruction execution time. For |  |  |  | typical | frequency ratios | of the 80286 and 80287 clocks, |
| 80287 execution occurs |  |  | in parallel | with the | operand | transfers. The operand transfers |
| determine |  | the overall execution time |  | of the | instructions. For 80286:80287 clock frequency |  |
| ratios of | 4:8, 1:1, | and | 8:5, the overall execution clock count for |  |  | this instruction is estimated at |
| 490,302, | and | 227 80287 clocks, respectively. |  |  |  |  |

FRSTOR source

#### `FSAVE`

*Save state*

#### `FNSAVE`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| 94 bytes |  | 197-207+EA | 205-215 | 375-376 |  | 2-4 FSAVE [BP] |
| Note: The 80287 execution clock |  |  |  | count for this | instruction | is not meaningful in determining |
| overall instruction execution time. |  |  |  | For typical | frequency ratios | of the 80286 and 80287 clocks, |
| 80287 execution occurs |  |  | in parallel | with the | operand transfers. The | operand transfers |
| determine |  | the overall execution time |  | of the | instruction. For 80286:80287 clock frequency |  |
| ratios of | 4:8, | 1:1, and | 8:5, the overall execution clock |  | count | for this instruction is estimated at |
| 376,233, | and | 17480287 clocks, respectively. |  |  |  |  |

FSAVE/FNSAVE destination

#### `FSCALE`

*Scale*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 32-38 | 32-38 | 67-86 | 31(30-32) | 2 FSCALE |

FSCALE (no operands)

#### `FSETPM`

*Set protected mode*

| Opcode | Instruction | 287 | Description |
|---|---|---|---|
| No operands |  | 2-8 | 2 FSETPM |

FSETPM (no operands)

#### `FSIN`

*Sine of S1(0)*

| Opcode | Instruction | 387 | 486 | Description |
|---|---|---|---|---|
| No operands |  | 122-771* | 241(193-279) | 2 FSIN |
| additional clocks |  | may be | needed to reduce | the operand. |

FSIN

> *These timings hold for operands in the range I x I /4. For operands not in this range, up to 76

#### `FSINCOS`

*Sine and cosine of S1(0)*

| Opcode | Instruction | 387 | 486 | Description |
|---|---|---|---|---|
| No operands |  | 194-809* | 291(243-329) | FSINCOS 2 |
| additional clocks |  | may | be needed to | reduce the operand. |

FSINCOS

> *These timings hold for operands in the range I x I /4. For operands not in this range, up to 76

#### `FSQRT`

*Square root*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 180-186 180-186 |  | 122-129 | 85.5(83-87) 2 | FSQRT |

FSQRT (no operands)

#### `FST`

*Store real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i) |  | 15-22 | 15-22 | 11 | 3 | 2 FSTST(3) |
| short real |  | 84-90+EA | 84-90 | 44 | 7 | 2-4 FST CORRELA nON [OI] |
| long real |  | 96-104+EA | 96-104 | 45 | 8 | 2-4 FST MEAN_READING |

FST destination

#### `FSTCW`

*Store control word*

#### `FNSTCW`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| 9~#it4$'" |  |  |  |  |  |  |
| 2 bytes |  | 12-18+EA | 12-18 | 15 |  | 2-4 FSTCW SA VB_CONTROL |

FSTCW destination

#### `FSTENV`

*Store environment*

#### `FNSTENV`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| 14 bytes |  | 40-50+EA | 40-50 | 103-104 |  | 2-4 FSTENV[BP] |

FSTENV destination

#### `FSTP`

*Store real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i) |  | 17-24 | 17-24 | 12 | 3 | 2 FSTPST(2) |
| short real |  | 86-92+EA | 86-92 | 44 | 7 | 2-4 FSTP [BX]. ADJUSTED_RPM |
| long real |  | 98-106+EA | 98-106 | 45 | 8 | 2-4 FSTP TOTAL_DOSAGE |
| Temp real |  | 52-58+EA | 52-58 | 53 | 6 | FSTP REG_SA VB [SI] 2-4 |

FSTP destination

#### `FSTSW`

*Store status word*

#### `FNSTSW`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| 2 bytes |  | 12-18+EA | 12-18 | 15 | 3 | 2-4 FSTSW SAVE_STATUS |

FSTSW /FNSTSW destination

#### `FSTSW AX`

*Store status word to AX*

#### `FNSTSWAX`

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| AX |  |  | 10-16 | 13 | 3 | 2 F5T5W AX |

FSTSW destination

#### `FSUB`

*Subtract real*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),5T |  |  |  |  |  |  |
| short real |  | 90-120+EA | 90-120 | 24-32 | 7(5-17) | 2-4 F5UB BA5E_ VALUE |
| long real |  | 95-125+EA | 95-125 | 28-36 | 7(5-17) | 2-4 F5UB COORDINATE.X |

Exceptions: I, 0, 0, U, P FSUB / /source/destination, source I 15T,5TI (i) I 70-100 70-100 26-37 7(5-17) 2 F5UB 5T,5T(2)

#### `FSUBP`

*Subtract real and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),5T |  | 75-105 | 75-105 | 26-37 | 7(5-17) | 2 F5UBP 5T(2),5T |

Exceptions: I, 0, 0, U, P FSUBP destination, source

#### `FSUBR`

*Subtract real reversed*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),5T |  |  |  |  |  |  |
| short real |  | 90-120+EA | 90-120 | 25-33 | 7(5-17) | 2-4 F5UBR VECTOR [51] |
| long real |  | 95-125+EA | 95-125 | 29-37 | 7(5-17) | .2-4 F5UBR [BX].INDEX |

Exceptions: I, 0, 0, U, P FSUBR / / source/ destination, source I 15T,ST(i) I 70-100 70-100 26-37 7(5-17) 2 F5UBR 5T,ST(1)

#### `FSUBRP`

*Subtract real reversed and pop*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| ST(i),5T |  | 75-105 | 75-105 | 26-37 | 7(5-17) | 2 F5UBRP ST(1),5T |

Exceptions: I, 0, 0, U, P FSUBRP destination, source

#### `FTST`

*Test stack top against +0.0*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | FIST (no | operands) |  |  |
| No operands |  | 38-48 | 38-48 | 28 | 4 | 2 FTST |

#### `FUCOM`

*Unordered compare*

| Opcode | Instruction | 387 | 486 | Description |
|---|---|---|---|---|
| / /ST(i) |  | 24 | 4 | 2 FUCOMST(l) |

#### `FUCOMP`

*Unordered compare*

| Opcode | Instruction | 387 | 486 | Description |
|---|---|---|---|---|
| / /ST(i) |  | 26 | 4 | 2 FUCOMP ST(2) |

#### `FUCOMPP`

*Unordered compare*

| Opcode | Instruction | 387 | 486 | Description |
|---|---|---|---|---|
| No operands |  | 26 | 5 | 2 FUCOMPP |

#### `FWAIT`

*Wait*

| Opcode | Instruction | 486 | Description |
|---|---|---|---|
|  | Exceptions: |  | None (CPU instruction) |
|  | FWAIT | (no | operands) |
| No operands | 3+5n* | 1-3 | FWAIT |
| instruction. |  |  | . |

> *n = number of time CPU examines BUSY line before 80287 completes execution of previous

#### `FXAM`

*Examine stack top*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
|  |  |  | Exceptions: | None |  |  |
| No operands |  | 12-23 | 12-23 | 30-38 | 8 | 2 FXAM |

FXAM (no operands)

#### `FXCH`

*Exchange registers*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| / /ST(i) |  | 10-15 | 10-15 | 18 | 4 | 2 FXCHST(2) |

FXCH / / destination

#### `FXTRACT`

*Extract exponent and significant*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 27"'-55 | 27-55 | 70-76 | 19(16-20) | 2 FXTRACT |

FXTRACT (no operands)

#### `FYL2X`

*Y* IOg2X*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 900-1100 900-1100 120-538 |  |  | 311(196-329) 2 | FYL2X |

FYL2X (no operands)

#### `FYL2XP1`

*IOg2(X 1)*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 700-1000 | 700-1000 | 257-547 | 313(171-326) 2 | FYL2XP1 |

FYL2XP1 (no operands)

#### `F2XM1 2x-1`

*P*

| Opcode | Instruction | 87 | 287 | 387 | 486 | Description |
|---|---|---|---|---|---|---|
| No operands |  | 310-630 310-630 |  | 211--476 | 242(140-279) | 2 F2XM1 |

-------------------------------------------- F2XMl (no operands)

