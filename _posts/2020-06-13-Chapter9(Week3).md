---
layout: post
title: 'Chapter 9'
date: 2020-06-07
author: Xiao Guo
cover: '/assets/img/MountAl.jpg'
tags: CS3114 week3 data-structures
---

> File Processing

### Definition and background
Often, we need to access certain file from certain memory. To reach the maximum efficiency, we're likely to store the information we need in the memory rather than the disk. However, it's not always applicable to store all the file in our memory, which leads us the topic we wanna discurss: the best way to access file, no matter where it is stored. In this chapter, we will focus on the concept of buffer pool, which is the basic of a cache system.

### Primary versus Secondary Storage
1. Primary storage: RAM
2. Secondary storage: Disk drives, solid state drives, or removable USB drives.
3. The advantage of secondary storage: It's much more chaper than the RAM. And the most importantly, the disk drive is persistent, which means the file inside will not disappear when the power is shutdown.
4. Minimize the disk access: with all these advantage, there is a fatal flaw of accessing file from a disk: it's too slow. The factor of how much it is faster to access the RAM comparing to disk is ranging from 100000 to 1000000. To avoid this, we need a better structure to store some information we want in the disk into the RAM, which is called caching.

### Disk Drives
The disk drive is called direct-access memory, which means the speed to access one file is always a certain amount no matter in what situation. This leads to a fact that there is always some file that can be accessed faster than others.

Structures: 
The disk is cmposed one or more round platters which stack on each other and connected with a certral spindle. While they spin, there is a I/O head which can read or write into the disk. (Note:this head doesn't really touch the platter, but keep a very short distance from it). Also, the track is divided into sectors which all store the same amount of data.

When reading the data, there is mainly three separate steps:
1. seek: the I/O head moves until it is positioned over the track where the data was stored.
2. The sector that contains the data will rotate to the I/O head.
3. the actual transfer of data.

Note:due to design reason, the cost to seek is always the biggest concern.

### Buffering Pool
1. the locality of referene: in practical, the most disk requests are closed the location of the previous request, which makes the chance of hitting the cache to be higher.
2. One important reason why new disk is quicker than the old one is because the innovation of cache system.
3. The process of using buffers as an intermediary between a user and the disk file is called buffering the file. The collection of all these buffers are called the buffering pool. The main goal of this pool is to decrease the amount of file that we need to access from the disk.

### Replacement Stretegy
1. We nned to replace some information when the buffering pool is full, which requires us to come up with a good stretegy for this.
2. FIFO: The information that we want to replace is which exists the longest. However, sometimes certain information will be used over and over agian which lead us to consider the frequency of one information.
3. LFU and LRU: They all count the frequency the we used certain information. However, the LRU can better handling the old information as well as the counting process, which made LRU one of the most used stretegy.


Note: some useful Java method listed in OpenDSA:
1. RandomAccessFile(String name, String mode): Class constructor, opens a disk file for processing.
2. read(byte[] b): Read some bytes from the current position in the file. The current position moves forward as the bytes are read.
3. write(byte[] b): Write some bytes at the current position in the file (overwriting the bytes already at that position). The current position moves forward as the bytes are written.
4. seek(long pos): Move the current position in the file to pos. This allows bytes at arbitrary places within the file to be read or written.
5. close(): Close a file at the end of processing.

### External Sorting
To maximize the efficiency of I/O, we want to sort the external file in a certain kind of order. However, it's not possible to use the internal sort that we are familiar with since the file size is often too large. 

A good summary from [openDSA](https://canvas.vt.edu/courses/111334/assignments/883572?module_item_id=901485)

In summary, a good external sorting algorithm will seek to do the following:

1. Make the initial runs as long as possible.
2. At all stages, overlap input, processing, and output as much as possible.
3. Use as much working memory as possible. Applying more memory usually speeds processing. In fact, more memory will have a greater effect than a faster disk. 4. A faster CPU is unlikely to yield much improvement in running time for external sorting, because disk I/O speed is the limiting factor.
5. If possible, use additional disk drives for more overlapping of processing with I/O, and to allow for sequential file processing.