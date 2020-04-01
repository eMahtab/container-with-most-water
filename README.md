# Container with most water
## https://leetcode.com/problems/container-with-most-water

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

![Area with most water](example.jpg?raw=true "Title")

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

**This a beautiful question showing, how to use the two pointer approach for better runtime**

### Implementation 1 : O(n^2)

```java
class Solution {
    public int maxArea(int[] height) {
        if(height == null || height.length == 0)
            return 0;
        int mostWater = Integer.MIN_VALUE;
        for(int i = 0; i < height.length - 1; i++) {
            for(int j = i + 1; j < height.length; j++) {
                mostWater = Math.max(mostWater, Math.min(height[i], height[j]) * (j-i));
            }
        }
        return mostWater;
    }
}
```
Above implementation have runtime complexity of O(n^2) and space complexity of O(1)

```
Runtime Complexity = O(n^2)
Space Complexity   = O(1)
```

### Implementation 2 : O(n)

```java
class Solution {
    public int maxArea(int[] height) {
        if(height == null || height.length == 0)
            return 0;
        int left = 0;
        int right = height.length - 1;
        int mostWater = Integer.MIN_VALUE;
        while(left < right) {
            int distance = right - left;
            int waterStored = Math.min(height[left], height[right]) * distance;
            mostWater = Math.max(mostWater, waterStored);
            if(height[left] <= height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return mostWater;
    }
}
```

Above implementation have runtime complexity of O(n) and space complexity of O(1)

```
Runtime Complexity = O(n)
Space Complexity   = O(1)
```
