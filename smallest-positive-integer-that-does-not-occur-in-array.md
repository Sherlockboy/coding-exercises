# Problem

Write a function:

`class Solution { public int solution(int[] A); }`

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].

# Solution:
```
class Solution {
    public int solution(int[] A) {
        int max = A[0];
        int min = A[0];

        // Find smallest and gratest numbers in the Array
        for(int i=0; i<A.length; i++) {
            if(A[i] > max)
                max = A[i];
            else if(A[i] < min)
                min = A[i];
        }

        // Return 1, if max or Array is negative
        if(max <= 0)
            return 1;

        // Check missing number between the range of [min+1, max-1]
        for(int i=min+1; i<max; i++) {
            boolean isFound = true;

            for(int index=0; index < A.length; index++) {
                if(i == A[index])
                    isFound = false;
            }

            if(isFound)
                return i;
        }

        // Return max + 1, if no missing number is found
        return max + 1;
    }
}
```

# Acceptance: 11%
