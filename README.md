<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name:  LOGESH S   </h3>
<h3>Register Number:   2305001014       </h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance

## PROGRAM
```python
import math

def print_board(b): 
    for i in range(3): 
        print(b[3*i], '|', b[3*i+1], '|', b[3*i+2]); 
        if i<2: print('---------')

def check(b):
    w=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]
    for x,y,z in w:
        if b[x]==b[y]==b[z] and b[x]!=' ': return b[x]
    return 'Draw' if ' ' not in b else None

def minimax(b,d,maxp,a,beta):
    r=check(b)
    if r=='X': return -10+d
    if r=='O': return 10-d
    if r=='Draw': return 0
    if maxp:
        v=-math.inf
        for i in range(9):
            if b[i]==' ':
                b[i]='O'
                v=max(v,minimax(b,d+1,0,a,beta))
                b[i]=' '
                a=max(a,v)
                if beta<=a: break
        return v
    else:
        v=math.inf
        for i in range(9):
            if b[i]==' ':
                b[i]='X'
                v=min(v,minimax(b,d+1,1,a,beta))
                b[i]=' '
                beta=min(beta,v)
                if beta<=a: break
        return v

def best_move(b):
    best=-math.inf;m=0
    for i in range(9):
        if b[i]==' ':
            b[i]='O'
            val=minimax(b,0,0,-math.inf,math.inf)
            b[i]=' '
            if val>best: best,val=i,val
    return best

def play():
    b=[' ']*9
    print("You='X' | CPU='O'")
    print_board(b)
    while 1:
        m=int(input("Move (1-9):"))-1
        if b[m]!=' ': print("Invalid!");continue
        b[m]='X';print_board(b)
        r=check(b)
        if r: print("Result:",r);break
        print("CPU thinking...")
        b[best_move(b)]='O';print_board(b)
        r=check(b)
        if r: print("Result:",r);break

if __name__=="__main__": play()


```
<hr>
<h2>Sample Input and Output:</h2>

<img width="454" height="768" alt="Screenshot 2025-10-24 084342" src="https://github.com/user-attachments/assets/a3a5409a-ca68-4ada-bee9-0b30a2231a63" />


## RESULT
We have successfully implemented Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game.
