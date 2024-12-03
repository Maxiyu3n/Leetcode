[leetcode: spiral matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/)

Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

Key Variables:

* startx, starty: Coordinates of the starting point of the current spiral layer.
* offset: Represents the shrinking size of the spiral layer as we move inward.
* layer: Number of spiral layers to process, computed as n // 2.
* mid: The middle point of the matrix (used if n is odd).
* nums: The resulting n x n matrix, initialized with zeros.
* count: Keeps track of the current number to be placed in the matrix.

Outer Loop for Layers:(make sure points are correct)

* For each spiral layer:
  * Traverse the top row of the layer from left to right.
  * Traverse the right column from top to bottom.
  * Traverse the bottom row from right to left.
  * Traverse the left column from bottom to top.
  * Shrinking the Spiral:
  * After completing a layer, increment startx and starty to move inward, and increase offset to adjust for the reduced size of the matrix.

Middle Element:
* If n is odd, place the last number (n^2) in the center of the matrix.


Messed up several times here. Make sure boundary condition and move startx, starty correctly.
```commandline
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        startx, starty = 0, 0
        offset = 1
        layer = n//2
        mid = n// 2
        nums = [[0] * n for _ in range(n)]
        count = 1
        for i in range(layer):
            for j in range(starty, n-offset):
                nums[startx][j] = count
                count = count + 1
            for j in range(startx, n-offset):
                nums[j][n-offset] = count
                count = count + 1
            for j in range(n-offset, starty, -1):
                nums[n-offset][j] = count
                count = count + 1
            for j in range(n-offset, startx, -1):
                nums[j][startx] = count
                count = count +1
            startx = startx + 1
            starty = starty + 1
            offset = offset + 1
        
        if n%2 != 0:
            nums[mid][mid] = count
        return nums
                

```
Complexity Analysis
* Time Complexity: O(n^2). Here, n is given input and we are iterating over n⋅n matrix in spiral form.
* Space Complexity: O(1) We use constant extra space for storing cnt.

