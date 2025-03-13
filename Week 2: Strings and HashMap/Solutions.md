# Week 2 Homework

- [String to integer atoi](https://leetcode.com/problems/string-to-integer-atoi/description/)
  - ```py
    class Solution:
        def myAtoi(self, input_string: str) -> int:
            upper_bound, lower_bound = 2**31 - 1, -2**31
            position, length = 0, len(input_string)
     
            # Skip leading whitespace
            while position < length and input_string[position] == ' ':
                position += 1
    
            # Handle sign
            multiplier = 1
            if position < length and input_string[position] == '-':
                multiplier = -1
                position += 1
            elif position < length and input_string[position] == '+':
                position += 1
    
            # Process digits
            number = 0
            while position < length and input_string[position].isdigit():
                current_digit = int(input_string[position])
                
                # Check for integer overflow
                if number > (upper_bound - current_digit) // 10:
                    return upper_bound if multiplier == 1 else lower_bound
                    
                number = number * 10 + current_digit
                position += 1
            
            return multiplier * number
    ```
- [Find all anagrams in a string](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)
  - ```py
    class Solution:
      def findAnagrams(self, s: str, p: str) -> List[int]:
          source_string, pattern = s, p
          character_counts = defaultdict(int)
          result_indices = []
          pattern_length = len(pattern)
          source_length = len(source_string)
          
          if pattern_length > source_length:
              return []
  
          # Build character frequency map from pattern
          for character in pattern:
              character_counts[character] += 1
  
          # Initialize sliding window by processing first (pattern_length-1) characters
          for index in range(pattern_length-1):
              if source_string[index] in character_counts:
                  character_counts[source_string[index]] -= 1
                  
          # Slide the window through the source string
          for window_start in range(-1, source_length-pattern_length+1):
              # Add the character moving out of the window
              if window_start > -1 and source_string[window_start] in character_counts:
                  character_counts[source_string[window_start]] += 1
                  
              # Remove the character moving into the window
              window_end = window_start + pattern_length
              if window_end < source_length and source_string[window_end] in character_counts:
                  character_counts[source_string[window_end]] -= 1
                      
              # Check if current window contains an anagram
              if all(count == 0 for count in character_counts.values()): 
                  result_indices.append(window_start + 1)
                      
          return result_indices
    ```
- [Reverse Words in a string](https://leetcode.com/problems/reverse-words-in-a-string/description/)
  - ```py
    class Solution:
      def reverseWords(self, s: str) -> str:
          input_string = s
          word_list = input_string.split()
          start_index, end_index = 0, len(word_list) - 1
          
          # Two Pointer Approach
          while start_index < end_index:
              word_list[start_index], word_list[end_index] = word_list[end_index], word_list[start_index]
              start_index += 1
              end_index -= 1
              
          return " ".join(word_list)
    ```
