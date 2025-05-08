# Compiler

> A teaching compiler written in Python that parses a small C‑like language (minimal++), generates equivalent C code, and then produces x86 assembly via GCC. The project implements lexical analysis, parsing, semantic checks, and code generation to demonstrate end‑to‑end compiler construction ([github.com](https://github.com/johnprif/Compiler)). 

## 📋 Table of Contents

1. [Overview](#overview)  
2. [Features](#features)  
3. [Test Programs](#test-programs)  
4. [Technologies](#technologies)  
5. [Installation](#installation)  
6. [Usage](#usage)  
7. [Architecture](#architecture)  
8. [Report & Grammar](#report--grammar)
8. [Contributing](#contributing)  
9. [License](#license)  
10. [Contact](#contact)  

## Overview
This project is an educational compiler implemented in Python 3 that takes as input programs written in minimal++ (a small C‑like grammar), translates them to C code, and then invokes GCC to produce x86 assembly and executable output. It covers all major compiler phases—lexing, parsing, semantic analysis, intermediate code generation, and final code emission. The goal is to understand how high‑level language constructs map to low‑level code and how an OS executes compiled programs.

## Features
- **Lexical Analysis**: Tokenizes minimal++ source using regex‑based scanner.
- **Parser**: Recursive‑descent parser for minimal++ grammar (operators, control flow, functions).
- **Semantic Checks**: Type checking, symbol table management, scope rules enforcement.
- **Code Generation**: Emits equivalent C code and then x86 assembly via `gcc -S`.
- **Test Suite**: Includes sample `.min` programs with expected C, assembly, and execution output.
- **Extensible**: Grammar and code‑gen modules separated for easy extension.

## Test Programs
Sample minimal++ programs are provided under `/`:

| File            | Description                                                                 |
|---------------------|-------------------------------------------------------------------------------|
| `test_1.min` | Arithmetic expressions and variable usage             |
| `test_2.min` | Control flow: `if`, `while` loops |
| `test_3.min`     | Functions and recursion               |
| `test_4.min`       | Array and pointer operations  

## Technologies
|             |                                                                  |
|---------------------|-------------------------------------------------------------------------------|
| Component | Arithmetic expressions and variable usage             |
| Language | Control flow: `if`, `while` loops |
| Compiler frontend     | Functions and recursion               |
| Code generation       | Array and pointer operations   |

## Installation
1. **Clone the repo**
```bash
git clone https://github.com/johnprif/Compiler.git
cd Compiler
```
2. **Install dependencies** (PLY)
```bash
pip install ply
```
3. **Ensure GCC** is installed and on your PATH for C and assembly generation

## **Usage**
Compile a `.min` file end‑to‑end:
```bash
python3 minimal++.py tests/test_1.min
# Generates test_1_quads.c, test_1_final.asm, and executable via gcc
./a.out
```
Control flags are available in the script for debug tracing of lexer/parser.

## Architecture
```plaintext
┌─────────────┐     ┌──────────┐     ┌──────────────┐
│ Source (.min)│ --> │ Lexer    │ --> │ Parser       │
└─────────────┘     └──────────┘     └──────────────┘
                                          │
                                          v
                                    ┌─────────────┐
                                    │ Semantic    │
                                    │ Analyzer    │
                                    └─────────────┘
                                          │
                                          v
                                    ┌─────────────┐
                                    │ Code Gen    │
                                    └─────────────┘
                                          │
                                          v
                         ┌───────────────────────────┐
                         │ Generated C & Assembly     │
                         └───────────────────────────┘
```
Follows classical compiler phases: scanning → parsing → semantic analysis → code generation.

## Report & Grammar
Detailed design, algorithmic choices, and test results are documented in `report.pdf`.
The minimal++ grammar is defined in `Η γραμματική της minimal++.v1.2.pdf` under the repo root.

## Contributing
Contributions are welcome! Please fork, create a feature branch, and submit a PR. For major changes, open an issue first to discuss.

## License
This project is licensed under the **MIT License**. See [LICENSE](https://github.com/johnprif/Compiler/blob/master/LICENSE) for full text.

## Contact
- GitHub: [johnprif](https://github.com/johnprif)
- Email: [giannispriftis37@gmail.com](mailto:giannispriftis37@gmail.com)
- Phone: [+306940020178](tel:+306940020178)

---
*Implemented as part of an academic workshop on compiler construction.*