# Matrix Chain Multiplication

#### Implementation
```cpp
class Solution {
public:
    int matrixMultiplication(int n, int a[]) {
        // code here
        // n => no. of matrices + 1
        int m = n - 1; // no. of matrices
        vector<vector<int>> dp(m + 1, vector<int>(m + 1, 1e9));
        for(int i = 0; i <= m; ++i)
            dp[i][i] = 0;
        for(int i = 1; i < m; ++i)
            dp[i][i+1] = a[i-1]*a[i]*a[i+1];
        
        for(int len = 3; len <= m; ++len) {
            for(int i = 1; i <= m - len + 1; ++i) {
                int j = i + len - 1;
                // multiply --> (i..k) * (k+1...j)
                for(int k = i; k < j; ++k)
                    dp[i][j] = min(dp[i][j], dp[i][k] + dp[k+1][j] + (a[i-1]*a[k]*a[j]));
            }
        }
        return dp[1][m];
    }
};
```
