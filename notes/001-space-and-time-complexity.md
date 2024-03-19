# Time & Space Complexity

>   ```Time Complexity``` is a concept in computer science that deals with the **quantification of the amount of time taken by a set of code or algorithm** to process or run as a function of the amount of input. In other words, the time complexity is how long a program takes to process a given input.

>   ```Space Complexity``` is the total memory space required by the program for its execution.

---

### What is Algorithm? 
- An **Algorithm** is a standard step-by-step unambiguous instructions to solve a given problem.
- There are 2 main criteria for judging the merits of algorithms:
  - **Correctness** : Does the algorithm give solution to the problem in a finite number of steps?
  - **Efficiency** : How many resources in terms of memory and time it takes to execute.

---

### Asymptotic notations
- To compare two or more algorithms rate of growth with respect to time and space, we need asymptotic notations.
- It is a tool to represent time and space complexity of algorithms for asymptotic analysis.
- There are mainly three types of it : `Big-O, Big-Omega, Big-Theta`.

##### Big-O Notation

```
It is defined as O(g(n)) = { f(n): there exist positive constants c and n0 such that 0 ≤ f(n) ≤ cg(n) for all n ≥ n0 }
```

- Big-O notation represents the upper bound of the running time of an algorithm. Therefore, it gives the worst-case 
  complexity of an algorithm.
- It returns the highest possible output value (big-O)for a given input.
- The execution time serves as an upper bound on the algorithm’s time complexity.
- We define an algorithm’s **worst-case** time complexity by using the Big-O notation


##### Omega Notation (Ω-Notation)
```
It is defined as Ω(g(n)) = { f(n): there exist positive constants c and n0 such that 0 ≤ cg(n) ≤ f(n) for all n ≥ n0 }
```

- Omega notation represents the lower bound of the running time of an algorithm. Thus, it provides the best case 
  complexity of an algorithm.
- The execution time serves as a lower bound on the algorithm’s time complexity.  
- It is defined as the condition that allows an algorithm to complete statement execution in the shortest amount of time.
- We define an algorithm’s **best-case** time complexity by using the Big-O notation


##### Theta Notation (Θ-Notation)
```
It is defined as Θ (g(n)) = {f(n): there exist positive constants c1, c2 and n0 such that 
0 ≤ c1 * g(n) ≤ f(n) ≤ c2 * g(n) for all n ≥ n0}
```

- Theta notation represents the upper and lower bound of the running time of an algorithm, thus it is used for 
  analyzing the average-case complexity of an algorithm.
- The execution time serves as a lower bound on the algorithm’s time complexity.
- It is defined as the condition that allows an algorithm to complete statement execution in the shortest amount of time.
- We define an algorithm’s **average-case** time complexity by using the Big-O notation

---

### How to Analyse Complexity for Algorithms

- Commonly used rate of growth
  ```shell
  (2^(2^n)) > n! > 4^n > 2^n > n^3> n^2 > n(logn) > log(n!) > n > 2^(logn) > log^2n > sqrt(logn) > log(logn) > 1 
  ```

#### Constant Time Complexity O(1)
- The time complexity of a function (or set of statements) is considered as O(1) if it doesn’t contain a loop, recursion, 
and call to any other non-constant time function.
- In computer science, O(1) refers to constant time complexity, which means that the running time of an algorithm 
  remains constant and does not depend on the size of the input.
```java
class Solution {
  public static void main(String[] args) {
    for (int i = 1; i <= 10; i++) {
      int counter = 2*i+1;  // O(1) expression
    }
  }
}
```

#### Linear Time Complexity O(n)
- The Time Complexity of a loop is considered as O(n) if the loop variables are incremented/decremented by a constant 
  amount.

```java
class Solution {
  public static void main(String[] args) {
    for (int i = 1; i <= n; i++) { // Since loop will run n times so O(n)
      int counter = 2*i+1;  // O(1) expression
    }
  }
}
```  

#### Quadratic Time Complexity O(n^c)
- The time complexity is defined as an algorithm whose performance is directly proportional to the squared size of 
  the input data, as in nested loops it is equal to the number of times the innermost statement is executed.
```java
class Solution {
  public static void main(String[] args) {
    // 2 nested loops which will run n times so O(n^2) 
    for (int i = 1; i <= n; i += c) {
      for (int j = 1; j <= n; j += c) {
        // some O(1) expressions
      }
    }

    // 3 nested loops which will run n times so O(n^3) 
    for (int i = 1; i <= n; i += c) {
      for (int j = 1; j <= n; j += c) {
        for (int k = 1; k <= n; k += c) {
          // some O(1) expressions
        }
      }
    }
  }
}
```    

#### Logarithmic Time Complexity O(log(n))
- The time Complexity of a loop is considered as O(Logn) if the loop variables are divided/multiplied by a constant amount.
- And also for recursive calls in the recursive function, the Time Complexity is considered as O(Logn).
```java
class Solution {
  public static void main(String[] args) {
    // below is reducing the size by constant c
    for (int i = 1; i <= n; i *= c) {
      // some O(1) expressions
    }
    for (int i = n; i > 0; i /= c) {
      // some O(1) expressions
    }
  }
}
```

#### Logarithmic Time Complexity O(log(log(n)))
- The Time Complexity of a loop is considered as O(LogLogn) if the loop variables are reduced/increased exponentially 
  by a constant amount.
```java
class Solution {
  public static void main(String[] args) {
    // Here c is a constant greater than 1
    for (int i = 2; i <= n; i = Math.pow(i, c)) {
      // some O(1) expressions
    }
    // Here fun is sqrt or cuberoot or any other constant root
    for (int i = n; i > 1; i = fun(i)) {
      // some O(1) expressions
    }
  }
}
```

---

#### Algorithm Analysis for different sorting techniques

Algorithm|	Best Case|	Average Case|	Worst Case|
---|---|---|---| 
Selection Sort	|O(n^2)	|O(n^2)	|O(n^2)
Bubble Sort	|O(n)|	O(n^2)|	O(n^2)
Insertion Sort	|O(n)|	O(n^2)|	O(n^2)
Tree Sort	|O(nlogn)|	O(nlogn)|	O(n^2)
Radix Sort	|O(dn)|	O(dn)|	O(dn)
Merge Sort	|O(nlogn)	|O(nlogn)	|O(nlogn)
Heap Sort	|O(nlogn)	|O(nlogn)|	O(nlogn)
Quick Sort	|O(nlogn)	|O(nlogn)	|O(n^2)
Bucket Sort	|O(n+k)	|O(n+k)	|O(n^2)
Counting Sort	|O(n+k)|	O(n+k)|	O(n+k)


#### Worst Case time complexity of different data structures for different operations

Data structure | Access | Search | Insertion | Deletion |
----------------|--------|--------|-----------|----------|
Array	    |   O(1)  | O(N) | O(N) | O(N) |
Stack	| O(N) | O(N)| O(1)| O(1) |
Queue	|O(N)	|O(N)	|O(1)	|O(1)|
Singly Linked list	|O(N)	|O(N)	|O(1)	|O(1)|
Doubly Linked List	|O(N)	|O(N)	|O(1)	|O(1)|
Hash Table	|O(N)	|O(N)	|O(N)	|O(N)
Binary Search Tree	|O(N)	|O(N)	|O(N)	|O(N)
AVL Tree	|O(log N)	|O(log N)	|O(log N)	|O(log N)
Binary Tree	|O(N)	|O(N)	|O(N)	|O(N)
Red Black Tree	|O(log N)	|O(log N)	|O(log N)	|O(log N)


---


### Space Complexity

- Space complexity refers to the amount of memory or storage space that an algorithm or function consumes based on the 
  size of its input. 
- It measures how the memory usage of an algorithm scales with the size of the input data. The goal is to optimize 
  memory usage and minimize the additional memory required during the execution of an algorithm or program.
- There are a lot of similarities between time and space complexity. We can use the same Big O notation to describe 
  space complexity. We have constant, linear, quadratic, logarithmic, exponential, and factorial space complexity.
- In many cases, the space complexity of a function will be the same as the time complexity. If a function 
  takes `O(n)` time, it will also take `O(n)` space. If a function takes `O(n^2)` time, it will also take `O(n^2)` 
  space. This is because the amount of memory used by a function is often directly related to the number of 
  operations it performs. However, this is not always the case. Sometimes a function will take up more memory than 
  time, or vice versa.

#### Rules for Calculating Space Complexity

1. **Variables and data structures take up space:** When you declare variables or use data structures (arrays, objects, etc.) in your code, they occupy memory space based on their size and data type. The space complexity increases with the number and size of variables and data structures used in your program.

2. **Function calls take up space:** Whenever you call a function, the program needs to allocate memory for the function call stack, which includes function arguments, local variables, return addresses, and other bookkeeping information. Each function call adds to the space complexity, and if you have nested function calls or recursive functions, it can lead to a significant increase in space usage.

3. **The space complexity of a function is the sum of the space complexities of all the variables, data structures, and function calls inside the function:** This means that to calculate the space complexity of a function, you need to consider all the variables and data structures used within the function and their space requirements. Additionally, if the function makes any recursive or nested function calls, you need to account for the space used by those function calls as well.

--- 

### Examples of Space Complexity

Let's take a look at some examples:

#### Constant Space `O(1)`

```java
class Solution {
    public void add(int num1, int num2) {
      return num1 + num2;
    }
}
```

- The space complexity of this function is `constant`. The function does not create any additional data structures or 
  variables that depend on the input size. It simply returns the result of the addition, so the amount of memory used 
  by the function does not change with the input size.
- We can describe this function as `O(1)` in Big O notation.

#### Linear Space `O(n)`

```java
class Solution {
  public int[] createArray(int num) {
    int [] arr = new int[num];
    for (int i = 0; i < num; i++) {
      arr[i] = i;
    }
    return arr;
  }
}

```

- The space complexity of the function createArray(num) is `linear`. This is because the function creates an array and 
  pushes elements into it using the for loop. As the input `num` increases, the size of the array also increases 
  proportionally. Therefore, the space complexity of the function grows linearly with the input.
- We can describe this function as `O(n)` in Big O notation.

#### Quadratic Space `O(n^2)`

```java
class Solution {
  public int[] createMatrix(int num) {
    int[] matrix = new int[num];

    for (int i = 0; i < num; i++) {
      matrix[i] = i;
      for (int j = 0; j < num; j++) {
        matrix[i][j] = i + j;
      }
    }
    return matrix;
  }
}
```

- The space complexity of the function createMatrix(num) is `quadratic`. This is because the function creates a 
  two-dimensional array and fills it with values using the nested for loops. As the input `num` increases, the size 
  of the matrix also increases proportionally. Therefore, the space complexity of the function grows quadratically 
  with the input.
- We can describe this function as `O(n^2)` in Big O notation.

#### Logarithmic Space `O(log n)`

```java
class Solution {
  public int findPower(int base, int exponent) {
    if (exponent == 0) {
      return 1;
    }

    if (exponent % 2 == 0) { 
      int halfPower = findPower(base, exponent / 2);
      return halfPower * halfPower;
    } else {
      int halfPower = findPower(base, (exponent - 1) / 2);
      return base * halfPower * halfPower;
    }
  }
}
```

- The space complexity of the function `findPower(base, exponent)` is `logarithmic`. This is because the function 
  uses recursion to calculate the power of a number. As the input `exponent` increases, the number of recursive calls 
  increases logarithmically. Therefore, the space complexity of the function grows logarithmically with the input.
- We can describe this function as `O(log n)` in Big O notation.

---