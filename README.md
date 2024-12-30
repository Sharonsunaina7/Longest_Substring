# Sliding Window Solution for Longest Substring Without Repeating Characters
# Longest Substring without Repeating Character

## Problem Description
Given a string `s`, find the length of the longest substring without repeating characters.

Leet Code Solution (https://leetcode.com/problems/longest-substring-without-repeating-characters/solutions/6203891/sliding-window-solution-for-longest-subs-daw6)

---

## Approach
We use the **Sliding Window** technique combined with a hash table to efficiently find the longest substring with unique characters. This approach ensures that each character in the string is processed only once, resulting in an optimal time complexity of `O(n)`.

---

## Algorithm
1. Use two pointers (`start` and `end`) to represent the current sliding window.
2. Use a hash table (dictionary) to store the last seen index of each character.
3. Iterate through the string with the `end` pointer:
    - If the character is already in the hash table and its last seen index is within the current window, adjust the `start` pointer to skip the duplicate.
    - Update the character's index in the hash table.
    - Calculate the length of the current window and update the maximum length if necessary.
4. Return the maximum length found.

---

## Code Implementation
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        index = {}  # Dictionary to store the last index of each character
        max_len = 0
        st = 0  # Start pointer for the sliding window

        for end, char in enumerate(s):
            if char in index and index[char] >= st:
                # Adjust the start pointer to skip the duplicate character
                st = index[char] + 1
            
            # Update the last seen index of the character
            index[char] = end

            # Update the maximum length of the substring
            max_len = max(max_len, end - st + 1)

        return max_len
```

---

## Complexity Analysis
- **Time Complexity**: `O(n)`
    - Each character is processed at most twice (once when expanding the window and once when contracting it).
- **Space Complexity**: `O(min(n, a))`
    - Where `n` is the length of the string and `a` is the size of the character set (e.g., 26 for lowercase English letters).

---

## Example Walkthrough
**Input**: `s = "abcabcbb"`

1. Start with `start = 0`, `end = 0`, and an empty dictionary.
2. Expand the window and process each character:
   - Add characters to the hash table, ensuring no duplicates in the window.
   - Adjust the start pointer as needed to maintain uniqueness.
   - Update the maximum length.

**Output**: The maximum length of a substring without repeating characters is `3` (`"abc"`).

---

## Tags
- Sliding Window
- Hash Table
- Two Pointers
- String Manipulation
