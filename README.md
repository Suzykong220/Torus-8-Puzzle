# Torus-8-Puzzle

8-puzzle is a sliding game, where the top, bottom, left, or right neighboring tile can
slide into the empty square. However, if the empty square is not in the middle, not all four neighbors exist.
A torus 8-puzzle is a variant with the following change: when the empty square is at the border, the tile
at the opposite end can slide into it, too. 

1 2 3
4 5
6 7 8
This state has four successors in torus 8-puzzle. Three of them are the standard:
1 2
4 5 3
6 7 8

1 2 3
4 5 8
6 7

1 2 3
4 5
6 7 8

However, the fourth successor allows the tile 4 to slide out to the left and re-enter from the right into the
empty square:
1 2 3
5 4
6 7 8
We can think of that row as a ring, where a tile going out of the board from one end automatically
enters from the other end. This is true for all rows and all columns. Technically (in topology), this is known
as a torus – hence the name. (Caution: If you search torus puzzle online, you may come across the paper
“How to Solve the Torus Puzzle.” That game is different.)
Here is another example state:
1 2
3 4 5
6 7 8
It has four successor states. Two are standard:
1 2
3 4 5
6 7 8

3 1 2
4 5
6 7 8
The third one comes from the torus row ring movement:
2 1
3 4 5
6 7 8
And the fourth one comes from the torus column ring movement:
CS 540 Fall 2017
6 1 2
3 4 5
7 8
It is easy to see that any state has exactly four successors in the torus 8-puzzle.
For this question, you will use iterative deepening depth-first search to find the shortest path from an
input state to the goal state (which will always be this state):
1 2 3
4 5 6
7 8
Write a program Torus.java with the following command line format:
$java Torus FLAG tile1 tile2 tile3 tile4 tile5 tile6 tile7 tile8 tile9
where FLAG is an integer that specifies the output of the program (see below). Tile1 – tile9 specify the
initial state in the natural reading order (left to right, top to bottom). These take values in integer 1–8
for the 8 tiles, plus 0 for the empty space. For example, if the initial state is our very first example and
FLAG=100, the command line would be
$java Torus 100 1 2 3 4 5 0 6 7 8

1. When FLAG=100, print out the four successor states of the initial state, in the order they are pushed
into the stack
2. When FLAG=2XX, perform a depth-limited depth-first search with cutoff depth XX
3. When FLAG=3XX, perform a depth-limited depth-first search with cutoff depth XX like in part b.
But this time, also print out the backpointers. That is, each printed state should be followed by the
word “parent,” then the parent state
4. When FLAG=4XX, perform a depth-limited depth-first search with cutoff depth XX like in part b.
But this time, only print out the prefix path (starting from the initial state) for the very first state you
goal-check at depth XX+1 (recall the initial state is goal-checked at depth 1). 
5. When FLAG=500, perform iterative deepening
