import random
import keyboard
import time
import os
x = 0
y = 0
fruitX = random.randint(2, 18)
fruitY = random.randint(2, 18)
if fruitX == 10 and fruitY == 10:
    fruitX = 13
    fruitY = 14
direction = "None"
rows = 20
columns = 20
prevX = 0
prevY = 0
prev2X = 0
prev2Y = 0
tailX = [None]*400
tailY = [None]*400
tail_len = 0

def clear():
    os.system('cls')

def gameover():
    exit("Game is over.")

def drawBoard():
    global x, y, fruitX, fruitY, rows, columns, tail_len
    for i in range(1, rows+1):
        for j in range(1, columns+1):
            if i == 1 or i == rows or j == 1 or j == columns:
                print("# ", end="")
            elif i == y and j == x:
                print("0 ", end="")
            elif fruitY == i and fruitX == j:
                print("* ", end="")
            else:
                printed = False
                for k in range(tail_len):
                    if tailX[k] == j and tailY[k] == i:
                        print("o ", end="")
                        printed = True
                if printed == False:
                    print(" ", end=" ")
        print()
    time.sleep(0.1)

def directionSet():

# Step-by-step movement block (wasd+ENTER);
    global direction
    choice = input()
    if choice == "w":
            direction = "UP"
    elif choice == "s":
            direction = "DOWN"
    elif choice == "a":
            direction = "LEFT"
    elif choice == "d":
            direction = "RIGHT"

# Continuous movement block; out of the two, one block MUST be uncommented.
    # global direction
    # if keyboard.is_pressed('w'):
    #     direction = "UP"
    # elif keyboard.is_pressed('a'):
    #     direction = "LEFT"
    # elif keyboard.is_pressed('d'):   
    #     direction = "RIGHT"
    # elif keyboard.is_pressed('s'):
    #     direction = "DOWN"


def logic():
    global x, y, fruitX, fruitY, rows, columns, prevX, prev2X, prevY, prev2Y, tail_len, direction, tailX, tailY
    prevX = tailX[0]
    prevY = tailY[0]
    tailX[0] = x
    tailY[0] = y
    for i in range(1, tail_len):
        prev2X = tailX[i]
        prev2Y = tailY[i]
        tailX[i] = prevX
        tailY[i] = prevY
        prevX = prev2X
        prevY = prev2Y

    if direction == "UP":
        y = y-1
    if direction == "DOWN":
        y = y+1
    if direction == "LEFT":
        x = x-1
    if direction == "RIGHT":
        x = x+1
    if x == fruitX and y == fruitY:
        tail_len += 1
        fruitX = random.randint(1, 19)
        fruitY = random.randint(1, 19)
    if fruitX == x and fruitY == y:
        fruitX = random.randint(1, 19)
        fruitY = random.randint(1, 19)
    if fruitX == x and fruitY == y:
        fruitX = random.randint(1, 19)  ## Checking for a total of 3 times may not be optimal, but isn't too computationally expensive.
        fruitY = random.randint(1, 19)  ## The chances of the fruit spawning in the same place this many times are extremely small.

    if x <= 1 or x >= columns or y <= 1 or y >= columns:
        gameover()
    for h in range(tail_len):
        if tailX[h] == x and tailY[h] == y:
            gameover()
while True:
    drawBoard()
    directionSet()
    logic()


