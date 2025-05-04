```cpp
class Solution {
public:
    // 方法 1：记忆化搜索（已注释掉，存在错误）
    /*
    vector<int> memo = vector<int>(46, -1);
    int dfs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        if (memo[n] != -1) {
            return memo[n];
        }
        memo[n] = dfs(n - 1) + dfs(n - 2);
        return dfs(n - 1) + dfs(n - 2);  // 错误：应该返回 memo[n]
    }
    */
    
    // 方法 2：动态规划（空间优化版）
    int dfs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        
        int dp0 = 1, dp1 = 1;
        int dp2;
        
        for (int i = 2; i <= n; i++) {
            dp2 = dp1 + dp0;
            dp0 = dp1;
            dp1 = dp2;
        }
        
        return dp2;
    }
    
    int climbStairs(int n) {
        return dfs(n);
    }
};
```
