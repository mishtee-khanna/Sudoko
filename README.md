# 🧩 Sudoku Solver

A clean, object-oriented Sudoku solver written in Python. Given any valid 9×9 puzzle, it finds the solution using a **backtracking algorithm** and prints both the unsolved and solved boards to the console.

---

## How It Works

The solver uses **recursive backtracking** — a classic constraint-satisfaction technique:

1. Find the next empty cell (marked as `0`)
2. Try placing digits `1–9` in that cell
3. Check if the digit is valid across the row, column, and 3×3 sub-square
4. If valid, place it and recurse to the next empty cell
5. If no digit works, backtrack and try the next candidate in the previous cell
6. Repeat until the board is fully filled or deemed unsolvable

---

## Example

**Input puzzle** (`0` represents an empty cell):

```
0 0 2 | 0 0 8 | 0 0 0
0 0 0 | 0 0 3 | 7 6 2
4 3 0 | 0 0 0 | 8 0 0
------+-------+------
0 5 0 | 0 3 0 | 0 9 0
0 4 0 | 0 0 0 | 0 2 6
0 0 0 | 4 6 7 | 0 0 0
------+-------+------
0 8 6 | 7 0 4 | 0 0 0
0 0 0 | 5 1 9 | 0 0 8
1 7 0 | 0 0 6 | 0 0 5
```

**Console output:**

```
Puzzle to solve:
* * 2 * * 8 * * *
* * * * * 3 7 6 2
4 3 * * * * 8 * *
* 5 * * 3 * * 9 *
* 4 * * * * * 2 6
* * * 4 6 7 * * *
* 8 6 7 * 4 * * *
* * * 5 1 9 * * 8
1 7 * * * 6 * * 5

Solved puzzle:
6 1 2 9 7 8 5 3 4
...
```

> The full solved grid is printed directly to your terminal when you run the script.

---

## Project Structure

```
mp_online/
└── sudoku_solver.py    # All code — Board class + solve_sudoku function
```

---

## Getting Started

### Prerequisites

- Python 3.8 or higher (uses the walrus operator `:=`)

### Run it

```bash
# Clone the repo
git clone https://github.com/mishtee-khanna/mp_online.git
cd mp_online

# Run the solver
python sudoku_solver.py
```

No external libraries needed — pure Python standard library.

---

## Usage

To solve your own puzzle, edit the `puzzle` list at the bottom of `sudoku_solver.py`. Use `0` for empty cells:

```python
puzzle = [
  [0, 0, 2, 0, 0, 8, 0, 0, 0],
  [0, 0, 0, 0, 0, 3, 7, 6, 2],
  # ... 9 rows total, each with 9 values (0 = empty)
]

solve_sudoku(puzzle)
```

Then run:

```bash
python sudoku_solver.py
```

If the puzzle has no valid solution, the program prints:

```
The provided puzzle is unsolvable.
```

---

## Code Overview

### `Board` class

| Method | Description |
|---|---|
| `__init__(board)` | Initialises the board from a 9×9 list of lists |
| `__str__()` | Pretty-prints the board; empty cells display as `*` |
| `find_empty_cell()` | Returns `(row, col)` of the next `0`, or `None` if fully filled |
| `valid_in_row(row, num)` | Checks `num` does not already exist in the given row |
| `valid_in_col(col, num)` | Checks `num` does not already exist in the given column |
| `valid_in_square(row, col, num)` | Checks `num` does not already exist in the 3×3 sub-square |
| `is_valid(empty, num)` | Returns `True` only if all three checks pass |
| `solver()` | Recursive backtracking solver; returns `True` when the board is solved |

### `solve_sudoku(board)`

Top-level function. Wraps a raw 2D list in a `Board`, runs the solver, and prints the puzzle before and after.

---

## Requirements

| Requirement | Detail |
|---|---|
| Python | 3.8+ |
| External packages | None |

---

## License

MIT — free to use, modify, and distribute.
