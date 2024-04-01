# Max Consecutive Ones

Given a binary array `nums`, return the maximum number of consecutive `1`'s in the array.

Example 1:
```bash
Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
```

Example 2:
```bash
Input: nums = [1,0,1,1,0,1]
Output: 2
```

**Constraints**:

* 1 <= nums.length <= 105
* nums[i] is either 0 or 1.


## Breakdown

* `public int findMaxConsecutiveOnes` represents the beginning of a function called  `findMaxConsecutivesOnes` that takes an array  of integers as input.

* Declare and initialise `maxCount` to 0 to track the maximum consecutive ones found and `currentCount` to 0 to track the current consecutive ones count.

* Loop over the array `nums`:
    * For each element `num` in `nums`:
        * If `num` is equal to 1, increment `currentCount`.
        * Else, update `maxCount` to the maximum value between `maxCount` and `currentCount`, and reset `currentCount` to 0.

* After the loop, update `maxCount` to the maximum value between `maxCount` and `currentCount`.

* Return `maxCount` as the result.

