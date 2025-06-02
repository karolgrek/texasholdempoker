# Poker Hand Evaluator

## Overview

A simple command-line tool that compares poker hands between two players based on Texas Hold'em rules.  
The program reads up to multiple game instances from standard input and determines the winner for each.

---

## Languages and Tools

* **C (C99) + POSIX**
* **CMake** (for compilation)  
* **tests-cut**
---

## Project Structure

| File                 | Description                                                                                                                  |
|----------------------|------------------------------------------------------------------------------------------------------------------------------|
| `main.c`             | Program's main loop. Coordinates input reading, hand evaluation, and result output.                                          |
| `utils.c` / `.h`     | Handles input parsing, validation and also output. Utility functions, card indexing, value translation, counting and sorting |
| `evaluator.c` / `.h` | Hand evalutation. Detects and compares hand types (high card, pair, flush, straight, etc.).                                  |
| `common.h`           | Defines the `Card` structure, constants, data types includes all header files.                                               |
| `CMakeLists`         | Build script for compiling the project                                                                                       |
| `test-mine.c`        | Contains some edge cases.                                                                                                    |

---

## How It Works

For each game instance, the program:

1. Reads two cards for **Player 1**
2. Reads two cards for **Player 2**
3. Reads five **table cards**
4. Determines the best 5-card hand each player can form using their 2 + 5 cards
5. Compares the hands and prints one of:
   - `Player 1(winner)`
   - `Player 2(winner)`
   - `Draw`

---

## Input Format

Each instance consists of **three lines**:

- Line 1: two cards of Player 1  
- Line 2: two cards of Player 2  
- Line 3: five community cards

Cards use the format `[VALUE][SUIT]`, where:

- Value: `2`–`9`, `T`, `J`, `Q`, `K`, `A`  
- Suit: `h` (♥), `d` (♦), `s` (♠), `c` (♣)

** How to run ** 
```
cmake -S . -Bbuild
cd build
make
./poker
```

## Examples:

### Example 1 (high-card wins)
```
./poker
Td As           # has high-card
Th Kd
8c 2h 6c Qs Jc

out:
Player 1
```
### Example 2 (multiple instances)
```
./poker
3d 3h
Ac Ts
Qd 8s 2c 4c Kh
4s 8d
5c 8h
7c 7h Ac Kd 2d
6s Kh
Ah 3c
Ac 4h 5h Ks Jh

out:
Player 1
Draw
Player 2
```

