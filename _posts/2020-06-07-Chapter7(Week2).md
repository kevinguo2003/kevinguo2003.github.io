---
layout: post
title: 'Chapter 7 Binary Trees'
date: 2020-06-07
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week2 data-structures trees
---

> Binary Trees

### Definition and background
Trees are widely used to store and manage large collections of data. A binary tree can either be empty or have a node called root with two subtrees.

Depth:the length of path from the root to the current node.
Height:the depth of the deepest node in the tree.
Level:All the nodes in one same depth forms a level.

Complete:The tree must be started at the root then filled by levels from left to right.
Full:each node is either an internal node with exactly two non-empty children or a leaf.

Note:the property of binary tree that a node can be defined whether as an single node or the root of another tree made binary tree naturally related with recursion.

Full Binary Tree Theorem: The number of leaves in a non-empty full binary tree is one more than the number of internal nodes.
Also, the number of empty subtrees in a non-empty binary tree is one more than the number of nodes in the tree.

### Traversals
1. Pre-Order: Visit every node before we visit its children.
![pre-order example](https://github.com/kevinguo2003/kevinguo2003.github.io/blob/master/assets/img/pre-order.png)
2. Post-Ordered: We first visit the children, and only after that we will visit their parent node.
[post-order example](https://github.com/kevinguo2003/kevinguo2003.github.io/blob/master/assets/img/post-order.png)
3. In-Ordered: First visit the left child, then the node, then finally the right child. We know BST can use in-order to print the nodes in increasing order.
[in-order example](https://github.com/kevinguo2003/kevinguo2003.github.io/blob/master/assets/img/in-order.png)
4. Implementation:
[implementation](https://canvas.vt.edu/courses/111334/assignments/883547?module_item_id=901421)
Note that recursion played an important role here helping improving the efficiency.

### Node implementation
We have very detailed example in openDSA:[openDSA](https://canvas.vt.edu/courses/111334/modules/items/901426)

Note: The most common nodes includes two fields pointing to two children. Also we want to implement the value to be comparable so that we can utilize the comparison to implement the tree-related method.

Note: Since node usually stores two pointers to other nodes, binary trees turns to be very space-consuming. However, by eliminating the pointers from leaf nodes in full binary trees.

### Other related trees

Composite-based Expression Tree:[implementation](https://canvas.vt.edu/courses/111334/modules/items/901427)

Dictionary Implementation Using a BST:
we can use BST to implement a dictionary-like database. This brings us an advantage that all the major operations like insert, remove and search can be O(log n) in the average case.
[Example from OpenDSA](https://canvas.vt.edu/courses/111334/modules/items/901427)

Huffman Coding Trees: Sorry I'm having a hard time understanding this, I will post it very quick before Monday ends.


### Heaps and Priority Queues
Priority queues: when elements in queue have their specified property of priority, the queue is called a priority queue.
Heap: A heap is a complete tree whose element was ordered according priority. Also, min heaps and max heaps all have their certain fit case.
[Specification from openDSA](https://canvas.vt.edu/courses/111334/assignments/883555?module_item_id=901441)

