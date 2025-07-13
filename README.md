# Simple Tic-Tac-Toe AI

board = [' ' for _ in range(9)]

def print_board():
    for i in range(3):
        print('|'.join(board[i*3:(i+1)*3]))
        if i < 2:
            print('-----')

def check_win(player):
    win_conditions = [
        [0,1,2], [3,4,5], [6,7,8],
        [0,3,6], [1,4,7], [2,5,8],
        [0,4,8], [2,4,6]
    ]
    for condition in win_conditions:
        if all(board[i] == player for i in condition):
            return True
    return False

def player_move():
    move = int(input("Enter your move (1-9): ")) - 1
    if board[move] == ' ':
        board[move] = 'X'
    else:
        print("Invalid move.")
        player_move()

def ai_move():
    for i in range(9):
        if board[i] == ' ':
            board[i] = 'O'
            return

print("You are X, AI is O")

while True:
    print_board()
    player_move()
    if check_win('X'):
        print_board()
        print("You win!")
        break
    if ' ' not in board:
        print_board()
        print("It's a tie!")
        break
    ai_move()
    if check_win('O'):
        print_board()
        print("AI wins!")
