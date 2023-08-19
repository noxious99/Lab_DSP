**Experiment No: 04**

**Experiment Name: Detecting Signal Delay Using Cross-correlation and
the Z Transform**

**Theory:** Cross-correlation is a mathematical process that determines
how similar two signals are as they are shifted relative to each other.
It is often used to find patterns, align signals, and perform other
analyses in signal processing, image analysis, and other domains.
Cross-correlation is similar to linear convolution in that it compares
two signals directly rather than convolving one signal with the
time-reversed version of the other.

The cross-correlation at time index n of two discrete signals x\[n\] and
y\[m\], where n and m are integer indices indicating time steps, is
defined as:

r\[n\] = ∑(m = -∞ to ∞) \[x\[n + m\] \* y\[m\]\]

The cross-correlation result at time index n is represented by r\[n\].
The correlation is computed at each shift as the reference signal y\[m\]
is shifted over the main signal x\[n\].

In practice, cross-correlation can be computed using a variety of
algorithms, including the direct computation demonstrated above, as well
as fast Fourier transforms (FFT) for increased efficiency. When dealing
with huge datasets, FFT-based approaches come in handy.

The Z-transform is a mathematical transformation that is often used to
analyze discrete-time signals and systems. It is similar to the Laplace
transform, which is used for continuous-time signals and systems. The
Z-transform represents discrete signals and systems in a complex
frequency domain, which is important for understanding their behavior,
stability, and response to different inputs.

The Z-transform of a discrete-time signal x\[n\] is denoted as X(z) and
is defined as a power series:

X(z) = ∑(n = -∞ to ∞) \[x\[n\] \* z\^(-n)\]

Here, z is a complex variable. The Z-transform essentially converts a
discrete signal from the time domain (n) to the Z-domain (z).

The Z-transform is very useful for studying difference equations
describing discrete-time linear systems. It\'s commonly utilized in
signal processing, control systems, digital filter design, and
communication systems, among other things.

**Required Software: MATLAB**

**Code:**

**Signal Delay (Continuous):**
```
clc;

clear all;

t=0:0.001:5;

x1= t\>=0 & t\<=1;

x2= t\>=1.5 & t\<=2.5;

x3= t\>=3 & t\<=4;

x=x1+2\*x2+x3;

d1= t\>=1 & t\<=2;

d2= t\>=2.5 & t\<=3.5;

d3= t\>=4 & t\<=5;

d=d1+2\*d2+d3;

N= -(length(t)-1):(length(t)-1);

c= xcorr(d,x);

subplot(3,1,1);

plot(x);

title(\'Input Signal\');

subplot(3,1,2);

plot(d);

title(\'Delayed Signal\');

subplot(3,1,3);

plot(N,c);

title(\'Correlated Signal\');
```
**Output:**

![](04_DSP/media/image2.jpg){width="5.030777559055118in"
height="3.7708333333333335in"}

**Signal Delay (Discrete):**
```
clc;

clear all;

t=0:0.1:5;

x1= t\>=0 & t\<=1;

x2= t\>=1.5 & t\<=2.5;

x3= t\>=3 & t\<=4;

x=x1+2\*x2+x3;

d1= t\>=1 & t\<=2;

d2= t\>=2.5 & t\<=3.5;

d3= t\>=4 & t\<=5;

d=d1+2\*d2+d3;

N= -(length(t)-1):(length(t)-1);

c= xcorr(x,d);

subplot(3,1,1);

stem(x);

title(\'Input Signal\');

subplot(3,1,2);

stem(d);

title(\'Delayed Signal\');

subplot(3,1,3);

stem(N,c);

title(\'Correlated Signal\');
```
**Output:**

![](04_DSP/media/image3.jpg){width="5.016879921259843in"
height="3.7604166666666665in"}

**Z-Transform:**
```
clc;

clear all;

x = \[1, 2, 4, 6, 8\];

H=0;

N = length(x);

y= sym(\'Z\');

for i=1:N

H= H+x(i)\*y\^(1-i);

end

display(H);
```
**Output:**

H =

2/Z + 4/Z\^2 + 6/Z\^3 + 8/Z\^4 + 1

**Discussion and Conclusion:** In this experiment, we looked at signal
delay detection in both continuous and discrete circumstances, as well
as the use of the Z-transform. We used cross-correlation techniques to
successfully locate signal delays, comparing an input signal with its
delayed form. Notably, the peak index of the resulting cross-correlation
provided us with critical timing information. The experiment gave the
predicted results in both cases.
