# Container with most water

## https://leetcode.com/problems/container-with-most-water

![Area with most water](example.jpg?raw=true "Title")

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
