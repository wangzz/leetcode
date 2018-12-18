## 4、Longest Palindromic Substring

Medium

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

#### Example 1:

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

#### Example 2:

```
Input: "cbbd"
Output: "bb"
```

#### Code

```
int palindromeLengthWithStr(char* s, int start, int end) {
    int strLength = strlen(s);
    while (start >= 0 && end < strLength && (s[start] == s[end])) {
        start--;
        end++;
    }

    return end - start - 1;
}

char* longestPalindrome(char* s) {
    int start = 0;
    int end = 0;
    int index = 0;
    int totalLength = strlen(s);
    while (index < totalLength) {
        int len1 = palindromeLengthWithStr(s,index,index);
        int len2 = palindromeLengthWithStr(s,index,index+1);
        int len = (len1 > len2) ? len1 : len2;
        if (len > end - start) {
          start = index - (len - 1) / 2;
          end = index + len / 2;
        }

        index++;
    }

    int maxLength = end - start + 1;
    char* maxSubStr = (char* )malloc((maxLength+1)*sizeof(char));    
    memset(maxSubStr, 0, maxLength+1);
    memcpy(maxSubStr, s+start, maxLength);

    return maxSubStr;
}
```
