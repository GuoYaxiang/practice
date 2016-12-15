```
class Solution {
    /**
      * @param board: the board
        @return: wether the Sudoku is valid
      */
    public boolean isValidSudoku(char[][] board) {
        int row = board.length;
        int col = board[0].length;
        int[] num = new int[81];
        int[] num_r = new int[81];
        int[] num_c = new int[81];
        
        int i,j;
        int cur = 0;
        for(i = 0; i < row; i++){
            for(j = 0; j < col; j++){
                char temp = board[i][j];
                if(temp != '.'){
                    num[cur] = temp - '0';
                    num_r[cur] = i;
                    num_c[cur] = j;
                    cur++;
                }
            }
        }
        
        for(i = 0; i < cur; i++){
            int temp = num[i];
            for(j = 0; j < i; j++){
                if(temp != num[j]) continue;
                else{
                    int r1 = num_r[i];
                    int r2 = num_r[j];
                    int c1 = num_c[i];
                    int c2 = num_c[j];
                    
                    if(r1 == r2 || c1 == c2 || (r1/3 == r2/3 && c1/3 == c2/3)) return false;
                }
            }
        }
        
        return true;
    }
};
```
