# Chapter Summaries

## Chapter 8 - Greedy algorithms

Greedy algorithms are simple. A greedy algorithm finds the optimal solution at each step, called the "local minimum", with the aim that it will lead to the overall best solution, or the "global minimum". For example, a greedy strategy for the **knapsack** is to find the most expensive item that fits in the knapsack for each turn. Finding the global minimum is not guaranteed, however. In the case of the knapsack problem, several smaller, less expensive items would have added up to more than just taking the most expensive.

While they may not find the global minimum, greedy algorithms can get close. For this reason, they offer useful approximations for when finding the best solution requires an unreasonable number of steps and would take too long to complete, such as is the case for the **set-covering** problem, and the **travelling salesmen** problem.

```javascript
// TODO: JS implementation of a greedy radio station set-covering problem
```

When an algorithm would take an unreasonable amount of time to complete, the problem may be a NP-complete problem. In fact, nondeterministic polynomial time (NP) complete problems are characterized by time required to solve the problem growing rapidly with size. They have no known fast solutions. A problem may be NP-complete when it

- slows down rapidly as the size of the problem grows
- requires the calculation of every possible version
- can be restated in terms of a known NP-complete problem

Examples of known NP-complete problems include the **knapsack** problem, the **travelling salesmen** problem, the **hamiltonian path** problem, the **subset sum** problem, **graph coloring** problem.

###### authors: [melanie]

## Chapter 9 - Dynamic programming

TODO: summary

###### authors:

## Chapter 10 - K-nearest neighbours

TODO: summary

###### authors:

## Chapter 11 - Where to go next

TODO: summary

###### authors:
