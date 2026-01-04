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
## Solution:

```text
def maxavgsubarr(a,k):
    win_start=0
    csum=0
    max_avg=0
    for win_end in range(len(a)):
        csum=csum+a[win_end]
        if win_end-win_start+1>=k:
            max_avg=max(max_avg,csum/k)
            csum=csum-a[win_start]
            win_start=win_start+1
    return max_avg

print(maxavgsubarr([1, 12, -5, -6, 50, 3],4))
print(maxavgsubarr([5],1))

```

## Complexity Analysis
Space: O(1)
Time: O(n)
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


```text
class MovingAverage :
    def __init__(self,size):
        self.csum=0
        self.cnt=0
        self.window=[0]*size

    def next(self,a):
        i=self.cnt%len(self.window)
        self.csum=self.csum+a-self.window[i]
        self.window[i]=a
        self.cnt+=1
        window_size=min(self.cnt,len(self.window))
        return self.csum/window_size

m=MovingAverage(3)
print(m.next(1))
print(m.next(10))
print(m.next(3))
print(m.next(5))

```


## Complexity Analysis
Space: O(1)
Time: O(1)

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


```text
def longsubstrwidoutrepeatchar(s):
    d={}
    win_start=0
    res=''
    for win_end in range(len(s)):
        rchr=s[win_end]
        if rchr not in d:
            d[rchr]=win_end
        else:
            if win_end-win_start+1>len(res):
                res=s[win_start:win_end]
                d.clear()
                d[rchr]=win_end
                win_start=win_end
    return len(res)

print(longsubstrwidoutrepeatchar('abcabcbb'))
print(longsubstrwidoutrepeatchar('bbbbb'))
print(longsubstrwidoutrepeatchar('pwwkew'))
```

## Complexity Analysis

Space: O(1)
Time: O(n)
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

```text
import math
def sol(a,b):
    pat={}
    for i in b:
        if i not in pat:
            pat[i]=1
        else:
            pat[i]+=1
    win_start=0
    cnt=0
    res=''
    min_cnt=math.inf
    for win_end in range(len(a)):
        rchr=a[win_end]
        if rchr in pat:
            pat[rchr]-=1
            if pat[rchr]==0:
                cnt=cnt+1
        while cnt==len(pat):
            if win_end-win_start+1<min_cnt:
                min_cnt=min(min_cnt,win_end-win_start+1)
                res=a[win_start:win_end+1]
            lchr=a[win_start]
            if lchr in pat:
                if pat[lchr]==0:
                    cnt=cnt-1
                pat[lchr]+=1
            win_start=win_start+1
    return res

print(sol('ADOBECODEBANC','ABC'))
print(sol('A','A'))
print(sol('A','AA'))

```

## Complexity Analysis
Space: O(1)
Time: O(m+n)

---
