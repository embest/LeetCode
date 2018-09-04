# 1. Two Sum

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have ***exactly*** one solution, and you may not use the same element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

```

# Analysis

1. 返回index,不能排序。
2. 两层循环 **超时**
3. Hash Map 记录每个数的索引值。

# Solution

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> map;
        vector<int> result;
        for(int i =0; i< nums.size(); i++){
            map[nums[i]] = i;
        }
        
        for(int i =0; i< nums.size(); i++){
            int num = target - nums[i];
            if(map.find(num)!=map.end() && map[num]>i){
                result.push_back(i);
                result.push_back(map[num]);
                break;
            }
        }
        return result;
    }
};
```