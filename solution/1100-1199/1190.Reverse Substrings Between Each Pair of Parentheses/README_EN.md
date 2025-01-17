# [1190. Reverse Substrings Between Each Pair of Parentheses](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses)

[中文文档](/solution/1100-1199/1190.Reverse%20Substrings%20Between%20Each%20Pair%20of%20Parentheses/README.md)

## Description

<p>You are given a string <code>s</code> that consists of lower case English letters and brackets.&nbsp;</p>

<p>Reverse the strings&nbsp;in each&nbsp;pair of matching parentheses, starting&nbsp;from the innermost one.</p>

<p>Your result should <strong>not</strong> contain any brackets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(abcd)&quot;
<strong>Output:</strong> &quot;dcba&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(u(love)i)&quot;
<strong>Output:</strong> &quot;iloveu&quot;
<strong>Explanation:</strong>&nbsp;The substring &quot;love&quot; is reversed first, then the whole string is reversed.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(ed(et(oc))el)&quot;
<strong>Output:</strong> &quot;leetcode&quot;
<strong>Explanation:</strong>&nbsp;First, we reverse the substring &quot;oc&quot;, then &quot;etco&quot;, and finally, the whole string.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a(bcdefghijkl(mno)p)q&quot;
<strong>Output:</strong> &quot;apmnolkjihgfedcbq&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> only contains lower case English characters and parentheses.</li>
	<li>It&#39;s guaranteed that all parentheses are balanced.</li>
</ul>


## Solutions

Use deque or stack to simulate the reversal process.

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def reverseParentheses(self, s: str) -> str:
        stack = []
        for c in s:
            if c == ")":
                tmp = []
                while stack[-1] != "(":
                    tmp += stack.pop()
                stack.pop()
                stack += tmp
            else:
                stack.append(c)
        return "".join(stack)
```

### **Java**

```java
class Solution {
    public String reverseParentheses(String s) {
        Deque<Character> deque = new ArrayDeque<>();
        for (char c : s.toCharArray()) {
            if (c == ')') {
                StringBuilder sb = new StringBuilder();
                while (deque.peekLast() != '(') {
                    sb.append(deque.pollLast());
                }
                deque.pollLast();
                for (int i = 0, n = sb.length(); i < n; i++) {
                    deque.offerLast(sb.charAt(i));
                }
            } else {
                deque.offerLast(c);
            }
        }
        StringBuilder sb = new StringBuilder();
        while (!deque.isEmpty()) {
            sb.append(deque.pollFirst());
        }
        return sb.toString();
    }
}
```

### **...**

```

```

<!-- tabs:end -->
