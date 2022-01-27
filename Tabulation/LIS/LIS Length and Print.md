```c++
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int ans = 1, n = size(nums);
        vector<int> dp(n, 1);
        
        //Parent vector to backtrack from the max element of LIS
        vector<int> parent(n, -1);
        //Index for max element of LIS
        int idx = 0;
        
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < i; j++){ 
                if(nums[i] > nums[j] && dp[i] < dp[j]+1){ 
				    dp[i] = max(dp[i], dp[j] + 1);
                    parent[i] = j; //it's difficult to explain this line, just take
                                   //a example and dry run this line in your head
                                   //to get the logic of this line.
                }
                if(ans < dp[i]){
                    ans = dp[i]; 
                    idx = i;
                }
            }
        }
        
        //Printing the LIS by backtracking from idx traversing 
        //through parent vector (alithough print will be reverse)
        while(idx != -1){
            cout<< nums[idx] <<" ";
            idx = parent[idx];
        }
        
        return ans;
    }
};
```