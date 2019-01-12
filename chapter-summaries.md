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

Big O notation is used to communicate the run time of an algorithm, which is useful to decide which algorithm should be used. (Different algorithms "grow" at different rates). Common run times: `O(logn)` or log time < `O(n)` or linear time < `O(nLogn)` < `O(n^2)` < `O(n!)`.

## Chapter 2 - Selection sort

Computer memory can be thought of as a chest of drawers. Arrays and linked lists are two ways to organize information into those drawers. While arrays store information contiguously in memory, linked-lists place items anywhere. For linked-lists each item stores the address to the next item in the list. This makes insertions and deletions faster for linked lists (`O(1)` vs. `O(n)`), but reading faster for arrays (`O(1)` vs. `O(n)`).

Another common task is sorting. For example, a collection needs to be sorted before it binary search can be used, for example. One sorting algorithm is **selection sort**. Selection sort runs through the entire collection, finds the item that should be first, and places it first in new array. It is not very efficient, `O(n^2)`.

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

## Chapter 4 - Quicksort

Divide and conquer (D&C) is a recursive approach to solving problems. The goal is to be able to sequentially break a problem into smaller and smaller pieces until it is no longer divisible - the base case - and then zip up the smaller solutions into a larger solution to the larger problem. D&C has two steps:

1. identify the base case - this is the simplest case
2. find a way to break down the problem until the base case is reached

Examples of D&C application are **Euclid's** algorithm, which can be used to find the largest squares that can evenly divide a rectangle, and **quicksort**. In quicksort a list of numbers is divided at a pivot, then the sub-arrays are sorted above and below the pivot. The process is repeated with the sub-arrays. Quicksort grows in `O(nlogn)`, while selection sort grows in `O(n^2)`. It's coefficient is also slightly faster than **merge sort**, but Sean May notes that merge sort is safer.

## Chapter 5 - Hash tables

Hash functions are functions that map strings to an index to enable the `O(1)` lookup of the value in an array-like data structure. There are three requirements for a hash function:

- the same input string should always returns the same index
- different input strings should map to different indexes (avoid collisions!)
- a hash function should never return indexes larger than are in the array

A hash function + array = a hash table (aka hash map, maps, dictionaries, objects). While arrays and linked-lists "map straight to memory", hash tables have extra logic to them. Hash tables are useful for

- lookups, e.g. DNS resolution
- checking for duplicates
- caching data

A good has function distributes values evenly within an array, which is kept at a low load factor. However, it's hard to write a hash functions that maps different strings to different indexes perfectly. A collision occurs when a hash function assigns data to the same "slot". If data would be assigned to the same slot, a linked list is used to store values at that index.

## Chapter 6 - Breadth-first search

A graph models a set of relationships between items. Items comprise the nodes of the graph and the lines or arrows between the nodes are the edges.

```javascript
// Example implementation of a graph
const you = { name: "you", mangoSeller: false };
const bob = { name: "bob", mangoSeller: true };
const alice = { name: "alice", mangoSeller: true };
const claire = { name: "claire", mangoSeller: true };
const anuj = { name: "anuj", mangoSeller: true };

const graph = {
  you: [alice, bob, claire],
  bob: [anuj, alice],
  alice: [anuj],
  claire: [bob, alice],
  anuj: []
};
```

If a problem can be modelled as a graph, a **breadth-first search** algorithm can be used to find 1) if a path exists, or 2) the shortest-path to the solution. A breadth-first search radiates out from a starting point: first-degree connections are checked before second-degree connections a.k.a first-degree connections are enqueued before second degreed connections. Nb. The definition of a queue is that is is FIFO. The definition of a stack is that it is LIFO.

```javascript
// Imperative breadth-first search algorithm implementation
const breadthFirstSearch = person => {
  let queue = [person];
  const searched = [];

  while (queue.length > 0) {
    const person = queue.shift();
    const hasBeenSearched = Boolean(
      searched.find(searched => searched.name === person.name)
    );

    if (!hasBeenSearched) {
      if (person.mangoSeller === true) {
        return person;
      } else {
        searched.push(person);
        graph[person.name].forEach(neighbour => queue.push(neighbour));
      }
    }
  }
  return false;
};
```

### Special types of graphs:

A graph that orders items in order of their dependencies is a special type of graph for which a **topological sort** algorithm could be used to generate a list of items ordered by their dependencies. A tree is a special type of graph where no child nodes ever point back to parent nodes.

## Chapter 7 - Dijkstra's algorithm

TODO: summary

## Chapter 8 - Greedy algorithms

Greedy algorithms are simple. A greedy algorithm finds the optimal solution at each step, called the "local maximum", with the aim that it will lead to the overall best solution, or the "global maximum". For example, a greedy strategy for the **knapsack** problem is to find the most expensive item that fits in the knapsack for each turn. Finding the global minimum is not guaranteed, however. In the case of the knapsack problem, several smaller, less expensive items would have added up to more than just taking the most expensive.

While they may not find the global maximum, greedy algorithms can get close quite quickly. For this reason, they offer useful approximations for when finding the best solution requires an unreasonable number of steps and would take too long to complete, such as is the case for the **set-covering** problem, and the **travelling salesmen** problem.

```javascript
// TODO: JS implementation of a greedy radio station set-covering problem
```

When an algorithm would take an unreasonable amount of time to complete, the problem may be a NP-complete problem. In fact, non-deterministic polynomial time (NP) complete problems are characterized by the fact that time required to solve the problem growing rapidly with size. They have no known fast solutions. A problem may be NP-complete when it

- slows down rapidly as the size of the problem grows (polynomial time)
- requires the calculation of every possible version
- can be restated in terms of a known NP-complete problem

Examples of known NP-complete problems include the **knapsack** problem, the **travelling salesmen** problem, the **hamiltonian path** problem, the **subset sum** problem, **graph coloring** problem.

## Chapter 9 - Dynamic programming

Approximation algorithms may or may not find the correct solution and come close, but dynamic programming _can_ be used to find optimal solutions. It entails breaking a problem into a collection of simpler subproblems, solving those, and saving the results in a grid-like data-structure. The solutions for the subproblems are then used to solve the overall problem. The goal of dynamic programming is usually to optimize an outcome given a constraint, a.k.a. a "decision" problem. For example, my knapsack can hold 6 lbs., what should I steal to make the money? In the case of the **knapsack** problem, the goal is to optimize the total value of items in a knapsack given their combined weight is under a certain amount. In the **longest common substring** problem, the goal is to find the longest matching string of characters, (the constraint is that they must be contiguous?).

The 5 characteristics of dynamic programming are

1. the problem can be broken into independent subproblems
2. the solution involves a grid
3. each grid-cell is a subproblem
4. each subproblem is discrete - it can't depend on another subproblem
5. you'll need to think real hard about the formula for filling in the grid cells

## Chapter 10 - K-nearest neighbours

TODO: summary

## Chapter 11 - Where to go next

TODO: summary
