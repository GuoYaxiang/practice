###代码  
以下是程序，在lintcode上的测试结果是7223ms，速度不太乐观。
```
public class Solution {
    /**
     * @param A an array of Integer
     * @return  an integer
     */
    public int longestIncreasingContinuousSubsequence(int[] A) {
        int len = A.length;
        
        if(len == 0) return 0;
        
        int inc = 1;
        int dec = 1;
        int res = 0;
        
        for(int i = 0; i < len-1; i++){
            int temp1 = A[i];
            int temp2 = A[i+1];
            
            if(temp1 == temp2){
                inc++;
                dec++;
            }else if(temp1 > temp2){
                dec++;
                res = res>inc ? res : inc;
                inc = 1;
            }else{
                inc++;
                res = res>dec ? res : dec;
                dec = 1;
            }
        }
        
        res = res>inc ? res : inc;
        res = res>dec ? res : dec;
        return res;
    }
}```
