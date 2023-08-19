**Experiment No. 05**

**Experiment name: Determining the Z-transform of a causal, anti-causal,
and non-causal signal in MATLAB**

**Theory**: A causal signal is one that exists and is nonzero only for
time indices that are nonnegative. In a more suitable domain for study,
the Z-transform can provide insights into the frequency characteristics,
stability, and reactivity of the causal signal.

The following is the generic formula for the Z-transform of a causal
discrete-time signal x\[n\]:

X(z) = ∑(n = 0 to ∞) \[x\[n\] \* z\^(-n)\]

A signal that occurs and is nonzero exclusively for negative time
indices is referred to as an anti-causal signal. The Z-transform can
provide information about the anti-causal signal\'s frequency
characteristics, stability, and response in the Z-domain.

The following is the generic formula for the Z-transform of an
anti-causal discrete-time signal x\[n\]:

X(z) = ∑(n = -∞ to -1) \[x\[n\] \* z\^(-n)\]

When dealing with a non-causal discrete-time signal, which occurs for
both positive and negative time indices, the Z-transform is frequently
divided into two parts: one for the positive time indices (causal
portion) and one for the negative time indices (anti-causal part). This
separation aids in dealing with the Z-transform of a signal that is
nonzero in both directions.

The generic formula for a non-causal discrete-time signal x\[n\]\'s
Z-transform can be stated as a combination of the causal and anti-causal
parts:

X(z) = X_causal(z) + X_anti_causal(z)

The Z-transform is a useful tool for evaluating discrete-time signals
and systems in the frequency domain in all instances. It provides
insights into system behavior, stability, frequency response, and other
qualities, making it an important concept in many domains, including
signal processing, control systems, and communication systems.

**Required Software: MATLAB**

**Code:**

**1. Causal Signal:**
```
clc;

clear all;

x=\[2 5 7 7 5 2\];

b=0;

n=length(x);

y=sym(\'z\');

for i=1:n

b=b+x(i)\*y\^(1-i);

end

disp(\'Z-Transform: \');

disp(b);
```
**Output:**

Z-Transform:

5/z + 7/z\^2 + 7/z\^3 + 5/z\^4 + 2/z\^5 + 2

**2. Anti-causal Signal:**
```
clc;

clear all;

x=\[1 3 5 7 3 1\];

b=0;

n=length(x);

y=sym(\'z\');

for i=1:n

b=b+x(i)\*y\^(i-1);

end

disp(\'Z-Transform: \');

disp(b);
```
**Output:**

Z-Transform:

z\^5 + 3\*z\^4 + 7\*z\^3 + 5\*z\^2 + 3\*z + 1

**3. Non-causal Signal:**
```
Clc;

clear all;

x=\[1 3 5 7 9\];

pos=input(\'input zero index: \');

n=length(x);

y=sym(\'z\');

b=0;

a=0;

for i=1:n

if i\>=pos

b=b+x(i)\*y\^(pos-i);

else

b=b+x(i)\*y\^((-1)\*(i-pos));

end

end

disp(\'Z-Transform: \');

disp( b);
```

**Output:**

input zero index: 4

Z-Transform:

5\*z + 9/z + 3\*z\^2 + z\^3 + 7

**Discussion and Conclusion:**

We learned about the z transformation of causal, anticausal, and
non-causal signals in this experiment. In the z domain, the power of z
for a causal signal is negative. For anticausal signal, the power of z
is positive in the z domain. A non-causal signal has two sides. We take
the zero position of a signal from the user and calculate the z
transformation based on that value for non-causal signals. We obtained
the exact value as theory for the MATLAB code.
