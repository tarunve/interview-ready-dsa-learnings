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