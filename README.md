# Tic-tac-toe Reinforcement Learning contest

When learning how to build up Reinforcement Learning (RL) algorithms, it is good to compare to others on well-kown tasks. Here, you may propose your own algorithms and stratgeies and compare them with dummy algorithms, humans, or other algorithms. The package makes it easy to build up a leaderboard of many players/algorithms.

## How to install?

Install necessary packages by running this in a terminal (if you do not know `pipenv`, see how to install [here](https://github.com/pypa/pipenv)):
```shell
pipenv sync
```

## How to run?

You can try it out-of-the-box by running this in a terminal:
```shell
# Enters pipenv virtual environment
pipenv shell

# Run contest (dummy vs dummy - dummy plays at random)
python tictactoe play --player1=dummy --player2=dummy
```

By default, `python tictactoe play` runs 1000 games of tic-tac-toe. Player 1 starts for the 500 firsts, and player 2 does for the remaining. This command returns global results.

## Adding your own strategy/algorithm

If you want to enter the contest, you just need to add your player to the `players` subfolder. This project is primarily designed towards value function-oriented and Q-learning algorithms. Therefore, say your name is Mark, you simply need to add to the `players` subfolder a `mark.json` file containing:
```json
{
    "firstname": "Mark",
    "lastname": "Twain",
    "type": "Q", # 
    "data": {
        "---------": {
            [1, 0.2],
            [2, 0.3],
            [3, 0.3],
            [4, 0.5],
            [5, 1],
            [6, 0.7],
            [7, 0.2],
            [8, 0.2],
            [9, 0.4]
        },
        ...
    }
}
}
```

It is very important to understand this format, especially the `"data"` part: for any possible tic-tac-toe state (`"---------"` in the example, meaning an empty board, at the very start of the game), it gives you the expected future value of any action. Actions range from 1 to 9. Action 1 means placing a mark in the upper-left corner of the board, and then it goes right and down: action 4, for instance, means placing a mark at the left side of the middle row.
Using the `"type"` argument, you may specidy a state value function (V) or a state-action value function (Q).
