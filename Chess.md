This Code Calculates And Stores The Win Rates, Draw Rates, And Counts For The First Moves In A Dataset Of Chess Games, Separately For White And Black Pieces, Helping To Understand The Effectiveness Of Different Opening Moves.


```python
# Create dictionaries to store win rates, draw rates, and counts for each first move
white_winrates = {}
black_winrates = {}
white_drawrates = {}
black_drawrates = {}
white_counts = {}
black_counts = {}

# Loop through the unique first moves to calculate win rates, draw rates, and counts storing them in the dictionaries
for move in unique_move1w:
    white_move_data = df[df['move1w'] == move]
    white_winrates[move] = white_move_data['perc_white_win'].mean()
    white_drawrates[move] = white_move_data['perc_draw'].mean()
    white_counts[move] = white_move_data.shape[0]

# Now for black
for move in unique_move1b:
    black_move_data = df[df['move1b'] == move]
    black_winrates[move] = black_move_data['perc_black_win'].mean()
    black_drawrates[move] = black_move_data['perc_draw'].mean()
    black_counts[move] = black_move_data.shape[0]
```
