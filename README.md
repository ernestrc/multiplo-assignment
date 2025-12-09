# Take home assignment

## Objectives
The focus is to show your software development skills. It is important to mention that the goal is not to finish the exercise; try to spend at most 1 hour working on it.

## How to start
1. **Decide** which **programming language** you are going to use, Golang or Javascript (NodeJS) are preferred.
2. **Read carefully the problem** described below and if you have any questions, please submit an issue in this repository.
3. Clone this repository, break down the problem into smaller tasks and show your work as an incremental stream of commits.
4. Once you're done, update the contents of this readme with instructions on how to run your program(s).
5. Finally create a new repository and share it with @ernestrc via settings/collaborators/add people. **Please do not fork this repository**.

***

## The Problem: Bowling Game

Create a program, which, given a sequence of rolls for one line of American Ten-Pin Bowling, produces the total score for the game. This includes two separate deliverables:

#### CLI
A CLI that takes a sequence of rolls as the first argument and prints to stdout the total score of the game. The CLI must satisfy the following --help output:
```
bowlingcalc <sequence> [options]

options:
  --json	Outputs the score as a json object with the score key set as "score".
            If this option is not passed, then score is printed to stdout.
```

#### HTTP service
An HTTP service that takes a sequence of rolls as a POST request and returns the score as a json object:
```
POST /calculate
Content-Type: json
Data: { "sequence": "9-9-9-9-9-9-9-9-9-9-"}

Content-Type: json
Data: { "score": "90"}
```

### Rules of the game

* Each game, or “line” of bowling, includes **ten turns**, or “frames” for the bowler.
* In **each frame**, the bowler gets up to **two tries** to knock down all the pins.
* If in two tries, he fails to knock them all down, **the score for that frame is the total number of pins knocked down** in his two tries.
* If in two tries he knocks them all down, this is called a **“spare”** and his score for the frame **is ten plus the number of pins knocked down on his next throw** (in his next turn).
* If on his first try in the frame he knocks down all the pins, this is called a **“strike”**. His turn is over, and his score for the frame **is ten plus the simple total of the pins knocked down in his next two rolls**.
* **If he gets a spare or strike in the last (tenth) frame, the bowler gets to throw one or two more bonus balls, respectively**. These bonus throws are taken as part of the same turn. If the bonus throws knock down all the pins, the process does not repeat: the bonus throws are only used to calculate the score of the final frame.
* The game score is the total of all frame scores.

Here are some things that the **program will not do**:

* We will not provide scores for intermediate frames. If the roll is invalid or there's an incorrect number of frames, you should surface the error.

The input is a scorecard from a finished bowling game, where “X” stands for a strike, “-” for no pins bowled, and “/” means a spare. Otherwise figures 1-9 indicate how many pins were knocked down in that throw.

#### Sample games:

```
12345123451234512345
```

always hitting pins without getting spares or strikes, a total score of 60

```
XXXXXXXXXXXX
```
a perfect game, 12 strikes, giving a score of 300

```
9-9-9-9-9-9-9-9-9-9-
```
heartbreak - 9 pins down each round, giving a score of 90

```
5/5/5/5/5/5/5/5/5/5/5
```
a spare every round, giving a score of 150

Have fun!
