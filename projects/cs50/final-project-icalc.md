# Final Project: iCalc

Part of [CS50x](../cs50.md) · **Language:** C · **Video demo:** [youtu.be/OQ-kzL3Th2g](https://youtu.be/OQ-kzL3Th2g)

iCalc is a command-line calculator written in C. It runs in a loop in the terminal: you type an expression like `12 * 4`, and it prints the result immediately. Typing `quit` exits.

## What it does
- Evaluates one operation per line: addition, subtraction, multiplication, or division.
- Prints **Invalid** for anything it can't safely evaluate, such as letters, malformed expressions, unsupported operators, or division by zero, instead of crashing.
- Compiles and runs with any standard C compiler, with no external libraries.

## How it works
- Input is read into a fixed-size buffer, and the trailing newline is stripped so commands like `quit` match reliably.
- Each line is parsed into two numbers and an operator, and anything that doesn't fit that format is rejected.
- Division by zero is checked explicitly before calculating.

## Challenges
- **Portability:** the first version used the CS50 library's input function, which failed to compile outside the course environment unless that library was linked. Switching to the standard C library's `fgets` made it build anywhere.
- **Input validation:** early versions behaved unpredictably on malformed input. Stricter parsing and explicit checks fixed that.

## Design choices and limits
I kept iCalc deliberately small: one operation per input, with no operator precedence, parentheses, or advanced functions. That traded features for a program that is predictable, readable, and portable. Natural next steps would be a full expression parser with precedence, more math functions, and a calculation history.

---
Code kept private per CS50's academic honesty policy. · [← CS50x overview](../cs50.md)
