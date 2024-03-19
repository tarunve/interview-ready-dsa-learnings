# Star Patterns (loops)

> We can solve it using the nested loops

- For the outer loop, count the number of lines i.e. rows.
- For the inner loop, focus on the columns and connect them somehow to the rows.
- Print as per required result inside the inner **for** loop. 
- Observe Symmetry [Optional]

---

### Problem 1: 

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
* * *
* * *
* * *
```

**Solution :** 
```java
public class Solution {
    public static void solve(int n) {
        for(int row=0; row<n; row++){
            for(int col=0; col<n; col++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 2:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
* 
* *
* * *
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=0; row<n; row++){
            for(int col=0; col<=row; col++){
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 3:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1
1 2 
1 2 3
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row<=n; row++){
            for(int col=1; col<=row; col++){
                System.out.print(col + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 4:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1
2 2 
3 3 3
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row<=n; row++){
            for(int col=1; col<=row; col++){
                System.out.print(row + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 5:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
* * *
* *
*
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            for(int col = n; col >= row; col--){
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 6:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1 2 3
1 2
1
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            int val = 1;
            for(int col = n; col >= row; col--){
                System.out.print(val++ + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 7:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
  *
 ***
*****
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            for(int space = 1; space <= n-row; space++){
                System.out.print(" ");
            }
            for(int col = 1; col <= (2*row-1); col++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 8:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
*****
 ***
  *
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=0; row < n; row++){
            for(int space = 0; space <= row-1; space++){
                System.out.print(" ");
            }
            for(int col = 1; col <= (2*n - 2*row -1); col++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 9:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
  *
 ***
*****
*****
 ***
  *
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= 2*n; row++){
            int spaces = (row <= n) ? (n-row) : (row-n-1) ;
            for(int space = 1; space <= spaces; space++){
                System.out.print(" ");
            }
            int stars = (row <= n) ? (2*row-1) : (4*n - 2*row +1); 
            for(int col = 1; col <= stars; col++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 10:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
*
**
***
**
*
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= 2*n-1; row++){
            int stars = (row <= n) ? row : (2*n - row) ;
            for(int col = 1; col <= stars; col++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 11:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1
0 1
1 0 1
```

**Solution :**
```java
public class Solution {
    // option 1:
    public static void solve_one(int n) {
        for (int row = 1; row <= n; row++) {
            for (int col = 1; col <= row; col++) {
                if ((row + col) % 2 == 0) {
                    System.out.print("1 ");
                } else {
                    System.out.print("0 ");
                }
            }

            System.out.println();
        }
    }
    
    // option 2:
    public static void solve_two(int n) {
        for(int row=1; row <= n; row++){
            int val = (row%2 == 0) ? 0 : 1;
            for(int col = 1; col <= row; col++){
                System.out.print(val%2 + " ");
                val++;
            }
            System.out.println();
        }
    }
}
```

---

### Problem 12:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1         1
1 2     2 1
1 2 3 3 2 1
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            int val = 1; 
            for(int col = 1; col <= row; col++){
                System.out.print(val++ + " ");
            }
            
            for(int space=1; space <= 2*(n-row); space++){
                System.out.print(" ");
            }
            
            val = row;
            for(int col = 1; col <= row; col++){
                System.out.print(val-- + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 13:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
1
2 3
4 5 6
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        int val = 1;
        for(int row=1; row <= n; row++){
            for(int col = 1; col <= row; col++){
                System.out.print(val++ + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 14:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
A
A B
A B C
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            char val = 'A';
            for(int col = 1; col <= row; col++){
                System.out.print(val++ + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 15:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
A B C
A B
A
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            char val = 'A';
            for(int col = n; col >= row; col--){
                System.out.print(val++ + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 16:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
A
B B
C C C
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            char val = (char)('A' + row - 1);
            for(int col = 1; col <= row; col++){
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 17:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
    A
  A B A
A B C B A
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            for(int space = 1; space <= n-row; space++){
                System.out.print(" ");
            }
            
            char val = 'A';
            for(int col = 1; col <= row; col++){
                System.out.print(val++ + " ");
            }
            
            val -= 2;
            for(int col = 1; col <= row-1; col++) {
                System.out.print(val-- + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 18:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
C
C B 
C B A
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            char val = (char)('A' + n - 1);
            for(int col = 1; col <= row; col++){
                System.out.print(val-- + " ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 19:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
* * * * * * 
* *     * * 
*         * 
*         * 
* *     * * 
* * * * * * 
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= 2*n; row++){
            int stars = (row <= n) ? (n-row+1) : (row-n);
            for(int col = 1; col <= stars ; col++){
                System.out.print("* ");
            }

            int spaces = (row <= n) ? 2*(row-1) : (4*n-2*row);
            for(int col = 1; col <= spaces; col++){
                System.out.print("  ");
            }

            stars = (row <= n) ? (n-row+1) : (row-n);
            for(int col = 1; col <= stars ; col++){
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 20:

Given an integer N, print the following pattern :

**Input:**

N = 3

**Output:**
```text
*         *
* *     * *
* * * * * *
* *     * *
*         *
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= 2*n-1; row++){
            int stars = (row <= n) ? row : (2*n-row);
            for(int col = 1; col <= stars ; col++){
                System.out.print("* ");
            }

            int spaces = (row <= n) ? 2*(n-row) : 2*(row-n);
            for(int col = 1; col <= spaces; col++){
                System.out.print("  ");
            }

            stars = (row <= n) ? row : (2*n-row);
            for(int col = 1; col <= stars ; col++){
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

### Problem 21:

Given an integer N, print the following pattern :

**Input:**

N = 4

**Output:**
```text
****
*  *
*  *
****
```

**Solution :**
```java
public class Solution {
    public static void solve(int n) {
        for(int row=1; row <= n; row++){
            for(int col = 1; col <= n ; col++){
                if(row == 1 || col == 1 || row == n || col == n) {
                    System.out.print("*");
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }
}
```

---

### Problem 22:

Given an integer N, print the following pattern :

**Input:**

N = 4

**Output:**
```text
4444444
4333334
4322234
4321234
4322234
4333334
4444444
```

**Solution :**
- **Hint** : Remove each value by n : it will give the minimum distance from top/bottom/left/right.
```java
public class Solution {
    public static void solve(int n) {
        for(int row=0; row < 2*n-1; row++){
            for(int col = 0; col < 2*n-1 ; col++){
                int top = row;
                int left = col;
                int right = 2*n-col-2;
                int bottom = 2*n-row-2;
                int min = Math.min(Math.min(top, bottom), Math.min(left, right));
                System.out.print(n-min);
            }
            System.out.println();
        }
    }
}
```