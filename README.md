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
### 29. Divide Two Integers
[Leetcode link](https://leetcode.com/problems/divide-two-integers/description/?envType=problem-list-v2&envId=math&status=TO_DO&difficulty=MEDIUM)
<br>
Given two integers dividend and divisor, divide two integers without using multiplication, division, and mod operator.
The integer division should truncate toward zero, which means losing its fractional part. For example, 8.345 would be truncated to 8, and -2.7335 would be truncated to -2.
Return the quotient after dividing dividend by divisor.
Note: Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [−231, 231 − 1]. For this problem, if the quotient is strictly greater than 231 - 1, then return 231 - 1, and if the quotient is strictly less than -231, then return -231.

Example 1:
Input: dividend = 10, divisor = 3
Output: 3
Explanation: 10/3 = 3.33333.. which is truncated to 3.

Example 2:
Input: dividend = 7, divisor = -3
Output: -2
Explanation: 7/-3 = -2.33333.. which is truncated to -2.
 
Constraints:
-231 <= dividend, divisor <= 231 - 1
divisor != 0

```java
class Solution 
{
    public int divide(int dividend, int divisor) 
    {
        long t =  ((long)dividend/(long)divisor);
        if(-t==Integer.MIN_VALUE) return Integer.MAX_VALUE;
        else return (int)t;
    }
}
```
- In this program only edge case is to whenver we divide the -2,147,483,648(Integer.MIN_VALUE) by -1 then it will give 2,147,483,648 but in the positive side it did not have the value we already know the integer range 	-2,147,483,648 to 2,147,483,647.
- So we check that edge case only in that time we manually return the Integer.MAX_VALUE.
- Otherwise we simply return the dividend/divisor(int).
### 2601. Prime Subtraction Operation
[Leetcode link](https://leetcode.com/problems/prime-subtraction-operation/?envType=daily-question&envId=2024-11-11)
<br>
You are given a 0-indexed integer array nums of length n.
You can perform the following operation as many times as you want:
Pick an index i that you haven’t picked before, and pick a prime p strictly less than nums[i], then subtract p from nums[i].
Return true if you can make nums a strictly increasing array using the above operation and false otherwise.
A strictly increasing array is an array whose each element is strictly greater than its preceding element.

Exmple 1:

Input: nums = [4,9,6,10]
Output: true
Explanation: In the first operation: Pick i = 0 and p = 3, and then subtract 3 from nums[0], so that nums becomes [1,9,6,10].
In the second operation: i = 1, p = 7, subtract 7 from nums[1], so nums becomes equal to [1,2,6,10].
After the second operation, nums is sorted in strictly increasing order, so the answer is true.

Example 2:
Input: nums = [6,8,11,12]
Output: true
Explanation: Initially nums is sorted in strictly increasing order, so we don't need to make any operations.

Example 3:
Input: nums = [5,8,3]
Output: false
Explanation: It can be proven that there is no way to perform operations to make nums sorted in strictly increasing order, so the answer is false.

Constraints:
1 <= nums.length <= 1000
1 <= nums[i] <= 1000
nums.length == n
```java
class Solution {
    public boolean primeSubOperation(int[] nums) {
        int[] copy = nums.clone();
        Arrays.sort(copy);
        int max = copy[copy.length-1];
        boolean[] prime = new boolean[max+1];
        Arrays.fill(prime,true);
        for(int i=2;i<Math.sqrt(prime.length);i++)
        {
            int index = 2;
            while(index*i<prime.length) 
            {
                prime[index*i] = false;
                index++;
            }
        }
        List<Integer> ans = new ArrayList<>();
        for(int i=2;i<prime.length;i++) 
        {
            if(prime[i]) ans.add(i);
        }
        Collections.reverse(ans);
        int prev = 0;
        for(int i=0;i<nums.length;i++)
        {
            int j=0;
            while((j<ans.size()) && ((nums[i]-ans.get(j))<0 || (nums[i]-ans.get(j))<=prev))
            {
                j++;
            }
            if(j<ans.size()) nums[i] = nums[i]-ans.get(j);
            prev = nums[i];
        }
        for(int i=0;i<nums.length-1;i++)
        {
            if(nums[i]>=nums[i+1]) return false;
        }
        return true;
    }
}
```
- In this code we initially getting the all prime numbers below the max element.
- To find the max element first we clone the array and sort the array and get the final element so that is the large element in the array.
- So declare a size of the array with max+1 and initialize to true.
- Then from the 2 the multiple of 2 is not the prime number so change to false same for the 3 the multiple of the three did not the prime number so change to true.
- This will ontinue till the half of the array.
- then true elements index are prime number so added to the list.
- for each element in the nums we must reduce to the small element then only we get the increasing sequence.
- so we move the j untill the subraction value greater than the prev value and greater than 0.
- so finally we check every ith element will less than the i+1 th element.
> [Reference](https://www.youtube.com/watch?v=Kq-UzuTd7Dg)
