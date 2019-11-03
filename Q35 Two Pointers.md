### Two Pointers 

- typically used for searching pairs in a ***sorted array***.

 Given a sorted array A (sorted in ascending order), having N integers, find if there exists any pair of elements (A[i], A[j]) such that their sum is equal to X. 

 ###### How the two-pointer technique works:

 We take two pointers, one representing the **first** element and other representing the **last** element of the array, and then we add the values kept at both the pointers. If their sum is smaller than X then we shift the left pointer to right or if their sum is greater than X then we shift the right pointer to left, in order to get closer to the sum. We keep moving the pointers until we get the sum as X. 



### Bisect Algorithm

-  to find a position in list where an element needs to be inserted to keep the list sorted. 

  **bisect(list, num, beg, end)** :- This function returns the **position** in the **sorted** list, where the number passed in argument can be placed so as to **maintain the resultant list in sorted order**.  



## Leetcode

```python
#Q35
'''
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
'''
# my answer
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        i = 0
        while i < len(nums):
            if nums[i] != target and nums[i] < target:
                i += 1
                continue
            elif nums[i] >= target:
                break
        return i     
            
```

```python
# bisect
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """       
        return len([x for x in nums if x<target])
```

```python
#binary search
def searchInsert(self, nums, target): # works even if there are duplicates. 
    l , r = 0, len(nums)-1
    while l <= r:
        mid=(l+r)/2
        if nums[mid] < target:
            l = mid+1
        else:
            if nums[mid]== target and nums[mid-1]!=target:
                return mid
            else:
                r = mid-1
    return l
```

