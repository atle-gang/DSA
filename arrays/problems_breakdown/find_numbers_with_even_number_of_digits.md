# Find Numbers with Even Number of Digits

Given an array `nums` of integers, return how many of them contain an **even number** of digits.

Example 1:
```bash
Input: nums = [12,345,2,6,7896]
Output: 2
Explanation: 
12 contains 2 digits (even number of digits). 
345 contains 3 digits (odd number of digits). 
2 contains 1 digit (odd number of digits). 
6 contains 1 digit (odd number of digits). 
7896 contains 4 digits (even number of digits). 
Therefore only 12 and 7896 contain an even number of digits.
```

Example 2:
```bash 
Input: nums = [555,901,482,1771]
Output: 1 
Explanation: 
Only 1771 contains an even number of digits.
```

** Constraints**
* 1 <= nums.length <= 500
* 1 <= nums[i] <= 105

## Breakdown

## Breakdown

* `public int findNumbers(int[] nums)` represents the beginning of a function called `findNumbers` that takes an array of integers as input.

* Declare and initialise `count` to 0 to track the number of integers with an even number of digits.

* Loop over the array `nums`:
    * For each element `num` in `nums`:
        * Declare a variable `digitCount` and update it by calling the helper method `countDigits` with `num` as input.
        * If `digitCount` is divisible by 2:
            * Increment `count`.

* Create a helper method named `countDigits` that takes an integer `num` as input and returns the count of its digits:
    * Declare and initialise `count` to 0.
    * Use a while loop to iterate over `num` until it becomes 0:
        * Divide `num` by 10 to remove the last digit.
        * Increment `count`.
    * Return `count`.

* After the loop, return `count` as the result.

