# Sorting Algorithms

Sorting data means arranging it in a certain order, often in an array-like data structure. 

## Bubble Sort 

Bubble sort works by swapping adjacent elements if they're not in the desired order. This process repeats from the beginning of the array until all elements are in order.

**Sample Input:**
```
arr = {12, 67, 34, 1}
```

**Sample Output:**
```
[1, 12, 34, 67]
```

```java
public static void sort(int[] arr) {
    int size = arr.length;
    for(int i=0; i<size-1; i++){
        for(int j=0; j<size-i-1; j++){
            if(arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    System.out.println(Arrays.toString(arr));
}
```

**Time Complexity** : O(n^2) <br/>
**Space Complexity** : O(1) - No extra space is being used.

## Insertion Sort

The idea behind Insertion Sort is dividing the array into the sorted and unsorted sub-arrays. We place the element 
to its correct position in sorted array. We do this by shifting all the elements to the right until we encounter the first element we don't have to shift.

**Sample Input:**
```
arr = {12, 67, 34, 1}
```

**Sample Output:**
```
[1, 12, 34, 67]
```

```java
public static void sort(int[] arr) {
    int size = arr.length;
    for(int i=1; i<size; i++){
        int currElem = arr[i];
        int j;
        for(j=i-1; j>=0 && currElem < arr[j]; j--) {
            arr[j+1] = arr[j];
        }
        arr[j+1] = currElem;
    }
    System.out.println(Arrays.toString(arr));
}
```

**Time Complexity** : O(n^2) <br/>
**Space Complexity** : O(1) - No extra space is being used.

### Selection Sort

Selection Sort also divides the array into a sorted and unsorted subarray. Though, this time, the sorted subarray is formed by inserting the minimum element of the unsorted subarray at the end of the sorted array, by swapping.

**Sample Input:**
```
arr = {12, 67, 34, 1}
```

**Sample Output:**
```
[1, 12, 34, 67]
```

```java
public static void sort(int[] arr) {
    int size = arr.length;
    for(int i=0; i<size; i++){
        int min = arr[i];
        int minIdx = i;
        for(int j=i+1; j<size; j++) {
            if(arr[j] < min) {
                min = arr[j];
                minIdx = j;
            }
        }
        int temp = arr[i];
        arr[i] = min;
        arr[minIdx] = temp;
    }
    System.out.println(Arrays.toString(arr));
}
```

**Time Complexity** : O(n^2) <br/>
**Space Complexity** : O(1) - No extra space is being used.

## Merge Sort

Merge Sort uses recursion to solve the problem of sorting more efficiently than algorithms previously presented, and in particular it uses a divide and conquer approach.

Using both of these concepts (recursion, divide & conquer), we break the whole array into two subarrays and then do following :
- Sort the left half of the array (recursively)
- Sort the right half of the array (recursively)
- Merge the sorted left and right array.

**Sample Input:**
```
arr = {12, 67, 34, 1}
```

**Sample Output:**
```
[1, 12, 34, 67]
```

```java
public static void sort(int[] arr) {
    sort(arr, 0, arr.length-1);
}

public static void sort(int[] arr, int start, int end) {
    if (end <= start) return;
    int mid = start + (end-start)/2;
    sort(arr, start, mid);
    sort(arr, mid+1, end);
    merge(arr, start, mid, end);
}

private static void merge(int[] arr, int start, int mid, int end) {
    int [] merged = new int[end-start+1];
    int k=0, s1 = start, e1 = mid, s2 = mid+1, e2 = end;
    while (s1 <= e1 && s2 <= e2) {
        if(arr[s1] < arr[s2]) {
            merged[k++] = arr[s1++];
        } else {
            merged[k++] = arr[s2++];
        }
    }
    while(s1<=e1){
        merged[k++] = arr[s1++];
    }
    while(s2<=e2){
        merged[k++] = arr[s2++];
    }
    int index = start;
    for(int i=0; i<k; i++){
        arr[index++] = merged[i];
    }
}
```

**Time Complexity** : O(n*log(n)) <br/>
**Space Complexity** : O(n)

## Quick Sort

Quicksort is another Divide and Conquer algorithm. It picks one element of an array as the pivot and sorts all of the other elements around it, for example smaller elements to the left, and larger to the right.

**Sample Input:**
```
arr = {12, 67, 34, 1}
```

**Sample Output:**
```
[1, 12, 34, 67]
```

```java
public static void sort(int[] arr) {
    sort(arr, 0, arr.length-1);
}

public static void sort(int[] arr, int start, int end) {
    if (end <= start) return;
    int pivot = partition(arr, start, end);
    sort(arr, start, pivot-1);
    sort(arr, pivot+1, end);
}

private static int partition(int[] arr, int start, int end) {
    int pivot = arr[start];
    int count = 0;
    for(int i=start+1; i<=end; i++){
        if(arr[i] <= pivot) {
            count++;
        }
    }
    arr[start] = arr[start+count];
    arr[start+count] = pivot;

    int i=start, j=end;
    while(i < start+count && j > start+count) {
        if(arr[i] <= pivot) {
            i++;
        } else if(arr[j] >= pivot) {
            j--;
        } else {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            i++;
            j--;
        }
    }
    return start+count;
}
```

**Time Complexity** : O(n*log(n)) <br/>
**Space Complexity** : O(1)