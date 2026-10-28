# Rock Paper Scissors (Python)

A command-line Rock Paper Scissors game built with Python, developed step by step in a Jupyter Notebook.

## How the Game Works

- The user picks first: **Rock**, **Paper** or **Scissors**.
- The computer then picks **randomly from the two remaining options**.
- The winner is decided by the standard rules:
  - Rock vs Paper → **Paper** wins
  - Rock vs Scissors → **Rock** wins
  - Paper vs Scissors → **Scissors** wins
- Each game has **3 rounds**, then the final score is shown.
- After each game you can choose to play again (`Y`) or quit (`N`).

> Note: because the computer chooses from the remaining two options, a round can never end in a tie.

## Project Structure

```
rock-paper-scissors-python/
├── rock_paper_scissors.ipynb   # Notebook with step-by-step development
├── README.md
├── requirements.txt
```

## Notebook Steps

1. Get the user's selection
2. Remove the user's choice from the options
3. Computer picks randomly from the remaining options
4. Apply the winning rules
5. Play 3 rounds and keep score
6. Repeat the game until the user quits

## Getting Started

**Requirements:** Python 3.8+ (no external libraries needed).

To explore the notebook:

```bash
pip install notebook
jupyter notebook rock_paper_scissors.ipynb
```

## Example Output

```
Enter your selection: Rock, Paper or Scissors: rock
User Select: Rock || Computer Select: Paper || Computer Win!
Enter your selection: Rock, Paper or Scissors: scissors
User Select: Scissors || Computer Select: Paper || User Win!
Enter your selection: Rock, Paper or Scissors: paper
User Select: Paper || Computer Select: Rock || User Win!

Final-Score!!
User Score: 2 || Computer Score: 1
Would you like to play again? [Y / N]: n
Thank you for playing Rock Paper Scissors!
```