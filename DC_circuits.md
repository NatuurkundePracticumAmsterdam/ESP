(DC_circuits)=
# DC circuits

In this chapter the behavior of DC - or direct current - circuits are studied. A number of basic principles and analyses techniques will be covered that can also be applied to AC - or alternating current - circuits.

## Basic electronic components
### Symbols
The five basic elements for electronic circuits are resistance ($R$), coil ($L$), capacitor ($C$), voltage source ($V$) and current source ($I$) as shown in {numref}`fig-dc01`. \
{numref}`fig-dc01` also shows the symbols used for these basic elements.

```{figure} /Fig-ch3/DC01.png
---
width: 400px
name: fig-dc01
---
Symbols for basic electronic elements
```

### Active and passive elements
An active element is an element that can add net energy to a circuit. A passive element cannot add energy to a circuit, instead it receives energy from a circuit. Resistors, coils and capacitors are therefore passive elements, while voltage and current sources are active elements.

### Linearity
The three passive basic elements are linear. A resistor is linear because the potential difference across a resistor depends linearly on the current passing through it. A coil is linear because the potential difference across a coil depends linearly on change of current passing through it. A capacitor is linear because the change of potential difference across a capacitor depends linearly on the current through it. The linearity of passive elements simplifies the analysis of circuits strongly.

### Kirchhoff's laws
Appendix B covers a number of basic laws, including Kirchhoff's laws.

## Network theorems
Electronic circuits constructed of several resistors and sources quickly become complex. This section covers a number of circuit analysis techniques that simplify complex circuits.

(Thevenin)=
### Thévenin's theorem

Th&eacute;venin's theorem offers the possibility to simplify complex circuits to a standard circuit with one voltage source and one resistor. The standard circuit is called the Th&eacute;venin equivalent circuit of the original complex circuit. 

Th&eacute;venin's theorem is defined as: 
> Any circuit with two terminals composed of resistors, voltage and/or current sources can be replaced by an ideal voltage source $V$ and a resistor $R$ in series.
 

The voltage $V$ is called the Th&eacute;venin equivalent voltage $V_{\rm Th}$ and resistor $R$ the Th&eacute;venin equivalent resistor $R_{\rm Th}$ (see {numref}`fig-dc02`).

```{figure} /Fig-ch3/DC02.png
---
width: 400px
name: fig-dc02
---
Th&eacute;venin equivalent circuit
```
> $V_{\rm Th}$ is equal to the open-circuit potential difference of the original circuit. 
>
> $R_{\rm Th}$ is the resistance measured between terminals $a$ and $b$ when all voltage and current sources are replaced by their internal resistances.

From {numref}`fig-dc02` it follows that $R_{\rm Th}$ is given by:

$$
R_{\rm Th} = \frac{V_{\rm open}}{I_{\rm SC}},
$$ (eq:Rth)

where $V_{\rm open}$ is the open-circuit potential difference and $I_{\rm SC}$ is the short-circuit current obtained when terminals $a$ and $b$ are short cut.

````{admonition} Example *Th&eacute;venin*
:class: tip

Consider the circuit shown in {numref}`fig-dc03`.

```{figure} /Fig-ch3/DC03.png
---
width: 400px
name: fig-dc03
---
Circuit example Th&eacute;venin
```

*Determination of* $V_{\rm Th}$: \
$V_{\rm Th}$ is the open-circuit potential difference between $a$ and $b$ in {numref}`fig-dc03`:

$$
V_{\rm Th} = V_{\rm open} = \frac{100}{100 + 200} \cdot 15 = 5 {\rm V}.
$$ (eq:Vth)

*Determination of* $R_{\rm Th}$: \
Assuming the voltage source is ideal, its resistance is 0 $\Omega$. By replacing the voltage source by its internal resistance, $R_{\rm Th}$ is obtained by determining the resistance between terminals $a$ and $b$ in {numref}`fig-dc04`:

```{figure} /Fig-ch3/DC04.png
---
width: 300px
name: fig-dc04
---
Circuit to determine $R_{\rm Th}$
```

$$
R_{\rm Th} = 50 \, \Omega + (200 \, \Omega || 100 \, \Omega) = 116.7 \, \Omega.
$$ (eq:ch3-1)

This results in the Th&eacute;venin equivalent cicuit shown in {numref}`fig-dc05`: 

```{figure} /Fig-ch3/DC05.png
---
width: 300px
name: fig-dc05
---
Th&eacute;venin equivalent circuit
```
````


````{admonition} Exercise 3.1
:class: note

* Determine and draw the Th&eacute;venin equivalent circuits of {numref}`fig-dc06` and {numref}`fig-dc07`. 

```{figure} /Fig-ch3/DC06.png
---
width: 350px
name: fig-dc06
---
Network with voltage source
```

```{figure} /Fig-ch3/DC07.png
---
width: 350px
name: fig-dc07
---
Network with current source
```

```{figure} /Fig-ch1/multisim.png
---
width: 50px
align: right
name: fig-multisim
---

```

* Open *Mult 3.1a* and *Mult 3.1b* and check your results.
````

:::{admonition} Answer
:class: dropdown

(a) Since there is no load between terminals $a$ and $b$ $V_{\rm Th}$ does not depend on the $3k3$ loads. $V_{\rm Th}$ is given by (see {numref}`fig-31a`):

```{figure} /Fig-sol/31a1.png
---
width: 400px
name: fig-31a
---
Determination of $V_{\rm Th}$
```

$$
V_{\rm Th} = \frac{2k35}{1k + 2k35} \cdot 10 = 7 V.
$$ (eq:ch3-2)

To calculate $R_{\rm Th}$ the voltage source should be removed (see {numref}`fig-31b`):

```{figure} /Fig-sol/31a2.png
---
width: 400px
name: fig-31b
---
Determination of $R_{\rm Th}$	
```

$$
R_{\rm Th} = 2 \cdot 3k3 + (1k || 2k35) = 7k3.
$$ (eq:ch3-3)

This results in {numref}`fig-31c`.

```{figure} /Fig-sol/31a3.png
---
width: 250px
name: fig-31c
---
Th&eacute;venin equivalent circuit	
```

(b) To determine $V_{\rm Th}$ you first need to determine $I_{\rm Th}$ (see {numref}`fig-31d`):

```{figure} /Fig-sol/31b1.png
---
width: 400px
name: fig-31d
---
Determination of $V_{\rm Th}$
```

$$
\begin{split}
&V_{\rm Th} = I_2 \cdot 15k \\
&I = I_1 + I_2 \\
&\sum V_{\rm Closed \; Loop} = 0 \\
&I_1 \cdot 5k - I_2 \cdot (6k8 + 15k) = 0 \\
&(I - I_2) \cdot 5k - I_2 \cdot (6k8 + 15k) = 0 \\
&I \cdot 5k - I_2 \cdot 26k8 = 0 \\
&I_2 = \frac{4 \; {\rm mA} \cdot 5k}{26k8} = 0.75 \; {\rm mA}. \\
&V_{\rm Th} = 0.75 \; {\rm mA} \cdot 15k \; \Omega = 11.2 \; {\rm V}.
\end{split}
$$ (eq:ch3-4)

To determine $R_{\rm Th}$ the current source should be removed by open terminals (see {numref}`fig-31e`), 

```{figure} /Fig-sol/31b2.png
---
width: 300px
name: fig-31e
---
Determination of $R_{\rm Th}$
```

so:

$$
R_{\rm Th} = (6k8 +5k) || 15k = 6k6.
$$ (eq:ch3-5)

This results in {numref}`fig-31f`.

```{figure} /Fig-sol/31b3.png
---
width: 250px
name: fig-31f
---
Th&eacute;venin equivalent circuit
```

The result in Multisim is the same (see {numref}`fig-31g`):

```{figure} /Fig-sol/31bMulti.png
---
width: 600px
name: fig-31g
---
The results of *Mult 3.1b*
```
:::


A second analysis technique to simplify circuits is *Norton's theorem*. This theorem results in replacing any circuit for an ideal current source $I$ in parallel with a resistor $R$. In this course we will limit ourselves to *Th&eacute;venin's theorem*.

(SuperPosition)=
### Superposition theorem
Some circuits contain more than one voltage and/or current source. In this situation the superposition theorem, derived from the linearity of basic elements, allows the determination of voltages across and currents through each of the sources separately. This is done by replacing sources by their internal resistance except for the source under consideration. For an ideal voltage source with internal resistance, replacing the source is the same as short cutting their terminals. For an ideal current source with infinite resistance replacing the source is the same as leaving their terminals open. \
The superposition theorem is defined as: 

> The potential difference across a certain element in a circuit containing several sources can be obtained by determining the potential differences across that element due to each source, whereby all other sources are replaced by their internal resistances. The overall potential difference across the element is given by the algebraic sum of the separately determined potential differences. 

For the current through a certain element a similar theorem applies. 

````{admonition} Example *Th&eacute;venin with two sources*
:class: tip

{numref}`fig-dc08` shows a circuit with a voltage and a current source.

```{figure} /Fig-ch3/DC08.png
---
width: 400px
name: fig-dc08
---
Th&eacute;venin with two sources
```

To find the Th&eacute;venin equivalent circuit the superposition theorem will be applied. The contributions of the voltage and current sources are calculated separately and then added. \
To calculate the contribution of the current source the voltage source is short cut (i.e. replaced by its internal resistance). This results in the circuit shown in {numref}`fig-dc09`.

```{figure} /Fig-ch3/DC09.png
---
width: 400px
name: fig-dc09
---
Electronic circuit with voltage source eliminated
```

The Th&eacute;venin equivalent voltage contribution of the current source is given by (*check this!*):

$$
\begin{split}
&{V^{\rm current}_{\rm Th} = I_2 \cdot 100} \\
&{I = I_1 + I_2} \\
&{\Sigma V_{closed\:loop}=0 } \\
&{I_1 \cdot 200 - I_2 \cdot (100 + 100) = 0} \\
\end{split}
$$ (eq:ch3-6)

$$
\begin{split}
&{I_2 = 0.5 \cdot I = 0.05 \, \rm A} \\
&{V^{\rm current}_{\rm Th} = 0.05 \cdot 100 = 5 \, \rm V.}
\end{split}
$$ (eq:ch3-7)

To calculate the contribution of the voltage source the current source terminals are kept open (replacement by its internal resistance). This results in the circuit shown in {numref}`fig-dc10`. 

```{figure} /Fig-ch3/DC10.png
---
width: 300px
name: fig-dc10
---
Electronic circuit with current source eliminated
```

Therefore (*check this, pay attention to signs!*):

$$
\nonumber
\begin{split}
{} & {V^{\rm voltage}_{\rm Th} = I \cdot 100} \\
{} & {I \cdot 100 +10 + I \cdot 200 + I \cdot 100 = 0} \\
{} & {I = -0.025 \, {\rm A}} \\
{} & {V^{\rm voltage}_{\rm Th} = -0.025 \cdot 100 = -2.5 \, {\rm V}} \\
{} & {\to V^{\rm tot}_{\rm Th} = 5 - 2.5 = 2.5 \, {\rm V.}}
\end{split}
$$ (eq:ch3-8)

To determine $R_{\rm Th}$ both sources have to be replaced by their internal resistances. This results in the circuit shown in {numref}`fig-dc11`:

```{figure} /Fig-ch3/DC11.png
---
width: 250px
name: fig-dc11
---
Th&eacute;venin circuit with both source eliminated to determine $R_{\rm Th}$
```

$R_{\rm Th}$ is the resistance between terminals $a$ and $b$ and is given by:

$$
R_{\rm Th} = 100 || (100 + 200) = 75 \, \Omega.
$$ (eq:ch3-9)

{numref}`fig-dc12` shows the Th{\'e}venin equivalent circuit.


```{figure} /Fig-ch3/DC12.png
---
width: 300px
name: fig-dc12
---
The Th&eacute;venin equivalent circuit
```
````

````{admonition} Exercise 3.2
:class: note

* Determine and draw the Th&eacute;venin equivalent circuit of {numref}`fig-dc13`. 

```{figure} /Fig-ch3/DC13.png
---
width: 400px
name: fig-dc13
---
Network with two current sources
```

```{figure} /Fig-ch1/multisim.png
---
width: 50px
align: right
name: fig-multisim
---

```

* Open *Mult 3.2* and check your results.
````

:::{admonition} Answer
:class: dropdown

In order to determine $V_{\rm Th}$ the circuit needs to be split up into two circuits with one current source each (see {numref}`fig-32a`). 

```{figure} /Fig-sol/32-1.png
---
width: 400px
name: fig-32a
---
Determination of $V_{\rm Th}^{\rm 3 \; mA}$ and $V_{\rm Th}^{\rm 2 \; mA}$
```

Then the $V_{\rm Th}$ can be determined for each circuit.

$$
\begin{split}
V_{\rm Th}^{\rm 3 mA} = I_2 \cdot 15k \\
I = I_1 + I_2 \\
\sum V_{\rm Closed \; Loop} = 0 \\
I_1 \cdot 18k - I_2 \cdot (6k8 + 15k) = 0 \\
(I - I_2) \cdot 18k - I_2 \cdot (6k8 + 15k) = 0 \\
I \cdot 18k - I_2 \cdot 39k8 = 0 \\
I_2 = \frac{3 \; {\rm mA} \cdot 18k}{39k8} = 1.36 \; {\rm mA}. \\
V_{\rm Th}^{\rm 2 \; mA} = 1.36 \; {\rm mA} \cdot 15k \; \Omega = 20.35 \; {\rm V}.
\end{split}
$$ (eq:ch3-10)

$$
\begin{split}
V_{\rm Th}^{\rm 2 mA} = I_2 \cdot 15k \\
I = I_1 + I_2 \\
\sum V_{\rm Closed \; Loop} = 0 \\
I_1 \cdot (6k8 + 18k) - I_2 \cdot 15k = 0 \\
(I - I_2) \cdot (6k8 + 18k) - I_2 \cdot 15k = 0 \\
I \cdot 24k8 - I_2 \cdot 39k8 = 0 \\
I_2 = \frac{2 \; {\rm mA} \cdot 24k8}{39k8} = 1.25 \; {\rm mA}. \\
V_{\rm Th}^{\rm 2 \; mA} = 1.25 \; {\rm mA} \cdot 15k \; \Omega = 18.69 \; {\rm V}.
\end{split}
$$ (eq:ch3-11)

So $V_{\rm Th}$ is

$$
V_{\rm Th} = 20.35 + 18.69 = 39.04 V.
$$ (eq:ch3-11)

To determine $R_{\rm Th}$ the current sources should be removed by open terminals (see {numref}`fig-32b`), 

```{figure} /Fig-sol/32-2.png
---
width: 400px
name: fig-32b
---
Determination of $R_{\rm Th}$
```

so:

$$
R_{\rm Th} = (6k8 +18k) || 15k = 9k35.
$$ (eq:ch3-13)

This results in {numref}`fig-32c`.

```{figure} /Fig-sol/32-3.png
---
width: 250px
name: fig-32c
---
Th&eacute;venin equivalent circuit
```

The result in Multisim is the same (see {numref}`fig-32d`):

```{figure} /Fig-sol/32Multi.png
---
width: 600px
name: fig-32d
---
The results of *Mult 3.2*
```
:::

(exTh)=
### Experimental determination of Thévenin and short cut values
So far $V_{\rm Th}$ and $R_{\rm Th}$ have been determined by calculation, which is an option when the circuit is known in detail. When this is not the case and the circuit has to be treated as a 'black box' with two terminal, the $V_{\rm Th}$ and $R_{\rm Th}$  can be determined experimentally. 

*Determination of $V_{\rm Th}$:* \
$V_{\rm Th}$ simply is the open-circuit potential difference and can be measured when no load is connected to the circuit. However, it is important to use a measuring device with a high input impedance (see {ref}`input_impedance`) to ensure that the load on the circuit is minimal. 

*Determination of $I_{\rm SC}$:* \
$I_{\rm SC}$ is the short cut current. In general it is not wise to measure this current directly as it might damage the circuit. It is possible to measure $I_{\rm SC}$ indirectly. \
To do so load the circuit with a variable resistor $R_{\rm v}$ as shown in {numref}`fig-dc14`. Measure the potential difference $V_{\rm ab}$ and current $I$ for several values of $R_{\rm v}$ and display the results in a graph (see {numref}`fig-dc15`). Extrapolate the graph to determine $I_{\rm SC}$ at $V_{\rm ab} = 0$. \
A simpler method is to vary $R_{\rm v}$ until  $V_{\rm ab} = \frac{1}{2} V^{\rm open}_{\rm ab}$.  For this resistance value  $R_{\rm v} = R_{\rm Th}$ (*check this!*). Using eqn. {eq}`eq:Rth` $I_{\rm SC}$ can be obtained.

```{figure} /Fig-ch3/DC14.png
---
width: 400px
name: fig-dc14
---
Experimental determination of $I_{\rm SC}$
```
```{figure} /Fig-ch3/DC15.png
---
width: 400px
name: fig-dc15
---
$V-I$-graph for the circuit shown in {numref}`fig-dc14`
```

(input_impedance)=
### Input impedance

A voltage source connected to the input terminals of a circuit usually results in a current running through the circuit. The strength of the current depends on the input impedance $R_{\rm i}$ of the circuit. Similar to the Th&eacute;venin equivalent circuit, which is used to describe the output of a circuit, the behavior of the input of a circuit may be described by using an equivalent input circuit, as shown in {numref}`fig-dc16`.

```{figure} /Fig-ch3/DC16.png
---
width: 250px
name: fig-dc16
---
Equivalent input circuit
```

$R_{\rm i}$ is given by

$$
R_{\rm i} = \frac{V_{\rm i}}{I_{\rm i}}.
$$ (eq:ch3-14)

When details on the circuit are available $V_{\rm i}$ and $I_{\rm i}$, and therefore $R_{\rm i}$ can be calculated. If this is not the case $R_{\rm i}$ can be determined experimentally in a similar way as the experimental determination of $R_{\rm Th}$ (see {ref}`exTh`): \
Connect a variable resistor and a voltage source to the circuit as shown in {numref}`fig-dc17`. \
Measure the output potential difference $V_{\rm s}$ of the voltage source and the input potential difference $V_{\rm i}$ of the test circuit. Vary $R_{\rm v}$ until $V_{\rm i} = \frac{1}{2} V_{\rm s}$. Then $R_{\rm i} = R_{\rm v}$ (*check this!*). \
Note that this method does not depend on the value of $R_{\rm s}$. This is due to measuring $V_{\rm s}$ rather than $V_{\rm open}$.

```{figure} /Fig-ch3/DC17.png
---
width: 600px
name: fig-dc17
---
Experimental determination of input impedance
```

(amplification)=
## Amplification

### Type of amplification
Different kinds of amplifiers can be classified.\
First, amplifiers for DC signals (*DC amplifiers*) and AC signals (*AC amplifiers*) are distinguished. \
Second, amplifiers are distinguished according to the type of signal which requires amplification. If the input and output signals are potential differences we refer to a *voltage amplifier*, if they are currents we refer to a *current amplifier*. If the input signal is a potential difference and the output signal a current we refer to a *voltage to current converter*, and in the reverse situation to a *current to voltage converter*. When the objective is to increase the power (rather than the potential difference or current), as is the case in an audio amplifier, we refer to a *power amplifier*. \
Amplification can be considered as a transfer function $A$ (see {ref}`transfer_function`), which signifies the relation between the output signal $y$ and the input signal $x$:

$$
A = \frac{y}{x}.
$$ (tf)

For voltage amplification eqn.(\ref{tf}) turns into:

$$
A_{\rm V} = \frac{V_{\rm out}}{V_{\rm in}},
$$ (eq:ch3-15)

for current amplification:

$$
A_{\rm I} = \frac{I_{\rm out}}{I_{\rm in}},
$$ (eq:ch3-16)

and for power amplification:

$$
A_{\rm P} = \frac{P_{\rm out}}{P_{\rm in}},
$$ (eq:PA)

where $V_{\rm in}$, $I_{\rm in}$ and $P_{\rm in}$ are the input potential difference, current and power, and $V_{\rm out}$, $I_{\rm out}$ and $P_{\rm out}$  the output potential difference, current and power, respectively. 

### Equivalent circuit amplifier
An amplifier is a circuit with an input and output. The input may be replaced by an effective input impedance (see {ref}`input_impedance`) and the output can considered as a voltage source en hence can be simplified using Th&eacute;venin's theorem (see {ref}`Thevenin`). \
{numref}`fig-dc18` shows the equivalent circuit of a voltage amplifier.

```{figure} /Fig-ch3/DC18.png
---
width: 400px
name: fig-dc18
---
Equivalent circuit of a voltage amplifier
```

$V_{\rm i}$ is the input potential difference, $R_{\rm i}$ the effective input impedance, $A_{\rm v}V_{\rm i}$ the equivalent Th&eacute;venin voltage source, $A_{\rm v}$ the voltage amplification, and $R_{\rm s}$ the Th&eacute;venin output impedance. Note that the Th&eacute;venin voltage source is not an actual voltage source, but rather a voltage source dependent on the input potential difference.

(matching)=
### Matching

When two electronic systems are interconnected it is important that the information from one system is transferred to the other in the correct manner. \
When a potential difference is the information carrier the potential difference should be transferred with minimal change. In other words, the output potential difference of the first system after connection to the second system should differ as little as possible from the  open output potential difference of the first system. \
{numref}`fig-dc19` shows a schematic, where system 1 is a voltage source with an open potential difference $V_{\rm open}$ and output impedance $R_{\rm s}$ and system 2 is characterized by the input impedance $R_{\rm i}$. 

```{figure} /Fig-ch3/DC19.png
---
width: 400px
name: fig-dc19
---
Example of connecting voltage source with a second system
```

The input potential difference of system 2 is given by:

$$
V_{\rm i} = \frac{R_{\rm i}}{R_{\rm s} + R_{\rm i}} \cdot V_{\rm open}.
$$ (eq:pd2)

From eqn. {eq}`eq:pd2` it follows that the voltage transfer improves as the input impedance $R_{\rm i}$ of system 2 increases. \
When a current is the information carrier the input current of the second system should differ as little as possible from the short cut current of the first system. \
{numref}`fig-dc20` shows a schematic, where system 1 is a current source $I$ with an output impedance $R_{\rm s}$ and system 2 is characterized by the input impedance $R_{\rm i}$. 

```{figure} /Fig-ch3/DC20.png
---
width: 400px
name: fig-dc20
---
Example of connecting a current source with a second system
```

The input current of system 2 is given by:

$$
I_{\rm i} = \frac{R_{\rm s}}{R_{\rm s} + R_{\rm i}} \cdot I.
$$ (eq:i2)

From eqn. {eq}`eq:i2` it follows that the current transfer improves as the input impedance $R_{\rm i}$ of system 2 decreases. 

So:
- $R_{\rm i}$ large: good voltage transfer, poor current transfer
- $R_{\rm i}$ small: good current transfer, poor voltage transfer

In many cases, e.g. when connecting a loudspeaker to an audio amplifier, the objective is not to facilitate an optimal voltage or current transfer, but to maximize the power transfer. What is the optimal value of $R_{\rm i}$ in that case? The power transfer at $R_{\rm i} = 0$ and $R_{\rm i} = \infty$ is 0 (*check this!*).\
Assume that in {numref}`fig-dc19` system 1 represents an audio amplifier and system 2 a loudspeaker. The power transferred to the loudspeaker is (using eqn. {eq}`eq:pd2`):

$$
P = V_{\rm i} \cdot I_{\rm i} = \frac{V_{\rm i}^2}{R_{\rm i}} = \frac{V_{\rm open}^2 \cdot R_{\rm i}}{\left( R_{\rm s} + R_{\rm i} \right)^2}.
$$ (eq:P)

To find the maximum power transfer the derivative of $P$ with respect to $R_{\rm i}$ is taken:

$$
\frac{{\rm d} P}{{\rm d} R_{\rm i}} = V_{\rm open}^2 \cdot \frac{\left( R_{\rm s} + R_{\rm i} \right)^2 - 2 R_{\rm i} \cdot \left( R_{\rm s} + R_{\rm i} \right)}{\left( R_{\rm s} + R_{\rm i} \right)^4}.
$$ (eq:deriv)

The maximum power transfer is obtained when eqn. {eq}`eq:deriv` is set to 0. *Check that this is the case for $R_{\rm i} = R_{\rm s}$.* \
This in fact shows that half of the power is dissipated in the output impedance $R_{\rm s}$ of the amplifier and the other half in the input impedance of the loudspeaker. \
Substitution of $R_{\rm i} = R_{\rm s}$ into eqn. {eq}`eq:P` give the maximum power transfer:

$$
P_{\rm max} = \frac{V_{\rm open}^2}{4 \cdot R_{\rm i}}.
$$ (eq:ch3-17)

Power amplification often is expressed in decibel (dB). Appendix C gives some examples of logarithmic forms.

## Application of a network
### The Wheatstone bridge
The Wheatstone bridge is an example of a network with a voltage source. The general configuration is shown in {numref}`fig-dc21`. This circuit is used to measure small changes in resistances, or to measure resistance values accurately.

```{figure} /Fig-ch3/DC21.png
---
width: 400px
name: fig-dc21
---
The Wheatstone bridge
```

Physical quantities, like temperature, pressure and deformation of materials, are usually measured using sensors dependent on resistance. For example, for temperature measurements  NTC resistors are used, which at room temperature have a value of 2 k$\Omega$, with a temperature co&euml;fficient  of 1 $\Omega / ^{\rm o}$C. Assume that we want to measure a temperature change of 1 $^{\rm o}$C with an accuracy of 5\%, then changes in resistance of about 0.05 $\Omega$ should be measured with a range of 2 k$\Omega$. With an ordinary multimeter this is very hard to realize. \
One way of do this is by using a Wheatstone bridge. A Wheatstone bridge is constructed using two parallel voltage dividers $R_1 / R_2$ and $R_3 / R_4$. \
With the right selection of resistors the bridge can be balanced, which results in a potential difference $V_{\rm AB} = 0 \, {\rm V}$. In that case:

$$
\frac{R_1}{R_2} = \frac{R_3}{R_4}.
$$ (eq:ch3-18)

Small changes in one of the resistors results in small potential differences  between $A$ and $B$. For the temperature measurement $R_1$ may be replaced by the NTC sensor, with $R_2 = R_3 = R_4 = 2 \, {\rm k} \Omega$. At room temperature the bridge is balanced. Small temperature changes will result in small changes in $V_{\rm AB}$. 

````{admonition} Exercise 3.3
:class: note

* Derive the relations for $V_{\rm AB}$ as a function of $V_{\rm ex}$, $R_1$, $R_2$, $R_3$ and $R_4$.

```{figure} /Fig-ch1/multisim.png
---
width: 50px
align: right
name: fig-multisim
---

```

* Open *Mult 3.3* and check for a number of values of $R_1$ the open potential differences $V_{\rm AB}$.


````

:::{admonition} Answer
:class: dropdown

{numref}`fig-wb1` tells us that

$$
\begin{split}
V_{\rm A} & = \frac{R_1}{R_1 + R_2}V_{\rm ex}, \\
V_{\rm B} & = \frac{R_3}{R_3 + R_4}V_{\rm ex}. 
\end{split}
$$ (eq:ch3-19)

```{figure} /Fig-sol/33WB.png
---
width: 300px
name: fig-wb1
---
The Wheatstone bridge
```

So $V_{\rm AB}$ is given by

$$
V_{\rm AB} = V_{\rm B} - V_{\rm A} = \left( \frac{R_3}{R_3 + R_4} - \frac{R_1}{R_1 + R_2} \right) V_{\rm ex}.
$$ (eq:ch3-20)

This is confirmed by Multisim: with $R_2 = R_3 = R_4 = 10 \; {\rm k} \Omega$ and varying $R_1$ from 9995 to 10005 $\Omega$ results in voltage steps of 250 $\mu$V (see {numref}`fig-wb2`). 

```{figure} /Fig-sol/33.png
---
width: 500px
name: fig-wb2
---
Results of the Wheatstone bridge measurement
```

:::

## Lab exercises
Before you start on the lab exercises read the section *Problem solving* ({ref}`ps`) and *Reporting* ({ref}`reporting`). 

````{admonition} Exercise 3.4
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

The terminals $A$ and $B$ of the voltage divider shown in {numref}`fig-dc22` can be considered terminals of a new voltage source with an internal resistance $R_{\rm i}$.

```{figure} /Fig-ch3/DC22.png
---
width: 250px
name: fig-dc22
---
Voltage divider
```
```{figure} /Fig-ch1/multisim.png
---
width: 50px
align: right
name: fig-multisim
---

```

* Design the circuit shown in {numref}`fig-dc22` using Multisim in such a way that $V_{\rm AB} \approx 0.5 \, {\rm V}$, while the power $P$ of the voltage source of 15 V ($R_{\rm i \, (15V)} = 5 \, \Omega$) does not exceed 150 mW. (Two conditions!)
* Construct the circuit.
* Determine the internal resistance $R_{\rm i}$ of the new voltage source by measuring $V_{\rm AB}$ for various loads $R_{\rm load}$ (see {numref}`fig-dc23`).

```{figure} /Fig-ch3/DC23.png
---
width: 400px
name: fig-dc23a
---

```
```{figure} /Fig-ch3/DC23a.png
---
width: 400px
name: fig-dc23
---
New voltage divider with $R_{\rm load}$
```

* Plot your data such that $R_{\rm i}$ can be determined from the graph.
* Compare the experimentally determined $R_{\rm i}$ with the calculated value. Give an explanation for any differences.
````

````{admonition} Exercise 3.5
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

An NTC has a resistance of $R_{\rm ref} = 2 \, {\rm k} \Omega$ at $T = 20 \, ^{\rm o} {\rm C}$ and a  temperature coefficient of $ 1 \, \Omega / ^{\rm o} {\rm C}$. Because it is hard to create different stable temperatures, the NTC will be simulated by a variable resistor. 
* Construct a Wheatstone bridge, as shown in {numref}`fig-dc21`, to measure temperatures close to room temperature. Use a variable resistor for $R_1$ and $V_{\rm ex} = 15 \, {\rm V}$.
* Derive a relation for $V_{\rm AB}$ as a function of $\Delta R$, $R$ and $V_{\rm ex}$ for the special case that NTC $R_1 = \Delta R + R$ and $R_2 = R_3 = R_4 = R$.
* Check this relation experimentally for a number of measurements. (For $\Delta R \ll R$.) Discuss your results.
* Calculate $V_{\rm AB}$ per $^{\rm o} {\rm C}$, and compare this value with the one experimentally determined.
````