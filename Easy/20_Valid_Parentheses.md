# 20. Valid Parentheses
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Note that an empty string is also considered valid.

Example 1:

```
Input: "()"
Output: true
```
Example 2:

```
Input: "()[]{}"
Output: true
```

Example 3:

```
Input: "(]"
Output: false
```

Example 4:

```
Input: "([)]"
Output: false
```

Example 5:

```
Input: "{[]}"
Output: true
```



# Analysis



# Solution
```
class Solution {
public:
    bool isValid(string s) {
        string left = "([{", right = ")]}";
        stack<char> myStack;
        for (auto c:s){
            if(left.find(c) != string::npos){
                myStack.push(c);
            }
            else{
                if(!myStack.empty() && c == right[left.find(myStack.top())])
                    myStack.pop();
                else
                    return false;
            }
        }
        return myStack.empty();
    }
};
```

