---
layout: post
title:      "Technical Interview Coding Challenge Experience"
date:       2020-05-02 11:55:03 -0400
permalink:  technical_interview_coding_challenge_experience
---


As we get closer to our move date from NYC to Los Angeles (less than six weeks now eek!), and amid the current public health situation, I feel really fortunate to get responses to some of the applications I have submitted to companies in the area. It's been a stressful week of putting myself out there and hoping I can convince employers that I'm the right fit for their role - I'd like to add that everyone I've had the privilege of speaking to has been truly wonderful, and made the experience a bit less stressful through their words of wisdom and willingness to get to know me better.

That being said, I would love to share one really positive experience that I had this week: my first technical interview code challenge! Although I had a mock technical interview a couple months back, have been honing my skills on HackerRank regularly, and have submitted take-home code challenges for some companies, this was the first on-the-spot challenge I have had to solve. Needless to say, I was a bit nervous that something might go wrong. *What if I couldn't figure out the particular data structures I needed to use? What if my syntax was all off? What if the interview ended without me able to reach a solution?* I'd built up this experience so much in my mind prior to the interview, and had truly mapped out every possible outcome (did I mention I have a tendency to overthink things?...).

However, when it came time for the interview, I truly had a blast! Although it was stressful, and certainly felt like a timecrunch, all these emotions reminded me exactly why I decided to pursuing data science. The feeling of the wheels churning in your mind. The thrill of sorting through different methods to reach a solution. The excitement you feel as you fit together one more piece of the puzzle. And the absolute relief you feel when you finally obtain that highly desired output: *"PASS!"* Data science gives me the opportunity to use logic and problem solving skills in a way that feels absent in my current teaching role. I'm so thrilled to get back into doing that hard, brain-melting work myself, and to collaborate with others on tough, data-driven problems.

Furthermore, despite some of the obstacles I faced during the challenge (whether my syntax was indeed correct, or when I misinterpreted the format of the input data), my interviewer was so patient with me and helped me a few times along the way. Though of course he already had the solution in mind, it was so exciting to be able to talk through the code with another person and feel as if we were collaborating to reach that final method that would pass. Given that I completed Flatiron's data science bootcamp program on the self-paced track, I've had few opportunities to talk about coding and data science with other people. Few people in my current teaching role have experience with the tech industry, and thus, I've really been craving opportunities to problem solve with others over coding problems.

Ultimately, though the experience was challenging and reminded me that I still have so much to learn in my first technical role, the thrill of that challenge reminded me of all the reasons that I'm so excited to enter the tech world and work in a data-driven environment. Although I do not know the outcome of any of my interviews thus far, each one has better prepared me for whatever steps may come next in my journey, and I'm so eager to see where they might take me.

### Code Challenge

Below is the code challenge presented to me in the interview and the final solution I reached:

*Given a "needle" in the form of three consecutive integers and a "haystack" comprised of many rows of random integers, if the needle exists within the haystack, output the row and column (as a tuple) of the haystack where the first digit of the needle is located.*

*For example:*

*Haystack*
```
1122344456
6678899990
0112334567
8891111233
3234556789
9011344445
```

*Needle*
```
66788
01123
88911
```

```
* * * * * * * * * *
66788 * * * * *
01123 * * * * *
88911 * * * * *
* * * * * * * * * *
* * * * * * * * * *
```

*The needle is located starting at  row 1, column 0*

**Solution**

```
def seeker(haystack, needle):
    for i, value in enumerate(haystack):
        for j, integer in enumerate(value):
            if haystack[i][j:j+len(needle[0])]==needle[0]:
                if haystack[i+1][j:j+len(needle[1])]==needle[1]:
                    if haystack[i+2][j:j+len(needle[2])]==needle[2]:
                        return (i,j)
```

This solution passes for needles comprised of three integers (satisfying the problem given during the code challenge!). However, after the interview, I played around with making a method for needles of any length. I ultimately produced the solution below:

```
def seeker(haystack, needle):
    for i in list(range(0,len(haystack))):
        for j in list(range(0,len(haystack[0]))):
            for x in list(range(0,len(needle))):
                if haystack[i+x][j:j+len(needle[x])]!=needle[x]:
                    break
                else:
                    return (i,j)
```
