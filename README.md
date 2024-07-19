# Math_Basic
### 7. Reverse Integer
[Leetcode link](https://leetcode.com/problems/reverse-integer/description/)
<br>
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.
Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

Example 1:
Input: x = 123
Output: 321

Example 2:
Input: x = -123
Output: -321

Example 3:
Input: x = 120
Output: 21
#### Code
```java
class Solution {
    public int reverse(int x) {
        int temp=x;
        x=(x<0)?-x:x;
        long h=0;
        while(x>0)
        {
            h=(h*10)+(x%10);
            x=x/10;
        }
        if(h>Integer.MAX_VALUE || h<Integer.MIN_VALUE)
        {
            return 0;
        }
        int k=(int)h;
        return temp<0?-k:k;
    }
}
```
- I use long if i reverse the number then it will exceed the integer byte value so i declare as long and convert to integer then return.
### 9. Palindrome Number
[Leetcode link](https://leetcode.com/problems/palindrome-number/description/)
<br>
Given an integer x, return true if x is a palindrome,and false otherwise.

Example 1:
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.

Example 2:
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Example 3:
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

```java
class Solution {
    public boolean isPalindrome(int x) {
        int h=0,temp=x;
        while(temp>0)
        {
            h=(h*10)+temp%10;
            temp=temp/10;
        }
        if(h==x) return true;
        else return false;

    }
}
```
