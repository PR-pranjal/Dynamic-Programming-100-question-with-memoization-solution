**Before you see this solution, I would highly suggest you to try these two below problem :**
***👉 [https://leetcode.com/problems/number-of-islands/***
***👉 https://leetcode.com/problems/max-area-of-island***

If you solved the above problems, that's great.👍 You can try again this problem and if you still can't, then continue seeing this solution.
In case you couldn't solve above link problems, just continue reading this solution post, everything will become crystal-clear to you.👇

**👾 Number of Islands Solution**
```c++
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int count= 0;
        for(int i=0; i<grid.size(); i++){
            for(int j=0; j<grid[i].size(); j++){
                if(grid[i][j] == '1')
                    count+= dfs(grid, i, j);
            }
        }
        
        return count;
    }
    
    int dfs(vector<vector<char>>& grid, int i, int j){
        if(i<0 || i>=grid.size() || j<0 || j>=grid[i].size() || grid[i][j] == '0')
            return 0;
        
        grid[i][j] = '0';
        dfs(grid, i+1, j);
        dfs(grid, i-1, j);
        dfs(grid, i, j+1);
        dfs(grid, i, j-1);
        return 1;
    }
};
```

**🤖 Max Area of Islands Solution**
```c++
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int maxarea= 0;
        for(int i=0; i<grid.size(); i++){
            for(int j=0; j<grid[i].size(); j++){
                if(grid[i][j] == 1){
                    maxarea = max(maxarea, dfs(grid, i, j));
                }
            }
        }
        
        return maxarea;
    }
    
    int dfs(vector<vector<int>>& grid, int i, int j){
        if(i<0 || i>=grid.size() || j<0 || j>=grid[i].size() || grid[i][j] == 0)
            return 0;
        
        grid[i][j] = 0;
        int count = 1;
        count += dfs(grid, i+1, j);
        count += dfs(grid, i-1, j);
        count += dfs(grid, i, j+1);
        count += dfs(grid, i, j-1);
        
        return count;
    }
};
```

***Finally, now if you think you can solve this problem, try again, & then go ahead if you can't.***

```c++
class Solution {
public:
    int dp[200][200];
    int n, m;
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        int cnt = 0;
        n = size(matrix), m = size(matrix[0]);
        for(int i = 0; i < n; i++)
            for(int j = 0; j < m; j++)
                cnt = max(cnt, dfs(matrix, i, j, -1));            
        return cnt;
    }
    
    int dfs(vector<vector<int>>& mat, int i, int j, int prev){
        //Base Case
        if(i < 0 || j < 0 || i >= n || j >= m || mat[i][j] <= prev) return 0;
        
        //Memoization check
        if(dp[i][j]) return dp[i][j];
        
        //Recursive relation
        return dp[i][j] = 1 + max({ dfs(mat, i + 1, j, mat[i][j]),
                                    dfs(mat, i - 1, j, mat[i][j]),
                                    dfs(mat, i, j + 1, mat[i][j]),
                                    dfs(mat, i, j - 1, mat[i][j]) });       
    }
};
```