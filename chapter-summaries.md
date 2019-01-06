[comment]: Links:
[melanie]: https://github.com/melaniebrgr
[stephanie]: https://github.com/stephanie56
[nick]: https://github.com/NicholasGWK
[stefan]: https://github.com/stefannew
[meltem]: https://github.com/turquoisemelon
[sarah]: https://github.com/srhboo
[jocelyn]: https://github.com/jocelynjeffrey
[shaun]: https://github.com/ShaunLloyd
[sean]: https://github.com/seanmay

# Chapter Summaries

## Chapter 1 - Introduction to algorithms

An algorithm is a set of instructions that accomplish a task. A common task is searching. A collection can be searched one at a time, or a **binary search** O(log2n) algorithm can be used on a sorted collection. Each step the collection is halved and the half the target value is in is retained.

```javascript
// Recursive binary search algorithm
const binarySearch = (arr, item) => {
  const searchRange = (low, high) => {
    const mid = Math.round((high + low) / 2);

    if (arr[mid] === item) return mid;
    if (low === high) return -1;
    return item < arr[mid]
      ? searchRange(low, mid - 1) // search bottom half
      : searchRange(mid + 1, high); // search top half
  };

  return searchRange(0, arr.length - 1);
};
```

Big O notation is used to communicate the run time of an algorithm, which is useful to decide which algorithm should be used. (Different algorithms "grow" at different rates). Common run times: O(logn) or log time < O(n) or linear time < O(nLogn) < O(n^2) < O(n!).

## Chapter 2 - Selection sort

Computer memory can be thought of as a chest of drawers. Arrays and linked lists are two ways to organize information into those drawers. While arrays store information contiguously in memory, linked-lists place items anywhere. For linked-lists each item stores the address to the next item in the list. This makes insertions and deletions faster for linked lists (O(1) vs. O(n)), but reading faster for arrays (O(1) vs. O(n)).

Another common task is sorting. For example, a collection needs to be sorted before it binary search can be used, for example. One sorting algorithm is **selection sort**. Selection sort runs through the entire collection, finds the item that should be first, and places it first in new array. It is not very efficient, O(n^2).

```javascript
// Recursive selection sort algorithm
const selectionSort = array => {
  let sortedArray = [];

  const findSmallest = array => {
    const init = { index: 0, value: array[0] };
    const smallest = array.reduce(
      (prev, curr, i) => (curr < prev.value ? { index: i, value: curr } : prev),
      init
    );
    sortedArray.push(smallest.value);
    return array.length > 1
      ? findSmallest([
          ...array.slice(0, smallest.index),
          ...array.slice(smallest.index + 1)
        ])
      : sortedArray;
  };

  return findSmallest(array);
};
```

## Chapter 3 - Recursion

TODO: summary

## Chapter 4 - Quick sort

TODO: summary

## Chapter 5 - Hash tables

TODO: summary

## Chapter 6 - Breadth-first search

TODO: summary

## Chapter 7 - Dijkstra's algorithm

TODO: summary

## Chapter 8 - Greedy algorithms

Greedy algorithms are simple. A greedy algorithm finds the optimal solution at each step, called the "local minimum", with the aim that it will lead to the overall best solution, or the "global minimum". For example, a greedy strategy for the **knapsack** problem is to find the most expensive item that fits in the knapsack for each turn. Finding the global minimum is not guaranteed, however. In the case of the knapsack problem, several smaller, less expensive items would have added up to more than just taking the most expensive.

While they may not find the global minimum, greedy algorithms can get close. For this reason, they offer useful approximations for when finding the best solution requires an unreasonable number of steps and would take too long to complete, such as is the case for the **set-covering** problem, and the **travelling salesmen** problem.

```javascript
// TODO: JS implementation of a greedy radio station set-covering problem
```

When an algorithm would take an unreasonable amount of time to complete, the problem may be a NP-complete problem. In fact, nondeterministic polynomial time (NP) complete problems are characterized by time required to solve the problem growing rapidly with size. They have no known fast solutions. A problem may be NP-complete when it

- slows down rapidly as the size of the problem grows (polynomial time)
- requires the calculation of every possible version
- can be restated in terms of a known NP-complete problem

Examples of known NP-complete problems include the **knapsack** problem, the **travelling salesmen** problem, the **hamiltonian path** problem, the **subset sum** problem, **graph coloring** problem.

###### authors: [melanie]

## Chapter 9 - Dynamic programming

While approximation algorithms can come close, dynamic programming can be used to find an optimal solution.

###### authors:

## Chapter 10 - K-nearest neighbours

TODO: summary

###### authors:

## Chapter 11 - Where to go next

TODO: summary

###### authors:
