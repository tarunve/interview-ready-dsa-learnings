# Searching Algorithms

There are two types of Search Algorithms : 
- **Linear Search** : Linear Search is defined as a sequential search algorithm that starts at one end and goes 
  through each element of a list until the desired element is found, otherwise the search continues till the end of the data set. Time Complexity - **O(n)**.
- **Binary Search** : Binary Search is defined as a searching algorithm used in a sorted array by repeatedly 
  dividing the search interval in half. The idea of binary search is to use the information that the array is sorted 
  and reduce the time complexity to **O(log(n))**.
  - Binary Search Code Format *[arr : array, element : element to be searched] :* 
  ```shell
  int start = 0;
  int end = arr.size-1;
  while(start<=end) {
    int mid = start + (end-start)/2;
    if(element == arr[mid]) {
      return mid;
    } else if (element < arr[mid]) {
      end = mid-1; 
    } else {
      start = mid+1;
    }
  }
  ```

---

## Linear Search Problems 
### Problem 1 
You are given an array `arr` containing `n` integers. You are also given an integer `num`, and your task is to find whether `num` is present in the array or not.

If `num` is present in the array, return the 0-based index of the first occurrence of `num`. Else, return -1.

**Sample Input:**
```
5 4
6 7 8 4 1
```

**Sample Output:**
```
3
```

**Solution :**
```java
public class Solution {
    public static int linearSearch(int n, int num, int [] arr){
        for(int i=0; i<n; i++){
            if(arr[i] == num){
                return i;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(n) <br/>
Space Complexity : O(1) - No extra space is being used.



---

## Binary Search Problems
### Problem 1 - [Binary Search on Reverse Sorted Array](https://www.geeksforgeeks.org/search-an-element-in-a-reverse-sorted-array/)
Given an array arr[] sorted in decreasing order, and an integer X, the task is to check if X is present in the given array or not. If X is present in the array, print its index ( 0-based indexing). Otherwise, print -1.

**Sample Input:**
```
arr[] = {5, 4, 3, 2, 1}, X = 4
```

**Sample Output:**
```
1
```

**Solution :**
```java
public class Solution {
    public static int search(int [] arr, int X) {
      return binarySearch(arr.length, X, arr);
    }
  
    public static int binarySearchSearch(int n, int num, int [] arr){
        int start = 0, end = n-1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == num) {
                return mid;
            } else if (arr[mid] < num) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 2 - [First & Last Occurrence of an Element](https://www.geeksforgeeks.org/find-first-and-last-positions-of-an-element-in-a-sorted-array/)
Given a sorted array arr[] with possibly duplicate elements, the task is to find indexes of the first and last occurrences of an element x in the given array.

**Sample Input:**
```
arr[] = {1, 3, 5, 5, 5, 5, 67, 123, 125}, x = 5
```

**Sample Output:**
```
2 5
```

**Solution :**
```java
public class Solution {
    
    public static void search(int [] arr, int target) {
      int firstOccurrence = firstOccurrence(arr.length, target, arr);
      int lastOccurrence = lastOccurrence(arr.length, target, arr);
      System.out.println(firstOccurrence + " " + lastOccurrence);
    }
  
    public static int firstOccurrence(int n, int num, int [] arr) {
        int start = 0, end = n-1, res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == num) {
                // We will need to store the current result and search further.
                res = mid;
                // Move the end pointer to the left of the array.
                end = mid-1;
            } else if (num < arr[mid]) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return res;
    }

    public static int lastOccurrence(int n, int num, int [] arr) {
        int start = 0, end = n-1, res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == num) {
                // We will need to store the current result and search further.
                res = mid;
                // Move the end pointer to the right of the array.
                start = mid+1;
            } else if (num < arr[mid]) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return res;
    }
}
```

Time Complexity : log(n) + log(n) => O(2*log(n)) => O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 3 - [Count of an Element in an Sorted Array](https://www.geeksforgeeks.org/count-number-of-occurrences-or-frequency-in-a-sorted-array/)
Given a sorted array arr[] and a number x, write a function that counts the occurrences of x in arr[]. Expected time complexity is O(Logn)

**Sample Input:**
```
arr[] = {1, 1, 2, 2, 2, 2, 3,},   x = 2
```

**Sample Output:**
```
4
```

**Solution :**
```java
public class Solution {
    
    public static int search(int [] arr, int target) {
      return countOfOccurrences(arr.length, target, arr);
    }
  
    public int countOfOccurrences(int n, int num, int [] arr) {
        int firstOccurrence = firstOccurrence(n, num, arr);
        if(firstOccurrence == -1) {
            return 0;
        }
        int lastOccurrence = lastOccurrence(n, num, arr);
        return lastOccurrence-firstOccurrence+1;
    }

    public int firstOccurrence(int n, int num, int [] arr) {
        int start = 0, end = n-1, res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == num) {
                res = mid;
                end = mid-1;
            } else if (num < arr[mid]) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return res;
    }

    public int lastOccurrence(int n, int num, int [] arr) {
        int start = 0, end = n-1, res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == num) {
                res = mid;
                start = mid+1;
            } else if (num < arr[mid]) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return res;
    }
}
```

Time Complexity : log(n) + log(n) => O(2log(n)) => O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 4 - [Number of times a Sorted Array is rotated](https://www.geeksforgeeks.org/find-rotation-count-rotated-sorted-array/)
Given an array arr[] of size N having distinct numbers sorted in increasing order and the array has been right rotated (i.e, the last element will be cyclically shifted to the starting position of the array) k number of times, the task is to find the value of k.

**Sample Input:**
```
arr[] = {15, 18, 2, 3, 6, 12}
```

**Sample Output:**
```
2
```

**Solution :**
```java
public class Solution {
    
    public static int search(int [] arr) {
      return binarySearch(arr.length, arr);
    }
    
    public static int binarySearch(int n, int [] arr) {
        int start = 0, end = n-1;
        while (start <= end){
            int mid = start + (end-start)/2;
            // Get previous & next element index from mid.
            int prev = (mid+n-1)%n, next = (mid+1)%n;
            // If mid is answer, it should be less than previous & next element.
            if (arr[mid] <= arr[prev] && arr[mid] <= arr[next]) {
                return mid;
            } else if(arr[mid] <= arr[end]) {
                end = mid-1;
            } else if (arr[start] <= arr[mid]) {
                start = mid + 1;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 5 - [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)
There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.

**Sample Input:**
```
nums = [4,5,6,7,0,1,2], target = 0
nums = [4,5,6,7,0,1,2], target = 3
nums = [1], target = 0
```

**Sample Output:**
```
4
-1
-1
```

**Solution :**
- We learned to retrieve the index to which array is rotated. We can use that and build solution further.
- We will get 2 sorted array from the above step and we can make 2 binary search calls to check if the array is 
  present in left or right sorted array. 
```java
public class Solution {

    public int search(int[] nums, int target) {
        int n = nums.length;
        // Get index where the array is rotated.
        int rotationIndex = getRotationIndex(n, nums);
        // search in the left sorted array.
        int searchLeft = binarySearch(nums, 0, rotationIndex-1, target);
        if(searchLeft != -1) {
            return searchLeft;
        }
        // search in right sorted array.
        return binarySearch(nums, rotationIndex, n-1, target);
    }

    public int binarySearch(int [] arr, int start, int end, int target) {
        while (start <= end){
            int mid = start + (end-start)/2;
            if (arr[mid] == target) {
                return mid;
            } else if(arr[mid] < target) {
                start = mid + 1;
            } else {
                end = mid-1;
            }
        }
        return -1;
    }

    public int getRotationIndex(int n, int [] arr) {
        int start = 0, end = n-1;
        while (start <= end){
            int mid = start + (end-start)/2;
            // Get previous & next element index from mid.
            int prev = (mid+n-1)%n, next = (mid+1)%n;
            // If mid is answer, it should be less than previous & next element.
            if (arr[mid] <= arr[prev] && arr[mid] <= arr[next]) {
                return mid;
            } else if(arr[mid] <= arr[end]) {
                end = mid-1;
            } else if (arr[start] <= arr[mid]) {
                start = mid + 1;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 6 - [Search in an almost sorted array](https://www.geeksforgeeks.org/search-almost-sorted-array/)
Given a sorted array arr[] of size N, some elements of array are moved to either of the adjacent positions, i.e., arr[i] may be present at arr[i+1] or arr[i-1] i.e. arr[i] can only be swapped with either arr[i+1] or arr[i-1]. The task is to search for an element in this array.

**Sample Input:**
```
arr[] =  {10, 3, 40, 20, 50, 80, 70}, key = 40
arr[] =  {10, 3, 40, 20, 50, 80, 70}, key = 90
```

**Sample Output:**
```
2
-1
```

**Solution :**
```java
public class Solution {

    public static int search(int [] arr, int target) {
        return binarySearch(arr,0, arr.length-1,  target);
    }

    public static int binarySearch(int [] arr, int start, int end, int target) {
        while (start <= end){
            int mid = start + (end-start)/2;
            // check if mid is answer
            if (arr[mid] == target) {
                return mid;
            } else if (mid-1 >= start && arr[mid-1] == target) { // check if mid-1 is answer
                return mid-1;
            } else if (mid+1 <= end && arr[mid+1] == target) { // check if mid+1 is answer
                return mid+1;
            } else if(arr[mid] < target) {
                start = mid + 2;
            } else {
                end = mid-2;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 7 - [Floor in a Sorted Array](https://www.geeksforgeeks.org/floor-in-a-sorted-array/)
Given a sorted array and a value x, the floor of x is the largest element in the array smaller than or equal to x. Write efficient functions to find the floor of x

**Sample Input:**
```
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 5
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 20
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 0
```

**Sample Output:**
```
2
19
-1
```

**Solution :**
```java
public class Solution {

    public static int search(int [] arr, int target) {
        int index = binarySearch(arr, 0, arr.length-1, target);
        return index == -1 ? -1 : arr[index];
    }

    public static int binarySearch(int [] arr, int start, int end, int target) {
        int res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if (arr[mid] == target) {
                return mid;
            } else if(arr[mid] < target) {
                // we need to store the result when mid element is less than target.
                res = mid;
                start = mid+1;
            } else {
                end = mid-1;
            }
        }
        return res;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 8 - [Ceil in a sorted array](https://www.geeksforgeeks.org/ceiling-in-a-sorted-array/)
Given a sorted array and a value x, the ceiling of x is the smallest element in an array greater than or equal to x, and the floor is the greatest element smaller than or equal to x. Assume that the array is sorted in non-decreasing order. Write efficient functions to find the floor and ceiling of x.

**Sample Input:**
```
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 5
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 20
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 0
arr[] = {1, 2, 8, 10, 10, 12, 19}, x = 1
```

**Sample Output:**
```
8
-1
1
1
```

**Solution :**
```java
public class Solution {

    public static int search(int [] arr, int target) {
        int index = binarySearch(arr, 0, arr.length-1, target);
        return index == -1 ? -1 : arr[index];
    }

    public static int binarySearch(int [] arr, int start, int end, int target) {
        int res = -1;
        while (start <= end){
            int mid = start + (end-start)/2;
            if (arr[mid] == target) {
                return mid;
            } else if(arr[mid] < target) {
                start = mid+1;
            } else {
                // we need to store the result when mid element is greater than target.
                res = mid;
                end = mid-1;
            }
        }
        return res;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 9 - [Find position of an element in a sorted array of infinite numbers](https://www.geeksforgeeks.org/find-position-element-sorted-array-infinite-numbers/)
Suppose you have a sorted array of infinite numbers, how would you search an element in the array?

**Sample Input:**
```
arr[] = {1, 2, 3, 4, 5, ..., infinite}, x = 5
```

**Sample Output:**
```
4
```

**Solution :**
```java
public class Solution {

    public static int search(int [] arr, int target) {
        // consider start as 0, end as 1 and move the end by multiplying it by 2 until target in within limits.
        int start = 0, end = 1;
        while(target > arr[end]) {
          start = end;
          end = end*2;
        }
        // apply binary search once we know the start and end.
        return binarySearch(arr, start, end, target);
    }

    public static int binarySearch(int [] arr, int start, int end, int target) {
        while (start <= end){
            int mid = start + (end-start)/2;
            if (arr[mid] == target) {
                return mid;
            } else if(arr[mid] < target) {
                start = mid+1;
            } else {
                end = mid-1;
            }
        }
        return res;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 10 - [Find the index of first 1 in an infinite sorted array of 0s and 1s](https://www.geeksforgeeks.org/find-index-first-1-infinite-sorted-array-0s-1s/)
Given an infinite sorted array consisting 0s and 1s. The problem is to find the index of first ‘1’ in that array. As the array is infinite, therefore it is guaranteed that number ‘1’ will be present in the array.

**Sample Input:**
```
arr[] = {0, 0, 1, 1, 1, 1, ..., infinite}
arr[] = {1, 1, 1, 1,, 1, 1, ...., infinite}
```

**Sample Output:**
```
2
0
```

**Solution :**
```java
public class Solution {

    public static int search(int[] arr) {
        // consider start as 0, end as 1 and move the end by multiplying it by 2 until target in within limits.
        int start = 0, end = 1, target = 1;
        while (target > arr[end]) {
            start = end;
            end = end*2;
        }
        // apply binary search once we know the start and end.
        return binarySearch(arr, start, end, target);
    }

    // Get First index of element using binarySearch
    public static int binarySearch(int[] arr, int start, int end, int target) {
        int res = -1;
        while(start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == target) {
                res = mid;
                end = mid-1;
            } else if(arr[mid] < target) {
                start = mid+1;
            } else {
                end = mid-1;
            }
        }
        return res;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 11 - [Absolute minimum difference in a Sorted Array from target](https://www.youtube.com/watch?v=3RhGdmoF_ac&list=PL_z_8CaSLPWeYfhtuKHj-9MpYb6XQJ_f2&index=15)
Given an infinite sorted array. You need to find the element with minimum difference from the target.

**Sample Input:**
```
arr[] = {1, 3, 8, 10, 15} , target = 12
```

**Sample Output:**
```
2
```

**Solution :**
```java
public class Solution {

    public static int binarySearch(int[] arr, int start, int end, int target) {
        while(start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == target) {
                // If element found - means difference is zero.
                return mid;
            } else if(arr[mid] < target) {
                start = mid+1;
            } else {
                end = mid-1;
            }
        }
        // Once we reach to the state where element is not present in array means either minimum diff is with start or end.
        return (Math.abs(arr[start]-target) < Math.abs(arr[end]-target)) ? arr[start] : arr[end];
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 12 - [Peak Element](https://leetcode.com/problems/find-peak-element/description/)
A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

**Sample Input:**
```
arr[] = {1, 3, 8, 10, 15} , target = 12
```

**Sample Output:**
```
2
```

**Solution :**
```java
public class Solution {
    
    public static int binarySearch(int[] arr, int start, int end) {
        int size = arr.length;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            // Check for middle elements if mid is greater than previous and next.
            if (mid > 0 && mid < size - 1) {
                if (arr[mid] > arr[mid - 1] && arr[mid] > arr[mid + 1]) {
                    return mid;
                } else if (arr[mid - 1] > arr[mid]) {
                    end = mid - 1;
                } else {
                    start = mid + 1;
                }
            } else if (mid == 0) {  // Check for 1st element
                return (arr[0] > arr[1]) ? 0 : 1;
            } else if (mid == size - 1) {  // Check for last element
                return (arr[size - 1] > arr[size - 2]) ? size - 1 : size - 2;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 13 - [Find an element in Bitonic array](https://www.geeksforgeeks.org/find-element-bitonic-array/)
Given a bitonic sequence of n distinct elements, and an integer x, the task is to write a program to find given element x in the bitonic sequence in O(log n) time

**Sample Input:**
```
arr[] = {-3, 9, 18, 20, 17, 5, 1}, target = 20
arr[] = {5, 6, 7, 8, 9, 10, 3, 2, 1}, target = 30
```

**Sample Output:**
```
3
-1
```

**Solution :**
- Maximum element in bitonic array is the same question as Peak Element. Because there will be an element which will be greater than previous and next element. [Maximum value in a bitonic array](https://www.includehelp.com/icp/maximum-value-in-a-bitonic-array.aspx#google_vignette)

```java
public class Solution {

    public static int search(int[] arr, int start, int end, int target){
        int peakElement = peakElement(arr, start, end);
        if(peakElement != -1){
            int leftSearch = binarySearchSorted(arr, start, peakElement, target);
            return (leftSearch != -1) ? leftSearch : binarySearchReverseSorted(arr, peakElement, end, target);
        }
        return -1;
    }

    // Binary Search in increasing sorted array.
    public static int binarySearchSorted(int[] arr, int start, int end, int target){
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                start = mid+1;
            } else {
                end = mid-1;
            }
        }
        return -1;
    }

    // Binary Search in decreasing sorted array.
    public static int binarySearchReverseSorted(int[] arr, int start, int end, int target){
        while (start <= end){
            int mid = start + (end-start)/2;
            if(arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return -1;
    }

    // Find peak element in the array which is greater than its previous and next element.
    public static int peakElement(int[] arr, int start, int end) {
        int size = arr.length;
        while(start <= end){
            int mid = start + (end-start)/2;
            // Check for middle elements if mid is greater than previous and next.
            if(mid > 0 && mid < size-1) {
                if(arr[mid] > arr[mid-1] && arr[mid] > arr[mid+1]) {
                    return mid;
                } else if(arr[mid-1] > arr[mid]){
                    end = mid-1;
                } else {
                    start = mid+1;
                }
            } else if(mid == 0) {  // Check for 1st element
                return (arr[0] > arr[1]) ? 0 : 1;
            } else if(mid == size-1){  // Check for last element
                return (arr[size-1] > arr[size-2]) ? size-1 : size-2;
            }
        }
        return -1;
    }
}
```

Time Complexity : O(3*log(n)) => O(log(n)) <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 14 - [Search in a row wise and column wise sorted matrix](https://www.geeksforgeeks.org/search-in-row-wise-and-column-wise-sorted-matrix/)
Given an n x m matrix and an integer x, find the position of x in the matrix if it is present. Otherwise, print “Element not found”. Every row and column of the matrix is sorted in increasing order. The designed algorithm should have linear time complexity

**Sample Input:**
```
arr[4][4] = { {10, 20, 30, 40},  x = 29
              {15, 25, 35, 45},
              {27, 29, 37, 48},
              {32, 33, 39, 50}}
arr[4][4] = { {10, 20, 30, 40},   x = 100
              {15, 25, 35, 45},
              {27, 29, 37, 48},
              {32, 33, 39, 50}};
```

**Sample Output:**
```
(2, 1)
-1
```

**Solution :**
- Mid-element in sorted matrix (row wise & column wise) would be the rightmost element in first row.

```java
public class Solution {

    private static int[] search(int[][] arr, int n, int m, int x) {
        int i=0, j=m-1;
        while(i >= 0 && i < n && j >= 0 && j < m) {
            if(arr[i][j] == x) {
                return new int[] {i, j};
            } else if (arr[i][j] > x) {
                j--;
            } else if(arr[i][j] < x) {
                i++;
            }
        }
        return new int[] {-1, -1};
    }
}
```

Time Complexity : O(n+m)     <br/>
Space Complexity : O(1) - No extra space is being used.

### Problem 15 - [Allocate Minimum Number of Pages from N books to M students](https://www.geeksforgeeks.org/allocate-minimum-number-pages/)
Given that there are N books and M students. Also given are the number of pages in each book in ascending order. The task is to assign books in such a way that the maximum number of pages assigned to a student is minimum, with the condition that every student is assigned to read some consecutive books. Print that minimum number of pages.



**Sample Input:**
```
N = 4, pages[] = {12, 34, 67, 90}, M = 2
```

**Sample Output:**
```
113
```

**Solution :**
- Decide the start/end of the array : start [max element in array], end [sum of all elements in array]
- Apply binary search and check for each mid element, if it is a valid number on which books can be divided.
  - If yes - store the result to check if any further minimum result exist or not.
- To check valid result, increase the student count if sum goes beyond the mid decided.


```java
public class Solution {

    public static int search(int[] pages, int k) {
        int totalPages = 0, maxNumPagesBook = 0;
        for (int numPagesCurrBook : pages) {
            maxNumPagesBook = Math.max(maxNumPagesBook, numPagesCurrBook);
            totalPages += numPagesCurrBook;
        }
        int start = maxNumPagesBook, end = totalPages, result = -1;
        while(start <= end) {
            int mid = start + (end-start)/2;
            if(isValid(pages, mid, k)) {
                result = mid;
                end = mid-1;
            } else {
                start = mid+1;
            }
        }
        return result;
    }

    private static boolean isValid(int [] pages, int maxNumPagesAllowed, int maxNumStudentsAllowed) {
        int noOfStudents = 1, totalPagesTillNow = 0;
        for (int numPagesCurrBook : pages) {
            totalPagesTillNow += numPagesCurrBook;
            if (totalPagesTillNow > maxNumPagesAllowed) {
                noOfStudents++;
                totalPagesTillNow = numPagesCurrBook;
            }
        }
        return (noOfStudents <= maxNumStudentsAllowed);
    }
}
```

Time Complexity : O(n*log(n))    <br/>
Space Complexity : O(1) - No extra space is being used.