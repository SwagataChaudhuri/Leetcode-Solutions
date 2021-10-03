# **Product of Array Except Self**

[Link](https://leetcode.com/problems/product-of-array-except-self/)

**Medium**

Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

**Example 2:**

```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

**Constraints:**

- `2 <= nums.length <= 105`
- `-30 <= nums[i] <= 30`
- The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

**Follow up:** Can you solve the problem in `O(1) `extra space complexity? (The output array **does not** count as extra space for space complexity analysis.)

**Solution 01**

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        result = []
        left_product, right_product = [0] * n, [0] * n
        left_product[0] = 1
        right_product[n - 1] = 1
        for i in range(1, n):
            left_product[i] = nums[i - 1] * left_product[i - 1]
        for i in range(n - 2, -1, -1):
            right_product[i] = nums[i + 1] * right_product[i + 1]
        for i in range(n):
            result.append(left_product[i] * right_product[i])
        return result
```

**Solution 02**

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        right, result = 1, [1] + [0] * (n - 1)
        for i in range(1, n):
            result[i] = nums[i - 1] * result[i - 1]
        for i in range(n - 1, -1, -1):
            result[i] *= right
            right *= nums[i]
        return result
```
