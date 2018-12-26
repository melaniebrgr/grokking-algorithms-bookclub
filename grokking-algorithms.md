# Chapter Summaries

## Chapter 8 - Greedy algorithms

Greedy algorithms are simple. A greedy algorithm finds the optimal solution at each step, called the "local minimum", with the aim that it will lead to the overall best solution, or the "global minimum". For example, a greedy strategy for the **knapsack problem** (p.144) is to find the most expensive item that fits in the knapsack for each turn. Finding the global minimum is not guaranteed, however. In the case of the knapsack problem, several smaller, less expensive items would have added up to more than just taking the most expensive.

While they may not find the global minimum, greedy algorithms can still get close. They can be useful approximations when finding the best solution requires an unreasonable number of steps and would take too long to complete, such as is the case for the **set-covering problem**.

```javascript
// TODO: JS implementation of radio station set-covering problem
```

TODO: NP-complete problems summary

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

---

## Problems

### Knapsack problem

Given a set of items, each with a weight and a value, determine the number of each item to include in a collection (knapsack) so that the total weight is less than or equal to a given limit and the total value is as large as possible. ([wikipedia](https://en.wikipedia.org/wiki/Knapsack_problem))

### Set-covering problem

Given a set of elements, e.g. `[1, 2, 3, 4, 5]` (called the universe) and a collection of sets, e.g. `[[1, 2, 3], [2, 4], [3, 4], [4, 5]]` whose union equals the universe, find the smallest sub-collection of sets whose union equals the universe. ([wikipedia](https://en.wikipedia.org/wiki/Set_cover_problem))
