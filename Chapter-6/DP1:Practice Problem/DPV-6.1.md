6.1. A contiguous subsequence of a list S is a subsequence made up of consecutive elements of S. For instance, if S is
5, 15, −30, 10, −5, 40, 10,
then 15, −30, 10 is a contiguous subsequence but 5, 15, 40 is not. Give a linear-time algorithm for
the following task:
Input: A list of numbers, a1, a2, . . . , an.
Output: The contiguous subsequence of maximum sum (a subsequence of length zero has sum zero).
For the preceding example, the answer would be 10, −5, 40, 10, with a sum of 55.
(Hint: For each j∈{1,2,...,n},
consider contiguous subsequences ending exactly at position j.)

### Pseudocode (Kadan's Algorithm)

    maxSum=-infinity (a very small number)
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
```
def solution(a):
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