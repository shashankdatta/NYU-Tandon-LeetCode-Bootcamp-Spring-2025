# Week 1 Homework

- [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
  - ```python
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
  - ```
    asdasd
    ```
- [Sort Colors](https://leetcode.com/problems/sort-colors/description/)
  - ```
    asdasd
    ```
