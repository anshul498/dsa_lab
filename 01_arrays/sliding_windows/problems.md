# Maximum Average Subarray I — LeetCode 643 (Easy)

## Problem Description
You are given an integer array `nums` consisting of `n` elements, and an integer `k`.
Find a **contiguous subarray** whose length is exactly `k` that has the **maximum average value**, and return this value.
Any answer with a calculation error less than `10⁻⁵` will be accepted.

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

## Class Definition

### `MovingAverage(int size)`
- Initializes the object with a window size.
- The window holds **at most `size` recent values** from the stream.

### `next(int val)`
- Adds a new integer `val` to the stream.
- Returns the average of the **most recent values** in the window.
- If the total number of values seen so far is less than the window size, return the average of **all values so far**.

## Example

```text
MovingAverage m = new MovingAverage(3);
m.next(1)  -> 1
m.next(10) -> (1 + 10) / 2
m.next(3)  -> (1 + 10 + 3) / 3
m.next(5)  -> (10 + 3 + 5) / 3
```

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

## Constraints

0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.

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

## Constraints

m == s.length
n == t.length
1 <= m, n <= 105
s and t consist of uppercase and lowercase English letters.

## Follow up: 
Could you find an algorithm that runs in O(m + n) time?

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

# Sliding Window Maximum — LeetCode 239 (Hard)

## Problem Description
You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

## Examples

### Example 1
**Input**
nums = [1,3,-1,-3,5,3,6,7], k = 3

**Output** 
[3,3,5,5,6,7]

**Explanation**

| Window Position (size = 3) | Max |
|----------------------------|-----|
| `[1,  3, -1]` -3  5  3  6  7 | 3 |
| 1 `[3, -1, -3]` 5  3  6  7 | 3 |
| 1  3 `[-1, -3, 5]` 3  6  7 | 5 |
| 1  3  -1 `[-3, 5, 3]` 6  7 | 5 |
| 1  3  -1  -3 `[5, 3, 6]` 7 | 6 |
| 1  3  -1  -3  5 `[3, 6, 7]` | 7 |


### Example 2
**Input**
nums = [1], k = 1
**Output** 
 [1]
 

## Constraints

1 <= nums.length <= 105
-104 <= nums[i] <= 104
1 <= k <= nums.length

## Solution

```text
import math
from collections import deque

def sliding_max(a,k):
    q=deque()
    res=[]
    def push(n):
        while q and q[-1]<n:
            q.pop()
        q.append(n)
    for i in range(k):
        push(a[i])
    res.append(q[0])
    for i in range(k,len(a)):
        if q[0]==a[i-k]:
            q.popleft()
        push(a[i])
        res.append(q[0])
    return res

print(sliding_max([1,3,-1,-3,5,3,6,7],3))
print(sliding_max([1],1))

```
## Complexity Analysis

Space: O(k)
Time:o(n)
---

# Fruit Into Baskets — LeetCode 904 (Medium)

## Problem Description
You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

## Examples

### Example 1
**Input**
fruits = [1,2,1]

**Output** 
3

**Explanation**
We can pick from all 3 trees.


### Example 2
**Input**
fruits = [0,1,2,2]
**Output** 
 3

**Explanation**
 We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].
 

## Constraints

1 <= fruits.length <= 105
0 <= fruits[i] < fruits.length

## Solution

```text
def getfruits(a,n):
    d={}
    cnt=0
    max_cnt=0
    win_start=0
    for win_end in range(len(a)):
        rchr=a[win_end]
        if rchr not in d:
            d[rchr]=1
        else:
            d[rchr]+=1
        while len(d)>n:
            lchr=a[win_start]
            d[lchr]-=1
            if d[lchr]==0:
                del d[lchr]
            win_start+=1
        max_cnt=max(max_cnt,win_end-win_start+1)
    return max_cnt

print(getfruits([1,2,1],2))
print(getfruits([0,1,2,1],2))


```
## Complexity Analysis
Space - O(1)
Time: O(n)
---

# Minimum Operations to Reduce X to Zero — LeetCode 1658 (Medium)

## Problem Description
You are given an integer array nums and an integer x. In one operation, you can either remove the leftmost or the rightmost element from the array nums and subtract its value from x. Note that this modifies the array for future operations.

Return the minimum number of operations to reduce x to exactly 0 if it is possible, otherwise, return -1.

## Examples

### Example 1
**Input**
nums = [1,1,4,2,3], x = 5   

**Output** 
2

**Explanation**
The optimal solution is to remove the last two elements to reduce x to zero.


### Example 2
**Input**
nums = [5,6,7,8,9], x = 4
**Output** 
 -1

### Example 3
**Input**
nums = [3,2,20,1,1,3], x = 10
**Output** 
 5

**Explanation**
The optimal solution is to remove the last three elements and the first two elements (5 operations in total) to reduce x to zero.
 

## Constraints

1 <= nums.length <= 105
1 <= nums[i] <= 104
1 <= x <= 109

## Solution

## Complexity Analysis

---

# Maximum Beauty of an Array After Applying Operation — LeetCode 2779 (Medium)

## Problem Description
You are given a 0-indexed array nums and a non-negative integer k.

In one operation, you can do the following:

Choose an index i that hasn't been chosen before from the range [0, nums.length - 1].
Replace nums[i] with any integer from the range [nums[i] - k, nums[i] + k].
The beauty of the array is the length of the longest subsequence consisting of equal elements.

Return the maximum possible beauty of the array nums after applying the operation any number of times.

Note that you can apply the operation to each index only once.

A subsequence of an array is a new array generated from the original array by deleting some elements (possibly none) without changing the order of the remaining elements.

## Examples

### Example 1
**Input**
nums = [4,6,1,2], k = 2

**Output** 
3

**Explanation**
In this example, we apply the following operations:
- Choose index 1, replace it with 4 (from range [4,8]), nums = [4,4,1,2].
- Choose index 3, replace it with 4 (from range [0,4]), nums = [4,4,1,4].
After the applied operations, the beauty of the array nums is 3 (subsequence consisting of indices 0, 1, and 3).
It can be proven that 3 is the maximum possible length we can achieve.


### Example 2
**Input**
nums = [1,1,1,1], k = 10
**Output** 
 4

**Explanation**
In this example we don't have to apply any operations.
The beauty of the array nums is 4 (whole array).
 

## Constraints

1 <= nums.length <= 105
0 <= nums[i], k <= 105

## Solution

## Complexity Analysis

---


# Frequency of the Most Frequent Element — LeetCode 1838 (Medium)

## Problem Description
The frequency of an element is the number of times it occurs in an array.

You are given an integer array nums and an integer k. In one operation, you can choose an index of nums and increment the element at that index by 1.

Return the maximum possible frequency of an element after performing at most k operations.

## Examples 

### Example 1:

Input: nums = [1,2,4], k = 5
Output: 3
Explanation: Increment the first element three times and the second element two times to make nums = [4,4,4].
4 has a frequency of 3.

### Example 2:

Input: nums = [1,4,8,13], k = 5
Output: 2
Explanation: There are multiple optimal solutions:
- Increment the first element three times to make nums = [4,4,8,13]. 4 has a frequency of 2.
- Increment the second element four times to make nums = [1,8,8,13]. 8 has a frequency of 2.
- Increment the third element five times to make nums = [1,4,13,13]. 13 has a frequency of 2.

### Example 3:

Input: nums = [3,9,6], k = 2
Output: 1
 
## Constraints:

1 <= nums.length <= 105
1 <= nums[i] <= 105
1 <= k <= 105

## Sol:

## Complexity Analysis:

---

# Find Longest Special Substring That Occurs Thrice I — LeetCode 2981 (Medium)

## Problem Description
You are given a string s that consists of lowercase English letters.

A string is called special if it is made up of only a single character. For example, the string "abc" is not special, whereas the strings "ddd", "zz", and "f" are special.

Return the length of the longest special substring of s which occurs at least thrice, or -1 if no special substring occurs at least thrice.

A substring is a contiguous non-empty sequence of characters within a string.


## Examples 

### Example 1:

Input: s = "aaaa"
Output: 2
Explanation: The longest special substring which occurs thrice is "aa": substrings "aaaa", "aaaa", and "aaaa".
It can be shown that the maximum length achievable is 2.

### Example 2:

Input: s = "abcdef"
Output: -1
Explanation: There exists no special substring which occurs at least thrice. Hence return -1.

### Example 3:

Input: s = "abcaba"
Output: 1
Explanation: The longest special substring which occurs thrice is "a": substrings "abcaba", "abcaba", and "abcaba".
It can be shown that the maximum length achievable is 1.

## Constraints:

3 <= s.length <= 50
s consists of only lowercase English letters.

## Sol:

## Complexity Analysis:

---

# Maximum Frequency of an Element After Performing Operations I — LeetCode 3346 (Medium)

## Problem Description
You are given an integer array nums and two integers k and numOperations.

You must perform an operation numOperations times on nums, where in each operation you:

Select an index i that was not selected in any previous operations.
Add an integer in the range [-k, k] to nums[i].
Return the maximum possible frequency of any element in nums after performing the operations.

## Examples 

### Example 1:

Example 1:

Input: nums = [1,4,5], k = 1, numOperations = 2
Output: 2

Explanation:

We can achieve a maximum frequency of two by:
Adding 0 to nums[1]. nums becomes [1, 4, 5].
Adding -1 to nums[2]. nums becomes [1, 4, 4].

### Example 2:

Input: nums = [5,11,20,20], k = 5, numOperations = 1
Output: 2

Explanation:
We can achieve a maximum frequency of two by:
Adding 0 to nums[1].

## Constraints:

1 <= nums.length <= 105
1 <= nums[i] <= 105
0 <= k <= 105
0 <= numOperations <= nums.length

## Sol:

## Complexity Analysis:

---

# Maximum Frequency of an Element After Performing Operations II — LeetCode 3347 (Hard)

## Problem Description
You are given an integer array nums and two integers k and numOperations.

You must perform an operation numOperations times on nums, where in each operation you:

Select an index i that was not selected in any previous operations.
Add an integer in the range [-k, k] to nums[i].
Return the maximum possible frequency of any element in nums after performing the operations.

## Examples 

### Example 1:
**Input**
nums = [1,4,5], k = 1, numOperations = 2
**Output**
2

**Explanation**
We can achieve a maximum frequency of two by:

- Adding 0 to nums[1], after which nums becomes [1, 4, 5].
- Adding -1 to nums[2], after which nums becomes [1, 4, 4].


### Example 2:
**Input**
nums = [5,11,20,20], k = 5, numOperations = 1
**Output**
2

**Explanation**
We can achieve a maximum frequency of two by:

- Adding 0 to nums[1].
## Constraints:
- 1 <= nums.length <= 10^5
- 1 <= nums[i] <= 10^9
- 0 <= k <= 10^9
- 0 <= numOperations <= nums.length

## Sol:

## Complexity Analysis:


---


#  Minimum Size Subarray Sum — LeetCode 209 (Medium)

## Problem Description
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.


## Examples 

### Example 1:
**Input**
target = 7, nums = [2,3,1,2,4,3]

**Output**
2

**Explanation**
The subarray [4,3] has the minimal length under the problem constraint

### Example 2:
**Input**
target = 4, nums = [1,4,4]

**Output**
1

### Example 3:
**Input**
target = 11, nums = [1,1,1,1,1,1,1,1]

**Output**
0

 ## Constraints
- 1 <= target <= 10^9
- 1 <= nums.length <= 10^5
- 1 <= nums[i] <= 10^4


## Sol:

## Complexity Analysis:

---

# Longest Repeating Character Replacement — LeetCode 424 (Medium)

## Problem Description
You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.


## Examples 

### Example 1:
**Input**
s = "ABAB", k = 2

**Output**
4

**Explanation**
Replace the two 'A's with two 'B's or vice versa.

### Example 2:
**Input**
s = "AABABBA", k = 1

**Output**
4

**Explanation**
Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achieve this answer too.

 

## Constraints:
- 1 <= s.length <= 10^5
- s consists of only uppercase English letters.
- 0 <= k <= s.length
- 
## Sol:

## Complexity Analysis:

---

# Subarray Product Less Than K — LeetCode 713 (Medium)

## Problem Description
Given an array of integers nums and an integer k, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than k.

## Examples 

### Example 1:

Example 1:

**Input**
nums = [10,5,2,6], k = 100

**Output**
8

**Explanation**
The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.


### Example 2:

**Input**
nums = [1,2,3], k = 0

**Output**
0

## Constraints:
- 1 <= nums.length <= 3 * 10^4
- 1 <= nums[i] <= 1000
- 0 <= k <= 10^6

## Sol:

## Complexity Analysis:

---

# Continuous Subarrays — LeetCode 2762 (Medium)

## Problem Description
You are given a 0-indexed integer array nums. A subarray of nums is called continuous if:

Let i, i + 1, ..., j be the indices in the subarray. Then, for each pair of indices i <= i1, i2 <= j, 0 <= |nums[i1] - nums[i2]| <= 2.
Return the total number of continuous subarrays.

A subarray is a contiguous non-empty sequence of elements within an array.

## Examples 

### Example 1:
**Input**
nums = [5,4,2,4]

**Output**
8

**Explanation**
Continuous subarray of size 1: [5], [4], [2], [4].  
Continuous subarray of size 2: [5,4], [4,2], [2,4].  
Continuous subarray of size 3: [4,2,4].  

There are no subarrays of size 4.

Total continuous subarrays = 4 + 3 + 1 = 8.

It can be shown that there are no more continuous subarrays.

### Example 2:
**Input**
nums = [1,2,3]

**Output**
6

**Explanation**
Continuous subarray of size 1: [1], [2], [3].  
Continuous subarray of size 2: [1,2], [2,3].  
Continuous subarray of size 3: [1,2,3].  

Total continuous subarrays = 3 + 2 + 1 = 6.
 

## Constraints:
- 1 <= nums.length <= 10^5
- 1 <= nums[i] <= 10^9


## Sol:

## Complexity Analysis:


---
