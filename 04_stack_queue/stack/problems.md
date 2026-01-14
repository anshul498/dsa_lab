
#  Valid Parentheses — LeetCode 20 (Easy)

## Problem Description
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

## Examples 

### Example 1:
**Input**
 s = "()"

**Output**
 true

### Example 2:
**Input**
s = "()[]{}"

**Output**
 true

### Example 3:
**Input**
 s = "(]"

**Output**
false
 
## Constraints:

1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
 

## Sol:

## Complexity Analysis:

---

# Longest Valid Parentheses — LeetCode 32 (Hard)

## Problem Description
Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring.

## Examples 

### Example 1:
**Input**
 s = "(()"
**Output**
 2
**Explanation**
 The longest valid parentheses substring is "()".

### Example 2:
**Input**
s = ")()())"
**Output**
 4
**Explanation**
 The longest valid parentheses substring is "()()".

### Example 3:
**Input**
 s = ""
Output: 0
 

## Constraints:

0 <= s.length <= 3 * 104
s[i] is '(', or ')'.

## Sol:

## Complexity Analysis:

---

#  Minimum Add to Make Parentheses Valid — LeetCode 921 (Medium)

## Problem Description
A parentheses string is valid if and only if:

It is the empty string,
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.
You are given a parentheses string s. In one move, you can insert a parenthesis at any position of the string.

For example, if s = "()))", you can insert an opening parenthesis to be "(()))" or a closing parenthesis to be "())))".
Return the minimum number of moves required to make s valid.

## Examples 

### Example 1:

Example 1:

**Input**
 s = "())"
**Output**
 1


### Example 2:

**Input**
 s = "((("
**Output**
 3

## Constraints:
1 <= s.length <= 1000
s[i] is either '(' or ')'.

## Sol:

## Complexity Analysis:

---

# Minimum Remove to Make Valid Parentheses — LeetCode 1249 (Medium)

## Problem Description
Given a string s of '(' , ')' and lowercase English characters.

Your task is to remove the minimum number of parentheses ( '(' or ')', in any positions ) so that the resulting parentheses string is valid and return any valid string.

Formally, a parentheses string is valid if and only if:

It is the empty string, contains only lowercase characters, or
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.

## Examples 

### Example 1:
**Input**
 s = "lee(t(c)o)de)"
**Output**
 "lee(t(c)o)de"
**Explanation**
 "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.

### Example 2:
**Input**
 s = "a)b(c)d"
**Output**
"ab(c)d"

### Example 3:
**Input**
s = "))(("
**Output**
 ""
**Explanation**
 An empty string is also valid.
 
 

## Constraints:
1 <= s.length <= 105
s[i] is either '(' , ')', or lowercase English letter.

## Sol:

## Complexity Analysis:


---

#  Minimum Number of Swaps to Make the String Balanced — LeetCode 1963 (Medium)

## Problem Description
You are given a 0-indexed string s of even length n. The string consists of exactly n / 2 opening brackets '[' and n / 2 closing brackets ']'.

A string is called balanced if and only if:

It is the empty string, or
It can be written as AB, where both A and B are balanced strings, or
It can be written as [C], where C is a balanced string.
You may swap the brackets at any two indices any number of times.

Return the minimum number of swaps to make s balanced.
 

## Examples 

### Example 1:
**Input**
 s = "()"s = "][]["

**Output**
 1

**Explanation** 
You can make the string balanced by swapping index 0 with index 3.
The resulting string is "[[]]".
Example 2:

### Example 2:
**Input**
s = "]]][[["

**Output**
 2

**Explanation** 
 You can do the following to make the string balanced:
- Swap index 0 with index 4. s = "[]][][".
- Swap index 1 with index 5. s = "[[][]]".
The resulting string is "[[][]]".

### Example 3:
**Input**
s = "[]"

**Output**
0

**Explanation** 
The string is already balanced.
 
## Constraints:

n == s.length
2 <= n <= 106
n is even.
s[i] is either '[' or ']'.
The number of opening brackets '[' equals n / 2, and the number of closing brackets ']' equals n / 2.

## Sol:

## Complexity Analysis:

---

# Min Stack — LeetCode 155 (Medium)

## Problem Description
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the MinStack class:

MinStack() initializes the stack object.
void push(int val) pushes the element val onto the stack.
void pop() removes the element on the top of the stack.
int top() gets the top element of the stack.
int getMin() retrieves the minimum element in the stack.
You must implement a solution with O(1) time complexity for each function.

## Examples 

### Example 1:
**Input**
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

**Output**
 [null,null,null,null,-3,null,0,-2]

**Explanation**
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2

## Constraints:

-231 <= val <= 231 - 1
Methods pop, top and getMin operations will always be called on non-empty stacks.
At most 3 * 104 calls will be made to push, pop, top, and getMin.

## Sol:

## Complexity Analysis:

---

#  Maximum Frequency Stack — LeetCode 895 (Hard)

## Problem Description
Design a stack-like data structure to push elements to the stack and pop the most frequent element from the stack.

Implement the FreqStack class:

FreqStack() constructs an empty frequency stack.
void push(int val) pushes an integer val onto the top of the stack.
int pop() removes and returns the most frequent element in the stack.
If there is a tie for the most frequent element, the element closest to the stack's top is removed and returned.

## Examples 

### Example 1:

**Input**
["FreqStack", "push", "push", "push", "push", "push", "push", "pop", "pop", "pop", "pop"]
[[], [5], [7], [5], [7], [4], [5], [], [], [], []]

**Output**
[null, null, null, null, null, null, null, 5, 7, 5, 4]


### Example 2:

**Explanation**
FreqStack freqStack = new FreqStack();
freqStack.push(5); // The stack is [5]
freqStack.push(7); // The stack is [5,7]
freqStack.push(5); // The stack is [5,7,5]
freqStack.push(7); // The stack is [5,7,5,7]
freqStack.push(4); // The stack is [5,7,5,7,4]
freqStack.push(5); // The stack is [5,7,5,7,4,5]
freqStack.pop();   // return 5, as 5 is the most frequent. The stack becomes [5,7,5,7,4].
freqStack.pop();   // return 7, as 5 and 7 is the most frequent, but 7 is closest to the top. The stack becomes [5,7,5,4].
freqStack.pop();   // return 5, as 5 is the most frequent. The stack becomes [5,7,4].
freqStack.pop();   // return 4, as 4, 5 and 7 is the most frequent, but 4 is closest to the top. The stack becomes [5,7].
 

## Constraints:
0 <= val <= 109
At most 2 * 104 calls will be made to push and pop.
It is guaranteed that there will be at least one element in the stack before calling pop.

## Sol:

## Complexity Analysis:

---

# Online Stock Span — LeetCode 901 (Medium)

## Problem Description
Design an algorithm that collects daily price quotes for some stock and returns the span of that stock's price for the current day.

The span of the stock's price in one day is the maximum number of consecutive days (starting from that day and going backward) for which the stock price was less than or equal to the price of that day.

For example, if the prices of the stock in the last four days is [7,2,1,2] and the price of the stock today is 2, then the span of today is 4 because starting from today, the price of the stock was less than or equal 2 for 4 consecutive days.
Also, if the prices of the stock in the last four days is [7,34,1,2] and the price of the stock today is 8, then the span of today is 3 because starting from today, the price of the stock was less than or equal 8 for 3 consecutive days.
Implement the StockSpanner class:

StockSpanner() Initializes the object of the class.
int next(int price) Returns the span of the stock's price given that today's price is price.

## Examples 

### Example 1:
**Input**
["StockSpanner", "next", "next", "next", "next", "next", "next", "next"]
[[], [100], [80], [60], [70], [60], [75], [85]]

**Output**
[null, 1, 1, 1, 2, 1, 4, 6]

**Explanation**
```text
StockSpanner stockSpanner = new StockSpanner();
stockSpanner.next(100); // return 1
stockSpanner.next(80);  // return 1
stockSpanner.next(60);  // return 1
stockSpanner.next(70);  // return 2
stockSpanner.next(60);  // return 1
stockSpanner.next(75);  // return 4, because the last 4 prices (including today's price of 75) were less than or equal to today's price.
stockSpanner.next(85);  // return 6
```
 
## Constraints:
1 <= price <= 105
At most 104 calls will be made to next.

## Sol:

## Complexity Analysis:


---
