# 35. Search Insert Position
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Example 1:

```
Input: [1,3,5,6], 5
Output: 2
```
Example 2:

```
Input: [1,3,5,6], 2
Output: 1
```
Example 3:

```
Input: [1,3,5,6], 7
Output: 4
```
Example 4:

```
Input: [1,3,5,6], 0
Output: 0
```


# Analysis



# Solution

```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int mid = nums.size()/2, start = 0, end = nums.size()-1;
        while(mid<=end && mid>=start){
            if(nums[mid]==target) return mid;
            else if(nums[mid] < target){
                if(nums[mid+1] > target) return mid+1;
                start = mid+1;
                mid = start + (end-start)/2;
            }else{
                if(nums[mid-1]<target)return mid;
                end = mid-1;
                mid = start + (end-start)/2;
            }
        }
        return mid;
    }
};
```