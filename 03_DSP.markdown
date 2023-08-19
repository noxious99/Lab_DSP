**Experiment No. 03**

**Experiment Name:** Study Auto-Correlation and Cross-Correlation in
MATLAB

**Theory:** The two forms of correlation used to evaluate time series
data are auto-correlation and cross-correlation.

The correlation of a signal with a delayed version of itself is referred
to as auto-correlation. In other words, auto-correlation assesses the
similarity between a signal and its shifted counterpart. It quantifies
the link between a signal and its own historical values.

The autocorrelation function of a discrete-time signal x(n) is described
mathematically as:

Rxx(m) = Σ \[x(n) \* x(n - m)\] ; in the autocorrelation function Rxx(m)
is a measure of the similarity between the signal x(n) and a delayed
version of itself.

Cross-correlation, on the other hand, calculates the similarity of two
signals as a function of a time delay given to one of them. It
quantifies the link between two distinct signals. In signal processing
and time series analysis, cross-correlation is frequently used to
compare two signals and evaluate their degree of similarity.

The cross-correlation function is defined mathematically as follows:

Rxy(m) = Σ \[x(n) \* y(n - m)\] ; in the cross-correlation function
Rxy(m) measures the similarity of two signals x(n) and y(n) when one is
delayed by m samples.

In both cases, correlation is a measure of the linear relationship
between two signals, with values ranging from -1 to 1. A number of 1
indicates a perfect positive correlation, while a value of -1 shows a
perfect negative correlation. A score of 0 implies that there is no
correlation between the signals.

**Code: Auto Correlation**
```
clc

clear all;

x=input(\'Enter the Array:\');

n1=input(\'Sample Range:\');

h=fliplr(x);

n2=-fliplr(n1);

z=\[\];

for i=1:length(x)

g=h.\*x(i);

z=\[z;g\];

end

\[r c\]=size(z);

k=r+c;

t=2;

y=\[\];

cd=0;

while(t\<=k)

for i=1:r

for j=1:c

if((i+j)==t)

cd=cd+z(i,j);

end

end

end

t=t+1;

y=\[y cd\];

cd=0;

end

subplot(3,1,1);

stem(x);

title(\'Auto Correlation-Signal\');

subplot(3,1,2);

nl=min(n1)+min(n2);

nh=max(n1)+max(n2);

t=nl:1:nh;

stem(t,y);

title(\'without function\');

subplot(3,1,3);

z=xcorr(x,x);

stem(t,z);

title(\'with function\');

```

**Input:**

![](03_DSP/image2.png){width="2.625in"
height="0.4479166666666667in"}

**Output:**

![](03_DSP/media/image3.jpg){width="6.837410323709537in"
height="5.125in"}

**Code: Cross-correlation**
```
clc

clear all;

x=input(\'Enter the first Array:\');

n1=input(\'Sample Range:\');

h=input(\'Enter the second Array:\');

n2=input(\'Sample Range:\');

n2=-fliplr(n2);

z=\[\];

w=fliplr(h);

for i=1:length(x)

g=w.\*x(i);

z=\[z;g\];

end

\[r c\]=size(z);

k=r+c;

t=2;

y=\[\];

cd=0;

while(t\<=k)

for i=1:r

for j=1:c

if((i+j)==t)

cd=cd+z(i,j);

end

end

end

t=t+1;

y=\[y cd\];

cd=0;

end

subplot(4,1,1);

stem(x);

title(\'First Array\');

subplot(4,1,2);

stem(h);

title(\'Second Array\');

subplot(4,1,4);

nl=min(n1)+min(n2);

nh=max(n1)+max(n2);

t=nl:1:nh;

stem(t,y);

title(\'Without Function\');

subplot(4,1,3);

p=xcorr(x,h);

stem(t,p);

title(\'With Function\');
```
**Input:**

![](03_DSP/media/image4.png){width="2.7175557742782153in"
height="0.6654527559055118in"}

**Output:**

![](03_DSP/media/image5.png){width="7.340284339457567in"
height="4.3282436570428695in"}

**Discussion and Conclusion:**

We studied the concepts of auto-correlation and cross-correlation in
time series analysis in this lab experiment. We then conducted tests to
demonstrate the features of these functions in MATLAB.
