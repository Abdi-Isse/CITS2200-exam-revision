# Sorting
Topics: 
- Insertion sort 
- Quicksort 
- Mergesort
- Heapsort


# Insertion sort
[Insertion sort in 2 minutes](https://www.youtube.com/watch?v=JU767SDMDvA)

Logic: 
1. Work left to right 
2. Examine each item and compare it to items on its left 
3. Insert the item in the correct position in the array 

Time complexity: O(n^2)
- Possibly need to swap every item which leads to O(n^2) 

# Mergesort
[Merge sort in 3 minutes](https://www.youtube.com/watch?v=4VqmGXwpLqc)
Merge sort is usually done recursively. Divide an conquer. 
Logic: 
1. An unsorted array is divided into smaller and smaller arrays recursively until we get single element arrays. This takes O(log n) time as the size of the array is reduced to half each time. 
2. Then the arrays are merged into larger and larger sorted arrays. Merging is O(n) at each level. 
Time complexity: 
- The overall complexity is O(n log n).
  - Merging is O(n) per level
  - there are O(log n) levels. 


# QuickSort
[Quick sort in 4 minutes](https://www.youtube.com/watch?v=Hoixgm4-P4M)

QuickSort is recursive. Uses a Pivot. 

A pivot is: 
1. Correct position in final, sorted array 
2. Items to the left are smaller 
3. Items to the right are larger

Choose a pivot that is the middle item. 
Time complexity: O(n^2). 
Average case: O(n log n) if a pivot is chosen properly. 


# Heapsort
[Heap sort in 4 minutes](https://www.youtube.com/watch?v=2DmK_H7IdTo)

Heap: ordered binary tree.
Max heap: a heap where parent > child 
Function:
- BuildMaxHeap: creates a max heap from unsorted array 
- Heapify: similar to BuildMaxHeap, but assumes that part of the array is already sorted 

Explanation: 
Heapsort uses buildMaxHeap and Heapify to sort an array. 
1. First a heap is created from an array by using BuildMaxHeap. 
2. Next, we take the top item from the heap and swap the position with the end of the unsorted portion of the array. This will also swap the position in the heap. We remove the max item from the heap. 
3. Next, we call heapify to sort the array again so that the max item appears at the top of the heap. 
4. We repeat step 2 and 3 until the array is sorted. 

Time Complexity:
- O(n log n) 
  - Build max heap : O(n)
  - Heapify: O(log n)