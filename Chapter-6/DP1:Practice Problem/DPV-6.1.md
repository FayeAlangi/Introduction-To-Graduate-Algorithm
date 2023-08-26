### Algorithms By: S. Dasgupta, C. H. Papadimitriou, and U. V. Vazirani July 18, 2006, Page 191
#### Problem 6.1
A contiguous subsequence of a list S is a subsequence made up of consecutive elements of S. For instance, if S is
5, 15, −30, 10, −5, 40, 10,
then 15, −30, 10 is a contiguous subsequence but 5, 15, 40 is not. Give a linear-time algorithm for
the following task:
Input: A list of numbers, a1, a2, . . . , an.
Output: The contiguous subsequence of maximum sum (a subsequence of length zero has sum zero).
For the preceding example, the answer would be 10, −5, 40, 10, with a sum of 55.
(Hint: For each j∈{1,2,...,n},
consider contiguous subsequences ending exactly at position j.)

If we use Brute-Force solution, we need to find all the possible 
sub arrays, and find the one with the maximum sum. The time complexity of this solution is
O(n^2).
### Python Implementation (Brute-Force Algorithm)
```agsl
def bf_solution(a):
    sum_arr=[]
    sub_arr=[]
    for i in range(len(a)):
        for j in range(i+1,len(a)+1):
            sub_arr.append(a[i:j])
            sum_arr.append(sum(a[i:j]))
    return sub_arr[sum_arr.index(max(sum_arr))],max(sum_arr)
```
Can we do better? With linear time complexity O(n)?

### Pseudocode (Kadan's Algorithm)

        maxSum = -infinity (a very small number)
        currSum=0
        subArr=[]
        For i in 0-> n:
            currSum=currSum+a[i]
            if currSum > maxSum:
                maxSum=currSum
            subArr add a[i]
            else if currSum < 0:
                currSum=0
                subArr->empty
        return maxSum,subArr

### Python Implementation
```agsl
def dp_solution(a):
    max_sum=-float('inf')
    curr_sum=0
    sub_arr=[]
    for i in range(len(a)):
        curr_sum+=a[i]
        if  max_sum < curr_sum:
            max_sum=curr_sum
        sub_arr.append(a[i])
        if curr_sum < 0:
            curr_sum=0
            sub_arr=[]
    return (max_sum,sub_arr)
```



### Leetcode : https://leetcode.com/problems/maximum-subarray/
### Python Implementation (Brute-Force Algorithm) : not accepted -> Time Limit Exceeded
```agsl
def maxSubArray(nums):
    max_sum= -float('inf')
    for i in range(len(nums)):
        for j in range(i+1,len(nums)+1):
            if sum(nums[i:j])>max_sum:
                max_sum=sum(nums[i:j])
    return max_sum
```
### Python Implementation (Dynamic Programming)

```agsl
def maxSubArray(self, nums: List[int]) -> int:
    max_sum=-float('inf')
    curr_sum=0
    for i in range(len(nums)):
        curr_sum+=nums[i]
        if  max_sum < curr_sum:
               max_sum=curr_sum
        if curr_sum < 0:
                curr_sum=0
    return max_sum
```