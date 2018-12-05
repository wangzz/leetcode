## 2. Add Two Numbers

Medium

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

#### Example:

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

#### Code:

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode* reveserList(struct ListNode* l) {
    if(l->next == NULL) {
        return l;
    }
    
    struct ListNode* result = NULL;
    struct ListNode* temp = NULL;
    while(l->next != NULL) {
        temp = l->next;
        l->next = temp->next;
        
        if (result == NULL) {
            temp->next = l;
        } else {
            temp->next = result;
        }
        result = temp;
    }
    
    return result;
}

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    int carry = 0;
    struct ListNode* result = NULL;
    struct ListNode* temp = NULL;
    while (l1 || l2 || carry) {
        struct ListNode* node = (struct ListNode*)malloc(sizeof(struct ListNode));
        node->next = NULL;
        node->val = carry;
        
        if (l1) {
            node->val += l1->val;
        }
        
        if (l2) {
            node->val += l2->val;
        }
        
        carry = 0;
        if (node->val >= 10) {
            node->val = node->val - 10;
            carry = 1;
        }
        
        if (result == NULL) {
            result = node;
        } else {
            temp->next = node;
        }
        temp = node;
        
        if (l1) {
            l1 = l1->next;
        }
        
        if (l2) {
            l2 = l2->next;
        }
    }
    
    return result;
}
```
