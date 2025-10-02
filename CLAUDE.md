# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a RISC-V microprocessor systems project for PUC's "Projeto de Sistemas Microprocessados" course (2026.1). The repository contains RISC-V architecture reference materials and will likely include hardware description code, assembly programs, and/or simulation tools.

## Reference Materials

- `risc-v.instruction_set.html`: Interactive HTML reference card for RISC-V ISA
  - RV32I Base Integer Instructions
  - RV32M Multiply Extension
  - RV32A Atomic Extension
  - RV32F/D Floating-Point Extensions
  - RV32C Compressed Extension
  - Pseudo Instructions
  - Register conventions (ABI names, calling conventions)

- `RISCV_CARD.pdf`: PDF version of RISC-V instruction set reference card

## RISC-V Architecture Notes

### Instruction Formats
- **R-type**: Register-register operations (add, sub, etc.)
- **I-type**: Immediate operations and loads (addi, lw, etc.)
- **S-type**: Store operations (sw, sh, sb)
- **B-type**: Branch operations (beq, bne, blt, etc.)
- **U-type**: Upper immediate (lui, auipc)
- **J-type**: Jump operations (jal)

### Register Conventions
- `x0` (zero): Always zero
- `x1` (ra): Return address (caller-saved)
- `x2` (sp): Stack pointer (callee-saved)
- `x8` (s0/fp): Frame pointer (callee-saved)
- `x10-x11` (a0-a1): Function arguments and return values
- `x12-x17` (a2-a7): Additional function arguments

### Common Coding Patterns
When writing RISC-V assembly:
- Use ABI register names (ra, sp, a0, etc.) instead of x-numbers for readability
- Respect calling conventions: save callee-saved registers (s0-s11) if modified
- Use pseudo-instructions when appropriate (e.g., `li`, `la`, `mv`, `ret`)
- Remember that there is no `sub immediate` instruction - use `addi` with negative values
