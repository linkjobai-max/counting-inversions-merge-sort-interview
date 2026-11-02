# Counting Inversions with Merge Sort: A Classic Divide and Conquer Interview Question

An inversion is a pair of indices i < j where a[i] > a[j]. Counting them by checking every pair is O(n^2). The interview question is to do better, and the standard answer piggybacks on merge sort for O(n log n).

Split the array in half, recursively sort and count inversions in each half, then count the inversions that cross the middle while merging. During the merge, when an element from the right half is placed before remaining elements of the left half, every one of those remaining left elements forms an inversion with it. Add (mid - i + 1) to the count at that moment.

Why this works: both halves are sorted during the merge, so if left[i] is greater than right[j], then every element after left[i] in the left half is also greater than right[j]. You count a whole block in one step instead of pair by pair.

Watch for equal elements: use <= when taking from the left so equal values are not counted as inversions. Use a 64-bit counter, since the count can reach about n^2/2.

Related problems use the same idea: Count of Smaller Numbers After Self, Reverse Pairs (a[i] > 2*a[j], counted in a separate pass before merging), and measuring how far an array is from sorted. A Fenwick tree over compressed values is an alternative worth mentioning.

Interview tips: say the brute force first, then explain that the cross-half pairs are the only hard part, and that sorting the halves is what makes them countable in linear time.

Disclosure: I work on Linkjob AI. If you want to rehearse problems like this with live hints, [Linkjob AI](https://www.linkjob.ai/) can help you practice explaining your approach.
