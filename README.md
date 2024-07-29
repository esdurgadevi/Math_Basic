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
### 2485. Find the Pivot Integer
[Leetcode link](https://leetcode.com/problems/find-the-pivot-integer/description/)
<br>
Given a positive integer n, find the pivot integer x such that:
The sum of all elements between 1 and x inclusively equals the sum of all elements between x and n inclusively.
Return the pivot integer x. If no such integer exists, return -1. It is guaranteed that there will be at most one pivot index for the given input.
 
Example 1:
Input: n = 8
Output: 6
Explanation: 6 is the pivot integer since: 1 + 2 + 3 + 4 + 5 + 6 = 6 + 7 + 8 = 21

Example 2:
Input: n = 1
Output: 1
Explanation: 1 is the pivot integer since: 1 = 1.

Example 3:
Input: n = 4
Output: -1
Explanation: It can be proved that no such integer exist.

```java
class Solution {
    public int pivotInteger(int n) {
       int sum = (n+1) * n/2;
       int pivot = (int)Math.sqrt(sum);
       return  pivot * pivot == sum ? pivot : -1;
    }
}
```
!<img width="427" alt="image" src="https://github.com/user-attachments/assets/20674d89-52fd-4f32-b7c3-66041607c6da">
- if 1 to x sum is equal to x to num sum then return x.
- So what i do is find the total sum for num
- then in for loop each i value i find the sum
- check if the i th sum is equal to total-i th sum + i
- If equal then return i
- else return -1.
