## 1. Two Sum

Easy

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

#### Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### Code:

```
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {    
    for(int i = 0; i < numsSize; i++) {
        for(int j = i+1; j < numsSize; j++) {
            if (target == (nums[i] + nums[j])) {
                int *a = (int *)malloc(2*sizeof(int));
                a[0] = i;
                a[1] = j;
                return a;
            }
        }
    }
    
    return NULL;
}
```
