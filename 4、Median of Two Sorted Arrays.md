## 4. Median of Two Sorted Arrays

Hard

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

#### Example 1:

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

#### Example 2:

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

#### Code:

```
double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size) {
    int count = nums1Size+nums2Size;
    int array[count];
    int index1 = 0;
    int index2 = 0;
    for (int i = 0; i<count; i++) {
        if ((index1 < nums1Size) && (index2 < nums2Size)) {
            int value1 = nums1[index1];
            int value2 = nums2[index2];
            if (value1 <= value2) {
                array[i] = value1;
                index1++;
            } else {
                array[i] = value2;
                index2++;
            }
        } else if (index1 < nums1Size) {
            array[i] = nums1[index1++];
        } else if (index2 < nums2Size) {
            array[i] = nums2[index2++];
        }
    }
        
    double result = 0;
    int sep = count/2;
    int odd = count%2;
    if (odd) {
        result = array[sep];
    } else {
        result = (array[sep - 1] + array[sep])/2.0f;
    }
    
    return result;
}
```
