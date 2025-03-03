# Week 1 Homework

- [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
  - ```py
    class Solution:
      def twoSum(self, numbers: List[int], target: int) -> List[int]:
          left = 0
          right = len(numbers) - 1
  
          while left < right:
              if numbers[left] + numbers[right] < target:
                  left += 1
              elif numbers[left] + numbers[right] > target:
                  right -= 1
              else:
                  return [left + 1, right + 1]
    ```
- [Products of array discluding self](https://leetcode.com/problems/product-of-array-except-self/description/)
  - ```py
    class Solution:
      def productExceptSelf(self, nums: List[int]) -> List[int]:
          n = len(nums)
          ans = [1] * n
  
          curr = 1
          for i in range(n):
              ans[i] = curr
              curr *= nums[i]
          
          curr = 1
          for j in range(n - 1, -1, -1):
              ans[j] *= curr
              curr *= nums[j]
          
          return ans
    ```
- [Sort Colors](https://leetcode.com/problems/sort-colors/description/)
  - ```py
    class Solution:
      def sortColors(self, nums: List[int]) -> None:
          """
          Do not return anything, modify nums in-place instead.
          """
          
          r = 0
          w = 0
          b = len(nums) - 1
          
          while w <= b:
              if nums[w] == 1:
                  w += 1
              elif nums[w] == 0:
                  nums[w], nums[r] = nums[r], nums[w]
                  r += 1
                  w += 1
              else:
                  nums[w], nums[b] = nums[b], nums[w]
                  b -= 1
    ```
