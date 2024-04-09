# Sliding Window Pattern

- Sliding Window Technique is a method used to efficiently solve problems that involve defining a window or range in 
  the input data (arrays or strings) and then moving that window across the data to perform some operation within the window. This technique is commonly used in algorithms like finding sub-arrays with a specific sum, finding the longest substring with unique characters, or solving problems that require a fixed-size window to process elements efficiently.
- There can be 2 types of window size problems : 
  - **Fixed size window** : The general steps to solve these questions by following below steps:
    - Find the size of the window required, say K. 
    - Compute the result for 1st window, i.e. include the first K elements of the data structure. 
    - Then use a loop to slide the window by 1 and keep computing the result window by window.
  - **Variable size window**: The general steps to solve these questions by following below steps:
    - In this type of sliding window problem, we increase our right pointer one by one till our condition is true. 
    - At any step if our condition does not match, we shrink the size of our window by increasing left pointer. 
    - Again, when our condition satisfies, we start increasing the right pointer and follow step 1. 
    - We follow these steps until we reach to the end of the array.


## Sliding Window Problems

### Problem 1 - [Max Sum Subarray of size K](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)

Given an array of integers Arr of size N and a number K. Return the maximum sum of a subarray of size K.

**NOTE**: A subarray is a contiguous part of any given array.

**Sample Input:**
```
N = 4, K = 2, Arr = [100, 200, 300, 400]
N = 4, K = 4, Arr = [100, 200, 300, 400]
```

**Sample Output:**
```
700
1000
```

```java
class Solution{

    // Brute Force - Time Complexity : O(n^2)
    public static long maximumSumSubarray(int K, ArrayList<Integer> Arr,int N){
        long sum = 0, maxSum = 0;
        for(int i=0; i<=N-K; i++){
            for(int j=i; j<i+K; j++){
                sum += Arr.get(j);
            }
            maxSum = Math.max(maxSum, sum);
        }
        return maxSum;
    }

    // Sliding Window
    public static long maximumSumSubarray(int K, ArrayList<Integer> Arr,int N){
        int start=0, end =0;
        long sum=0, maxSum = 0;
        while(end < n){
            // calculation for adding element from end
            sum += arr.get(end);
            // check for window size
            if(end-start+1 == k){
                // calculation for the result
                maxSum = Math.max(sum, maxSum);
                // calculation for removing element from start - for sliding the window
                sum = sum - arr.get(start);
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }
        return maxSum;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(1)

### Problem 2 - [First negative integer in every window of size k](https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1)

Given an array A[] of size N and a positive integer K, find the first negative integer for each and every window(contiguous subarray) of size K.

**Sample Input:**

```
N = 5, A[] = {-8, 2, 3, -6, 10}, K = 2
N = 8, A[] = {12, -1, -7, 8, -15, 30, 16, 28}, K = 3
```

**Sample Output:**
```
-8 0 -6 -6
-1 -1 -7 -15 -15 0 
```

```java
class Solution{

    // Brute Force - Time Complexity : O(n^2)
    public static long[] printFirstNegativeInteger(long[] arr, int n, int k) {
        long[] res = new long[n-k+1];
        int idx = 0;
        for(int i=0; i<=n-k; i++){
            for(int j=i; j<=i+k; j++){
                if (j == i+k) {
                    res[idx++] = 0;
                    break;
                } else if(arr[j] < 0) {
                    res[idx++] = arr[j];
                    break;
                }
            }
        }
        return res;
    }

    // Sliding Window
    public static long[] printFirstNegativeIntegerTwo(long[] arr, int n, int k) {
        Queue<Long> q = new LinkedList<>();
        long[] res = new long[n-k+1];
        int start=0, end=0;
        while(end < n){
            // calculation for adding element from end
            if(arr[end] < 0){
                q.add(arr[end]);
            }
            // check for window size
            if(end-start+1 == k){
                // calculation for the result
                if(q.isEmpty()){
                    res[start] = 0;
                } else {
                    res[start] = q.peek();
                }
                // calculation for removing element from start - for sliding the window
                if(!q.isEmpty() && arr[start] == q.peek()){
                    q.remove();
                }
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }
        return res;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(1)

### Problem 3 - [Count Occurrences of Anagrams](https://www.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1)

Given a word pat and a text txt. Return the count of the occurrences of anagrams of the word in the text.

**Sample Input:**

```
txt = forxxorfxdofr, pat = for
txt = aabaabaa, pat = aaba
```

**Sample Output:**
```
3
4
```

```java
class Solution{

    // Brute Force - T(n) : O((n-m)*(m)), S(n) : O(26)
    public static int countAnagrams(String pat, String txt) {
        int res = 0;
        int size1 = pat.length();
        int size2 = txt.length();

        for (int i = 0; i < size2 - size1 + 1; i++) {
            String s1 = txt.substring(i, i + size1);
            if (areAnagram(s1, pat)) {
                res++;
            }
        }
        return res;
    }
    public static boolean areAnagram(String s1, String s2)
    {
        Map<Character, Integer> m = new HashMap<>();
        for (int i = 0; i < s1.length(); i++) {
            char c = s1.charAt(i);
            m.put(c, m.getOrDefault(c, 0) + 1);
        }
        for (int i = 0; i < s2.length(); i++) {
            char c = s2.charAt(i);
            m.put(c, m.getOrDefault(c, 0) - 1);
        }
        for (int count : m.values()) {
            if (count != 0) {
                return false;
            }
        }
        return true;
    }

    // sliding window
    public static int countAnagrams(String pat, String txt) {
        int n = txt.length();
        Map<Character, Integer> mp = new HashMap<>();
        for(char ch : pat.toCharArray()){
            mp.put(ch, mp.getOrDefault(ch, 0) + 1);
        }
        int k = mp.size(), count = mp.size();
        int countOfAnagrams=0;

        int start=0, end=0;
        while(end < n){
            // calculation for adding element from end
            if(mp.containsKey(txt.charAt(end))){
                mp.put(txt.charAt(end), mp.get(txt.charAt(end))-1);
                if(mp.get(txt.charAt(end))==0){
                    count--;
                }
            }
            // check for window size
            if(end-start+1 == k){
                // calculation for the result
                if(count == 0){
                    countOfAnagrams++;
                }
                // calculation for removing element from start - for sliding the window
                if(mp.containsKey(txt.charAt(start))){
                    mp.put(txt.charAt(start), mp.get(txt.charAt(start))+1);
                    if(mp.get(txt.charAt(start)) > 0){
                        count++;
                    }
                }
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }

        return countOfAnagrams;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)

### Problem 4 - [Maximum of all sub arrays of size k](https://www.interviewbit.com/problems/sliding-window-maximum/)

Given an array of integers A.  There is a sliding window of size B which is moving from the very left of the array to the very right. You can only see the w numbers in the window. Each time the sliding window moves rightwards by one position. You have to find the maximum for each window.

**Sample Input:**

```
A = {1, 3, -1, -3, 5, 3, 6, 7}, B = 3
```

**Sample Output:**
```
[3, 3, 5, 5, 6, 7]
```

```java
class Solution{

    public static int[] slidingMaximum(final int[] A, int B) {
        int n = A.length, start=0, end = 0;
        Deque<Integer> q = new ArrayDeque<>();
        int [] res = new int[n-B+1];
        while (end < n){
            // calculation for adding element from end
            while (!q.isEmpty() && A[end] > q.getLast()){
                q.removeLast();
            }
            q.addLast(A[end]);
            // check for window size
            if(end-start+1 == B){
                // calculation for the result
                if(q.isEmpty()){
                    res[start] = 0;
                } else {
                    res[start] = q.getFirst();
                }
                // calculation for removing element from start - for sliding the window
                if(A[start] == q.getFirst()){
                    q.removeFirst();
                }
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }
        return res;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)

### Problem 5 - [Longest sub-array having sum k](https://www.geeksforgeeks.org/longest-sub-array-sum-k/)

Given an array arr[] of size n containing integers. The problem is to find the length of the longest sub-array having sum equal to the given value k.

**Sample Input:**

```
arr[] = { 10, 5, 2, 7, 1, 9 }, k = 15
arr[] = {-5, 8, -14, 2, 4, 12}, k = -5
```

**Sample Output:**
```
4
5
```

```java
class Solution{

    // Brute Force - T(n) : O(n^2), S(n) : O(1)
    public static int lenOfLongSubarr(int[] arr, int n, int k) {
        int maxlength = 0;
        for (int i = 0; i < n; i++) {
            // Variable to store sum of sub arrays
            int Sum = 0;
            for (int j = i; j < n; j++) {
                // Storing sum of sub arrays
                Sum += arr[j];
                // if Sum equals K
                if (Sum == k) {
                  // Update maxLength
                  maxlength = Math.max(maxlength, j - i + 1);
                }
            }
        }
        // Return the maximum length
        return maxlength;          
    }

    // Max Length Subarray for sum == k
    // Sliding Window , T(n) - O(n) , S(n) - O(1)
    // It will work only with positive integers set.
    public static int lenOfLongSubarr(int[] arr, int n, int k) {
        int start = 0, end = 0, sum = 0, maxLength = 0;
        while(end < n){
            // calculation for adding element from end
            sum += arr[end];
            // check for window size
            if(sum == k){
                // calculation for the result
                maxLength = Math.max(maxLength, end-start+1);
            }
            // calculation for removing element from start - for sliding the window
            while(sum > k){
                sum -= arr[start];
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }
        return maxLength;
    }

    // Sliding Window
    // It will work with positive/negative integers set.
    public static int lenOfLongSubarr(int[] arr, int n, int k) {
        Map<Integer, Integer> mp = new HashMap<>();
        int i=0, res = 0;
        int sum = 0;
        mp.put(0, -1);
        while (i<n){
            sum += arr[i];
            if(mp.get(sum-k) != null){
                int length = i-mp.get(sum-k);
                res = Math.max(res, length);
            }
            mp.putIfAbsent(sum, i);
            i++;
        }
        return res;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)

### Problem 6 - [Longest K unique characters substring](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1)

Given a string you need to print the size of the longest possible substring that has exactly K unique characters. If there is no possible substring then print -1.

**Sample Input:**

```
S = "aabacbebebe", K = 3
S = "aaaa", K = 2
```

**Sample Output:**
```
7
-1
```

```java
class Solution{

    public static int longestKSubstr(String str, int k) {
        int maxLength = -1, n = str.length();
        Map<Character, Integer> mp = new HashMap<>();
        int start = 0, end = 0;
        while(end < n){
            if(mp.size() > k){
                mp.put(str.charAt(start), mp.get(str.charAt(start))-1);
                if(mp.get(str.charAt(start)) == 0){
                    mp.remove(str.charAt(start));
                }
                start++;
            }
            mp.put(str.charAt(end), mp.getOrDefault(str.charAt(end), 0) + 1);
            if(mp.size() == k){
                maxLength = Math.max(maxLength, end-start+1);
            }
            end++;
        }
        return maxLength;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)

### Problem 7 - [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

Given a string s, find the length of the longest substring without repeating characters.

**Sample Input:**

```
s = "abcabcbb"
s = "bbbbb"
s = "pwwkew"
```

**Sample Output:**
```
3
1
3
```

```java
class Solution{

    public int lengthOfLongestSubstring(String s) {
        int maxLength = 0, n = s.length(), start=0, end=0 ;
        Map<Character, Integer> mp = new HashMap<>();
        while(end < n){
            // calculation for adding element from end
            mp.put(s.charAt(end), mp.getOrDefault(s.charAt(end), 0)+1);
            // check for window size
            if(mp.size() == end-start+1){
                // calculation for the result
                maxLength = Math.max(maxLength, end-start+1);
            }
            // calculation for removing element from start - for sliding the window
            while(mp.size() < end-start+1) {
                mp.put(s.charAt(start), mp.get(s.charAt(start)) - 1);
                if (mp.getOrDefault(s.charAt(start), 0) == 0) {
                    mp.remove(s.charAt(start));
                }
                // move start pointer
                start++;
            }
            // move end pointer
            end++;
        }
        return maxLength;
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)

### Problem 8 - [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)

Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string.

**Sample Input:**

```
s = "ADOBECODEBANC", t = "ABC"
s = "a", t = "a"
s = "a", t = "aa"
```

**Sample Output:**
```
"BANC"
"a"
""
```

```java
class Solution{

    public String minWindow(String s, String t) {
        Map<Character, Integer> mp = new HashMap<>();
        for(Character ch : t.toCharArray()){
            mp.put(ch, mp.getOrDefault(ch, 0) + 1);
        }
        
        int count=0, start=0, end=0, minLeft=0, minLength=Integer.MAX_VALUE;
        while(end<s.length()){
            Character endChar = s.charAt(end);
            if(mp.containsKey(endChar)){
                mp.put(endChar, mp.get(endChar) - 1);
                if(mp.get(endChar) >= 0){
                    count++;
                }
            }
            while(count == t.length()){
                Character startChar = s.charAt(start);
                if(minLength > end-start+1){
                    minLength = end-start+1;
                    minLeft = start;
                }
                if(mp.containsKey(startChar)){
                    mp.put(startChar, mp.get(startChar)+1);
                    if(mp.get(startChar) > 0){
                        count--;
                    }
                }
                start++;
            }
            end++;
        }
        return (minLength == Integer.MAX_VALUE) ? "" : s.substring(minLeft, minLeft+minLength);
    }
}
```

**Time Complexity** : O(n) <br/>
**Space Complexity** : O(n)