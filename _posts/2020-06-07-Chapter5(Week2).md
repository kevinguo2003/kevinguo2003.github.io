---
layout: post
title: 'Chapter 5 Linear Structures'
date: 2020-06-07
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week2 data-structures 
---

> Linear Structures

### Definition and background
This chapter will focus on simple linear data structures including list, stack, and queue. When we don't have intense demand for searching or ordered data storage, these kinds of list-like structures are good enough to handle the problem with less effort and complexity required.

### Key Ideas
1. Ordered: This means every element in the list has a clear position, which is not necessarily ordered according to a certain rule.
2. A list has head, tail, and size.

For the array-based list:
[implementation](https://canvas.vt.edu/courses/111334/assignments/883534?module_item_id=901388)
We shall have insert(append) and remove method.

For the linked list:
[implementation](https://canvas.vt.edu/courses/111334/assignments/883535?module_item_id=901390)
The linked list will allocate memory dynamically, which is allocates memory for new elements as needed. The whole concept of "linked" is achieved by nodes. The node object usually has two fields links to its left and right node, which make all the nodes interconnected with two nodes near each individual node. To resolve the problem of special cases, we introduce an additional head node to be the first node of the list. Its value is ignored though its existence can help us better arrange the list.

### Comparison between two kinds of list
The biggest con of an array-based list is that its size was pre-determined which made this data structure wasted a lot of space when dealing with a small amount of element. However, if we choose the linked list, the space usage of these links will become too large if we're dealing with the small-size element. So we need to decide a mathematical balance point between these two lists: the break-even point. 
Equation n>DE/(P+E) (specification:[openDSA]https://canvas.vt.edu/courses/111334/assignments/883536?module_item_id=901392)

Note: Doubly Linked Lists
This kind of list has fields like curr, head, and tail. Every two near nodes are interconnected. Also, we need to consider whether to enforce homogeneity or not.

### Stacks
Stacks have long been used to store data. It simply follows a rule called "LIFO"(Last in, first out). All the data manipulation happens at one and only one end of the list.
Basic operation:
clear, push, pop, length

Linked stacks:
[implementation](https://canvas.vt.edu/courses/111334/modules/items/901400)
Comparison:
All operations for both array-based stacks and linked stacks cost a constant time, which makes these two kinds of implementation kind of equally efficient.

Free list:
[implementation](https://canvas.vt.edu/courses/111334/assignments/883539?module_item_id=901399)
Search:(GeeksforGeeks.org)

### Queues
Unlike the stack, the queue follows another kind of order rule: "FIFO"(First-in, first-out). The basic operation includes clear, enqueue, dequeue. There are array-based queue, circular queue, and linked queue.
[implementation](https://canvas.vt.edu/courses/111334/assignments/883540?module_item_id=901403)
