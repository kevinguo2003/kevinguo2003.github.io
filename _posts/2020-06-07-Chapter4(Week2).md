---
layout: post
title: 'Chapter 4 Algorithm Analysis'
date: 2020-06-07
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week2 data-structures
---

> Analyze the algorithms

### Background
When we solving real-life problems, it's very often that we need to consider the efficiency in order to assure we have best utilized the limited resource we have. In this chapter we will learn a very basic but important tool: asymptotic algorithm analysis. This method focus on estimating the resource consumption of one certain algorithm. 
Key ideas:
1. growth rate, the rate at which the cost of the algorithm increases as the size of its input increases.
2. we have upper bound and lower bound for each of growth rates.
3. There is difference between the cost of an algorithm and an problem.

### Key ideas of problems, algorithms, programs
1. The reason why we want to know more different algorithms is because the situation varies which will make each of the algorithms to have it's best-fit situation.(For example, sorting)
2. Definition of some process to be called as an algorithm: correct, a series of concrete steps, no ambiguity, finite number of steps, and finally it must be terminated(no infinite loops)

### Comparing algorithms
Firstly, we need to be clear that comparing two algorithms by implementing them each and run is not practical(programming effort, unfair test cases, both out of budget, etc). The best way to estimate the cost of one algorithm is to asymptotic algorithm analysis. To do that, we want to analyze starts from basic operations.

General rule of growth rate comparison:
1. look at the n, especially when it's at exponential position.
2. ignore the constant multiplier
3. loglogn grows slower than log^2n

Note: In real-life situation, we usually need to consider the worst case of  time cost of a algorithm. The characteristics of data distribution sometimes plays an important role here because when we know the distribution well, we can then hope to focus on the average case.

Another note on computer: the higher growth rate a algorithm has, the less improvement can be made with the same increase of computer speed. This applies especially to those non-linear time complexity.

### Upper bound, lower bound
The upper bound is not equal to the worst case, they are the mathematical upper bound for the time complexity of the algorithm in each situation. So there could be 3 upper bounds for each case including best, worst and average.

### Calculating the running time
1. basic operation like assignment and arithmetic operation are O(1). 
2. for nested for loops, it can be n^a.

Final note regards bounds:
The upper bound indicates the best we can do. The lower bound tell us how much we have to do to satisfy the requirement. 

### Common Misunderstandings
1. confusion with bounds and cases.
2. We can't directly relate the input size with the cases situation.

## Space Bounds
We need to make tradeoff between space complexity and time complexity. Look up table, for example, shows how the increase of space needed can reduce time cost.

