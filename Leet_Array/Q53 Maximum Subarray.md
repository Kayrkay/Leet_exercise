### Q53 Maximum Subarray

 Kadane's algorithm 

#### Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum. 

idea: to look for all positive contiguous segments of the array. And keep track of the maximum sum contiguous segment among all segments. 

![image-20191103172719330](C:\Users\Kay\AppData\Roaming\Typora\typora-user-images\image-20191103172719330.png)

```python
def maxSubArraySum(a,size): 
      
    max_so_far = 0
    max_ending_here = 0
      
    for i in range(0, size): 
        max_ending_here = max_ending_here + a[i] 
        if max_ending_here < 0: 
            max_ending_here = 0
        # Do not compare for all elements. Compare only    
        # when  max_ending_here > 0 
        elif (max_so_far < max_ending_here): 
            max_so_far = max_ending_here 
              
    return max_so_far 
```

 **The implementation handles the case when all numbers in array are negative. **

```python
def maxSubArraySum(a,size): 
      
    max_so_far =a[0] 
    curr_max = a[0] 
      
    for i in range(1,size): 
        curr_max = max(a[i], curr_max + a[i]) 
        max_so_far = max(max_so_far,curr_max) 
          
    return max_so_far

```

**To print the subarray with the maximum sum, we maintain indices whenever we get the maximum sum.  **



```python
# Function to find the maximum contiguous subarray 
# and print its starting and end index 
def maxSubArraySum(a,size): 
    max_so_far = -maxsize - 1
    max_ending_here = 0
    start = 0
    end = 0
    s = 0
    for i in range(0,size): 
        max_ending_here += a[i] 
        if max_so_far < max_ending_here: 
            max_so_far = max_ending_here 
            start = s 
            end = i 
        if max_ending_here < 0: 
            max_ending_here = 0
            s = i+1
    print ("Maximum contiguous sum is %d"%(max_so_far)) 
    print ("Starting Index %d"%(start)) 
    print ("Ending Index %d"%(end)) 
```

##### Easy solution

```python
for i in range(1, len(nums)):
        if nums[i-1] > 0:
            nums[i] += nums[i-1]
    return max(nums)
```

 **The thought follows a simple rule:
If the sum of a subarray is positive, it has possible to make the next value bigger, so we keep do it until it turn to negative.
If the sum is negative, it has no use to the next element, so we break.
it is a game of sum, not the elements. **

