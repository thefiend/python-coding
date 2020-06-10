
## Easy
### 1. Two Sum
https://leetcode.com/problems/two-sum/
```
class Solution(object):
    def twoSum(self, nums, target):
        map = {}
        for i in range(len(nums)):
            map[nums[i]] = i
        for i in range(len(nums)):
            diff = target-nums[i]

           ## check if diff exist in map, and index for both numbers are diff
            if diff in map and map[diff] != i:
                return [i, map[diff]]
```

## Medium

### 55. Jump Game
https://leetcode.com/problems/jump-game/
```
class Solution(object):
    def canJump(self, nums):
        pos = len(nums)-1
        for i in reversed(range(len(nums))):
            if nums[i] +i >= pos:
                pos = i    
        return pos == 0
```

### 215. Kth Largest Element in an Array
https://leetcode.com/problems/kth-largest-element-in-an-array/
```
class Solution(object):
    def findKthLargest(self, nums, k):
        nums.sort()
        return nums[len(nums)-k:][0]
```