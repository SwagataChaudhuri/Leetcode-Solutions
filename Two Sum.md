# **Two Sum**

[Link](https://leetcode.com/problems/two-sum/)

**Easy**

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

**Follow-up:** Can you come up with an algorithm that is less than `O(n2) `time complexity?

**Solution 01**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        result = []
        for i, j in enumerate(nums):
            temp = target - j
            if temp in nums:
                if temp == j:
                    for k in range(i + 1, len(nums)):
                        if nums[k] == temp:
                            result.append(i)
                            result.append(k)
                            break
                else:
                    result.append(i)
                    result.append(nums.index(temp))
                    break
        return result
```

**Solution 02**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        result = []
        for i, j in enumerate(nums):
            temp1 = target - j
            temp2 = nums[i + 1:]
            if temp2.count(temp1) > 0:
                result.append(i)
                result.append(temp2.index(temp1) + i + 1)
                break
        return result
```

**Solution 03**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        op = {}
        for i, j in enumerate(nums):
            temp = target - j
            if temp in op.keys():
                return [op.get(temp), i]
            else:
                op[j] = i
   
```

