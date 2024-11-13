java c
Systems Modelling and Analysis – Assignment 3
Assignment Background
This assignment is a continuation of Assignment 1 and 2, where you have modelled the DC-motor driven positioning system. No material from Assignment 1 or 2 is required to complete this assignment.
Recall that V (s) = L {v(t)} is the voltage supplied to the DC motor and Y (s) = L {y(t)} is the dartboard’s vertical position. The transfer function GOL(s) = VY ((ss))is exactly
GOL(s) =s6 + 3167s5 + 646300s4 + 135539583s3 + 407750000s2 + 13530000000s − 0.00003/1250s 2 + 250000s + 75000000
Please run the code in MATLAB:
num = [1250 250000 75000000];
den = [1 3167 646300 135539583 407750000 13530000000 -0.00003];
G_OL = tf(num,den);
Assume zero initial conditions when required.
Part 1: Dartboard Positioning System, Sinusoidal Inputs
Q1-2. Using MATLAB, plot the Bode diagram of GOL(s) (with a grid). Observe the behaviour at low frequencies and at high frequencies (for both magnitude and phase).
(Q1) Is the gain larger at low or high frequencies? [Canvas Input: Select Low or High]
(Q2) Is the phase lag smaller at low or high frequencies? [Canvas Input: Select Low or High]
Q3-4. Apply sinusoids of varying amplitude (v = Asin(t)) and observe the steady-state behaviour of y(t) (i.e. yss(t)). For each question below, you are given a specific value A. Use this value of A to answer the question.
(Q3) What is the phase shift between yss(t) and v(t)? (The answer should be in degrees and in the range [−180o, 180o))?
(Q4) What is the average value of yss(t)?
[Canvas Input: Two signed numbers - 5% tolerance allowed]
Q5-6. Now apply sinusoids of varying frequency (v = 1000 sin(ωt)) and observe the steady state behaviour of y(t) (i.e. yss(t)). For each question below, you are given a specific value ω, use this value of ω to answer the question.
(Q5) What is the phase shift between yss(t) and v(t)? (The answer should be in degrees and in the range [−180o, 180o))?
(Q6) For yss(t), what is the maximum deviation from its average value?
[Canvas Input: Two signed numbers - 5% tolerance allowed]
Q7. Amplify the voltage supplied to the motor by a constant A, so that v(t) = A sin(t) is supplied to the motor.
Find the largest integer A such that |y(t)| ≤ 0.5[m]. [Canvas Input: One integer]
Hint: It is sufficient to use a trial-and-error approach.
Part 2: Dartboard Positioning System, Closed-Loop Control and Discrete Systems
To simplify the problem now approximate the open-loop system with a lower order system as follows: G˜OL(s) = s(s+1.284)/0.007118. Use this for all subsequent analysis involving the open-loop system. Part 1 has shown us that tuning parameters A and w for input v = Asin(wt) to achieve a desired behaviour of y(t) is not efficient, so we turn again to closed-loop control. A position sensor is purchased to measure y(t) accurately. First, use a controller C(s) = K such that the voltage supplied to the motor is v = K(r − y), where r is a reference signal.
Q8-13. Produce the Bode Diagram for the closed-loop system with K = 80. On the Canvas quiz, you will be given different values of ω.
(Q8-10) Find the values of gain [dB] for the given values of ω. [Canvas Input: two signed numbers - 5% tolerance allowed]
(Q11-13) Find the values of phase [deg] for the given values of ω. (The answer should be in degrees and in the range [−180o, 180o)) [Canvas Input: two signed numbers - 5% tolerance allowed]
Q14-16. For K = 800, plot r(t) = 10 sin (ωt) and the corresponding y(t) for ω = 0.73 [rad/sec], ω = 7.3 [rad/sec], ω = 73.0 [rad/sec] (two graphs on the same axes for each frequency). Capture enough time to show the steady-state response of y(t).
Find the value of y(t) − r(t) when t is 50 s for ω = 0.73, 7.3, 73.0 [rad/sec]. [Canvas Input: Three signed numbers - 5% tolerance allowed]
For K = 100 and the reference signal r(t) = 0.1 sin(t), we will find the magnitude and the phase-shift of yss(t) in three ways:
Q17-18. Graphically, by reading values from the Bode diagram of the closed-loop system. Using the Bode diagram, find the magnitude [dB] and phase [deg] of yss(t). (The answer of the phase should be in degrees and in the range [−180o, 180o))[LMS Input: Two signed numbers - 5% tolerance allowed]
Q19-20. Graphically, by reading values from the response plot y(t) after it reac代 写Systems Modelling and Analysis – Assignment 3Matlab
代做程序编程语言hes a steady-state. For the response plot y(t), let the first peak in y(t) after t = 50 sec be at time ty. Let t1 be the closest r(t) peak preceding time ty and t2 be the closest r(t) peak following ty.
(Q19) What is y(ty)? [Canvas Input: One signed numbers - 5% tolerance allowed]
(Q20) Select the equation that approximates the phase [deg] of yss(t) from Figure 1. [Canvas Input: One integer]

Figure 1: Selection options for Q19
Q21-22. Analytically, by substituting s = j · 1 into the transfer function of the closed-loop system. Find the (Q21) real and (Q22) imaginary parts of the resulting complex number. [Canvas Input: Two signed numbers - 5% tolerance allowed]
Q23-24. We wish to avoid the dartboard going outside the boundary at a steady-state mode (if there is a finite number of exits - it is acceptable). Assume that we would like to operate at high frequencies (i.e. ω > 1 rad/s). If K = 7000 and the total width of the safe zone is 1500 [mm], which frequencies ω should not be used where the reference signal is r(t) = 0.5 sin (ωt)[m]?
Using the Bode diagram, find the range ω ∈ [ωmin, ωmax] [rad/sec] such that the reference signal is not suitable. [Canvas Input: Two signed numbers - 5% tolerance allowed]
Set K = 2000 from now on forming a closed loop system GCL(j, ω). We would like to address the long phase-lag produced in this system when r(t) = 0.1sin(t).To improve performance, we will use an additional controller with transfer function C1(s) = a 0.0001s+1/bs+1 outside the feedback loop such that
V (s) = K (C1(s)R(s) − Y (s))
(R(s) is the Laplace transform. of r(t)). We would like the output y(t) to exactly match the reference signal r(t) = 0.1sin(t) and can do so by tuning the values of a and b in the controller.
Q25-26. Find |GCL(jω)| [unitless] and ∠GCL(jω) [deg] for ω = 1 rad/sec for the original closed loop system GCL(jω). (The answer of the phase should be in degrees and in the range [−180o, 180o))
[Canvas Input: Two signed numbers - 5% tolerance allowed]
Q27-28. Find a and b such that the output for the new system matches the reference signal (yss(t) = r(t) = 0.1 sin(t)). [Canvas Input: Two signed numbers - 5% tolerance allowed]
Q29-32. Reflect on the usage of closed-loop control for the positioning system. What are the benefits which can be achieved by using it, compared to open-loop control?
Select true or false for the following statements
The closed loop control system:
(Q29) does not require a sensor. [Canvas Input: Select True or False]
(Q30) can allow the poles of the system to be moved to the LHP and make the system exponentially stable.
[Canvas Input: Select True or False]
(Q31) can allow better tracking of a reference signal. [Canvas Input: Select True or False]
(Q32) results in a system that is more robust to errors due to the presence of feedback. [Canvas Input: Select True or False]
After analysing the system in continuous time, now investigate how the system behaves in discrete time.
Q33. Start by converting the continuous-time system G˜OL(s) into a discrete-time system G˜OL(z) using the bilinear transformation (Tustin’s Method) with the sampling time T = 1s. Let the open-loop transfer function be ˜GOL(z) = z2+b1z+b2/a0z2+a1z+a2. What is the value of b2? [Canvas Input: one signed numbers - 5% tolerance allowed]
Q34. Then calculate the discrete-time frequency wd [rad/s] corresponding to the continuous-time operating frequency wa = 1 [rad/s]. What is the value of wd? [Canvas Input: one signed numbers - 5% tolerance allowed]
Q35-37. Lastly, apply a known input, collect data from the sensor and use that data to perform. a system ID to validate the model of the system you have worked with.

Which of the options in Figure 2 is the correct parameter vector p? [Canvas Input: one integer]
(Q36-37) Let the input u[k] = {0, 0.2, 0.35, 0.68, 0.83, 0, 0, 0, . . . } (i.e. u[0] = 0, u[1] = 0.2, u[2] = 0.35, u[3] = 0.68, u[4] = 0.83 and u[i] = 0 for i > 4). The output data collected by the sensor is given in y_dat.mat. Perform. a system ID on the given data set. Let the open-loop transfer function obtained from the data be ¯GOL(z) = z2+b1z+b2/¯a0z2+¯a1z+¯a2.
Q36. What is a¯1?
Q37. What is ¯b1? [Canvas Input: Two signed numbers - 5% tolerance allowed]








         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
