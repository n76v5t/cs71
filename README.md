java c
Mathematics IA 
Calculation of harmonic oscillator global displacements by numerical integration 
(pages:14) 
Introduction 
When I was studying travel problems in elementary school, I once learned an interesting topic. A small bird traveled back and forth between trains traveling in opposite directions at an infinite constant speed, and it was necessary to solve for the total distance the bird flew before the trains met. At that time, although I got the conclusion by calculating the total length of the bird's flight, some real-world problems still puzzled me, such as the time for the bird to make a U-turn was not concerned. What intrigued me more was the precise process and exact method of calculating this infinite motion, where the total distance of each segment was decreasing and approaching zero. As my horizons broadened, I gradually discovered more similar problems, such as Zeno's Achilles' paradox, which made me realize that the so-called infinite number of motion processes ultimately lead to a finite or even definite value.
It wasn't until I studied the ideas of minimization and accumulation in calculus that I finally had a way to think deeply about how this problem, which had long piqued my curiosity, should be solved. After deep thinking, I decided to use numerical integration in this paper to solve some problems with realism around me, such as the calculation of the cumulative displacement of a damped harmonic oscillator in physics, to satisfy my very original curiosity and conclude my learning.
Background knowledge 
Before the study begins, first we need to know something about damped resonators. A harmonic oscillator is a system that studies motion under the action of a restoring force, mostly found in springs. Neglecting the effects of all other forces, its equation of motion is:

where t is the time, m is the mass, k is the spring constant and x is the displacement, which is a function of t, so we can represent it as x(t).
The solution of this equation is a sine or cosine wave with a natural frequency ω0, where:


However, in systems with spring packs, this reciprocating motion under restoring forces is actually affected by the damping coefficient of the spring oscillator, so we need more comprehensive equations of motion, that is, equations of motion for damped harmonic oscillators:

In this function, besides the previously mentioned variables, the new damping coefficient b and the combined external force F(t) are taken into consideration to mature the system. And when the combined external force F(t) is 0, the function 
should be like:

And for computational convenience, we will set up this scenario in our study.
It is also important to note that damped resonators move differently at different damping coefficients.
When ， the damping is too strong so the system will return to the equilibrium position without oscillating. The displacement solution at this point is:
where r1 and r2 are characteristic root , in which  refers to the damping coefficient after deflation. Specially, when b2 = 4mk, the system will return to the equilibrium position at the fastest speed. 
When b2 < 4mk, the damping is not strong enough so the system oscillates with the gradually decaying amplitude. The displacement solution at this point is:

where  refers to the damping coefficient after deflation,  refers to the damped oscillation frequency, and A refers to the initial amplitude, i.e. maximum displacement.
From those background knowledge we can clearly find that calculating how Damped Harmonic Oscillator moves in the latter situation is the desired goal of the study.
In the equation and derivation above, by means of differential equations, we came up with when the oscillations happen and how to calculate the displacement of the damped resonator at a given moment in time, and then through numerical integration, we were able to obtain the cumulative displacement.
So, we should also understand what numerical integration is. The goal of numerical integration is to approximate the integral value in a discrete way, usually in the absence of an analytic solution. The central idea of numerical integration is to transform. the problem of integrating continuous functions into a discrete summation problem. Common ideas include the left rectangle rule, the right rectangle rule, the midpoint rule, the trapezoidal rule, Simpson's rule, and the Gauss-Legendre integral. In addition, some of the libraries in python can help with related computations.
Methodology 
In the numerical calculation of the cumulative values of displacements, I plan to use three methods.
The first is to use the midpoint rule, in which the interval will be divided into small intervals and values will be taken at the midpoint of each small interval, thus calculating the area of each small rectangle and obtaining the overall integral value.
Take a function defined in the interval, for example, we can divide it into n small intervals of equal length, each of length , for which the midpoints is for the  interval, from this we obtain that the integral in this interval  can be approximated as . Accumulating the valuations of the function integrals in each of the small intervals gives us the valuation of the function integrals over the whole interval:

where  and .
The second method is to use the trapezoidal rule. With this rule, we use a similar partitioning, except that in the numerical computation of the integrals of the functions in each of the subintervals, we approximate the computation as the area of a trapezoid.
Take a function defined in the interval and divide it in the same way, the integral in 代 写Mathematics IA Calculation of harmonic oscillator global displacements by numerical integrationPython
代做程序编程语言the  interval can be approximated as . Similarly, we can approximate the valuation of the function integrals over the whole interval:

where  and .
The third method is to use Simpson's rule. This rule employs a similar interval segmentation, but in the numerical integration operation of the function on each small interval, a quadratic function is considered to fit the function image of that small segment, so after interpolation, we include both the function values corresponding to the ends of the intervals and at the midpoints in the computation of the numerical values of the integrals in the estimated intervals.
Take a function defined in the interval and divide it in the same way, the integral in the  interval can be approximated as . Similarly, we can approximate the valuation of the function integrals over the whole interval:

where  and . But in this rule, it’s also important to note that n must be even.
Other numerical integration methods that I considered before my research began include the left rectangle rule, the right rectangle rule, and the Gauss-Lejeune rule.
With the same interval segmentation, the right rectangle rule and the left rectangle rule are the following two formulas, respectively:


where  and .
However, these two methods are only useful for cases where the function mean is similarly the value of the function at one end of each division interval, and in most cases, including the function I want to study, there is a large error, so they can be ruled out.
Regarding the Gauss-Lejeune law, it is characterized by the selection of appropriate nodes and weights to reduce the error between the approximation and the true value. For the integral of a function on an interval , the formula should be:

Where  is the selected node, and  are different weights for each node.
The advantage of this method is that it performs well for complex functions with multiple inflection points, and the disadvantage is that it is relatively cumbersome to compute both nodes and weights. Considered in conjunction with our function, its inflection points are relatively fixed and its form. is relatively simple, so this approach can be ruled out for computational simplicity.
Calculation Process 
Before starting the calculations, I first made some basic value settings. I set the spring constant k to 1, the amplitude A to 1, damping factor of the spring is 0.2 and the mass m to 1 for ease of calculation. In addition, my study addresses vibrations within 10 seconds and divides the interval [0, 10] into 10 sub-intervals, thus being able to satisfy the requirements of the three rules for interval partitioning. Based on previous background knowledge, the values of the following variables can be obtained:



Also, the motion of the damped harmonic oscillator can be described as follow: 
Midpoint rule: 
Using the midpoint rule, we can perform. the calculation as follows:=[0.5, 1.5, 2.5, 3.5, 4.5, 5.5, 6.5, 7.5, 8.5, 9.5]

Calculation of example at midpoints:

Similarly, we can calculate the corresponding displacements for the remaining midpoints as shown in the table below:

0.5 0.836 1.5 0.067 2.5 -0.618 3.5 -0.664 4.5 -0.148 5.5 0.398 6,5 0.513 7.5 0.180 8.5 -0.243 9.5 -0.387 
According to the former formula, we can get the result:

Trapezoidal rule: 
Using the trapezoidal rule, we can perform. the calculation as follows:
Calculation of example at end points:

Similarly, we can calculate the corresponding displacements for the remaining end points as shown in the table below:t 
0 1 1 0.493 2 -0.333 3 -0.732 4 -0.448 5 0.157 6 0.522 7 0.386 8 -0.048 9 -0.363 10 -0.318 
According to the former formula, we can get the result:

Simpson's Rule: 
Using the Simpson's Rule, with the calculation of midpoints and end points above, we can perform. the calculation as follows:

Tests of calculations 
In order to check the calculation results under the three rules, I conducted a simulation experiment and obtained the following table of cumulative displacement versus time:Time Cumulative Displacement 0 0 0.5 0.468082 1 0.80586 1.5 0.947035 2 1.021936 2.5 1.266058 3 1.611202 3.5 1.967341 4 2.250451 4.5 2.401518 5 2.44006 5.5 2.582782 62.8181276.53.08244773.3114
7.53.45500983.4930138.53.5679193.7229179.53.914296104.093995
From the table, we can clearly see that the accurate cumulative displacement of the damped resonator is about 4.094 meters when the vibration time is 10 seconds. Thus observing the error in the final number obtained under the three rules, we can get the following table:Rule Error Error rate midpoint rule
-0.04-0.98%trapezoidal rule
0.0471.15%Simpson's Rule-0.011-0.27%
Conclusion and Reflection 
Conclusion: 
By comparing the results of the calculations under the three rules to the true values, I found that the numerical integration algorithm under Simpson's rule resulted with the most accurate. This may be due to the fact that it uses a quadratic function to fit the image of a function in a small interval, which gives a better fit than the midpoint rule, which simply takes the median, and the trapezoidal rule, which is similar to a primary function that fits the image of a function.
In this case, the midpoint rule performs better than the trapezoidal rule probably because in each small interval, the function image is more similar to a concave function, which results in the average of the values taken from the two endpoints of the interval being larger than the actual mean value of the interval, whereas the midpoint value is relatively closer to the real mean value.


         
加QQ：99515681  WX：codinghelp
