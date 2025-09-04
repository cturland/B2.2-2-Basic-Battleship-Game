# Battleship Lite (Python + 2D Lists)

## 🎯 Learning goals
- I can create and use a **2D list** in Python.  
- I can update and traverse a 2D list using loops.  
- I can build a simple interactive program using input and output.  

---

## 📖 Task
Create a simplified version of the classic game **Battleship**.

- The computer sets up a hidden board.  
- The player tries to guess the locations of ships by entering row and column numbers.  
- The board updates after each guess.  

---

## 📝 Step 1: Create the board
We need a **5 × 5 grid** to represent the ocean. Each space starts as `"~"` (water).

**Long version (easier to understand):**
```python
board = []               # start with an empty list
for i in range(5):       # loop 5 times (for 5 rows)
    row = []             # make an empty row
    for j in range(5):   # loop 5 times (for 5 columns)
        row.append("~")  # add water to the row
    board.append(row)    # add the row to the board
```

**Short version (Pythonic):**
```python
board = [["~" for _ in range(5)] for _ in range(5)]
```
Both create the same board:
```python
~ ~ ~ ~ ~
~ ~ ~ ~ ~
~ ~ ~ ~ ~
~ ~ ~ ~ ~
~ ~ ~ ~ ~
```

---

## 🛳️ Step 2: Place a ship
- Choose one location (row, col) and mark it with "S".
- Later, you can hide this from the player (use a separate hidden board).

```python
ship_row, ship_col = 2, 3
board[ship_row][ship_col] = "S"
```

---

## 🎯 Step 3: Player guesses
- Ask the player to type a row and column number (0–4).
- If they hit the ship → mark "X".
- If they miss → mark "O".
- Show the updated board after each guess.
  
```python
guess_row = int(input("Row (0-4): "))
guess_col = int(input("Col (0-4): "))

if board[guess_row][guess_col] == "S":
    board[guess_row][guess_col] = "X"
    print("Hit!")
else:
    board[guess_row][guess_col] = "O"
    print("Miss!")
```

Print the board neatly:
```python
for row in board:
    print(" ".join(row))
```

---

## ✅ Step 4: Winning condition
- If the player hits all ship parts → display “You sank the ship!”
- End the game.

For a single-cell ship, you can end immediately on first hit.
For multi-cell ships, count remaining "S" cells.

---

## ✔️ Success Criteria

- Use a 2D list for the board.
- Add ships by updating elements in the list.
- Let the player guess multiple times until the ship is sunk.
- Print the board after each guess.

---

## ⭐ Extension Challenges

1. Multiple ships: Add more than one ship (at random positions).
2. Longer ships: Ships that take 2–3 cells (horizontal or vertical).
3. Hidden board:
-- Keep a hidden board with the ships.
-- Show the public board with only hits ("X") and misses ("O").
4. Input validation: Prevent crashes on bad inputs; reject out-of-range indices.
5. Scoring system: Track how many guesses the player needed to win.
6. Limited turns: Give the player a fixed number of shots.
7. Random placement: Place ships randomly without overlapping.

---

## 💡 Hints

Use nested loops to print or traverse a 2D list:
```python
for r in range(len(board)):
    for c in range(len(board[r])):
        # work with board[r][c]
        pass
```

To check if all ship parts are sunk:
```python
def all_sunk(board):
    for row in board:
        if "S" in row:
            return False
    return True
```
Consider separating responsibilities into functions (e.g. print_board, place_ships, take_guess).

---

## 📦 Optional structure (suggested files)

- main.py – your game loop
- board.py – helper functions (create board, print board, place ships)

---
