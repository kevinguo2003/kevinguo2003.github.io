---
layout: post
title: 'Chapter1:Introduction to data structures and algorithms '
date: 2020-05-29
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week1 data-structures
---

> 1.1 Data Structures and Algorithms

### Definition and background
In this course, we mainly focus on a core question to programmer: how to make our algorithms become more sufficient. The reason why we need this is because there is always a limit of computational power as well as time provided to solve a problem. When these certain constraints are applied to our problem-solving process, it's of our essential concern to come up with a good algorithm choice.

### Data Structures
We have learned many data structures including arrays, stack, hashTable or even an integer can be considered as a data structure. All these structures have their unique pros and cons which implies we need to choose which to use according to the real situation since there is hardly a perfect data structure for all the circumstances. When we consider the cost of a data structure, there are mainly three things: the time it needs to solve the problem, the system space(memory space) it needs, and finally the programming effort it needs. We say one structure is more efficient to the problem if it is with the resource constraints and cost less than others.

### Selecting a data structure
Essentially there are three main steps to select an appropriate data structure:
1. Analyze the problem needs and identify what function does the problem requires the data structure to perform.
2. Quantify all the cost and resource constraints for the required operations.
3. Select the best data structure that fits the needs.

This is my first step toward my blog. Hope years after I can still remember my feeling right now.

### Examples
[Examples from OpenDSA](https://canvas.vt.edu/courses/111334/assignments/883515?module_item_id=901327)

> 1.2 Abstract Data Types

### Definition and background
There are several definitions regarding data types:
1. Type: a collection of values with no subparts. Example: Boolean and integer.
2. Composite type(aggregate type, data item): A entity that contains several types. For example, a bank account contains names, addresses, and account balances, etc.
3. The abstract data type(ADT): a specification of one data type in a certain language. In other words, it's a comprehensive representation of one idea of data type and implemented with one certain language. An ADT is usually represented by an interface where the function and general rule are regulated but programmers are free to use any implementation method. For an ADT, the user only needs to know the functions and use them without knowing how the functions work.(Encapsulation)
4. Data structure: simply is the implementation of the ADT. We use method(member function)within a class to implement the ADT, all the methods together became the data structure.

### Logical and Physical form
Logical form: the concept and idea of the data types including its definition, usage, and function.

Physical form: the code that implements the data structure. We need the physical form to achieve the function we want from a certain data structure.
