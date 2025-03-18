# Week 3 Homework

- [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/description/)
  - ```py
    class Solution:
      def reverse(self, head: ListNode) -> ListNode:
          prev = None
          curr = head
          while curr:
              next_temp = curr.next
              curr.next = prev
              prev = curr
              curr = next_temp
          return prev

      # Fast and slow pointer method to get the second half of linked list to be reversed
      def isPalindrome(self, head: Optional[ListNode]) -> bool:
          slow = head
          fast = head
          while fast and fast.next:
              slow = slow.next
              fast = fast.next.next
          rev = self.reverse(slow)
          while rev:
              if head.val != rev.val:
                  return False
              head = head.next
              rev = rev.next
          return True
    ```
- [Reorder List](https://leetcode.com/problems/reorder-list/description/)
  - ```py
    class Solution:
      def reorderList(self, head: Optional[ListNode]) -> None:
          fast = head
          slow = head
  
          # Find the middle of the list
          while fast and fast.next:
              fast = fast.next.next
              slow = slow.next
  
          # Reverse the second half of the list
          second = slow.next
          slow.next = None
          node = None
  
          while second:
              temp = second.next
              second.next = node
              node = second
              second = temp
  
          # Merge the two halves
          first = head
          second = node
  
          while second:
              temp1, temp2 = first.next, second.next
              first.next, second.next = second, temp1
              first, second = temp1, temp2
    ```
- [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/)
  - ```py
    class Solution:
      def setZeroes(self, matrix: List[List[int]]) -> None:
          """
          Do not return anything, modify matrix in-place instead.
          """
          rows = len(matrix)
          cols = len(matrix[0])
  
          first_row_has_zero = False        
          first_col_has_zero = False
  
          # check if the first row contains zero
          for c in range(cols):
              if matrix[0][c] == 0:
                  first_row_has_zero = True
                  break
  
          # check if the first column contains zero
          for r in range(rows):
              if matrix[r][0] == 0:
                  first_col_has_zero = True
                  break
          
          # use the first row and column as a note
          for r in range(1, rows):
              for c in range(1, cols):
                  if matrix[r][c] == 0:
                      matrix[r][0] = 0
                      matrix[0][c] = 0
          
          # set the marked rows to zero
          for r in range(1, rows):
              if matrix[r][0] == 0:
                  for c in range(1, cols):
                      matrix[r][c] = 0
  
          # set the marked columns to zero
          for c in range(1, cols):
              if matrix[0][c] == 0:
                  for r in range(1, rows):
                      matrix[r][c] = 0
      
          # set the first row to zero if needed
          if first_row_has_zero:
              for c in range(cols):
                  matrix[0][c] = 0
  
          # set the first column to zero if needed
          if first_col_has_zero:
              for r in range(rows):
                  matrix[r][0] = 0
          
          return matrix
    ```
