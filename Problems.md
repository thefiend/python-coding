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

### 20. Valid Parentheses

https://leetcode.com/problems/valid-parentheses/

```
def isValid(self, s):
    ans=[];map={'{':'}','[':']','(':')'}
    for char in s:
        if char in map:
            ans.append(map[char])
        else:
            if len(ans) > 0 and ans[-1] == char:
                ans.pop(-1)
            else:
                return False
    return len(ans) == 0
```

### 92. Reverse Linked List II

https://leetcode.com/problems/reverse-linked-list-ii/

```
def reverseBetween(self, head: ListNode, m: int, n: int) -> ListNode:
    nums=[]
    while head:
        nums.append(head.val)
        head = head.next
    # reverse the array from m to n
    nums[m-1:n] = list(reversed(nums[m-1:n]))

    # make our new node
    temphead = head = ListNode(nums[0])

    #construct our ll
    for i in range(1, len(nums)):
        head.next = ListNode(nums[i])
        head = head.next
    return temphead
```

### 121. Best Time to Buy and Sell Stock

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

```
def maxProfit(self, prices):
    """
    :type prices: List[int]
    :rtype: int
    """
    max_profit, min_price = 0, float('inf')
    for price in prices:
        min_price = min(min_price, price)
        profit = price - min_price
        max_profit = max(max_profit, profit)
    return max_profit
```

### 204. Count Primes (To explore)

https://leetcode.com/problems/count-primes/

```
def countPrimes(self, n):
        if n < 2:
            return 0
        strikes = [1] * n
        strikes[0] = 0
        strikes[1] = 0
        for i in range(2, int(n**0.5)+1):
            if  strikes[i] != 0:
                strikes[i*i:n:i] = [0] * ((n-1-i*i)//i + 1)
        return sum(strikes)
```

### 206. Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```
def reverseList(self, head):
    prev = None
    while head:
        head.next, head, prev = prev, head.next, head
    return prev
```

### 217. Contains Duplicate

https://leetcode.com/problems/contains-duplicate/

```
def containsDuplicate(self, nums):
        return not len(nums) == len(set(nums))
```

### 238. Product of Array Except Self

https://leetcode.com/problems/product-of-array-except-self/

```
def productExceptSelf(self, nums: List[int]) -> List[int]:
    prefix = list(accumulate(([1] + nums), mul))[:-1]
    suffix = list(accumulate(([1] + nums[::-1]), mul))[::-1][1:]
    return list(map(lambda x, y: x * y, prefix, suffix))
```

### 242. Valid Anagram

https://leetcode.com/problems/valid-anagram/

```
def isAnagram(self, s, t):
    """
    :type s: str
    :type t: str
    :rtype: bool
    """
    maps = {}
    mapt = {}
    for c in s:
        maps[c] = maps.get(c,0)+1
    for c in t:
        mapt[c] = mapt.get(c,0)+1
    return maps == mapt
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

### 15. 3Sum

https://leetcode.com/problems/3sum/

```
def threeSum(self, nums):
        nums.sort()
        result = []
        for i in range(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l = i+1
            r = len(nums)-1
            while(l < r):
                sum = nums[i] + nums[l] + nums[r]
                if sum < 0:
                    l += 1
                elif sum > 0:
                    r -= 1
                else:
                    result.append([nums[i], nums[l], nums[r]])
                    while l < len(nums)-1 and nums[l] == nums[l + 1]:
                        l += 1
                    while r > 0 and nums[r] == nums[r - 1]:
                        r -= 1
                    l += 1
                    r -= 1
        return result
```

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
    return sorted(nums)[-k]
```
