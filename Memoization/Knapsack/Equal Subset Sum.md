**👾 Partition Equal Subset Sum**

```c++
class Solution {
public:
    bool helper(vector<int> &nums,int i,int sum,vector<vector<int>> &dp){
        if(sum == 0){
            return true;
        }
        if(i >= nums.size() || sum < 0) return false;

        if(dp[i][sum] != -1) return dp[i][sum];
        bool first = helper(nums,i+1,sum - nums[i],dp);
        if(first) return dp[i][sum] = true;
        bool second = helper(nums,i+1,sum,dp);
        return dp[i][sum] = second;
    }
    bool canPartition(vector<int>& nums) {
        int sum = 0;
        for(int e:nums){
            sum += e;
        }

        if(sum % 2 != 0) return false;
        int n = nums.size();
        vector<vector<int>> dp(n + 1,vector<int>(sum/2 + 1,-1));
        return helper(nums,0,sum/2,dp);
    }
};
```
