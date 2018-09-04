# 7. Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```
Input: 123
Output: 321
```

**Example 2:**

```
Input: -123
Output: -321
```

**Example 3:**

```
Input: 120
Output: 21
```
**Note:**

Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2<sup>31</sup>,  2<sup>31</sup> − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

# Analysis
- 要解决溢出问题。
	- 使用long long中间变量
	- 使用int中途判断

# Solution 1


```
class Solution {
public:
    int reverse(int x) {
        long long rev = 0;
        while (x != 0) {
            rev = rev * 10 + x%10;
            x /= 10;
        }
        return (rev>INT_MAX || rev<INT_MIN)?0:rev;
    }
};

```


# Solution 2 *


```
class Solution {
public:
    int reverse(int x) {
        int rev = 0;
        while (x != 0) {
            int pop = x % 10;
            x /= 10;
            if (rev > INT_MAX/10 || (rev == INT_MAX/10 && pop > 7)) return 0;
            if (rev < INT_MIN/10 || (rev == INT_MIN/10 && pop < -8)) return 0;
            rev = rev * 10 + pop;
        }
        return rev;
    }
};
```