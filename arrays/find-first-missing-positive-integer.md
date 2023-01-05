# Find first missing positive integer

## Problem statement
Given an unsorted integer array nums, return the smallest missing positive integer.
You must implement an algorithm that runs in O(n) time and uses constant extra space.

## Brute Force approach
The value of smallest missing positive integer in an array of size n can be maximum of n+1. So the answer is going to lie between 1 to n+1.

for numbers from 1 to n+1 , check their presence in the given array this takes O(n^2) complexity.

## Solution with O(n) space complexity
If its ok to use extra space, build a frequency map for all the numbers in the array then for numbers from 1 to n+1 , check the frequency in the map, if its 0 , return this takes O(n) space complexity.

## Solution with O(n) time complexity and O(1) space complexity

Home sending technique.
if there is no missing numbers in the array , it would be like [1,2,3,4,5,6..] which means A[i] = i+1;

Step 1: ignore all the negative integer and numers > n ( our interest is positive       interger)

Step2 : check all the index and their values for the condition A[i] = i+1. if not return i+1

Step3 : if answer is not found in step2 , then return n+1;

```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int arraySize = nums.length;
        for(int i = 0; i < arraySize; i++) {
            while(nums[i] > 0 && nums[i] <= arraySize && nums[i] != nums[nums[i] -1]) {
                swap(nums, i, nums[i]-1);
            }
        }
        
        for(int i = 0; i < arraySize; i++) {
            if(nums[i] != i+1){
                return i+1;
            }
        }

        return arraySize+1;
    }

    public void swap(int[] a, int i, int j) {
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }
}
```