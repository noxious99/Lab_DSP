**Experiment No. 02**

**Experiment Name: Write a code for linear convolution and plot the
signal using MATLAB**

**Theory:** Linear convolution is a fundamental operation in signal
processing and mathematics that is widely utilized in image processing,
audio analysis, and other domains. It is a method of combining two
functions or sequences to get a third function that depicts the overlap
of the two original functions as they are shifted relative to each
other.

If the input and impulse response of a system are x\[n\] and h\[n\]
respectively, the convolution is given by the expression,

**x\[n\] \* h\[n\] = ε x\[k\] h\[n-k\]**

In this equation, x(k), h(n-k), and y(n) represent the system\'s input
and output at time n. We can observe that when one of the input signals
is multiplied by the other, it shifts in time by a value. Linear
Convolution is a popular method for building various types of filters.

Filtering, blurring, edge detection, and more applications use linear
convolution. In practice, for discrete signals, the convolution process
can be computed using a sliding window technique, in which the impulse
response is shifted across the input signal and multiplication and
summation are performed at each place to produce the output signal.

Linear convolution assumes a linear and time-invariant system. When
working with real-world data, factors such as boundary effects may need
to be addressed in order to produce correct results.

**Required Software: MATLAB**

**Code:**
```
clc;

clear all;

xn = \[1 2 3 4\];

hn = \[4 3 2 5\];

L = length(xn);

M = length(hn);

X = \[xn, zeros(1,L)\];

H = \[hn, zeros(1,M)\];

for n = 1:L+M-1

y(n)=0;

for i = 1:L

if(n-i+1\>0)

y(n) = y(n)+X(i)\*H(n-i+1)

end

end

end

subplot(3,1,1)

stem (xn)

title(\'x(n)\')

subplot(3,1,2)

stem (hn)

title(\'h(n)\')

subplot(3,1,3)

stem (y)

title(\'y(n)\')
```

**Output:**

y =

4 11 20 34 28 23 20

![](02_DSP/media/image2.jpg){width="5.822916666666667in"
height="4.364583333333333in"}

**Discussion and Conclusion:**

The linear convolution code was created in MATLAB. To put the code into
action, two 1x4 matrices were declared. The length function was then
used to calculate the matrix\'s length.

After that, a nested for loop was used. The first for loop ran from 1 to
L+M-1. An if condition was utilized to apply a condition in the second
for loop. Using the if condition, a formula for the output was built. In
this example, a subplot was used. I plotted the signal using the stem
function because it was discrete.
