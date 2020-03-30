---
layout: post
title:      "Runtime Complexity"
date:       2020-03-29 20:42:21 -0400
permalink:  runtime_complexity
---


### Introduction

While reading through some discussion posts and attempting technical challenges on HackerRank, I came across a topic over and over for which I realized my knowledge has been fairly limited. Although we addressed **runtime complexity** vaguely throughout Flatiron's data science bootcamp, content about the topic was usually restricted to the practicalities of optimzing code to increase the speed of our programs. We learned that neural networks especially have lengthy runtimes given the complexity of hidden layers. Throughout different projects, I encountered pieces of code every now and then, usually loops iterating through dataframes with thousands of rows, that executed with much longer runtimes than expected, and I would have to step away from computer for a bit to let the code finish running. In a HackerRank challenge this week, I approached the challenge ["Picking Numbers"](https://www.hackerrank.com/challenges/picking-numbers/) with the following solution, with too great a runtime complexity to finish executing:

```
from itertools import combinations
def pickingNumbers(a):
    lengths = []
    for r in list(range(1,len(a),1)):
        combs = combinations(a, r)
        for comb in combs:
            if len(list(set(comb)))==1:
                lengths.append(1)
            elif len(list(set(comb)))<=2 and (list(set(comb))[1]-list(set(comb))[0])<=1:
                lengths.append(r)
    return max(lengths)
```

While the code produced correct solutions for the first three test cases, the remaining cases timed out due to the complexility of iterating through every combination of every possible length in our input array. During this process, I realized that I know little about the theoretical underpinnings of runtime complexity, and sought out some additional information about computational complexity.

### What is Runtime Complexity?

Computational complexity for a given algorithm or section of code refers to the length of time (time complexity) and amount of space (space complexity) required in order to execute that code for any input of given size *n*. This concept remains crucial for data scientists when making decisions about what particular algorithms and data structures to utilize, given the expected dimensions of input values or structures. An entire field of data science, computational complexity, revolves around the study of these concepts. Given that our final runtime complexity varies with the size of our input, as well as the specific data structures embedded within our code, "runtime complexity is commonly estimated by counting the number of elementary operations performed by the algorithm, supposing that each elementary operation takes a fixed amount of time to perform."

For each algorithm, we consider three cases of runtime complexity:
* Best-case: As it sounds, this is our fastest or best-case scenario for runtime. For example, if we wanted to find a specific item from a list, if that item is the first in our list, this would be our best-case.
* Average-case: Most commonly utilized, our average-case scenario depends on the range of values in our input.
* Worst-case: This is our slowest, and thus, worst-case, scenario with regards to runtime. In searching our list for a specific item, if that item is at the very end, this would be our worst-case.

### Big-O Notation

When discussing runtime complexity, data scientists utilize the mathematical language of Big-O notation to describe as specifically as possible the length of time required for a given algorithm. Big-O notation is relative and depends on the data structures utilized within the algorithm at hand. It is commonly referred to as "asymptotic notation" as well, and describes the limiting factor in our algorithm when the input size approaches infinity (or in certain cases, a specific value).

With regards to time complexity, we use the following notations:
* O(1) - constant time
* O(log n) - logrithmic time
* O(n) - linear time
* O(n log n) - quasilinear time
* O(n^2) - quadratic time
* O(2^n) - exponential time
* O(n!) - factorial time

As illustrated in the graph of operations vs. elements below, our above list is order from fastest to slowest notation.

![](https://github.com/huntersapienza/Blogging/blob/master/Runtime%20Complexity/Runtime%20Complexity%20Graph.jpeg?raw=true)

**O(1) - Constant Time**

No matter how large the input size, the computational complexity for the algorithm remains constant. For example, when determining if two items are absolutely equal to one another, resulting in a single step that outputs 'True' or 'False.'

**O(log n) - Logrithmic Time**

As the size of the input value increases, the runtime increases exponentially. In logarithmic time, each step of the runtime reduces the size of the data. A common example is a binary search tree, which operates similarly to the halflife of a chemical compound, dividing the data in half each time in search of a particular value.

**O(n) - Linear Time**

As the size of the input value increases, the runtime increases linearly. The algorithm likely must examine each value in the input in order to execute the code. For example, if we wanted to sum all the items of a list, we must iterate over each iterm individually, resulting in linear time complexity.

**O(n log n) - Quasilinear Time**

Combining logrithmic and linear time, quasilinear time complexity occurs when a series of multiple operations within an algorithm posses, at most, logrithmic time complexity. Building on our prior example, if our input is a list of values and each value is subsequently inserted into a binary tree, this would result in quasilinear time complexity.

**O(n^2) - Quadratic Time**

Similar to quasilinear time, quadratic time complexity occurs when a series of multiple operations within an algorithm have linear time complexity.

**O(2^n) - Exponential Time**

Exponential time complexity occurs when each addition to input size results in a doubling of the runtime. The recursive calculation of Fibonacci sequences is a great example of exponential time complexity.

**O(n!) - Factorial Time**

Our final Big-O notation, factorial time, occurs when runtime grows in a factorial nature as the input size increases.
