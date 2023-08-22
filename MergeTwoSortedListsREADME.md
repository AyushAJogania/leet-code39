# leet-code39

# Merging Two Sorted Linked Lists

This code is a C++ implementation of the **mergeTwoLists** function that merges two sorted linked lists. The function takes in two pointers to the heads of two sorted linked lists and returns a pointer to the head of the merged sorted list.

## Approach

The merging of two sorted linked lists can be done by iterating through both lists and adjusting the pointers to maintain the correct order. The key idea is to keep track of the last node in the first list (denoted as `temp`) to properly connect the nodes during merging.

1. If one of the lists is empty, return the other list as the result.
2. Determine the smaller value node between the two lists' heads as the starting point for the merged list.
3. Iterate through both lists using a while loop until one of the lists becomes empty.
4. In each iteration, find the position in the first list where the current node from the second list should be inserted. This is done by comparing values and finding the last node (`temp`) before the insertion point.
5. Update the pointers to connect the nodes in the merged list correctly.
6. Swap the pointers of the two lists to alternate between them in the next iteration.

## Implementation

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1 == nullptr) {
            return list2; // If list1 is empty, return list2
        }

        if(list2 == nullptr) {
            return list1; // If list2 is empty, return list1
        }

        if(list1->val > list2->val) {
            swap(list1, list2); // Ensure list1 always starts with the smaller value node
        }

        ListNode* res = list1; // Store the head of the merged list

        while(list1 != nullptr && list2 != nullptr) {
            ListNode* temp = nullptr; // Temporary pointer to keep track of the last node in list1
            
            // Find the position in list1 where the current node from list2 should be inserted
            while(list1 != nullptr && list1->val <= list2->val) {
                temp = list1; // Keep track of the last node in list1 before the next node
                list1 = list1->next;
            }
            
            temp->next = list2; // Connect the last node of the sublist in list1 to the current node of list2
            swap(list1, list2); // Swap the lists to alternate between them
        }
        
        return res; // Return the merged sorted list
    }
};
```

## Complexity Analysis

- Time Complexity: O(n + m), where n and m are the lengths of the two input linked lists, respectively. The algorithm iterates through both lists once.
- Space Complexity: O(1), as only a few additional pointers are used to perform the merging, and no additional data structures are required.

## Usage

To use the **mergeTwoLists** function, you can create linked lists and call the function with the heads of the two lists. The function will return the head of the merged sorted list.

```cpp
ListNode* mergedList = Solution().mergeTwoLists(list1_head, list2_head);
```
