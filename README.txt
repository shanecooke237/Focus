<-README->

I've commented on the majority of my code so in this README I'll mainly be going through the code logic rather than specifics. 

Board:
You'll notice I changed the layout of the board print I understand its not the prettiest to look at however it makes the game lot easier 
to play. The format I choose is the following:
For a red square with size one: R [1,1]: 1|
For a green square with size 4: G [6,1]: 4|
For an empty square E [0,2]: 0|
Where the coorindates of a square is [x,y]

main.c
This is where the game begins and ends. I initialize the players, the board, and have a small portion of the games' functionality here. I start the game off with a while loop that is terminated by an end_game boolean having a true value. This end_game variable is only changed by the result of a function 'board_status'. 'board_status' will check the board at the start of every move and make sure a player can make a move i.e. if they've control of at least one stack or have a reserved piece beginning their go. The code to change a player after each move is right at the beginning of this while loop. To make the game easy to follow I print the current player stats at the start of each move with a 'print_player_stats' function. One final thing to note in main.c, there is a condition to check if the current player has a reserved piece. If they do they can either place a reserved piece or proceed with a normal move. 
Other than that the game is controlled by two initiating functions 'validate_move' and 'selectpieces'. 

game_init.c
I commented quite a lot in this file so to keep this short I'll explain a few things I did here. I implemented the stack using a linked list. When moving either the top or all of one stack (original) to another (destination). I iterated through the linked list of the original stack adding all the piece colors to a list, be it one or all of the stack pieces. Once I had these colors I added each of them from this list to the top of the destination stack in order of back to front. In order to mimic placing this original stack on top of the destination stack. 
Then I went back to the linked list of the original stack and removed any pieces from there that I added to the destination stack. 
Another thing I did was allow players to move a piece or stack from one square to another with a distance of x. Where x is less than or equal to the number of pieces the player chooses to move. 
Initially I made it so they could only move an absolute distance equating to the number of pieces they choose to move. However, after consideration, I changed it so they could move any distance up to an absolute distance of 1-stack_size.
The rest of the code is well commented, if you have any questions about any of the code I'd be happy to answer. 

