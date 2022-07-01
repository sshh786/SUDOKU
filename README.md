import numpy as np

suduko = [[0,0,0,1,0,10,0,12,0,0,0,0,0,8,4,7],[7,4,2,0,0,0,0,0,1,0,5,8,0,13,0,16],[0,12,15,0,6,0,13,0,0,3,0,10,0,0,0,0],[14,8,13,9,1,0,0,0,0,11,0,0,12,10,2,0],[0,0,3,5,16,0,0,2,11,0,0,0,1,0,0,4],[0,0,0,0,4,7,0,0,16,14,0,0,0,0,11,0],[0,15,0,14,0,0,6,8,3,0,0,1,0,0,0,9],[0,0,0,4,11,0,0,0,0,0,6,7,0,0,0,10],[8,0,0,0,10,2,0,0,0,0,0,3,13,0,0,0],[5,0,0,0,15,0,0,13,8,1,0,0,16,0,10,0],[0,10,0,0,0,0,9,1,0,0,13,6,0,0,0,0],[15,0,0,13,0,0,0,6,4,0,0,2,3,5,0,0],[0,5,8,3,0,0,2,0,0,0,0,14,4,11,13,6],[0,0,0,0,13,0,14,0,0,5,0,11,0,1,12,0],[16,0,10,0,9,1,0,7,0,0,0,0,0,14,5,3],[1,14,4,0,0,0,0,0,10,0,3,0,9,0,0,0]]

print(np.matrix(suduko))

def possible(y,x,n):
    global suduko
    for i in range(0,16):
        if suduko[y][i] == n:
            return False
    for i in range(0,16):
        if suduko[i][x] == n:
            return False
    box_y = (y//4)*4
    box_x = (x//4)*4
    for i in range(0,4):
        for j in range(0,4):
            if suduko[box_y+i][box_x+j]==n:
                return False
    return True

print("\n\n")

def solve():
    for y in range(0,16):
        for x in range(0,16):
            if suduko[y][x] == 0:
                for n in range(1,17):
                    if possible(y,x,n):
                        suduko[y][x] = n
                        solve()
                        suduko[y][x] = 0
                return
    print(np.matrix(suduko))

solve()
