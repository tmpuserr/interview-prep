# 80. Remove Duplicates from Sorted Array II

#### Implementation
```cpp
class Solution {
public:
    int removeDuplicates(vector<int> &nums) {
        int k = 0, n = (int)nums.size(), cnt = 1;
        for(int i = 1; i < n; ++i) {
            if(nums[i]^nums[k]) {
                if(cnt > 1)
                    nums[k+1] = nums[k], ++k;
                
                nums[++k] = nums[i];
                cnt = 1;
            } else
                ++cnt;
        }
        if(cnt > 1)
            nums[k+1] = nums[k], ++k;
        return k + 1;
    }
};
```
