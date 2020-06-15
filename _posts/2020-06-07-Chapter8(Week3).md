---
layout: post
title: 'Chapter 8'
date: 2020-06-13
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week3 data-structures
---

> Sorting

### Definition and background
Sorting was long a problem that exists in every place of our lives. Nowadays, we need a sorting algorithm to best achieve certain programming goals. Therefore, the study on sorting algorithms and their cost are needed for future development.

### Sorting Terminology and Notation
1. Stable: the result after sorting doesn't change the relative order of data that holds the same value.

2. empirical comparison: Compare two algorithms by measure the time they actually cost. Usually not applicable since it's hard to be fair when testing.

Note: In tradition, we analyze the cost of one algorithm by calculating the amount of comparison it takes. However, sometimes we need to count the amount of swapping operation it does or the memory it requires.

### Sort algorithm we learned in CS2114
1. Insertion Sort: code implementation from [openDSA](https://canvas.vt.edu/courses/111334/assignments/883559?module_item_id=901452)


static <T extends Comparable<T>> void inssort(T[] A) {
  for (int i=1; i<A.length; i++) // Insert i'th record
    for (int j=i; (j>0) && (A[j].compareTo(A[j-1]) < 0); j--)
      Swap.swap(A, j, j-1);
}


Average: O(n^2), stable

2. Bubble Sort: 

code implementation from [openDSA](https://canvas.vt.edu/courses/111334/assignments/883560?module_item_id=901454)


  for (int i=0; i<A.length-1; i++) // Insert i'th record
    for (int j=1; j<A.length-i; j++)
      if (A[j-1].compareTo(A[j]) > 0)
        Swap.swap(A, j-1, j);
}


Average: O(n^2), stable

3. Selection Sort:code implementation from [openDSA](https://canvas.vt.edu/courses/111334/assignments/883561?module_item_id=901456)


static <T extends Comparable<T>> void selsort(T[] A) {
  for (int i=0; i<A.length-1; i++) {       // Select i'th biggest record
    int bigindex = 0;                      // Current biggest index
    for (int j=1; j<A.length-i; j++)       // Find the max value
      if (A[j].compareTo(A[bigindex]) > 0) // Found something bigger  
        bigindex = j;                      // Remember bigger index
    Swap.swap(A, bigindex, A.length-i-1);  // Put it into place
  }
}


Average:  O(n^2), unstable

Note: The essential bottleneck for these three kinds of a sorting algorithm is because of the cost of swapping.

Optimization: We can focus either on the compiler or the algorithm itself.

### Some new sort algorithm 

1. Shell sort(diminishing increment sort)


implementation from[openDSA](https://canvas.vt.edu/courses/111334/assignments/883563?module_item_id=901461)


static void shellsort(int[] A) {
  for (int i=A.length/2; i>2; i/=2) // For each increment
    for (int j=0; j<i; j++)         // Sort each sublist
      inssort2(A, j, i);
  inssort2(A, 0, 1);     // Could call regular inssort here
}

/** Modified Insertion Sort for varying increments */
static void inssort2(int[] A, int start, int incr) {
  for (int i=start+incr; i<A.length; i+=incr)
    for (int j=i; (j>=incr) && (A[j] < A[j-incr]); j-=incr)
      Swap.swap(A, j, j-incr);
}


Average: O(n(logn)^2) unstable



2. Merge sort(divide and conquer) 
The merge sort breaks the list into pieces then process each of them. Finally put it back in a certain way.


implementation from[openDSA](https://canvas.vt.edu/courses/111334/assignments/883565?module_item_id=901465)


  static void mergesort(Comparable[] A, Comparable[] temp, int left, int right) {
  if (left == right) return;         // List has one record
  int mid = (left+right)/2;          // Select midpoint
  mergesort(A, temp, left, mid);     // Mergesort first half
  mergesort(A, temp, mid+1, right);  // Mergesort second half
  for (int i=left; i<=right; i++)    // Copy subarray to temp
    temp[i] = A[i];
  // Do the merge operation back to A
  int i1 = left;
  int i2 = mid + 1;
  for (int curr = left; curr <= right; curr++) {
    if (i1 == mid+1)                 // Left sublist exhausted
      A[curr] = temp[i2++];
    else if (i2 > right)             // Right sublist exhausted
      A[curr] = temp[i1++];
    else if (temp[i1].compareTo(temp[i2]) <= 0)  // Get smaller value
      A[curr] = temp[i1++];
    else
      A[curr] = temp[i2++];
  }
}


Average: O(n logn), stable

3. Quick sort: It was named quick because when implemented correctly, quicksort is usually the quickest sort algorithm.


implementation from[openDSA](https://canvas.vt.edu/courses/111334/assignments/883566?module_item_id=901467)


static void quicksort(Comparable[] A, int i, int j) { // Quicksort
  int pivotindex = findpivot(A, i, j);  // Pick a pivot
  Swap.swap(A, pivotindex, j);               // Stick pivot at end
  // k will be the first position in the right subarray
  int k = partition(A, i, j-1, A[j]);
  Swap.swap(A, k, j);                        // Put pivot in place
  if ((k-i) > 1) quicksort(A, i, k-1);  // Sort left partition
  if ((j-k) > 1) quicksort(A, k+1, j);  // Sort right partition
}


Average: O(n logn), unstable

4. Heap sort: Since the efficiency of quick sort was strongly effected by the structure of the BST, we now want a balanced tree, which can be well-represented by the heap, on which the heap is based.


implementation from[openDSA](https://canvas.vt.edu/courses/111334/assignments/883567?module_item_id=901469)


static void heapsort(Comparable[] A) {
  // The heap constructor invokes the buildheap method
  MaxHeap H = new MaxHeap(A, A.length, A.length);
  for (int i=0; i<A.length; i++)  // Now sort
    H.removemax(); // Removemax places max at end of heap
}


Average:o(n logn), unstable

5. Bin sort: The basic idea of bin is to divide the list into small piles.
implementation from[openDSA](https://canvas.vt.edu/courses/111334/modules/items/901470)


static void binsort(int[] A) {
  List[] B = new LinkedList[MaxKeyValue+1];
  int item;
  for (int i=0; i<=MaxKeyValue; i++)
    B[i] = new LinkedList();
  for (int i=0; i<A.length; i++) B[A[i]].append(A[i]);
  int pos = 0;
  for (int i=0; i<=MaxKeyValue; i++)
    for (B[i].moveToStart(); (item = B[i].getValue()) != -1; B[i].next())
      A[pos++] = item;
}


Average: O(n+k)(from bucket sort) stable

6. Radix Sort
implementation from[openDSA](https://canvas.vt.edu/courses/111334/assignments/883568?module_item_id=901472)



static void radix(Integer[] A, int k, int r) {
  Integer[] B = new Integer[A.length];
  int[] count = new int[r];     // Count[i] stores number of records with digit value i
  int i, j, rtok;

    for (i=0, rtok=1; i<k; i++, rtok*=r) { // For k digits
    for (j=0; j<r; j++) count[j] = 0;    // Initialize count

    // Count the number of records for each bin on this pass
    for (j=0; j<A.length; j++) count[(A[j]/rtok)%r]++;

    // count[j] will be index in B for last slot of bin j.
    // First, reduce count[0] because indexing starts at 0, not 1
    count[0] = count[0] - 1;
    for (j=1; j<r; j++) count[j] = count[j-1] + count[j];

    // Put records into bins, working from bottom of bin
    // Since bins fill from bottom, j counts downwards
    for (j=A.length-1; j>=0; j--) {
      B[count[(A[j]/rtok)%r]] = A[j];
      count[(A[j]/rtok)%r] = count[(A[j]/rtok)%r] - 1;
    }
    for (j=0; j<A.length; j++) A[j] = B[j]; // Copy B back
  }
}

Average: O(nk), stable

### General comparison

The old three sorting algorithms(insertion, bubble, selection) are really time-consuming and should be avoided. However, we observe that among the newest sort algorithm, the radix sort is not that promising as it seems.

A final note about lower bound: There is no comparison-based sorting algorithm that can perform the sort with better time complexity of O(nlogn). [proof](https://canvas.vt.edu/courses/111334/assignments/883570?module_item_id=901476)

