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


---
