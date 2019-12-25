# Container with most water


### Implementation

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

```java
public int maxArea(int[] height) {
		int maxArea = Integer.MIN_VALUE;
		int left_pointer = 0;
		int right_pointer = height.length - 1;
		while (left_pointer < right_pointer) {
			int area = Math.min(height[left_pointer], height[right_pointer]) * 
			                   (right_pointer - left_pointer);
			maxArea = Math.max(maxArea, area);

			if (height[left_pointer] < height[right_pointer]) {
				left_pointer++;
			} else {
				right_pointer--;
			}
		}
	 
   return maxArea;
}
```

Above implementation have runtime complexity of O(n) and space complexity of O(1)

```
Runtime Complexity = O(n)
Space Complexity   = O(1)
```
