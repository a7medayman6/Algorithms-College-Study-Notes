# Algorithms - Divide & Conquer I


1. Divide the problem into small distinct sub-problems.
2. Conquer the sub-problems by solving them recursively in the same manner.
3. Combine the solutions of the sub-problems to get the final solution.
 


## Merge Sort

1. Divide : Split the array into two halves.
2. Conquer : Recursively sort two sub-arrays.
3. Combine : Merge the two sorted sub-arrays.

### Merge Sort Analysis
1. Divide -> Trivial time.
2. Conquer -> two recursions on half the size -> 2T(N/2).
3. Combine -> Linear Time.
T(N) = 2 T(N/2) + Theta(N)
Master Method : Case #2 - > T(N) = Theta(N Log N).

## HOW?

1. Divide the array into two halves 
2. Repeat step 1 until the size of the array to split is 1
3. On your way back from the last recursion level,
	at each recursion level you have two arrays.
4. Compare the top of each array with the other and put the smaller
 value in the output array, then remove this value from its original array.
5. Repeat step 4 until the two arrays are empty.

### Example
![Merge Sort](https://github.com/a7medayman6/Algorithms-College-Study-Notes/blob/master/3.%20Design%20of%20Algorithms%20-%20Divide%20%26%20Conquer%20I/Images/mergesortexample.gif)

## Pseudocode
```
MergeSort(arr[], l,  r)**
If r > l
     1. Find the middle point to divide the array into two halves:  
             middle m = (l+r)/2
    2. Call mergeSort for first half:   
             Call mergeSort(arr, l, m)
     3. Call mergeSort for second half:
             Call mergeSort(arr, m+1, r)
     4. Merge the two halves sorted in step 2 and 3:
             Call merge(arr, l, m, r)
```
## Advantages 
- Running Time always guaranteed to run in <b> Theta(N log N) </b>

## Disadvantages
- Requires Extra Space.

## C++ Code
[The code original article]([https://www.geeksforgeeks.org/merge-sort/](https://www.geeksforgeeks.org/merge-sort/))

```cpp
void merge(int arr[], int l, int m, int r)
{
    int n1 = m - l + 1;
    int n2 = r - m;
 
    // Create temp arrays
    int L[n1], R[n2];
 
    // Copy data to temp arrays L[] and R[]
    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];
 
    // Merge the temp arrays back into arr[l..r]
 
    // Initial index of first subarray
    int i = 0;
 
    // Initial index of second subarray
    int j = 0;
 
    // Initial index of merged subarray
    int k = l;
 
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
 
    // Copy the remaining elements of
    // L[], if there are any
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
 
    // Copy the remaining elements of
    // R[], if there are any
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}
 
// l is for left index and r is
// right index of the sub-array
// of arr to be sorted */
void mergeSort(int arr[],int l,int r){
    if(l>=r){
        return;//returns recursively
    }
    int m = (l+r-1)/2;
    mergeSort(arr,l,m);
    mergeSort(arr,m+1,r);
    merge(arr,l,m,r);
}

```