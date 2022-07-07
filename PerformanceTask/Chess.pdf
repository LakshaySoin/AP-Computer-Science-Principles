# 2d matrix to hold data to display to the user
board = [
    [" 8 ", "[R2]", "[K2]", "[B2]", "[Q2]", "[G2]", "[B2]", "[K2]", "[R2]"], 
    [" 7 ", "[P2]", "[P2]", "[P2]", "[P2]", "[P2]", "[P2]", "[P2]", "[P2]"],
    [" 6 ", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]"],
    [" 5 ", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]"],
    [" 4 ", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]"], 
    [" 3 ", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]", "[  ]"],
    [" 2 ", "[P1]", "[P1]", "[P1]", "[P1]", "[P1]", "[P1]", "[P1]", "[P1]"],
    [" 1 ", "[R1]", "[K1]", "[B1]", "[Q1]", "[G1]", "[B1]", "[K1]", "[R1]"],
    ["   ", " A  ", " B  ", " C  ", " D  ", " E  ", " F  ", " G  ", " H  "]
]
# 2d matrices to track the locations of the pieces on the board
pieceLocations = [
    ["R", "K", "B", "Q", "G", "B", "K", "R"],
    ["P", "P", "P", "P", "P", "P", "P", "P"],
    ["", "", "", "", "", "", "", ""],
    ["", "", "", "", "", "", "", ""],
    ["", "", "", "", "", "", "", ""],
    ["", "", "", "", "", "", "", ""],
    ["P", "P", "P", "P", "P", "P", "P", "P"],
    ["R", "K", "B", "Q", "G", "B", "K", "R"]
]
numberLocations = [
    [1, 1, 1, 1, 1, 1, 1, 1],
    [1, 1, 1, 1, 1, 1, 1, 1],
    [-1, -1, -1, -1, -1, -1, -1, -1],
    [-1, -1, -1, -1, -1, -1, -1, -1],
    [-1, -1, -1, -1, -1, -1, -1, -1],
    [-1, -1, -1, -1, -1, -1, -1, -1],
    [0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0]
]
# easier to iterate over these lists then use if statements for each letter
pieceNames = ["R", "K", "B", "Q", "G", "P"]
locationLetters = ["A", "B", "C", "D", "E", "F", "G", "H"]
# function to display the entire board after every move
def displayBoard():
    for i in range(9):
        for x in range(9):
            print(board[i][x], end = " ")
        print()
# function to check wheter the king is threatened or not
def checkValidPosition(x , y, counter):
    for i in range(8):
        for j in range(8):
            if pieceLocations[i][j] == "R" and numberLocations[i][j] != counter:
                if (i - x == 0 or y - j == 0):
                    return False
            if pieceLocations[i][j] == "K" and numberLocations[i][j] != counter:
                if ((abs(i - x) == 2 and abs(j - y) == 1) or (abs(i - x) == 1 and abs(j - y) == 2)):
                    return False
            if pieceLocations[i][j] == "B" and numberLocations[i][j] != counter:
                if (abs(i - x) == abs(j - y)):
                    return False
            if pieceLocations[i][j] == "Q" and numberLocations[i][j] != counter:
                if (abs(i - x) == abs(j - y) or j == y or i == x):
                    return False
            if pieceLocations[i][j] == "G" and numberLocations[i][j] != counter:
                if (abs(i - x) == 1 or abs(j - y) == 1):
                    return False
            if pieceLocations[i][j] == "P" and numberLocations[i][j] != counter:
                if (counter == 0):
                    if (y - j == 1 and x - i == 1):
                        return False
                elif (counter == 1):
                    if (j - y == 1 and i - x == 1):
                        return False
    return True
# function to check if a move the user entered is valid
def checkValidMove(loc, piece, num, original):
    x_final = 8 - (int(loc[1]) - 1)
    y_final = ord(loc[0]) - 65
    if piece == "R":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if (y_final == y_init or x_final == y_init and (x_final != x_init and y_final != y_init)):
            return True
        else:
            return False
    if piece == "K":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if ((abs(x_final - x_init) == 2 and abs(y_final - y_init) == 1) or (abs(x_final - x_init) == 1 and abs(y_final - y_init) == 2)):
            return True
        else:
            return False
    if piece == "B":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if (abs(x_final - x_init) == abs(y_final - y_init) and (x_final != x_init and y_final != y_init)):
            return True
        else:
            return False
    if piece == "Q":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if (abs(x_final - x_init) == abs(y_final - y_init) or y_final == y_init or x_final == x_init and (x_final != x_init and y_final != y_init)):
            return True
        else:
            return False
    if piece == "G":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if (abs(x_final - x_init) == 1 or abs(y_final - y_init) == 1):
            return True
        else:
            return False
    if piece == "P":
        x_init = 8 - (int(original[1]) - 1)
        y_init = ord(original[0]) - 65
        if num == 0:
            if (x_init - x_final == 1 or (abs(y_final - y_init) == 1 and x_init - x_final == 11 and numberLocations[x_final][y_final] != -1) or (x_init == 7 and x_init - x_final == 2)):
                return True
            else:
                return False
        elif num == 1:
            if (x_final - x_init == 1 or (abs(y_init - y_final) == 1 and x_final - x_init == 1 and numberLocations[x_final][y_final] != -1) or (x_init == 2 and x_final - x_init == 2)):
                return True
            else:
                return False
# function to determine a checkmate
def checkWinner(counter):
    for i in range(8):
        for x in range(8):
            if (pieceLocations[i][x] == "G" and numberLocations[i][x] == counter):
                if (checkValidPosition(i, x, counter)):
                    return True
                if i - 1 >= 0:
                    if (checkValidPosition(i - 1, x, counter) and numberLocations[i - 1][x] != counter):
                        return True
                if i + 1 < 8:
                    if (checkValidPosition(i + 1, x, counter) and numberLocations[i + 1][x] != counter):
                        return True
                if x - 1 >= 0:
                    if (checkValidPosition(i, x - 1, counter) and numberLocations[i][x - 1] != counter):
                        return True
                if x + 1 < 8:
                    if (checkValidPosition(i, x + 1, counter) and numberLocations[i][x + 1] != counter):
                        return True
                if i - 1 >= 0 and x - 1 >= 0:
                    if (checkValidPosition(i - 1, x - 1, counter) and numberLocations[i - 1][x - 1] != counter):
                        return True
                if i - 1 >= 0 and x + 1 < 8:
                    if (checkValidPosition(i - 1, x + 1, counter) and numberLocations[i - 1][x + 1] != counter):
                        return True
                if i + 1 < 8 and x - 1 >= 0:
                    if (checkValidPosition(i + 1, x - 1, counter) and numberLocations[i + 1][x - 1] != counter):
                        return True
                if i + 1 <= 8 and x + 1 < 8:
                    if (checkValidPosition(i + 1, x + 1, counter) and numberLocations[i + 1][x + 1] != counter):
                        return True
                return False
counter = 0
# a maximum of 50 moves can be made during the game
# driver code
while (counter < 50):
    displayBoard()
    loc = ""
    piece = ""
    original = ""
    if (counter % 2 == 0):
        while True:
            good = False
            while not good:
                piece = input("Player 1, enter the piece that you would like to move: ")
                piece = piece.upper()
                for i in pieceNames:
                    if piece == i:
                        good = True
            good = False
            while not good:
                original = input("Player 1, enter the location of the piece you want to move: ")
                original = original.upper()
                for i in locationLetters:
                    if original[0] == i:
                        good = True
                for i in range(1, 9):
                    if original[1] == i:
                        good = True
            good = False
            while not good:
                loc = input("Player 1, enter your move: ")
                loc = loc.upper()
                for i in locationLetters:
                    for x in range(1, 9):
                        if (loc == (i + str(x))):
                            good = True
                if (numberLocations[7 - (int(loc[1]) - 1)][ord(loc[0]) - 65] == counter % 2):
                    good = False
            if (checkValidMove(loc, piece, counter % 2, original)):
                break
    elif (counter % 2 == 1):
        while True:
            good = False
            while not good:
                piece = input("Player 2, enter the piece that you would like to move: ")
                piece = piece.upper()
                for i in pieceNames:
                    if piece == i:
                        good = True
            good = False
            while not good:
                original = input("Player 2, enter the location of the piece you want to move: ")
                original = original.upper()
                for i in locationLetters:
                    if original[0] == i:
                        good = True
                for i in range(1, 9):
                    if original[1] == i:
                        good = True
            good = False
            while not good:
                loc = input("Player 2, enter your move: ")
                loc = loc.upper()
                for i in locationLetters:
                    for x in range(1, 9):
                        if (loc == (i + str(x))):
                            good = True
                if (numberLocations[7 - (int(loc[1]) - 1)][ord(loc[0]) - 65] == counter % 2):
                    good = False
            if (checkValidMove(loc, piece, counter % 2, original)):
                break
    # update the data within the 2d lists
    board[8 - (int(original[1]))][ord(original[0]) - 64] = "[  ]"
    board[8 - (int(loc[1]))][ord(loc[0]) - 64] = "[" + piece + str((counter % 2) + 1) + "]"
    pieceLocations[7 - (int(original[1]) - 1)][ord(original[0]) - 65] = ""
    numberLocations[7 - (int(original[1]) - 1)][ord(original[0]) - 65] = -1
    pieceLocations[7 - (int(loc[1]) - 1)][ord(loc[0]) - 65] = piece
    numberLocations[7 - (int(loc[1]) - 1)][ord(loc[0]) - 65] = counter % 2
    # check to see if player 1 or 2 has won
    if not checkWinner(0):
        displayBoard()
        print("Player 2 has won the game!")
        break
    elif not checkWinner(1):
        displayBoard()
        print("Player 1 has won the game!")
        break
    counter += 1
# if 50 moves have finished, the game must have ended in a tie
if (counter == 50):
    print("The game has ended in a tie!")