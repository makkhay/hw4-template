#HW4 Parallel Sorting
#### First-Name Last-Name
TODO - Update your name in this readme.

TODO - Add a badge from travis CI here

## Problem statement:

Create two arrays of size 2<sup>P</sup> (where P is a command-line argument) and store a random integer in each array location of the two arrays. (At each index the two arrays should have the same random integer.)
Divide one of the arrays into 2<sup>N</sup> partitions (where N is another command-line argument) and create
threads to do an insertion sort of each partition of this array (so there will be 2<sup>N</sup> threads overall). Each
thread can calculate which locations of the array it should sort given its thread index (0, 1, ..., 2<sup>N</sup>-1). For example, if N=1 and P=9, then thread 0 should sort array locations [0, 255] and thread 1 should sort array locations [256, 511]. Note that since the threads do not share any data, they do not need to be synchronized, however the main thread does need to wait until the last worker thread completes processing before continuing on to the next stage. After all threads have exited, the main thread should print the integers in order. This should be implemented with a `get_next()` function that returns the next integer in the sorted ordering each time it is called. To implement `get_next()`, declare an array
of 2<sup>N</sup> indices called min_indices and initialize this array with the smallest index in each partition. This array will be used to keep track of the index of the smallest integer in each partition that has not been returned by `get_next()`. Here is pseudocode for `get_next()`:

```
int get_next() {
     int min_index = 0;
     int min = array[min_indices[min_index]];
     for (i = 1; i < # of partitions; i++)
          if (array[min_indices[i]] < min) {
               min_index = i;
               min = array[min_indices[min_index]];
          }
     min_indices[min_index]++;
return min; 
}
```
Note that you will need to add code that determines when a partition is exhausted and must be skipped over.

The main thread should report the length of time required to spawn the threads and wait for them to finish sorting their partitions. Do not include any of the print statements in the timed portions of your program, as these take considerable time themselves relative to the sorting time. After you have finished printing the array in sorted order, do a sequential insertion sort on the large array and report the time taken to do it. (There is no need to print the sorted array after the sequential sort.) Try all combinations of the values 8, 16 and 24 for P and 1, 2 and 3 for N. Discuss the speed-up evident in the times in your writeup. Are your results as expected?

Prepare a short writup as a pdf or into this README. You must also include the necessary design documentation. Your design documentation should include a short description of the assignment and the major design decisions you
made in implementing it.

## Plagiarism
Please do not copy-paste from the internet or from friends. The plagiarism detection system will flag it.

## Note
* There is **no partial credit** for code that does not compile
* It is required that you add your **name** to your readme.
* Make sure your last push is before the deadline. Your last push will be considered as your final submission.
* If you need to be considered for partial grade for any reason(failing tests on travis,etc). Then email the staff before the deadline. Late email requests may not be considered.
* Post questions on Piazza if you have any questions.
* Please contact the course staff if you run into issues. We are here to help you!
