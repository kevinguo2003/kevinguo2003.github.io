---
layout: post
title: 'Chapter2 and Class Notes'
date: 2020-05-31
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week1 data-strcutures
---

> Eclipse-related topic and Java-debugging

### Command line
1. useful instructions:-h(help), -v(increase output), man command(show help page for the certain command)
2. Java ignores the first word, which is the command, and only pass the parameters the args[] array.
3. In Eclipse, choose"run configuration" and manually enter the arguments to automatically run with the command line.

### Common debugging methods
1. Print: Use the console to display the output and compare with the value we expected
2. Rubber Duck: Carefully examine each line and explain how that line works.
3. Worf Fence debugging: Splitting the whole program and locate which area of code the bug is. Repeating this process to find the bug.
Note: Eclipse provided us with a powerful debugger. It has common functionality like stepinto, stepover, resume, and most importantly, placing breakpoints. Detailed tutorials can be found at [Debugger Tutorial from Eclipse official page](https://www.eclipse.org/community/eclipse_newsletter/2017/june/article1.php)

### JUnit Test
JUnit test are designed to allow the program to run in the specified condition and examine whether the input was the expected value. The test cases should be independent and cover most of the program.\n
In Eclipse, we can find out how many percents of the code was tested by selecting Window-Show View-Other-Java-Coverage.
P.S: Since we're very familiar with the Junit test by practicing in CS2114, I believe we have a decent understood of the Junit test.

> Classnotes

### Program management
There are several important ideas:
1. Start the project early, since there is a strong relationship between start time and final score.
2. Debug early. Write tests right after the function. Also, we should have a clear idea of the design before we start to implement it.
3. Keep the code clean and readable. This will help both in developing and debugging.

### Algorithm Analysis
All the bigO complexity:[cheatsheet](https://www.bigocheatsheet.com/)