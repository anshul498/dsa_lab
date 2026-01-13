
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
