# Simple Arithmetic Calculator in Assembly

This repository contains an assembly language project that performs basic arithmetic operations: addition, subtraction, multiplication, and division. The calculator reads two single-digit numbers from the user, processes the operations, and stores the results.

## Features

- **Reading Input**: Reads two single-digit numbers from the user.
- **Arithmetic Operations**: Performs addition, subtraction, multiplication, and division.
- **Result Storage**: Stores the results of the operations in memory for further use.

### Code Snippets

#### Reading Input
The calculator reads the first and second number from the user and converts them from ASCII to hexadecimal.

```assembly
; Read the first number
LEER:
    MOV AH, 01H ; Service 01H for reading a character
    INT 21H     ; Store the ASCII code of the character in AL
    CMP AL, 30H ; Check if the digit is less than '0'
    JL LEER
    CMP AL, 39H ; Check if the digit is greater than '9'
    JG LEER
    SUB AL, 30H ; Convert ASCII to hexadecimal
    MOV NUM1, AL

; Read the second number
LEER2:
    MOV AH, 01H ; Service 01H for reading a character
    INT 21H     ; Store the ASCII code of the character in AL
    CMP AL, 30H ; Check if the digit is less than '0'
    JL LEER2
    CMP AL, 39H ; Check if the digit is greater than '9'
    JG LEER2
    SUB AL, 30H ; Convert ASCII to hexadecimal
    MOV NUM2, AL
 ```

#### Arithmetic Operations

The calculator performs addition, subtraction, multiplication, and division, and stores the results.

```assembly
; Addition
ADD AL, NUM1 ; NUM1 + NUM2
MOV SUM, AL  ; Store the result

; Subtraction
MOV AL, NUM1
SUB AL, NUM2 ; NUM1 - NUM2
MOV RES, AL  ; Store the result

; Multiplication
MOV AL, NUM1
MOV CL, NUM2
MUL CL  ; NUM1 * NUM2
MOV MULTI, AL ; Store the result

; Division
MOV AL, NUM1
MOV BL, NUM2
DIV BL ; NUM1 / NUM2
MOV COCI, AL ; Store the quotient
MOV RESI, AH ; Store the remainder
```

### Usage

1.  Assemble and link the code using an assembler (e.g., TASM, MASM).
2.  Run the executable.
3.  Input two single-digit numbers when prompted.
4.  The calculator will perform the operations and store the results.

### Memory Variables

-   `NUM1`: First number
-   `NUM2`: Second number
-   `SUM`: Result of addition
-   `RES`: Result of subtraction
-   `MULTI`: Result of multiplication
-   `COCI`: Quotient of division
-   `RESI`: Remainder of division