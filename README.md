# Food Delivery Compiler

A 7-phase mini-compiler for an Automated Catering System, built with Flex and Bison.

## Overview

This project implements a Domain-Specific Language (DSL) for restaurant ordering commands. It demonstrates a complete compiler pipeline:

| Phase | Module | Description |
|-------|--------|-------------|
| 1 | Flex Scanner (`food.l`) | Lexical Analysis |
| 2 | Bison Parser (`food.y`) | Syntax Analysis |
| 3 | `semantic_check()` | Semantic Analysis |
| 4 | `print_tree()` | Parse Tree Generation |
| 5 | `generate_icg()` | Intermediate Code Generation |
| 6 | `optimize_code()` | Code Optimization |
| 7 | `generate_target_code()` | Target Code Generation |

## Supported Commands

- `MENU` — Display available items
- `ORDER &lt;item&gt; &lt;qty&gt;` — Add item to cart
- `REMOVE &lt;item&gt;` — Remove item from cart
- `SHOW_CART` — Display current cart
- `TOTAL` — Calculate bill total
- `DISCOUNT &lt;percent&gt;` — Apply discount
- `PLACE_ORDER` — Finalize order
- `EXIT` — Quit the shell

## Build Instructions

```bash
# Generate parser
bison -d food.y

# Generate lexer
flex food.l

# Compile
gcc food.tab.c lex.yy.c -o food -lfl

# Run
./food
