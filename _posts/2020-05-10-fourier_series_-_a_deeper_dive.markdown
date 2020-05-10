---
layout: post
title:      "Fourier Series - A Deeper Dive"
date:       2020-05-10 19:08:58 +0000
permalink:  fourier_series_-_a_deeper_dive
---


Building off the content of my blog post from last week, I wanted to share some of the additional learning I pursued after my technical interview. During the technical portion of the interview, the interviewer asked me a series of questions about trigonometric equations, such as:

* What is the period of the equation *y = sin(x)*?
* What about the period of *y = sin(x/2pi)*?
* What is the period of the function *y = sin(x) + sin(x/2pi)*?
* If you are given the function *y = f(x)* and series of inputs and outputs that satisfy the function, how can you determine the trigonometric components of this function?

While the emphasis on trigonometry threw me off entirely (we did not cover anything with regards to these types of functions in the Flatiron School curriculum), the last question especially threw me for a loop. I was honest and upfront about not having explored such concepts for several years; I taught one year of Algebra II with basic trigonometry concepts in my first year of teaching, but haven't done rigorous differential equations and linear algebra since sophomore year of college. However, I tried my best to provide a logical guess-timate as to the process that you might be able to use, in an effort to display some sort of problem solving skills. *Maybe you could add or subtract sine and cosine functions from the function and evaluate their effect on the output values. Or instead of addition and subtraction, use division to factor out different trigonometric functions to determine the components of the overall equation.* Ultimately, we moved on from the topic, but I was left feeling a bit frustrated with my inability to answer these questions. Thus, I decided to take a bit of time to learn some more about Fourier analysis, to satistfy my own desire for knowledge, and just in case I get asked similar questions in the future! Below, I summarize some of my intial findings about Fourier Series:

A Fourier series is an infinite sum of sine and cosine functions that relies on the orthagonality of these two trigonometric functions. While several types of Fourier Series exist (right), the one I relied on for my first solution was the square wave (left).


![](https://github.com/huntersapienza/Blogging/blob/master/Fourier%20Series/FourierSeriesSquareWave_800.gif?raw=true) ![](https://github.com/huntersapienza/Blogging/blob/master/Fourier%20Series/FourierSeriesExamples_1200.gif?raw=true)

When studying the square wave solution, I went through the full process of finding integrals for multiple combinations of sine and cosine, some with coefficients and some without. Ultimately, with this "toolbox" of integrals, we are able to solve for three coefficients that enable us to define the infinite series. In summary, the overall process runs something like this:

1. Write *f(t)* as the sum of constant *a0* and sine/cosine terms of various frequencies with unknown coefficients.
2. Evaluate the integrals of *f(t)*, *f(t)cos(nt)*, and *f(t)sin(nt)* for the length of the function's period to determine the coefficients *a0*, *an*, and *bn*.
3. Rewrite *f(t)* as a series composed of the sum of the components determined by these integrals.

Written as mathematical formulas, the integrals for the coefficients can be solved as shown below:

![](https://github.com/huntersapienza/Blogging/blob/master/Fourier%20Series/fourier-series-coefficients.png?raw=true)

Once you have the coefficients for the sine and cosine functions, as you add more and more terms to the infinite series, the function will get closer and closer (due to it's infinite characterization) to the perfect square wave that we saw above.

Ultimately, this is a fairly foundational understanding of Fourier Series, and I'm excited to continue learning more about this particular concept, as well as its applications to real-world problems, particularly in different aspects of the aerospace industry. While I can't say that I was able to answer this question perfectly during the interview (far from it, in fact!), I feel a bit more satisfied knowing I can leave the situation able to identify some of the gaps in my knowledge and continue to learn about all that there is to discover!
