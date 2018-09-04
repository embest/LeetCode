# 9. Palindrome Number

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example 1:

```
Input: 121
Output: true
```

Example 2:

```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

Example 3:

```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```
Follow up:

Coud you solve it without converting the integer to a string?


# Analysis
- 所有负数 不是回文
- 所有数字翻转，与原数相同则是回文（需要全部数字翻转一遍）
- 翻转一半数字，
	- 10: 1~1, 要剔除
	- 101: 1~10
	- 1001: 10~10	

# Solution 1

```
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0) return false;
        int res = 0;
        int tmp = x;
        while(tmp){
            res = res*10 + tmp%10;
            tmp/=10;
        }
        return (res==x);
    }
};
```



# Solution 2 *

```
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0 || (x%10==0 && x!=0)) return false;
        int res = 0;
        while(res < x){
            res = res*10 + x%10;
            x/=10;
        }
        return (res==x || res/10==x);
    }
};
```

