```c++
class Solution {
public:
    int bestTeamScore(vector<int>& scores, vector<int>& ages) {
        
        //Initializing a vector of pairs of scores and ages
        vector<pair<int,int>> sage;
        for(int i=0; i<scores.size(); i++){
            sage.push_back(make_pair(ages[i], scores[i]));
        }
        
        //Sorting according to age so we don't have to deal with age factor
        sort(sage.begin(), sage.end());
        
        //Initializing the result answer and DP 
        int ans = 0, n = size(sage);
        vector<int> dp(n, 0);
        
        for(int i = 0; i < n; i++){
            //Just like in LIS, default value of LCS array elements (DP array) is 1, so here it would be "current score" value.
            dp[i] = sage[i].second;
            
            //LIS Code based on the scores 
            for(int j = 0; j < i; j++){ 
                if(sage[i].second >= sage[j].second) 
				    dp[i] = max(dp[i], dp[j] + sage[i].second);
            }
            
            ans = max(ans, dp[i]);
        }
        
        return ans;
    }
};
```