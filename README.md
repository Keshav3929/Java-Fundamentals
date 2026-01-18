# Java-Fundamentals
In this my main focus is on user input mechanism
# In this we'll be making a small basic structred tic-tac-toe game which will be made only using java.
1. In the first step we will be using our complete knowledge of user input through scanner and other functions and will be writing the code for it and keeping it way simple.
2. In the second step today we are writing the code of how the structure would be looking after code to the user experinece.
3. In the third step we are checking the flow of code and the error's.
Yep! It's ready

// TIC TAC TOE GAME
import java.util.Scanner;
public class practice{
/**
 * @param args
 */
public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
        char[][] board = new char[3][3];
        initialize(board);
        startGame(board, 'X');
    }

    public static void initialize(char[][] board){
        for(int row=0;row<board.length;row++){
            for(int col=0;col<board.length;col++){
                board[row][col] = ' ';
            }
        }
    }

    public static void printBoard(char[][] board){
        for(int row=0;row<board.length;row++){
            System.out.println("-----------");
            for(int col=0;col<board.length;col++){
                System.out.print(board[row][col] + " | ");
            }
            System.out.println();
        }
        System.out.println("-----------");
    }

    public static void startGame(char[][] board, char player){
        int c = 0;
        boolean gameOver = false;
        Scanner input = new Scanner(System.in);

        while(!gameOver){
            
            if(c == board.length * board.length){
                    System.err.println("Match Draw!! No Further Moves Available");
                    break;
            }
            printBoard(board);
            
            System.out.print("Player " + player + " Enter position: ");
            int row = input.nextInt();
            int col = input.nextInt();
            System.out.println();

            if(board[row][col] == ' '){
                board[row][col] = player;
                c++;
                gameOver = haveWon(board, player);

                if(gameOver){
                    System.out.println("Player " + player + " has won!");
                }
                else{
                    player = (player == 'X') ? 'O' : 'X';
                }
            }
            else{
                System.err.println("Invalid Position. Try Again!");
            }
        }
        printBoard(board);

    }

    public static boolean haveWon(char[][] board, char player){
        // row
        for(int row=0;row<board.length;row++){
            if(board[row][0] == player && board[row][1] == player && board[row][2] == player){
                return true;
            }
        }

        // column
        for(int col=0;col<board[0].length;col++){
            if(board[0][col] == player && board[1][col] == player && board[2][col] == player){
                return true;
            }
        }

        // diagonal
        if (board[0][0] == player && board[1][1] == player && board[2][2] == player) {
            return true;
        }

        if (board[0][2] == player && board[1][1] == player && board[2][0] == player) {
            return true;
        }

        return false;
    }
    }
