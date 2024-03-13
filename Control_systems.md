exercise(control_systems)=
# Control systems

In this chapter a number of basic principles of control systems are covered. The following will be discussed:
- Open and closed loop method
- PID controller

Also check out {ref}`feedback`.

## Control systems and PID controllers
Control systems are applied when a 'process' needs to be controlled. An example of such a process is a heater system (stabilization of temperature) or a liquid level regulator (stabilization of liquid level). \
A common characteristic of such a process is that it can be controlled. In other words, it has an input (e.g. a current to a heating element, the inflow of a liquid, etc.) and it gives an output (e.g. the temperature, liquid level, etc.). \
Considering the electric heating as an example, there are two ways to reach a desired temperature: through a open and closed loop method.

### Open loop method
For this method there is no feedback. A certain current is set to run through the heating element. After some time a thermal equilibrium will be reached between the heating element and the surrounding. A temperature equilibrium is reached. \
The disadvantage of such a method is that the equilibrium temperature depends on external factors such as the outside temperature and/or isolation from the air outside.

### Closed loop method (feedback)
The temperature is measured using a sensor position in the place that needs to be temperature stabilized. The sensor signal is compared with the desired value, which is set. The difference between the actual and desired value (the error signal) is processed by a control system and used to steer the process. \
This is shown in an abstract schematic in {numref}`fig:cs01`.

```{figure} /Fig-ch7/CS01.png
---
width: 500px
name: fig:cs01
---
Schematic control system
```

For the analysis of these sort of systems transfer functions can be assigned for the individual parts.

For the control system shown in {numref}`fig:cs01` we obtain:

$$
\begin{split}
y(t) &= H \cdot r(t) \\
r(t) &= G \cdot e(t) \\
e(t) &= x(t) - y(t),
\end{split}
$$ (eq:tf)

where $H$ is the transfer function of the process, $G$ the transfer function of the control system, and $e$ is the error signal (difference between the desired and actual value). \
These equations are easily combined to find an expression for $y(t)$:

$$
y(t) = \frac{HG}{1 + HG} \cdot x(t).
$$ (eq:yt)

$\frac{HG}{1 + HG}$ is the transfer function for the total system (the process and control system combined). \
The objective at the design of control systems is to design the feedback system such that the process can be optimally controlled. Often the objective is to tune the system to the desired value $y(t)$ after a sudden change of $x(t)$. \
One way to characterize systems is to look at the response of $y(t)$ after a step of $x(t)$, the so called 'step response of the system'. \
$x(t)$ then has the shape shown in {numref}`fig:cs02`.

```{figure} /Fig-ch7/CS02.png
---
width: 400px
name: fig:cs02
---
Step signal at input
```

Every system has its own characteristic way in responding to the step in $x(t)$. \
The transfer function of the process in general is not a simple constant. If often contains differential an integral elements:

$$
\begin{split}
y(t) &= H \cdot r(t) \\
&= \alpha \cdot r(t) + \beta \int r(t) {\rm d} t + \gamma \frac{{\rm d}}{{\rm d} t} r(t).
\end{split}
$$ (eq:ch7-1)

Also the control system in its most general form has a similar transfer function:

$$
\begin{split}
r(t) & = G \cdot e(t) \\
& = \lambda \cdot e(t) + \frac{1}{\tau_{\rm i}} \int e(t) {\rm d} t + \tau_{\rm d} \frac{{\rm d}}{{\rm d} t} e(t).
\end{split}
$$ (eq:ch7-2)

A device with such a characteristic is called a *PID* controller. The *P* stands for proportional (the proportionality constant $\lambda$ in the transfer characteristic), the *I* for the integration and the *D* for differentiation. 

A control system $r(t)$ that only has a proportional feedback may have a step response as shown in {numref}`fig:cs03`.

```{figure} /Fig-ch7/CS03.png
---
width: 450px
name: fig:cs03
---
Step response with an integrating process $y(t)$
```

In the case shown in {numref}`fig:cs03` there is an integrating element present in the process, which prevents the process to respond instantly on the input step. For systems with a proportional control system only there is always a difference signal for control (the error signal, which directly follows from eqn. {eq}`eq:tf`). \
One method to reduce the error signal is to increase the product of $GH$. In practice this is limited. Another method is to include integration in the control system. Then the difference between $x(t)$ and $y(t)$ can be minimized. \
Another characteristic that can be improved at the same time is the rise time of the signal. As the derivative of the error signal at the start (close after t = 0) is large, the differential part of the PID can be used to increase $r(t)$ giving $y(t)$ a steeper shape. \
When there is also a differential element present in the process an 'overshoot' can occur. The response then looks like {numref}`fig:cs04`. 

```{figure} /Fig-ch7/CS04.png
---
width: 450px
name: fig:cs04
---
Step response with an overshoot
```

By tuning the values of $\lambda$, $\tau_{\rm i}$ and $\tau_{\rm d}$ of the PID the characteristics of the total system can be optimized (e.g. the damping) improving the step response. The exact response and optimal settings of $\lambda$, $\tau_{\rm i}$ and $\tau_{\rm d}$  of a PID is hard to predict (a.o. because in most cases the behavior of the process is not exactly known). In practice (e.g. at stabilizing the temperature in a cryostat) you can adjust the settings by trial-and-error. There are also methods to calculate the optimal PID setting, but that is beyond the scope of this course. \

A good example of a control system is an OpAmp amplifier with feedback as shown in {numref}`fig:cs05`.

```{figure} /Fig-ch7/CS05.png
---
width: 300px
name: fig:cs05
---
Inverting OpAmp amplifier
```

The amplifier circuit of {numref}`fig:cs05` is controlled by a proportional feedback system and in general will have a step response as shown in {numref}`fig:cs04`. \
For this circuit the following holds:

$$
\begin{split}
y(t) &= \frac{A}{1 + A \lambda} \cdot x(t) \\
\lambda &= \frac{R_1}{R_1 + R_2}.
\end{split}
$$ (eq:ch7-3)

If we consider the amplifier to be the process the feedback system takes a slightly different form from what is shown in {numref}`fig:cs01`. However, both systems can easily be expressed in each other through a simple calculation.

````{admonition} Exercise 7.1
:class: note

```{figure} /Fig-ch7/CS06.png
---
width: 400px
name: fig:cs06
---
Equivalent control systems
```

- Verify the rule that is displayed graphically in {numref}`fig:cs06`.
````

::::{admonition} Answer
:class: dropdown

For the first control system the following holds:

$$
\begin{split}
        y(t) &= G \cdot r(t) \\
        r(t) &= F \cdot e(t) \\
        e(t) &= x(t) - y(t).
    \end{split}
$$ (eq:ch7-10)

Substituting the last two equations into the first one gives

$$
\begin{split}
        & y(t) = G \cdot F \cdot x(t) - G \cdot F \cdot y(t) \\
        & y(t) + G \cdot F \cdot y(t) = G \cdot F \cdot x(t) \\
        & y(t) \cdot (1 + G \cdot F) = (G \cdot F) \cdot x(t) \\
        & y(t) = \frac{(G \cdot F)}{(1 + G \cdot F)} \cdot x(t).
    \end{split}
$$ (eq:ch7-11)

For the second control system the following holds:

$$
\begin{split}
        y(t) &= G \cdot e(t) = r(t)\\
        e(t) &= F \cdot x(t) - F \cdot r(t)\\
    \end{split}
$$ (eq:ch7-12)

Combining these two equations results in 

$$
\begin{split}
        & y(t) = G \cdot F \cdot x(t) - G \cdot F \cdot r(t) =  G \cdot F \cdot x(t) - G \cdot F \cdot y(t)\\
        & y(t) + G \cdot F \cdot y(t) = G \cdot F \cdot x(t) \\
        & y(t) \cdot (1 + G \cdot F) = (G \cdot F) \cdot x(t) \\
        & y(t) = \frac{(G \cdot F)}{(1 + G \cdot F)} \cdot x(t).
    \end{split}
$$ (eq:ch7-13)

So both control systems are indeed equivalent.
::::

## Distance measurement
In this section a control system will be presented to stabilize the height of a floating ball using a proportional control only.\
{numref}`fig:cs07` schematically shows the control system including the process. 

```{figure} /Fig-ch7/CS07.png
---
width: 300px
name: fig:cs07
---
Height control system
```

The process is defined by a distance sensor (check data sheet). The distance sensor contains an infra red emitting diode, a position sensitive detector and a signal processing and conditioning circuit.\
The distance measuring range is from about 10 cm to 80 cm which results in an analog output of resp. about 2 to 0.5 Volt.
The relationship between the analog output and the inverse of the measured distance can be assumed linear over the sensor's measuring range (check the data sheets).
In this experiment you should choose the desired height $V_{\rm ref}$ of the floating ball somewhere in the middle of the tube. Due to  spinning behaviour of the ball the air flow around the ball changes continuously and results in small height changes. To stabilize the height, the air flow produced by the fan blowers needs to be adjusted continuously.\
In the following sections the various parts of the total height control system will be discussed.

:::{note}
For the exercises, do not remove the parts that you construct. At the end all parts will be connected to form the total control system. \
In the lab journal the upcoming exercises may be seen as parts of one overall task. Therefore, for each of the exercises (parts) there is no need to keep the structure discussed in the {ref}`Introduction`.
:::

### Proportional feedback system

The output voltage $V_{\rm dist}$ of the height sensor (corresponding to $y(t)$ of {numref}`fig:cs01`) has to be compared with the set value $V_{\rm ref}$ (corresponding to $x(t)$ of {numref}`fig:cs01`). For this we use a differential amplifier. This combines the comparator and the proportional feedback system. ({numref}`fig:cs10`)

````{admonition} Exercise 7.2
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Show that the circuit in {numref}`fig:cs10` is a proportional feedback system with $V_{\rm r} = \lambda \left( V_{\rm ref} - V_{\rm dist} \right)$.
- Build the circuit of {numref}`fig:cs10` for $\lambda = 1$, and verify its operation. To be able to change $\lambda$ between 1 and 10 use two variable resistors for $R_1$ or $R_2$.

```{figure} /Fig-ch7/CS10.png
---
width: 300px
name: fig:cs10
---
Proportional feedback amplifier
```
````

### Measuring amplifier for the distance sensor

The output of the distance sensor can be directly connected to one of the inputs of the comparator. But because the input impedance of the comparator changes due to different amplification settings ($\lambda$) it is possible that the output voltage of the distance sensor changes due to the relative high output impedance of the distance sensor. To exclude this phenomena a buffer amplifier can be used (see {ref}`buffer_amplifier`).  

````{admonition} Exercise 7.3
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Build the circuit shown in {numref}`fig:oa13`. Connect the analog output of the distance sensor to the input of the buffer amplifier.
- Verify the output of the buffer amplifier.
(note: Be sure a **positive 5 V** power supply is connected to the distance sensor)
- To complete this part of the circuit connect the output of the buffer amplifier to the $V_{\rm dist}$ input of the comparator.  
````

### Control circuit for the fan blower
The output voltage $V_{\rm r}$ correspond to $r(t)$ shown in {numref}`fig:cs01`, which is the control signal for the fan blowers. If output voltage $V_{\rm r}$ is directly connected to the fan blowers no reaction is observed, because the current needed to control the fan blowers cannot be supplied by the 741 OpAmp used in the proportional feedback amplifier. For this reason a voltage controlled current converter is introduced.  The converter is placed between the proportional feedback amplifier and the fan blowers. The circuit in {numref}`fig:cs11vcc` shows how it is done.

```{figure} /Fig-ch7/CS11vcc.png
---
width: 300px
name: fig:cs11vcc
---
Voltage controlled current converter
```

The voltage controlled current converter is a combination of an OpAmp and a power transistor. The TIP31 is a power transistor which can deliver sufficient current for the fan blowers ($R_{\rm  fan \; blower}$). The voltage $V_{\rm r}$, the output of the proportional feedback amplifier, is connected to the non-inverting input of the OpAmp. The output of the OpAmp is directly connected to the base $b$ of the transistor and the emitter output $e$ directly to the inverting input of the OpAmp. The high open loop gain of the OpAmp will force the emitter gate of the transistor to the required voltage $V_{\rm r}$ (because $V_{\rm +} = V_{\rm -}$), which is also across $R_{\rm fan \; blower}$. The current $I_{\rm fan \; blower} = V_{\rm r}/R_{\rm fan \; blower}$ only flows from collector $c$ to emitter $e$ and through $R_{\rm fan \; blower}$ and can reach a maximum of 0.5 A.\
In the transistor a small potential difference can be observed between the base and the emitter. This voltage drop is constant (about 0.7 V) and independent of the collector voltage, as long as the collector voltage is substantially higher than that of the base. That condition is certainly met for the circuit shown in {numref}`fig:cs11vcc`.

````{admonition} Exercise 7.4
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Build the circuit of {numref}`fig:cs11vcc` with a TIP31 power transistor and a 741 OpAmp. To test this part of the circuit, connect temporarily the non-inverting input of the voltage controlled current converter to the analog output of the variable power supply+. Change the variable power supply values from 0 to +12 V and investigate what happens to the fan blower.
````

In this control system we want to measure the height of a floating ball. The height is determined by the amount of air flow produced by the fan blower. In the previous exercise you encountered a problem that the fan blower only starts to rotate if $V_{\rm r}$ is above about 8 V. To control the system $V_{\rm r}$ must be between 8 and 15 V (maximum). For this reason we need to add an offset value of about 8 V to the output voltage $V_{\rm r}$ coming from the feedback amplifier. This can be done with a non-inverting sum amplifier (see [Exercise 6.4](#ex64) and {numref}`fig:oa12`).
The sum amplifier is placed between the proportional feedback amplifier and the voltage controlled current converter.

````{admonition} Exercise 7.5
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Build a sum amplifier as described in [Exercise 6.4](#ex64). An offset value can be set by the analog output (AO 1) of the NI Elvis system. To operate the analog output AO 1 use the 'DC Level' instrument on your NI ELVISmx Instrument Launcher.
Check this part of the circuit.
- Connect the output of the sum amplifier to the input of the voltage controlled current converter and the Fan blowers. Investigated this circuit. Use temporarily the analog output of the variable power supply+ as second input of the sum amplifier together with the offset voltage from AO 1. 
````

````{admonition} Exercise 7.6
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Complete the total circuit of the height control by connecting all parts. The two inputs of the proportional feedback amplifier can be measured by the two analog inputs AI 0 and AI 1. The two signals, Vref and the offset voltage, can be controlled with resp. AO 0 and AO 1.
- To investigate the proportional feedback system use the measuring program 'Measure input data.vi'. In this program you can select the analog inputs AI 0, AI 1 and outputs AO 0 and AO 1. Study the step response for at least 6 different values of $\lambda$. Measure how long it takes to stabilize the system without almost any oscillations after a step-like change, and/or study the final average height of the ball after the oscillation are damped.
- When the ball oscillates free with a constant amplitude, no damping and almost no growth in amplitude is observed, the ball is oscillating with the natural frequency of the system. Try to measure the natural frequency of your floating ball system.
````

## The digital PID controller
More and more computers are used to control physical systems. The advantage  of using a digital PID controller is the freedom a developer gets to design a control programme  with far more options for decision making. \
Sample time and bit resolution play an important role in designing a PID controller. When both can be kept small enough compared to the process variable the digital signals can be considered continuous. \
Important characteristics of a closed control system are: the stability, the response time and the accuracy. The first and most important condition is for the control system to be stable, next that the output reaches the desired (set) values.

A closed control system is stable when an input signal within defined boundaries (like a step function) results in an output signal also limited within certain boundaries. When the output signal diverges to infinity the control system is unstable: the change induced by the step  function does not die out. The boundary of stability in a closed system can be traced a.o. by checking the frequency dependent amplification (using a Bode plot). If we take a sinusoidal input signal the total system (PID controller and process) will cause a phase shift and amplification/attenuation of the output signal. The amount of  amplification/attenuation is given by the absolute value of the transfer function of the closed system (see eqn. {eq}`eq:yt`). The amplification is infinite when the denominator of eqn. {eq}`eq:yt` is zero:

$$
\begin{split}
1 + H ( \omega ) G ( \omega ) & = 0 \,\, \to \\
H ( \omega ) G ( \omega ) & = -1.
\end{split}
$$ (eq:ch7-4)

When $H ( \omega ) G ( \omega ) = -1$ the system is on the verge of stability. This means that:

$$
\begin{split}
| H ( \omega ) G ( \omega ) | & = 1  \\
\arg \left( H ( \omega ) G ( \omega ) \right) & = 180^{\rm o}.
\end{split}
$$ (eq:ch7-5)

The frequency of the input signal which brings the system on the verge of stability is called the *natural eigenfrequency* of the closed system. The output then oscillates with a constant amplitude. When the amplitude of the natural eigenfrequency is increased by amplification using the PID controller, through feedback the output signal will continue to grow and diverges to infinity causing the closed system to become unstable.

### Nyquist plot
An other way to display the frequency characteristic of a system is by using a Nyquist plot. In a Nyquist plot for several frequencies $\omega$ the real and imaginary parts of the complex transfer function are plotted. For a low-pass filter this results in (*check this!*):

$$
\begin{split}
{\rm Re} \left[ A(\omega) \right] & = \frac{1}{1 + \tau^2 \omega^2} \\
{\rm Im} \left[ A(\omega) \right] & = \frac{- \tau \omega}{1 + \tau^2 \omega^2}.
\end{split}
$$ (eq:ch7-6)

To obtain the sign of the Nyquist plot in various regions some coordinates are determined:

:::{list-table} Asymptotic behaviour low-pass filter
: align: left
: name: tab3

*    - $\omega = 0$ 
     - ${\rm Re[A(0)]} = 1$
     - ${\rm Im[A(0)]} = 0$
*    - $\omega=1/\tau$
     - ${\rm Re[A(1/\tau)]} = 1/2$
     - ${\rm Im[A(1/\tau)]} = -1/2$ 
*    - $\omega= \infty$
     - ${\rm Re[A(\infty)]} = 0$
     - ${\rm Im[A(\infty)]} = 0$
:::

The Nyquist plot is shown in {numref}`fig:cs12`.

```{figure} /Fig-ch7/CS12.png
---
width: 400px
name: fig:cs12
---
Nyquist plot
```

Each point on the half-circle is determined by a vector with length $| A |$ and angle $\phi = \arg(A)$ (see {numref}`tab1`).

````{admonition} Exercise 7.7
:class: note

- Draw a Nyquist plot for a first order high-pass filter. Use the results from [Exercise 4.1](#ex41).
- Verify your results with the LabVIEW programme “Show Nyquist Plot”.
````

::::{admonition} Answer
:class: dropdown

The circuit of a high-pass filter is shown in {numref}`fig:87-1`.

```{figure} /Fig-sol/87-1.png
---
width: 300px
name: fig:87-1
---
A high-pass filter
```

The transfer function for a high-pass filter is given by

$$
A ( \omega ) = \frac{R}{R + 1 / j \omega C} = \frac{j \omega \tau}{1 + j \omega \tau} = \frac{j \omega \tau}{1 + j \omega \tau} \cdot \frac{1 - j \omega \tau}{1 - j \omega \tau} = \frac{\omega^2 \tau^2 + j \omega \tau}{1 + \omega^2 \tau^2},
$$ (eq:ch7-14)

so

$$
\begin{split}
{\rm Re} [ A ( \omega ) ] &= \frac{\omega^2 \tau^2}{1 + \omega^2 \tau^2},\; {\rm and} \\
{\rm Im} [ A ( \omega ) ] &= \frac{\omega \tau}{1 + \omega^2 \tau^2}.
\end{split}
$$ (eq:ch7-15)

This leads to

:::{list-table} Asymptotic behaviour low-pass filter
: align: left
: name: tab4

*    - $\omega = 0$ 
     - ${\rm Re[A(0)]} = 0$
     - ${\rm Im[A(0)]} = 0$
*    - $\omega=1/\tau$
     - ${\rm Re[A(1/\tau)]} = 1/2$
     - ${\rm Im[A(1/\tau)]} = 1/2$ 
*    - $\omega= \infty$
     - ${\rm Re[A(\infty)]} = 1$
     - ${\rm Im[A(\infty)]} = 0$
:::

This results in the following Nyquist plot ({numref}`fig:87-2`).

```{figure} /Fig-sol/87-2.png
---
width: 500px
name: fig:87-2
---
Sketch of Nyquist plot for a high-pass filter
```

Using the *Show Nyquist Plot.vi* we can simulate the effect of several filter. For a first order Butterworth high pass filter the result shown in {numref}`fig:87-3` which matches the sketch, is obtained.

```{figure} /Fig-sol/87-3.png
---
width: 600px
name: fig:87-3
---
Nyquist plot for a high-pass filter obtained from simulation	  
```
::::

In a Nyquist plot it is easy to see whether a closed system is stable or not (see {numref}`fig:cs13`). 

```{figure} /Fig-ch7/CS13.png
---
width: 400px
name: fig:cs13
---
Nyquist plot of a closed system
```

In {numref}`fig:cs13`a the amplitude transfer is larger than 1 at a phase transfer of 180$^{\rm o}$: the signal is amplified through the feedback and the closed system becomes unstable. \
In {numref}`fig:cs13`b the amplitude transfer is smaller than 1 at a phase transfer of 180$^{\rm o}$: the signal is attenuated through the feedback and the closed system is stable.

### PID controllers
PID controllers can be in series or in parallel. Both options give more or less the same result in closed systems. In this course we will limit ourselves to PID controllers in parallel. The response function of the PID controller is given by:

$$
\begin{split}
r(t) &= G \cdot \varepsilon(t) \\
&= K_{\rm R} \left( \varepsilon(t) + \frac{1}{\tau_{\rm i}} \int_{\rm i} \varepsilon(t) {\rm d} t + \tau_{\rm d}\frac{\rm d}{{\rm d} t}_{\rm d}  \varepsilon(t) \right).
\end{split}
$$ (eq:ch7-8)

{numref}`fig:cs14` shows a block diagram for a parallel PID controller.

```{figure} /Fig-ch7/CS14.png
---
width: 450px
name: fig:cs14
---
Block diagram for a parallel PID
```

{numref}`fig:cs15` shows the step response of a parallel PID controller.

```{figure} /Fig-ch7/CS15.png
---
width: 500px
name: fig:cs15
---
Step response for a parallel PID
```

````{admonition} Exercise 7.8
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

In the lab exercise below you will investigate a number of characteristics of a closed PID control system through tuning procedure. 
- Build a third order low-pass filter with $RC = 0.5 {\rm s}$. Take different values of $C$, such that the three filters do not influence each other. Connect the output signal of the filter to AI 0+, the input signal to AO 0 and use the GROUND connection for AI 0- and ground of this filter. This filter, together with the software programme “Measure Nyquist plot PID <span>system.vi</span>” makes a closed control system.
- Measure the Nyquist plot of this closed control system using the programme “Measure Nyquist plot PID <span>system.vi</span>”. Set the PID parameters in the programme first at $K_{\rm R} = 2$, $T_{\rm i} = 0$ en $T_{\rm d} = 0$. (Note: because of the $RC$-value of 0.5 s, the Nyquist plot measurement takes more time. Once started the program has to be stopped manualy!)
- Determine from the saved Nyquist plot data the natural frequency of the closed system. (The phase shift of the output signal is then 180$^{\rm o}$ with respect to the input signal.)
- Now open the “PID <span>control.vi</span>” programme and start again the PID control. Take the start values: $K_{\rm R} = 2$, $T_{\rm i} = 0$ en $T_{\rm d} = 0$. Setting a step function at $x(t)$ of about 2 V, we can observe the step response of the closed system. Increase the proportional factor $K_{\rm R}$ and keep increasing until the closed control system is on the verge of stability. The output signal will then oscillate with a constant amplitude. Important: each time use the same step-like function in your study.
- Is this oscillation frequency equal to the previously found natural frequency? What can you say about the stability of this closed control system?
- Tune the PID control system as described in the *Dale’s closed loop PI tuning techniques* (see Canvas).
- Add various noise signals to the output of the control system using your software programme. Study the suppression of the noise with respect to the frequencies of the noise with your selected PID settings. Investigate this for about 10 frequencies between 5 and 0.001 Hz.
````