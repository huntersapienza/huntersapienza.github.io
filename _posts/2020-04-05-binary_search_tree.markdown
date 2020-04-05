---
layout: post
title:      "Binary Search Tree"
date:       2020-04-05 16:31:21 +0000
permalink:  binary_search_tree
---


### Introduction

When I was writing my blog post on runtime complexity last week, I utilized binary search tree as a key example for logrithmic runtime complexity, expressed with the notation O(log n). While I briefly read an overview regarding the uses of binary search trees, I once again found that this was I concept I knew little about. However, another HackerRank challenge just days later gave me the opportunity to dive deeper into binary search trees and discover what they're all about. I certainly did not expect the challenge [Climbing the Leaderboard](https://www.hackerrank.com/challenges/climbing-the-leaderboard/problem), with a medium difficulty level, to provide as great a challenge as it ultimately became.

My first solution (below) passed the intial test cases, but when I submitted the solution, it failed four of the final cases due to timeout errors.

```
def climbingLeaderboard(scores, alice):
    ranks = []
    for a in alice:
        count = 1
        for score in list(set(scores)):
            if score>a:
                count +=1
        ranks.append(count)
    return ranks
```

So I tried again...

```
def climbingLeaderboard(scores, alice):
    ranks = []
    for a in alice: 
        ranks.append(sum(1 for i in set(scores) if i>a)+1)
    return ranks
```

...and again...

```
def climbingLeaderboard(scores, alice):
    ranks = []
    for a in alice:
        ranks.append(len([i for i in set(scores) if i>a])+1)
    return ranks
```

...and again.

```
def climbingLeaderboard(scores, alice):
    ranks = []
    for a in alice:
        ranks.append(reduce(lambda sum, j: sum +(1 if j>a else 0), set(scores), 0)+1)
    return ranks
```

All of the above situations provided the same result, passing the initial test cases but failing others due to timeout errors. However, this is unsurprising, given what I learned about runtime complexity last week. Each of these above solutions, while slightly different, produced code with similar, if not the same runtime complexity, iterating through each element of the "scores" arrary, for each new score in our "alice" array. Doing so results in a quadratic time complexity, much too great to be executed within the given time constraints. I clearly need a new strategy. Ultimately, this led me to binary search trees...

### Binary Search Tree

Given an ordered set of data, in this case a list, the binary search tree allows us to more quickly sort through data to find a given value. When executing a binary search tree, the algorithm searches the tree from root to leaf, following a path organized with all values to the left of a given node smaller than the value of that node, and subsequently, all values to the right of that node larger than the value of the node. Thus, on average, we can reduce the search time to half given the structure of the tree, and the time complexity becomes logrithmic instead of linear, greatly improving the efficiency of our algorithm. Below, an example of a binary search tree displays this structure:

![Binary Search Tree example](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary_search_tree.svg/800px-Binary_search_tree.svg.png)

Typically, binary search trees are utilized throughout programming applications to find specific, pre-existing elements within an array or dictionary. The basic code for a binary search tree is displayed below. Essentially, it recursively searches the tree, with each subsequent algorithm depending on the results of the prior. Each application of the binary search algorithm shrinks the size of the input array to half the size of the prior search, narrowing the index values at hand until reaching the desired value.

```
# Returns index of x in arr if present, else -1 
def binarySearch (arr, l, r, x): 
  
    # Check base case 
    if r >= l: 
  
        mid = l + (r - l) // 2
  
        # If element is present at the middle itself 
        if arr[mid] == x: 
            return mid 
          
        # If element is smaller than mid, then it can only be present in left subarray 
        elif arr[mid] > x: 
            return binarySearch(arr, l, mid-1, x) 
  
        # Else the element can only be present in right subarray 
        else: 
            return binarySearch(arr, mid + 1, r, x) 
  
    else: 
        # Element is not present in the array 
        return -1
```

When running this code, we start with the following arguments, representing the array to be searched, the two endpoint values, and the desired value. The result will be the index value of x.

```
result = binarySearch(arr, 0, len(arr)-1, x) 
```

The image below visualizes this process in the context of searching an ordered list:

![Finding a Value via Binary Search](https://github.com/huntersapienza/Blogging/blob/master/Binary%20Search%20Tree/Binary-Search.png?raw=true)

### Climbing the Leaderboard Solution

Now, with a better understanding of the basic operations of binary search tree algorithms, I jumped back over to the HackerRank challenge at hand. Given what I had learned about binary search trees, I knew that implementing this algorithm would reduce the runtime complexity of my code, hopefully enough to pass the rest of the test cases. However, I needed to modify the code, as that in the previous section searches for *existing* values, and I knew that the new scores might not perfectly match those in the preexisting leaderboard. Below is the modified code I produced, with if-statements added for the cases when:
1. the item is present (identical to) one of the endpoints
2. the item might be valued such that it becomes the new endpoint (either first or last place)
3. the item does not exist in the list, but fits between two existing items

```
# Returns index of x in arr, else -1 if error occurs
def binarySearch (arr, l, r, x): 
  
    # Check base case 
    if r >= l: 
  
        mid = l + (r - l) // 2
  
        # If item is present at the middle or an endpoint itself 
        if arr[mid] == x: 
            return mid-1
        elif arr[r] == x:
            return r+1
        elif arr[l]== x:
            return l+1
        
        # If item does not exist in the list, but fits between two existing items
        elif arr[r]>x:
            return len(arr)+1
        elif arr[l]<x:
            return 1
        elif arr[mid]>x and arr[mid+1]<x:
            return mid+2
          
        # If item is smaller than mid, then it can only be present in left subarray 
        elif arr[mid] > x: 
            return binarySearch(arr, mid+1, r, x) 
  
        # Else the item can only be present in right subarray 
        else: 
            return binarySearch(arr, l, mid-1, x) 
  
    else: 
        # Error occurs when placing item within list 
        return -1 
```

With this modified binary search tree algorithm at hand, I placed the method within my climbingLeaderboard method below, iterating through each of Alice's scores to find it's place in the leaderboard.

```
def climbingLeaderboard(scores, alice):
    ranks = []
    set_scores = list(set(scores))
    set_scores.sort(reverse=True)
    for a in alice:
        result = binarySearch(set_scores, 0 , len(set_scores)-1, a)
        ranks.append(result)
    return ranks
```

Ultimately, this code reduced the runtime complexity enough to pass all the test cases become approved as a verified solution! While the challenge presented much more difficulty than I originally anticipated, it offered the opporutnity to learn more about a previously unexplored concept, and led me to a correct solution, so I can't complain about that :) As I continue to prepare for technical interviews, I am eager to continue learning and developing my knowledge about data science. The learning truly never stops.
