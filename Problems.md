
## Easy
### 1. Two Sum
https://leetcode.com/problems/two-sum/
```
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

### 387. First Unique Character in a String
https://leetcode.com/problems/first-unique-character-in-a-string/
```
def firstUniqChar(self, s):
    """
    :type s: str
    :rtype: int
    """
    counter = {}
    string = list(s.strip())
    
    for c in string:
        if c in counter:
            counter[c] = counter[c] + 1
        else:
            counter[c] = 1
    for c in string:
        if counter[c] == 1:
            return string.index(c)
    return -1
```

## Medium

### 55. Jump Game
https://leetcode.com/problems/jump-game/
```
def canJump(self, nums):
    pos = len(nums)-1
    for i in reversed(range(len(nums))):
        if nums[i] +i >= pos:
            pos = i    
    return pos == 0
```

### 144. Binary Tree Preorder Traversal
https://leetcode.com/problems/binary-tree-preorder-traversal/
```
def preorderTraversal(self, root):        
    self.ans =[]
    def preorder(root):
        if root:
            self.ans.append(root.val)
            preorder(root.left)
            preorder(root.right)
    preorder(root)
    return self.ans
```

### 215. Kth Largest Element in an Array
https://leetcode.com/problems/kth-largest-element-in-an-array/
```
def findKthLargest(self, nums, k):
    nums.sort()
    return nums[len(nums)-k:][0]
```