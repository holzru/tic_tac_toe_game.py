import ast
import sys
def checker(board, row, column):
    try:
        row = int(row)
        column = int(column)
    except ValueError:
        print "That's not a valid move, please enter a number"
        return False
    if row > 2 or row < 0 or column > 2 or column < 0:
        print "That's not on the board!"
        return False
    elif board[row][column] != ' ':
        print "Someone is already there!"
        return False
    else:
        return True

def printer(board):
    print "    |      |      "
    print " "  +  str(board[0][0])  +  '  |  '   +  str(board[0][1])  +  '   |  '  + str(board[0][2])
    print "    |      |      "
    print '-----------------'
    print "    |      |      "
    print " "  +  str(board[1][0])  +  '  |  '   +  str(board[1][1])  +  '   |  '  + str(board[1][2])
    print "    |      |      "
    print '-----------------'
    print "    |      |      "
    print " "  +  str(board[2][0])  +  '  |  '   +  str(board[2][1])  +  '   |  '  + str(board[2][2])
    print "    |      |      "

def turn_move(turn=0, board=[[' ', ' ', ' '],[' ', ' ', ' '],[' ', ' ', ' ']]):
    if turn == 0:
        styler()
        print "move = 2 inputs: x & y where x is the row and y is the column"
        print "move values run from 0 to 2"
        print "Decide who is X and O, Xs move first"
        print "Enter yes to start"
        answer = ''
        while answer != 'yes':
            answer = raw_input("Are you ready?")
    if turn % 2 == 0:
        styler()
        print "X's turn"
        printer(board)
        player1_row = raw_input("Enter your row: ")
        player1_column = raw_input("Enter your column: ")
        if checker(board, player1_row, player1_column) == True:
            board[int(player1_row)][int(player1_column)] = 'X'
        else:
            turn_move(turn, board)
        turn += 1
        if game(turn, board) == 'next':
            turn_move(turn, board)
        else:
            styler()
            return game(turn, board)
    else:
        styler()
        print "O's turn"
        printer(board)
        player2_row = raw_input("Enter your row: ")
        player2_column = raw_input("Enter your column: ")
        if checker(board, player2_row, player2_column) == True:
            board[int(player2_row)][int(player2_column)] = 'O'
        else:
            turn_move(turn, board)
        turn += 1
        if game(turn, board) == 'next':
            turn_move(turn, board)
        else:
            styler()
            return game(turn, board)

def styler():
    print "=============================================================="

def game(turn, board):
    if isSolved(board) == 0 and turn < 9:
        return "next"
    else:
        if isSolved(board) != 0:
            print "{} is the winner!".format(isSolved(board))
            styler()
            play_again()
        else:
            print "Cats Game"
            styler()
            play_again()

def play_again():
    answer = raw_input("Would you like to play again (Y/N)?  ")
    if answer.lower() == 'y':
        turn_move(0, [[' ', ' ', ' '],[' ', ' ', ' '],[' ', ' ', ' ']])
    else:
        print "Thanks for playing!"
        sys.exit(0)


def isSolved(board):
    board = converter(board)
    for a in range(3):
        for i in range(3):
            if across(board, a) != None:
                return across(board, a)
                break
            if down(board, i) != None:
                return down(board, i)
                break
            if diagnol(board, a, i) != None:
                return diagnol(board, a, i)
                break
    return 0


def down(board, b_coor):
    check = []
    for item in board:
        check.append(item[b_coor])
    if check[0]==check[1]==check[2] != ' ':
        return check[0]
    else:
        return None

def across(board, a_coor):
    check = board[a_coor]
    if check[0]==check[1]==check[2] != ' ':
       return check[0]
    else:
        return None

def diagnol(board, a, b):
    check = []
    if a == 0:
        if b == 0:
            check.append(board[a][b])
            check.append(board[a+1][b+1])
            check.append(board[a+2][b+2])
        elif b == 2:
            check.append(board[a][b])
            check.append(board[a+1][b-1])
            check.append(board[a+2][b-2])
    elif a == 1:
        if b == 1:
            check.append(board[a][b])
            check.append(board[a-1][b-1])
            check.append(board[a+1][b+1])
            check.append(board[a][b])
            check.append(board[a-1][b+1])
            check.append(board[a+1][b-1])
        else:
            return None
    else:
        if b == 0:
            check.append(board[a][b])
            check.append(board[a-1][b+1])
            check.append(board[a-2][b+2])
        elif b == 2:
            check.append(board[a][b])
            check.append(board[a-1][b-1])
            check.append(board[a-2][b-2])
        else:
            return None
    if len(check) == 3 and check[0]==check[1]==check[2] != ' ':
        return check[0]
    elif len(check) == 6 and check[3]==check[4]==check[5] != ' ':
        return check[3]
    elif len(check) == 6 and check[0]==check[1]==check[2] != ' ':
        return check[0]
    else:
        return None

def converter(x):
    res = []
    if len(x) > 1:
        for item in x:
            if isinstance(item, basestring):
                res.append(ast.literal_eval(item))
            else:
                res.append(item)
        return res
    elif len(x) == 1:
        for item in x[0]:
            if isinstance(item, basestring):
                res.append(ast.literal_eval(item))
            else:
                res.append(item)
        return res
    else:
        return None



turn_move()
