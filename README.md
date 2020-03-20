# Container with most water


### Implementation 1 : O(n^2)

```java
public int maxArea(int[] height) {
    int maxArea = Integer.MIN_VALUE;
		for (int i = 0; i < height.length - 1; i++) {
			for (int j = i + 1; j < height.length; j++) {
				int area = Math.min(height[i], height[j]) * (j - i);
				maxArea = Math.max(maxArea, area);
			}
		}
    
	 return maxArea;
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
