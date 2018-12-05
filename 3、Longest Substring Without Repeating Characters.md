## 3. Longest Substring Without Repeating Characters

Medium

Given a string, find the length of the longest substring without repeating characters.

#### Example 1:

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

#### Example 2:

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

#### Example 3:

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

#### Code:

```
int lengthOfLongestSubstring(char* s) {    
    char set[256];
    memset(set,0,sizeof(set));
    int maxlen = 0;
    int index = 0;
    while(*s) {
        int lastIndex = set[*s];
        if (lastIndex) { // 当前字符已经存在了
            int count = index - lastIndex + 1;
            if (count > maxlen) {
                maxlen = count;
            }
            
            if (lastIndex > maxlen) {
                maxlen = lastIndex; // 处理 cdd 
            }
            
            if (index > maxlen) {
                maxlen = index; // 处理 abcb
            }
            
            s -= (count - 1);
            index = 0;
            memset(set,0,sizeof(set));
        }
        
        set[*s] = ++index;
        s++;
    }

    if (index > maxlen) { // 处理整个串都是同一个字符的情况
        maxlen = index;
    }
    
    return maxlen;
}
```
