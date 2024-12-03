[leetcode:minimum-size-subarray-sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

Given an array of positive integers nums and a positive integer target, return the minimal length of a 
subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Key Point:
* sliding window:
  * Use two pointers (left and right) to represent a sliding window in the array.
  * Expand the window by moving the right pointer to include more elements and increase the sum.
  * Shrink the window from the left by moving the left pointer to minimize the subarray length while keeping the sum greater than or equal to the target.

Steps:
* Initialize:
* left and right pointers at the start of the array.
* res to store the current window sum.
* min_length to store the smallest subarray length, initialized to infinity (float('inf')).

Expand the window:
* Add the value at nums[right] to res.
* Increment right to expand the window.
Shrink the window:
* While the sum res is greater than or equal to target:
* Calculate the current subarray length as right - left + 1.
* Update min_length with the smaller value between min_length and the current length.
* Subtract nums[left] from res and increment left to shrink the window.

```commandline
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        left = 0
        right = 0
        size = len(nums) - 1
        res = 0 
        min_length = float('inf')

        while right <= size:
            res = res + nums[right]
            while res >= target:
                min_length = min(min_length, right - left +1)
                res = res - nums[left]
                left = left + 1
            right = right + 1
        return min_length if min_length != float('inf') else 0

```
Time complexity: O(n). Space complexity: O(1).