[leetcode Remove Element](https://leetcode.com/problems/remove-element/)

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

Key Points：
* Arrays store data in contiguous memory locations, an individual element of an array cannot be deleted; it can only be overwritten.
* Use a two-pointer technique (slow and fast) to traverse the array.
  * fast pointer scans every element in the array.
  * slow pointer marks the position where the next valid (non-val) element should be placed.


```
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:

        slow, fast = 0, 0
        size = len(nums) - 1
        while fast <= size:
            if nums[fast]!= val:
                nums[slow] = nums[fast]
                slow += 1
            fast += 1
        return slow

```
Time Complexity: O(n): The array is traversed once.

Space Complexity: O(1): No additional space is used beyond variables.