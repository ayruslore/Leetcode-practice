## Question : Longest Palindromic Substring

Given a string `s`, return the longest palindromic substring in `s`.

**Example:**
```
Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

## Solution :

```python3
class Solution:
    def expandFromMiddle(self, s, left, right):
        if s == None or left > right:
            return 0
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        return right - left - 1

    def longestPalindrome(self, s):
        if s == None or len(s) < 1:
            return ""
        start = 0
        end = 0
        for i in range(len(s)):
            len1 = self.expandFromMiddle(s, i, i)
            len2 = self.expandFromMiddle(s, i, i+1)
            len0 = max(len1, len2)
            if len0 > end - start:
                start = i - ((len0 - 1)//2)
                end = i + (len0//2)
        return s[start:end+1]
```