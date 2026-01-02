# Maximum Average Subarray I — LeetCode 643 (Easy)

## Problem Description
You are given an integer array `nums` consisting of `n` elements, and an integer `k`.
Find a **contiguous subarray** whose length is exactly `k` that has the **maximum average value**, and return this value.
Any answer with a calculation error less than `10⁻⁵` will be accepted.

---

## Examples

### Example 1
**Input**
nums = [1, 12, -5, -6, 50, 3], k = 4

**Output**
12.75

**Explanation**
Maximum average is:
(12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75

---

### Example 2
**Input**
nums = [5], k = 1

**Output**
5.00

---

## Constraints
- `n == nums.length`
- `1 <= k <= n <= 10⁵`
- `-10⁴ <= nums[i] <= 10⁴`

## Solution

## Complexity Analysis

---

# Moving Average from Data Stream — LeetCode 346 (Easy)

## Problem Description
Given a stream of integers and a window size, calculate the **moving average** of all integers in the sliding window.

Implement a class `MovingAverage` that computes the moving average from a data stream using a **fixed-size sliding window**.

---

## Class Definition

### `MovingAverage(int size)`
- Initializes the object with a window size.
- The window holds **at most `size` recent values** from the stream.

### `next(int val)`
- Adds a new integer `val` to the stream.
- Returns the average of the **most recent values** in the window.
- If the total number of values seen so far is less than the window size, return the average of **all values so far**.

---

## Example

```text
MovingAverage m = new MovingAverage(3);
m.next(1)  -> 1
m.next(10) -> (1 + 10) / 2
m.next(3)  -> (1 + 10 + 3) / 3
m.next(5)  -> (10 + 3 + 5) / 3
```

---

## Solution

## Complexity Analysis


---

# Longest Substring Without Repeating Characters — LeetCode 3 (Medium)

## Problem Description

Given a string s, find the length of the longest substring without duplicate characters.

 ---

## Example

```text
Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

---

## Constraints

0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.

---

## Solution

## Complexity Analysis


---

# Minimum Window Substring — LeetCode 76 (Hard)

## Problem Description

Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.

 ---

## Example

```text
Example 1:

Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
Example 2:

Input: s = "a", t = "a"
Output: "a"
Explanation: The entire string s is the minimum window.
Example 3:

Input: s = "a", t = "aa"
Output: ""
Explanation: Both 'a's from t must be included in the window.
Since the largest window of s only has one 'a', return empty string.
```

---

## Constraints

m == s.length
n == t.length
1 <= m, n <= 105
s and t consist of uppercase and lowercase English letters.

## Follow up: 
Could you find an algorithm that runs in O(m + n) time?

---

## Solution

## Complexity Analysis


---
