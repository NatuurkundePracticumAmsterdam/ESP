(OpAmps)=
# OpAmp circuits

So far only use has been made of discrete components like resistors, capacitors, coils and diodes. In many electronic circuits use is made of integrated circuits (ICs). ICs are small electronic blocks with specific functionality, which contain many (sometimes over a thousand) components like resistors, capacitors, coils, diodes and transistors integrated on a single device. \
An example of an IC is the operational amplifier (*OpAmp*). This chapter covers basic concepts of the OpAmp and several exercises to become familiar with common OpAmp circuits. \
The following topics will be covered:
- Differential amplifiers
- Operational amplifiers
- Feedback
- Amplifier circuits
- Differentiators and integrators
- Active filters and oscillators  

## Differential amplifiers
For amplifiers covered in {ref}`amplification` a potential difference is amplified with respect to a reference potential difference (usually 0 V or ground). A situation which  often occurs is that one needs to measure the difference between two nearly equal quantities. This for example is the case when both measured signals contain the same signal component (e.g.through pick up of noise). To address these sort of situations a differential amplifier has been designed. This amplifier has two inputs and one output with respect to ground, as shown in {numref}`fig:oa01`. 

```{figure} /Fig-ch6/OA01.png
---
width: 400px
name: fig:oa01
---
Differential amplifier
```

An ideal differential amplifier only amplifies the signal difference $v_{\rm d}$ (*differential mode*) and is not susceptible to the common signal $v_{\rm c}$ (*common mode*) at both inputs. So for identical input signals the output signal is zero. In practice, this is never the case. The quality of the amplifier is  signified in how well it is able to suppress the common mode signal. A measure for this is the C(ommon) M(ode) R(ejection) R(atio), which is defined as the ratio of the amplification of the differential mode signals $A_{\rm DM}$ and the amplification of the common mode signals $A_{\rm CM}$:

$$
CMRR = \frac{A_{\rm DM}}{A_{\rm CM}}.
$$ (eq:ch6-1)

````{admonition} Exercise 6.1
:class: note

One wants to amplify two input signals each with a common DC-component of 10 V ( =$V_{CM_{in}}$). The difference between the two input signals is in the order of 0.01 V ( =$V_{DM_{in}}$). The output signal of the amplifier is $V_{_{out}}=V_{DM_{out}}+V_{CM_{out}}$
- What is the minimal CMRR value under the condition that the unwanted part in the output signal ($V_{DM_{out}}$), due to the common signal ($V_{CM_{out}}$), is less then 1 \%?   
````

::::{admonition} Answer
:class: dropdown

Given that $V_{\rm CM}$ = 10 V, $V_{\rm D}$ = 0.01 V and $V_{\rm out, \; CM}$ = 0.01 $\cdot V_{\rm out, \; DM}$ we get 

$$
{\rm CMRR} = \frac{A_{\rm DM}}{A_{\rm CM}} = \frac{\frac{V_{\rm out, \; DM}}{V_{\rm in, \; DM}}}{\frac{V_{\rm out, \; CM}}{V_{\rm in, \; CM}}} = \frac{V_{\rm out, \; DM}}{V_{\rm out, \; CM}} \frac{V_{\rm in, \; CM}}{V_{\rm in, \; DM}} = \frac{V_{\rm out, \; DM}}{0.01 \cdot V_{\rm out, \; DM}} \frac{10}{0.01} = 10^5.
$$ (eq:ch6-2)
::::

(OA)=
## Operational amplifiers

The most common form of a difference amplifier is the operational amplifier (*OpAmp*). {numref}`fig:oa02` shows the symbols used for an OpAmp.

```{figure} /Fig-ch6/OA02.png
---
width: 250px
name: fig:oa02
---
Symbol for OpAmp
```

The $V_+$-input is called the non-inverting input when a positive potential at this input with respect to the other input results in a positive output voltage (w.r.t. ground). The $V_-$-input is called the inverting input when a positive potential at this input with respect to the other input results in a negative output voltage (w.r.t. ground). \
Depending on its use an ideal amplifier should meet certain specifications. To get an insight into this the following sections will cover a number of characteristics of OpAmps. \
OpAmps in most applications are used as voltage amplifiers. To amplify voltages correctly the settings for ideal OpAmps will be specified. For the 741-type of OpAmp, which will be used in the lab, settings will also be given within boundaries of proper operation.

### Voltage amplification
An ideal OpAmp has an amplification factor of $\infty$. This is explained in {ref}`feedback`. \
The 741 has an amplification factor of 106 dB. This corresponds to a voltage amplification of $2 \cdot 10^5$. \
There are OpAmps available with amplification factors of over 150 dB (a voltage amplification of over $3.2 \cdot 10^7$). \
A complication is that the amplification factor is often temperature dependent, even between OpAmps of the same type. {ref}`feedback` covers how the stability of amplification can be improved through feedback.

### Input impedance
Based on matching ({ref}`matching`) an ideal OpAmp should have an input impedance of infinity. \
The 741 has an input impedance of 2 M$\Omega$. \
There are OpAmps with an input impedance of $10^{12} \, \Omega$.

### Output impedance
Again, based on matching ({ref}`matching`) an ideal OpAmp should have an output impedance of zero. \
The 741 has an output impedance of 75 $\Omega$. \
There are OpAmps with an output impedance of a few Ohm only.

### Maximum output current
As important as the low output impedance is the maximum output current an OpAmp can deliver. \
For the 741 the maximum output current is 20 mA. \
For high power applications OpAmps are available that can deliver a maximum output current of a few amperes.

### Voltage supply
An OpAmp usually has one or two input supplies. The exact values of the voltage supplies is not so important, however, the stability is. \
The 741 can be operated at voltage supplies between $\pm$ 5 to $\pm$ 15 V.

### Output voltage range
The output voltage of an OpAmp is limited by the voltage supply chosen. At a voltage supply of $\pm$ 15 V the output voltage will always remain below +15 V and above -15 V. How much less or more depends on the type of OpAmp. \
So due to the large amplification factors, only for very small input potential differences $V_{\rm out} = A \cdot V_{\rm in}$. This seems odd. However, in {ref}`feedback` we will show that using external components larger input signals can be amplified.

### Common mode rejection ration
An ideal OpAmp used as a difference amplifier should have a CMRR of infinity. \
The 741 has a CMRR of 90 dB. \
The best available OpAmps have a CMRR over 160 dB.

### Input 'bias current'
When the potential difference of the input signals of an OpAmp is zero for an ideal OpAmp also the  currents of both inputs will be zero. For real OpAmps this is not the case (see {numref}`fig:oa03`). This is due to the way OpAmps internally operate. The size of these currents, which are called bias currents, depend on whether the input circuit of the OpAmp uses transistors or FETS. \
The 741, based on transistors, has a bias current of about 80 nA. \
For OpAmps based on FETS smaller bias currents below $10^{-15}$ A can be reached. \
The bias currents result in potential differences across resistors connected to the inputs of the OpAmp. For small input signals this may lead to errors in the output signal.

```{figure} /Fig-ch6/OA03.png
---
width: 400px
name: fig:oa03
---
Input bias currents
```

### Input 'offset' potential difference
For an ideal OpAmp when the input potential difference is zero the output potential difference is also zero. Again, due to the internal components used in an OpAmp this is not the case for real OpAmps.  \
The input offset potential difference is defined as the potential difference required at the inputs to obtain a zero output potential difference. \
For a 741 the offset potential difference is about 2 mV.\
For better OpAmps the offset potential difference is less than 1 mV. \
Most OpAmps offer to tune the offset potential difference to zero using an external voltage divider. In practice this does not function perfectly as the offset potential difference is temperature dependent. \
For the 741 the temperature dependence is about $10 \, \mu {\rm V} / {\rm K}$. \
For better OpAmps this value is less than $1 \, \mu {\rm V} / {\rm K}$.

(fOpAmp)=
### Frequency characteristic of an OpAmp

An ideal OpAmp has an amplification factor which is independent of frequency. In practice this is not the case. A real OpAmp behaves like an ideal OpAmp followed by a low pass filter. \
{numref}`fig:oa04` shows the frequency characteristic of a 741.

```{figure} /Fig-ch6/OA04.png
---
width: 500px
name: fig:oa04
---
Frequency characteristic of a 741 OpAmp
```

The very low cutoff frequency, and hence small bandwidth of only a few Hz, seems to make the 741 useless for nearly any application. In {ref}`feedback` it will be shown that feedback can enhance the bandwidth of the amplifier considerably.

(feedback)=
## Feedback

Not only in electronics, but also for control systems feedback plays an important role. \
The importance of feedback will be illustrated by two examples of how to control the room temperature.

### Open and closed loop systems
The first way to control the room temperature is to turn the knob of the radiator a certain amount and hope that this will result in the desired room temperature. In general this will of course result in a room temperature that is either too high or too low. Even if the person that turns the knob based on experience sets it nearly correct the desired temperature may still differ due to external factors, such as a change in the temperature outside or e.g. the opening of a window. Clearly, this example of an *'open loop'* system does not provide an optimal solution. \
A much better solution is to install a thermostat. The user sets the thermostat to the desired temperature. The thermostat measures the actual room temperature, compares it to the temperature set and based on the difference determines whether the heater should be turned on more or less. The knob on the  radiator does not need to be adjusted (although it should be set such that water can flow through the radiator obviously). At a change of the temperature outside the thermostat will keep the room temperature at the desired setting. Such a system that includes feedback is called a *'closed loop* system.\
Systems including feedback use information provided by the output signal to regulate the signal at the input in such a way that the output signal reaches it desired value. \
{numref}`fig:oa05` illustrates schematically the difference between an open and closed loop system. 

```{figure} /Fig-ch6/OA05.png
---
width: 500px
name: fig:oa05
---
Open and closed loop system
```
The user has an *objective* and hopes that the *result* will match it. The *'forward path'* converts the input signal into an output signal. In the open loop system the position of the knob on the radiator could represent the input signal and the amount of heat per second given by the radiator the output signal. In fact the final output signal is the temperature reached, which is determined by the heat given by the radiator, and the heat lost through the walls, windows, etc. \
In the closed loop system apart from the *'forward path'* a *'feedback path'* is present. Through the latter the output signal, in the example the actual temperature, is fed to the input for comparison with the user set temperature through the *'comparator'*. The difference (*'error'*) signal is used as an input for the forward path (the heater).

### Feedback mechanisms

Feedback systems are distinguished by positive and negative feedback. \
At negative feedback the feedback signal tries to reduce the input signal, positive feedback tries to increase the input signal. \
For a quantitative treatment of feedback {numref}`fig:oa06` is useful. 

```{figure} /Fig-ch6/OA06.png
---
width: 400px
name: fig:oa06
---
Feedback system
```

$A$ represents the transfer function of the forward path and $B$ the transfer function of the feedback path, which, in principle both may be complex. Instead of the transfer function often the term amplification factor or 'gain' is used. \
From {numref}`fig:oa06` it follows that

$$
\frac{Y}{A} = X - BY.
$$ (eq:ch6-3)

This may be re-expressed as

$$
\begin{split}
G &= \frac{Y}{X} = \frac{A}{1 + AB} \\
\\
G &= \frac{{\rm Forward \, Gain}}{1 + {\rm Loop \, Gain}}.
\end{split}
$$ (eq:G)

:::{note}
Eqn. {eq}`eq:G` follows from {numref}`fig:oa06` assuming the feedback signal is subtracted from the input signal. Some textbooks add both signals. In that case eqn. {eq}`eq:G` becomes

$$
G = \frac{A}{1 - AB}.
$$ (eq:ch6-4)
:::

The term *'loop gain'* refers to the amplification through the forward path and back through the feedback path. \
The quantity $G$ is the ratio between the output and input signal and represents the *'overall gain'* of the total system. \
Since the 'forward gain' $A$ is the gain for the system without feedback (so without a closed loop) it is often called the *'open loop gain'*. $G$ is also referred to as the *'closed loop gain'*. \
The behavior of the total system depends on the magnitudes and signs of both $A$ and $B$. The following situations can be distinguished:
- **No feedback:** $B$ = 0 \
Eqn. {eq}`eq:G` turns into: $G = A$. \
The overall gain without feedback is equal to the  forward or open loop gain.
- **For the loop gain holds:** $-2 < AB < 0$ \
In this case the absolute value of the term $1 + AB$ is less than 1. From eqn. {eq}`eq:G` it then follows that $|G| > |A|$. Effectively the feedback causes an increase of the input signal: we are dealing with positive feedback.
- **The loop gain $AB$ is equal to -1** \
This is a special case of feedback. Eqn.{eq}`eq:G` gives $G = \infty$. \
This is a remarkable result. Any input signal is amplified infinitely. In practice this means that any input signal, even close to zero, will push the output of the system to a maximum positive or negative output signal. A system with such an extreme form of feedback turns out to be an essential part of an oscillator, as we will see later.
- **The loop gain $AB$ is positive** \
In this case the term $1 + AB$ is larger than 1. Eqn.{eq}`eq:G` gives $G < A$. Effectively the feedback results in a reduction of the input signal: we are dealing with negative feedback. \
When the loop gain $AB >> 1$ eqn. {eq}`eq:G` can be simplified to eqn. {eq}`eq:G2` (*check this!*). \
This also is a remarkable result. The 'overall gain' $G$ in this case is  determined by the characteristics of the 'feedback path' B and not by the characteristics of the original system without feedback. B is also called the feedback coupling factor.

$$
G \approx \frac{1}{B}.
$$ (eq:G2)

````{admonition} Example 
:class: tip

Assume that in the circuit shown in {numref}`fig:oa06` system $A$ is an OpAmp with an amplification factor of $A = 100000$. System $B$ is designed such that the feedback signal is 1 \% of the output signal. So $B = 1 / 100$. \
Substituting $A$ and $B$ into eqn. {eq}`eq:G` gives $G = 99.90$. \
Using eqn. {eq}`eq:G2` results in $G = 100$. The approximation in this case leads to an error of 0.1 \%. \
When $A$ is increased by a factor of 2 eqn.{eq}`eq:G` gives $G = 99.95$. So a change in $A$ by a factor of 2 causes a change in the 'overall gain' of 0.05 \% only!
````

### Effect of negative feedback on the frequency characteristic
The frequency characteristic of an OpAmp drops already after a few Hz as was shown in {ref}`fOpAmp`. In this section we will show that this frequency characteristic can be improved  using negative feedback. \
The characteristic of {numref}`fig:oa04` strongly resembles that of a low pass filter. Therefore is seems logical to replace the 'open loop gain' $A$ by $A(\omega)$, where:

$$
A(\omega) = \frac{A_0}{1 + j \omega \tau}.
$$ (eq:Alp)

$A_0$ is the open loop amplification of the DC-signal and $\tau$ is the time constant of the low pass filter. Substitution of eqn. {eq}`eq:Alp` into eqn. {eq}`eq:G` gives:

$$
G(\omega) = \frac{\frac{A_0}{1 + j \omega \tau}}{1 + \frac{A_0}{1 + j \omega \tau} \cdot B}.
$$ (eq:Glp)

Eqn. {eq}`eq:Glp` can be re-written as:

$$
G(\omega) = \frac{A_0}{1 + A_0 \cdot B} \cdot \frac{1}{1 + j \omega \frac{\tau}{ {1 + A_0 B}}}.
$$ (eq:Glp2)

Based on eqn. {eq}`eq:Glp2` the following can be concluded:

For DC-signals the feedback results in a decrease of the amplification factor of $1 + A_0 B$.

For AC-signals the feedback results in a decrease of the amplification factor and also of the time constant of $1 + A_0 B$. As a consequence the cutoff frequency increases with a factor of $1 + A_0 B$ and the same holds for the bandwidth of the amplifier. Combining these two  effects results in: 

> *amplification factor x bandwidth = constant* 

In relation to the above the quantity *'unity-gain-bandwidth'* is often used. This refers to the bandwidth where the amplification is reduced to one. So: 

> *amplification factor x bandwidth = unity-gain-bandwidth* 

{numref}`fig:oa07` shows the frequency characteristic of the 741 OpAmp with feedback, illustrating the effects discussed above.

```{figure} /Fig-ch6/OA07.png
---
width: 500px
name: fig:oa07
---
Frequency characteristic of the 741 OpAmp with feedback
```

{numref}`fig:oa07` shows that the unity-gain-bandwidth of the 741 OpAmp is about 1 MHz.

````{admonition} Exercise 6.2
:class: note

- A particular OpAmp had a unity-gain-bandwidth of $10^7$ Hz and a steady state amplification of $A > 10^5$. One builds with this OpAmp an amplifier with a feedback coupling factor of 1/50. Determine the gain factor and the bandwidth of this amplifier.   
- One wants to build an amplifier with a wide frequency bandwidth and a large amplification factor $D$. \
Explain why it is better to use two amplifier stages, each with a gain equal to $\sqrt{D}$, than to use one amplifier with an amplification of $D$.
````

::::{admonition} Answer
:class: dropdown

We consider an OpAmp with a $UGB$ of $10^7$ Hz, a steady state amplification of $A > 10^5$ and a feedback $B = 0.02$. \
The gain factor of the amplifier is 

$$
G = \frac{A}{1 + AB} \approx \frac{1}{B} = \frac{1}{0.05} = 50.
$$ (eq:ch6-6)

Since $UGB = G \cdot BW$ the bandwidth is given by

$$
BW = \frac{UGB}{G} = \frac{10^7 \; {\rm Hz}}{50} = 2 \cdot 10^5 > 10^5 \; {\rm Hz}.
$$ (eq:ch6-7)

Using two amplifiers with lower $G$ is better as at lower $G$ the bandwidth is larger (the BW at $\sqrt{G}$ is larger than at $G$). 
::::

### Effect of negative feedback on the input and output impedance
{numref}`fig:oa08` shows an amplifier with an 'open loop gain' $A$ and a feedback factor $B$.

```{figure} /Fig-ch6/OA08.png
---
width: 400px
name: fig:oa08
---
OpAmp with negative feedback
```

The behavior of the feedback on input will be considered where the feedback signal is subtracted from the input signal:

$$
\begin{split}
V_{\rm in}^{'} = V_{\rm in} - B \cdot V_{\rm out} = V_{\rm in} - AB \cdot V_{\rm in}^{'} \\
\to V_{\rm in}^{'} \left( 1 + AB \right) = V_{\rm in}.
\end{split}
$$ (eq:Vin)

From eqn. {eq}`eq:Vin` and $V_{\rm in}^{'} = I_{\rm in }Z_{\rm in}$ it follows that the input impedance of the OpAmp with negative feedback is given by:

$$
Z_{\rm in, \, eff} = \frac{V_{\rm in}}{I_{\rm in}} = Z_{\rm in} \left( 1 + AB \right).
$$ (eq:ch6-8)

So the effective input impedance $Z_{\rm in, \, eff}$ is increased by a factor of $(1 + AB)$ due to the negative feedback. \
{numref}`fig:oa09` shows the same amplifier with negative feedback as {numref}`fig:oa08` but with a focus on the output signal. 

```{figure} /Fig-ch6/OA09.png
---
width: 400px
name: fig:oa09
---
OpAmp with negative feedback
```

The amplifier can be considered as a voltage source with an output voltage equal to $A$ times the potential difference $V_{\rm in}$ and $B V_{\rm out}$ in series with an output impedance $Z_{\rm out}$. The direction of the output current is into the amplifier (by definition). The following holds:

$$
V_{\rm out} = A \left( V_{\rm in } - B V_{\rm out} \right) + I_{\rm out}Z_{\rm out},
$$ (eq:Vout)

where it is assumed that the current through $B$ is very small. \
The effective output impedance is equal to the ratio of $V_{\rm out}$ and $I_{\rm out}$  when the input is short cut (i.e. $V_{\rm in} = 0$). Substitution into eqn. {eq}`eq:Vout` gives:

$$
Z_{\rm out, \, eff} = \frac{Z_{\rm out}}{1 + AB}.
$$ (eq:ch6-9)

So the effective output impedance $Z_{\rm out, \, eff}$ is decreased by a factor of $(1 + AB)$ due to the negative feedback. \
Concluding, negative feedback by increasing the input impedance and reducing the output impedance, improves the behavior of the voltage amplifier.

## OpAmp circuits with negative feedback
An OpAmp amplifies the difference signal of the two inputs. When including feedback {numref}`fig:oa06` can be replaced by {numref}`fig:oa10`.

```{figure} /Fig-ch6/OA10.png
---
width: 300px
name: fig:oa10
---
OpAmp with feedback
```

Below a number of OpAmp ciruits with feedback will be discussed, assuming ideal OpAmps. In other words, we assume that:
- the 'open loop gain' is infinite
- the input impedance of the OpAmp is infinite
- the output impedance of the OpAmp is zero

### Non-inverting amplifier
{numref}`fig:oa11` shows a schematic of a non-inverting amplifier.

```{figure} /Fig-ch6/OA11.png
---
width: 300px
name: fig:oa11
---
Non-inverting amplifier
```

Comparing {numref}`fig:oa10` and {numref}`fig:oa11` gives:

$$
B = \frac{R_1}{R_1 + R_2}.
$$ (eq:ch6-10)

According to eqn. {eq}`eq:G2`:

$$
G = \frac{1}{B} = \frac{R_1 + R_2}{R_1}.
$$ (eq:G3)

This result can also be derived as follows: \
Since $A$ is infinitely large and $V_{\rm out}$ is finite:

$$
V_- = V_+ = V_{\rm in}.
$$ (eq:Vin2)

:::{note}
This argument holds for all OpAmp circuits with negative feedback, so eqn. {eq}`eq:Vin2` can be applied to all of them.
:::

Due to the infinite high input impedance no current runs to the inputs of the OpAmp. Therefore:

$$
V_- = \frac{R_1}{R_1 + R_2} V_{\rm out}.
$$ (eq:Vmin)

Combining eqns. {eq}`eq:Vin2` and {eq}`eq:Vmin` gives:

$$
G = \frac{V_{\rm out}}{V_{\rm in}} = \frac{1}{B} = \frac{R_1 + R_2}{R_1},
$$ (eq:G4)

which is the same as eqn. {eq}`eq:G3`.

````{admonition} Exercise 6.3
:class: note

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Design in Multisim a non-inverting amplifier with a gain of 10.
````

::::{admonition} Answer
:class: dropdown

For the amplifier with a gain of 10 we used $R_1 = 1 \; {\rm k}\Omega$ and $R_2 = 9 \; {\rm k}\Omega$.

$$
G = \frac{R_1 + R_2}{R_1} = 10.
$$ (eq:ch6-11)

The Multisim circuit and result is shown in {numref}`fig:63`. 

```{figure} /Fig-sol/63.png
---
width: 600px
name: fig:63
---
Amplifier with a gain of 10
```
::::

:::{admonition} Exercise 6.4
:class: note
:name: ex64

- Give for the circuit shown in {numref}`fig:oa12` an expression for $V_{\rm out}$ as a function of $V_1$ and $V_2$.
- What is the name of this circuit?

```{figure} /Fig-ch6/OA12.png
---
width: 450px
name: fig:oa12
---
A non-inverting amplifier
```
:::

::::{admonition} Answer
:class: dropdown

The circuit under investigation is shown in {numref}`fig:64`. 

```{figure} /Fig-sol/64.png
---
width: 600px
name: fig:64
---
Non-inverting sum amplifier
```

The gain is given by

$$
G = \frac{R_1 + R_2}{R_1} = \frac{5{\rm k} + 10{\rm k}}{5{\rm k}} = 3.
$$ (eq:ch6-12)

The Th&eacute;venin voltages are

$$
\begin{split}
V_{\rm Th}^1 &= \frac{(10{\rm k} || 10{\rm k})}{10{\rm k} + (10{\rm k} || 10{\rm k})} V_1 = \frac{5{\rm k}}{10{\rm k} + 5{\rm k}} V_1 = \frac{1}{3} V_1, \\
V_{\rm Th}^2 &= \frac{1}{3} V_2, \\
V_{\rm Th} &= \frac{1}{3} \left( V_{\rm Th}^1 + V_{\rm Th}^2 \right).
\end{split}
$$ (eq:ch6-13)

So

$$
V_{\rm out} = 3 \cdot \frac{1}{3} \left( V_{\rm Th}^1 + V_{\rm Th}^2 \right) = V_1 + V_2.
$$ (eq:ch6-14)

This amplifier is called a non-inverting sum amplifier. 
::::

(buffer_amplifier)=
### Buffer amplification (voltage follower)
A special case of a non-inverting amplifier is a buffer amplifier as shown in {numref}`fig:oa13`.

```{figure} /Fig-ch6/OA13.png
---
width: 300px
name: fig:oa13
---
A buffer amplifier
```

Comparing {numref}`fig:oa11` and {numref}`fig:oa13` tels us $R_1 = \infty$ and $R_2 = 0$. Substitution into eqn. {eq}`eq:G4` gives:

$$
G = \frac{0 + \infty}{\infty} = 1.
$$ (eq:ch6-15)

The amplification factor is 1. This is not a shocking result. However, do realize that the input signal is connected to a very high input impedance of the OpAmp. So the input source hardly experiences a load. Later we will show that the buffer amplifier has a very low output impedance, and therefore can have a substantial load.

### Inverting amplifier
{numref}`fig:oa14` shows the schematic of an inverting amplifier.

```{figure} /Fig-ch6/OA14.png
---
width: 500px
name: fig:oa14
---
Inverting amplifier
```

The $+$ input of the OpAmp in {numref}`fig:oa14` is grounded. So $V_+ = 0$. Then using eqn.{eq}`eq:Vin2` $V_- = 0$. The $-$ input is connected to a *'virtual ground'*. \
Because the inputs of the OpAmp draw no current, any current running throufg $R_1$ also has to run through $R_2$. This results in:

$$
I = \frac{V_{\rm in } - 0}{R_1} = \frac{0 - V_{\rm out}}{R_2}.
$$ (eq:I)

From eqn. {eq}`eq:I` it follows that:

$$
G = \frac{V_{\rm out}}{V_{\rm in}} = -\frac{R_2}{R_1}.
$$ (eq:Gia)

````{admonition} Exercise 6.5
:class: note

{numref}`fig:oa15` shows a special case of an inverting amplifier, a *current to voltage converter*.  
- Give an expression for the output voltage $V_{\rm out}$ as a function of the input current $I$ for the circuit shown in {numref}`fig:oa15`.

```{figure} /Fig-ch6/OA15.png
---
width: 500px
name: fig:oa15
---
Current to voltage converter
```

If we use a resistor instead of this circuit, we can also convert current into voltage.
- What is the major advantage of the circuit in {numref}`fig:oa15` compared to a resistance.  
````

::::{admonition} Answer
:class: dropdown

* Using {numref}`fig:oa15` we get:

$$
\begin{split}
&V_- - V_{\rm out} = IR, \\
&V_+ = V_- = 0V, \\
&V_{\rm out} = - IR.
\end{split}
$$ (eq:ch6-16)

* Using an OpAmp is better than using a resistor as $Z_{\rm in} = \infty$ and $Z_{\rm out} = 0$. 
::::

````{admonition} Exercise 6.6
:class: note

{numref}`fig:oa16` also shows a special case of an inverting amplifier, using a Zener diode instead of a resistor in the feedback.  

```{figure} /Fig-ch6/OA16.png
---
width: 400px
name: fig:oa16
---
Inverting amplifier with Zener diode in feedback
```

Given $V_{\rm in}$ as a sinusoidal signal with an
amplitude of 10 V and $Z_{\rm d}$ as a Zener diode with
a zener voltage of 4 V and a turn on voltage
0.7 V:
- Sketch $V_{\rm in}$ and $V_{\rm out}$ as a function of time. Explain the sketches. 

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```

- Verify your result using Multisim.
````

::::{admonition} Answer
:class: dropdown

The circuit concerned is show in {numref}`fig:66`.

```{figure} /Fig-sol/66.png
---
width: 600px
name: fig:66
---
Inverting amplifier with Zener diode in feedback
```

The signal is inverted and clipped at +4 V and -0.6 V.\
When $V_-$ gets only a little bit positive (the blue trace in figure 6.6) $V_{\rm out}$ becomes negative. So the diode is forward biased with a gain $G = 1 / B = 1$. At a low frequency the amplification will cause $V_{\rm out}$ to grow towards -15 V. However, at approximately -0.6 V the diode will conduct with a voltage drop across the diode of approximately -0.6 V. Because there is feedback $V_+ = V_- = 0$ V. Hence, there will be a voltage drop across the resistor $R$. \
When $V_-$ gets only a little bit negative $V_{\rm out}$ becomes positive. So the diode is reversed biased with a gain $G = A / 1 + AB = A$. At a low frequency the amplification A will be large and immediately result in $V_{\rm out}$ = +15 V. However, when the Zener breakdown voltage of 4 V is reached the diode will clip $V_{\rm out}$ to 4 V. 
::::

### Differential amplifier
The amplifier circuit shown in {numref}`fig:oa17` is a combination of a non-inverting and inverting amplifier. 

```{figure} /Fig-ch6/OA17.png
---
width: 400px
name: fig:oa17
---
Differential amplifier
```

To determine the relation between $V_{\rm out}$, $V_1$ and $V_2$ the superposition theorem is used.

*Effect of $V_1$ on $V_{\rm out}$ ($V_2$ is grounded)* \
This situation resembles an inverting amplifier:

$$
V_{\rm out, \, 1} = - \frac{R_2}{R_1} \cdot V_1 .
$$ (eq:ch6-17)

*Effect of $V_2$ on $V_{\rm out}$ ($V_1$ is grounded)* \
This situation resembles a non-inverting amplifier. $V_{+}$ is given by:

$$
V_+ = \frac{R_2}{R_1 + R_2} \cdot V_2.
$$ (eq:Vplus) 
Combining eqns. {eq}`eq:G4` and {eq}`eq:Vplus` results in:

$$
V_{\rm out, \, 2} = \frac{R_2}{R_1} \cdot V_2.
$$ (eq:ch6-18)

The total output voltage $V_{\rm out}$ is thus given by:

$$
V_{\rm out} = V_{\rm out, \, 1} + V_{\rm out, \, 2} =  \frac{R_2}{R_1} \cdot (V_2 - V_1).
$$ (eq:Vdiff)

The output voltage is proportional to the potential difference between both inputs.

### Instrumentation amplifier
The differential amplifier of {numref}`fig:oa17` has the disadvantage of a relatively low input impedance. For the $-$ input $Z_{\rm in} = R_1$ and for the $+$ input $Z_{\rm in} = R_1 + R_2$. \
Another disadvantage is the relative low CMRR as a result of the tolerances of the resistors used. For the differential amplifier the output voltage is given eqn. {eq}`eq:Vdiff`. Only the difference between $V_1$ and $V_2$ is amplified. A common component in both $V_1$ and $V_2$ does not contribute to $V_{\rm out}$. The CMRR should therefore be infinite. However, in the derivation of eqn. {eq}`eq:Vdiff` it is assumed that the two resistors $R_1$ are identical and that the same holds for the two resistors $R_2$. In practice, this is never exactly the case. When the tolerances of the resistors are $\varepsilon \cdot 100$\%, then it can be shown that:

$$
{\rm CMRR} \geq \frac{1 + R_2/R_1}{4 \varepsilon}.
$$ (eq:CMMR)

````{admonition} Exercise 6.7
:class: note

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
-  First design in Multisim a differential amplifier ({numref}`fig:oa17`) with a gain factor of 10.
- Calculate with eqn. {eq}`eq:CMMR` the lower limit of the CMRR. The tolerance of resistor $R_1$ and $R_2$ are both 5\%.
```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
-  Verify this result of CMRR with the Multisim design by increasing a resistance $R_1$ with 5\% and lowering the corresponding resistance of $R_2$ with 5\%, and also lowering the other $R_1$ with 5\% and increasing the corresponding resistor $R_2$ with 5\%.
````

::::{admonition} Answer
:class: dropdown

The circuit concerned and relevant values for each component is shown in {numref}`fig:67`.

```{figure} /Fig-sol/67.png
---
width: 600px
name: fig:67
---
Differential amplifier with a gain of 10
```

The lowest CMRR value is found with $R_2 - 5\%$ and $R_1 + 5 \%$.
With $V_{\rm out} = \frac{R_2}{R_1} (V_2 - V_1)$, $R_2 = 10$ k$\Omega$, $R_1 = 1$ k$\Omega$, and $\epsilon$ = 0.05 we get 

$$
{\rm CMRR} \geq \frac{1 + R_2 / R_1}{4 \epsilon} \geq \frac{1 + 9500/1050}{0.2} \geq 50.24.
$$ (eq:ch6-19)

From the measurement it follows that 

$$
\begin{split}
&V_2 = V_1 = 0.5 \; {\rm V} \rightarrow A_{\rm CM} = \frac{V_{\rm out, \; CM}}{V_{\rm in, \; CM}} = \frac{0.083173}{0.5} = 0.166346 \\
&V_3 = 0.4 \; {\rm V}, \; V_4 = 0.6 \; {\rm V} \rightarrow A_{\rm DM} = \frac{V_{\rm out, \; DM}}{V_{\rm in, \; DM}} = \frac{1.909}{0.2} = 9.545 \\
&{\rm CMRR} = \frac{A_{DM}}{A_{CM}} =\frac{9.545}{0.166346} = 57.4 > 50.24.
\end{split}
$$ (eq:ch6-20)
::::

Both disadvantages are considerably reduced for the circuit shown in {numref}`fig:oa18`. 

```{figure} /Fig-ch6/OA18.png
---
width: 500px
name: fig:oa18
---
Instrumentation amplifier
```

The first part (A) of this circuit has two functions: (1) increasing the input impedances, and (2) increasing the CMRR. The second part (B) is an ordinary differential amplifier.\
First, consider part A. The OpAmps 1 and 2, both with feedback $R_{\rm b}$ act as buffer amplifiers, increasing the input impedances substantially. \
The resistor $R_{\rm a}$ acts like a balancing resistor, increasing the CMRR. This can be seen by considering the pure common mode signal first: $V_1 = V_2 = V_{\rm c}$. Due to the feedback through resistors $R_{\rm b}$ the voltages on both sides of $R_{\rm a}$ are equal. Therefore, no current runs through $R_{\rm a}$, and also not through  the resistors $R_{\rm b}$. Hence, $V_1^{'} = V_1$ and $V_2^{'} = V_2$. For a common mode signal the total circuit acts the same as the original differential amplifier. \
Next consider the purely differential signal: $V_1 = - V_2 = V_{\rm d}/2$. The potential difference across $R_{\rm a}$ then equals $V_{\rm d}$, resulting in a current through $R_{\rm a}$ of $V_{\rm d}/R_{\rm a}$. This is also the current that passes through $R_{\rm b}$, resulting in a potential difference across resistors $R_{\rm b}$ of $R_{\rm b} V_{\rm d}/R_{\rm a}$. \
The input voltages of the differential amplifier are given by:

$$
\begin{split}
V_1^{'} &= V_1 + (R_{\rm b}/R_{\rm a}) V_{\rm d} \\
V_2^{'} &= V_2 - (R_{\rm b}/R_{\rm a}) V_{\rm d} \\
\Delta V &= V_1^{'} - V_2^{'} = V_{\rm d} ( 1 + 2 R_{\rm b}/R_{\rm a}).
\end{split}
$$ (eq:deltaV)

The differential amplification is therefore increased by a factor $1 + 2 R_{\rm b}/R_{\rm a}$, while the common mode amplification remained the same. The CMRR is therefore also increased by a factor of $1 + 2 R_{\rm b}/R_{\rm a}$.


````{admonition} Exercise 6.8
:class: note

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
-  Design in Multisim an instrumentation amplifier with a differential amplification factor of 30. Make use of your design of exercise 6.7.
- Check whether the CMRR is really increased by the factor $1 + 2 R_{\rm b} /R_{\rm a}$.
````

::::{admonition} Answer
:class: dropdown

The circuit concerned and relevant values for each component is shown in {numref}`fig:68`.

```{figure} /Fig-sol/68.png
---
width: 600px
name: fig:68
---
Instrumentation amplifier with a gain of 30
```

The same input voltages were used as in exercise 6.7: $R_a = R_b = 1$ k$\Omega$, which should result in an increase in the amplification $A$ and CMRR by a factor of $(1 + 2 R_b / Ra) = 3$ so the overall gain becomes 30. This is the case. Also for the measurement (using the circuit of exercise 6.7) the CMRR increases with a factor of 3 for $R_b = R_a$.

The overall gain of the instrumentation amplifier is

$$
G = \frac{5.561}{0.2} = 27.8.
$$ (eq:ch6-21)

This is nearly the same as $3 \cdot 9.545 = 28.6$. The slight difference is due to resistor values of the differential amplifier part of the instrumentation amplifier.
The CMMR is

$$
{\rm CMRR} = \frac{5.561 / 0.2}{0.083173 / 0.5} = 167.
$$ (eq:ch6-22)

This is nearly the same as $3 \cdot 57.4 = 172$, three times the CMRR of the differential amplifier of exercise 6.7.
::::

### Integrator
The integrator ({numref}`fig:oa19`) strongly resembles the inverting amplifier ({numref}`fig:oa14`), where $R_2$ is replaced by a capacitor $C$. Also for the integrator the $V_-$ is connected to a virtual ground and $I_{\rm C} = I_{\rm R}$.  

```{figure} /Fig-ch6/OA19.png
---
width: 400px
name: fig:oa19
---
Integrator
```

So:

$$
I_{\rm C} = \frac{V_{\rm in}}{R} =I_{\rm R}.
$$ (eq:IC)

Since $V_-$ is connected to a virtual ground:

$$
V_{\rm out} = - V_{\rm C},
$$ (eq:Vout2)

where $V_{\rm C}$ is the potential difference across the capacitor $C$. The minus sign is from the definition that $I_{\rm C}$ is directed from $V_-$ to $C$. The relation between $I_{\rm C}$  and $V_{\rm C}$ is given by:

$$
I_{\rm C} = \frac{\partial Q_{\rm C}}{\partial t} = C \frac{\partial V_{\rm C}}{\partial t}.
$$ (eq:IC2)

Combining eqns.{eq}`eq:IC`, {eq}`eq:Vout2` and {eq}`eq:IC2`, the solution of the differential equation is given by:

$$
V_{\rm out} = - \frac{1}{RC} \int \limits_0^t{V_{\rm in} {\rm d}t} + V_{\rm out}(t = 0).
$$ (eq:Vout3)

So the output voltage is proportional to the integrated input voltage. The proportionality constant is the time constant $RC$. It is also called the integration constant. \
A problem for the integrator is that even at an input signal of 0 after some time due to the offset voltage and the bias current of the OpAmp the capacitor $C$ gets charged. Since $V_-$ is connected to a virtual ground $V_{\rm out}$ will  grow until it either reaches the positive or negative voltage supply. This is called *drift*. This drift can be prevented using a bypass resistor $R_{\rm C}$ parallel to the capacitor $C$ (see {numref}`fig:oa20`). 

```{figure} /Fig-ch6/OA20.png
---
width: 400px
name: fig:oa20
---
Integrator with a bypass resistor
```

Through the bypass resistor $R_{\rm C}$ the capacitor $C$ can discharge the voltage build up due to the offset voltage and bias current. \
To determine the value of $R_{\rm C}$ the frequency characteristic of the circuit shown in {numref}`fig:oa20` should be investigated. Applying eqn. {eq}`eq:Gia` for the inverted amplifier with  $R_1 = R$  and $R_2 = Z \cdot ( R_{\rm C} || C)$ results in the transfer function (*check this!*):

$$
A = - \frac{R_{\rm C}}{R} \cdot \frac{1}{1 + j \omega R_{\rm C} C}.
$$ (eq:Abp)

Without the bypass resistor $R_{\rm C}$ the transfer function would be:

$$
A = - \frac{1}{j \omega RC}.
$$ (eq:Abp2)

From eqn. {eq}`eq:Abp2` it can be seen directly that slowly varying signals, such as offset voltages and bias currents result in a large transfer function. Eqn. {eq}`eq:Abp` limits the transfer function for slowly varying signals to $- R_{\rm C}/R$. \
When $\omega \gg 1/(R_{\rm C}C)$ eqns. {eq}`eq:Abp` and {eq}`eq:Abp2` are nearly the same, and the circuit shown in {numref}`fig:oa20` therefore behaves as an integrator.

````{admonition} Exercise 6.9
:class: note

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Design in Multisim an integrator (with a bypass resistor $R_{\rm C}$) having a time constant of 0.01 s and check eqn. {eq}`eq:Vout3`. 
- Study the frequency behavior and give the results in a Bode plot (both phase and amplitude) and check whether it corresponds with eqn. {eq}`eq:Abp`.
````

::::{admonition} Answer
:class: dropdown

The circuit and components chosen are shown in {numref}`fig:69-1`.

```{figure} /Fig-sol/69-1.png
---
width: 600px
name: fig:69-1
---
Integrator circuit
```

The output voltage is given by 

$$
V_{\rm out} = - \frac{1}{RC} \int_0^t V_{\rm in} {\rm d}t + V_{\rm out} (t=0).
$$ (eq:ch6-23)

The amplification is given by 

$$
A = - \frac{R_C}{R} \cdot \frac{1}{1+ j \omega R_C C}.
$$ (eq:ch6-24)

For slowly varying signals $A \approx - \frac{R_C}{C}$ and for $\omega \gg 1 / R_C C$ $A \approx \frac{1}{j \omega R C}$. 

The modulus $|A|$ and phase $\Phi$ are given by 

$$
\begin{split}
&|A ( \omega) | = \frac{R_C}{\sqrt{R^2 + (\omega R R_C C)^2}} = \frac{R_C}{\sqrt{R^2 + (2 \pi f R R_C C)^2}}, \\
&\Phi = \tan^{-1} \left( \frac{0}{R_C} \right) - \tan^{-1} \left( \omega R_C C \right) = - \tan^{-1} \left( 2 \pi f R_C C \right).
\end{split}
$$ (eq:ch6-25)

{numref}`fig:69-2` to {numref}`fig:69-4` show the results of the simulation and a comparison between the simulation and the theoretical calculations.

```{figure} /Fig-sol/69-2.png
---
width: 600px
name: fig:69-2
---
Multisim simulation of the integrator
```

Note that in the horizontal part the gain is $G = -20 \log \frac{R_C}{R}$ and that the integrating part falls off by $1/\omega$. For large frequencies (not shown) the gain goes up again. This is where the OpAmps does not function reliable anymore. 

```{figure} /Fig-sol/69-3.png
---
width: 400px
name: fig:69-3
---
Comparison of modulus between Multisim and calculation of the integrator
```

```{figure} /Fig-sol/69-4.png
---
width: 400px
name: fig:69-4
---
Comparison of phase between Multisim and calculation of the integrator
```
::::

### Differentiator

````{admonition} Exercise 6.10
:class: note

{numref}`fig:oa21` shows a circuit of a differentiator. 

```{figure} /Fig-ch6/OA21.png
---
width: 350px
name: fig:oa21
---
Differentiator
```

- Derive using {numref}`fig:oa21` that the output voltage is given by:

$$
V_{\rm out} = - RC \frac{{\rm d}V_{\rm in}}{{\rm d}t}.
$$ (eq:Vout4)

````

::::{admonition} Answer
:class: dropdown

The circuit of the differentiator is given in {numref}`fig:oa21`.

Analysis of the circuit: 

$$
\begin{split}
&I_R R = V_- - V_{\rm out}, \; {\rm and} \; I_C = I_R \rightarrow V_{\rm out} = - I_C R, \; {\rm or} \; I_C = \frac{- V_{\rm out}}{R}, \\
&I_C = \frac{\partial Q_C}{\partial t} = C \frac{{\rm d} V_{\rm in}}{{\rm d} t} \rightarrow \frac{- V_{\rm out}}{R} = C \frac{{\rm d}V_{\rm in}}{{\rm d} t} \rightarrow V_{\rm out} = - R C \frac{{\rm d}V_{\rm in}}{{\rm d} t}.
\end{split}
$$ (eq:ch6-26)
::::

The proportionality constant is the time constant $RC$, which in this case is also known as the differential constant.

````{admonition} Exercise 6.11
:class: note

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Design in Multisim a differentiator with a time constant of 1 ms and verify that eqn. {eq}`eq:Vout4` holds.
````

::::{admonition} Answer
:class: dropdown

The Multisim circuit for a differentiator with a time constant of 1 ms is shown in {numref}`fig:611-1`.

```{figure} /Fig-sol/611-1.png
---
width: 600px
name: fig:611-1
---
Differentiator with time constant of 1 ms
```

Since

$$
\begin{split}
&A = - \frac{R}{1 / j \omega C} = - j \omega R C, \\
&|A| = \omega R C, \\
&\Phi = - \tan^{-1} \left( \frac{\omega R C}{0} \right) =- \frac{\pi}{2} \pm {\rm k} \pi.
\end{split}
$$ (eq:ch6-27)

The bode plot is shown in {numref}`fig:611-2`, the sine/cosine traces in {numref}`fig:611-3`. \
So $|A|$ vs. $f$ results in a straight line with a slope of $2 \pi R C$.

```{figure} /Fig-sol/611-2.png
---
width: 600px
name: fig:611-2
---
Modulus and phase of differentiator with time constant of 1 ms
```

You can also look at the sine/cosine traces, which are 90 degrees out of phase ({numref}`fig:611-3`). 

```{figure} /Fig-sol/611-3.png
---
width: 500px
name: fig:611-3
---
The sine/cosine traces, 90 degrees out of phase
```

$|A| = 0.062832$ for f = 10 Hz and $|A| = 62.43594$ for f = 10 kHz. So the slope/${2 \pi}$ is

$$
\frac{{\rm slope}}{2 \pi} = \frac{\frac{62.43594 - 0.062832}{10000 - 10}}{2 \pi} = 0.99 \; {\rm ms}.
$$ (eq:ch6-28)
::::

## Active filters
In this section a number of active filters that make use of OpAmps are presented. These filters are called *active* because use is made of an active element, in this case an OpAmp. \
In chapter 4 it was shown for a low pass filter made of a resistor and a capacitor that the amplitude characteristic in the bandwidth range clearly starts to decrease. This effect becomes more stronger when two of more of these types of filters are used consecutively. OpAmps in combination with well chosen values for resistors and capacitors offers the construction of filters where the amplitude characteristic starts to drop much closer toward the end of a pass band. Usually these active filters do exhibit small oscillations (ripples) in the pass band. In general these oscillations are stronger the faster the cutoff in the frequency characteristic. \
For some applications the shape phase characteristic is more important than the amplitude characteristic. For example, at the transfer of pulses it is more important that all frequencies that make up the pulse experience the same shift over time such that the pulse width remains conserved. In that case the phase characteristic within the frequency band width should be linear with frequency. \
There are many different filter designs. They are chosen depending on the application. In literature three basic types with characteristic features are found:
- The **Butterworth** filter is optimized to facilitate a flat frequency band width. As a result it has a slow cutoff near the end of the frequency band width and the phase transfer is less perfect.
- The **Chebyshev** filter produces a sharp transition from the pass band to the stop band. The pass band exhibits some ripples and the phase characteristic is poor. Pulse shapes are clearly deformed.
- The **Bessel** filter has an optimized linear phase transfer and is therefore best suited for pulse shaped signals. The amplitude characteristics is less sharp compared to the Butterworth filter and much less sharp compared to the Chebyshev filter.

The next section discusses the Butterworth filter as an example.

### The Butterworth filter
The amplitude transfer function of the $n^{\rm th}$ order Butterworth filter has the following shape:

$$
| A | = \frac{1}{\sqrt{\left( 1 + \left( \omega / \omega_{3 \, {\rm dB}} \right)^{2n} \right)}}.
$$ (eq:ch6-29)

{numref}`fig:oa22` shows the schematic of an active second order low pass filter, called a *Sallen and Key* filter.

```{figure} /Fig-ch6/OA22.png
---
width: 500px
name: fig:oa22
---
Active second order low pass filter
```

The transfer function that may be derived is given by:

$$
A(\omega) = \frac{1}{\left( 1 + j \omega \left( R_{\rm A} + R_{\rm B} \right) C_{\rm B} - \omega^2 \tau_{\rm A} \tau_{\rm B} \right) },
$$ (eq:ch6-30)

where $\tau_{\rm A} = R_{\rm A} C_{\rm A}$ and $\tau_{\rm B} = R_{\rm B} C_{\rm B}$. 
The amplitude transfer function is then given by:

$$
| A(\omega) | = \frac{1}{\sqrt{\left( 1 - \omega^2 \tau_{\rm A} \tau_{\rm B} \right)^2 + \omega^2 \left(  R_{\rm A} + R_{\rm B} \right)^2 C_{\rm B}^2 }}.
$$ (eq:ch6-31)


````{admonition} Exercise 6.12
:class: note

- Assuming $R_{\rm A} = R_{\rm B} = R$, what is the relation between $C_{\rm A}$ and $C_{\rm B}$ for the active second order low pass filter shown in {numref}`fig:oa22` to be a Butterworth filter?

````

::::{admonition} Answer
:class: dropdown

The analysis, with $R_A = R_B = R$ is as follows:  

$$
| A ( \omega ) | = \frac{1}{\sqrt{\left( 1 - \omega^2 \tau_A \tau_B \right)^2 + \omega^2 \left( 2 R \right)^2 C_B^2}} = \frac{1}{\sqrt{1 + \left( \omega / \omega_{3 \; {\rm dB}} \right)^{2 n}}}.
$$ (eq:ch6-32)

So 

$$
\begin{split}
\left( 1 - \omega_{3 \; {\rm dB}}^2 \tau_A \tau_B \right)^2 + \omega^2 \left( 2 R \right)^2 C_B^2 &= 1 + \left( \omega / \omega_{3 \; {\rm dB}} \right)^{2 n}, \\
1 - 2 \omega^2 \tau_a \tau_B + \omega^4 \tau_A^2 \tau_B^2 + 4 \omega^2 R^2 C_B^2 &= 1 + \left( \omega / \omega_{3 \; {\rm dB}} \right)^{2 n}, \\
\omega^4 \tau_A^2 \tau_B^2 + 2 \omega^2 \left( - \tau_A \tau_B + 2 R^2 C_B^2 \right) &= \left( \omega / \omega_{3 \; {\rm dB}} \right)^{2 n}.
\end{split}
$$ (eq:ch6-33)

The second term on the left-hand side must be zero and $n$ must be 2:

$$
\begin{split}
2 R^2C_B^2 &= \tau_a \tau_B, \\
2 R^2C_B^2 &= R C_A R C_B, \\
C_A &= 2 C_B.
\end{split}
$$ (eq:ch6-34)

Then 

$$
\omega_{3 \; {\rm dB}} = \frac{1}{\tau_A^2 \tau_B^2} \rightarrow \omega_{3 \; {\rm dB}} = \frac{1}{\tau_A \tau_B} = \frac{1}{2 R^2 C_B^2}.
$$ (eq:ch6-35)
::::



## Lab exercises
### Pin layout of the 741 OpAmp
As mentioned in {ref}`OA` in the lab exercises we will use the 741 OpAmp. {numref}`fig:oa23` shows the pin layout of the 741 OpAmp. 

```{figure} /Fig-ch6/OA23.png
---
width: 300px
name: fig:oa23
---
Pin layout of the 741 OpAmp
```

{numref}`fig:oa23` shows a top view so the pins are located at the bottom of the IC.
- Pin 1 and 5 are connectors to compensate the offset at the inputs (see {numref}`fig:oa24`).
- Pin 2 is the inverting input (-).
- Pin 3 is the non-inverting input (+).
- Pin 4 is the connection for the negative voltage supply ($V^{-}$), in our case -15 V.
- Pin 6 is the output.
- Pin 7 is the connection for the positive voltage supply ($V^{+}$), in our case +15 V.
- Pin 8 is not connected.

### Offset compensation for the 741 OpAmp
Particularly for amplifying DC signals reliably the input offset should be compensated. {numref}`fig:oa24` shows how this is done.

```{figure} /Fig-ch6/OA24.png
---
width: 250px
name: fig:oa24
---
Offset compensation
```

- Both the inverting and non-inverting inputs are grounded.
- A resistor is placed between the offset pins.
- The centre terminal of the pot is connected to the negative voltage supply.
- The pot is tuned such that the output signal is 0 V.

Note that this will not be required for the lab exercises 6.13 to 6.15.

````{admonition} Exercise 6.13
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```
```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Design in Multisim an instrumentation amplifier with an adjustable differential amplification factor of 2 to 10. (Use an amplification factor of 1 for part B.)
- Build and test parts A and B of an instrumentation amplifier separately  ({numref}`fig:oa18`).
- Connect parts A and B together and test the instrumentation amplifier.
- Determine the CMRR experimentally and compare this with the theoretical expected increase described bellow eqn. {eq}`eq:deltaV`. Investigate this for different amplification factors.
````

````{admonition} Exercise 6.14
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```
- Design and build an integrator with a time constant of 0.01 s.
- Verify experimentally whether the integration constant corresponds with the theoretically expected value by using $v_{out}$ and $V_{in}$ displayed as oscilloscope traces and rewriting eqn. {eq}`eq:Vout3`.
- Investigate and explain the drift of the integrator output. Why is it useful to use a square wave input signal in this investigation?
- Reduce the drift by  application of a bypass resistor $R_{\rm C}$ and justify your choice of the resistance value.
- Examine the frequency behavior of the circuit ($A ( \omega )$, $| A ( \omega ) |$, asymtotic behavior) and enter the results of Multisim and NI Elvis in a Bode plot for 3 different $R_C$ values ($100 \Omega, 500 \Omega, 1500 \Omega$).
````

````{admonition} Exercise 6.15
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```
- Design and build a Sallen and Key filter (see {numref}`fig:oa22`) with a 3 dB point of 1 kHz, which complies with the Butterworth characteristic (see also exercise 6.12).
- Examine the behavior of the circuit and give the result in a Bode plot.
- Compare the results with exercise 4.4 (use a multiplot graph).
````