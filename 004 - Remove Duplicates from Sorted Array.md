# Remove Duplicates from Sorted Array

#### Implementation
```cpp
class Solution {
public:
    int removeDuplicates(vector<int> &nums) {
        int k = 0, n = (int)nums.size();
        for(int i = 1; i < n; ++i) {
            if(nums[k]^nums[i])
                nums[++k] = nums[i];
        }
        return k + 1;
    }
};
```
