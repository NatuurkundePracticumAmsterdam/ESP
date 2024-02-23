(diodes)=
# Diodes

Most modern electronic systems are based on *semiconductor* components, such as diodes and transistors. This chapter briefly discusses the physical properties of semiconductors and how this plays a role in diodes. For a more detailed treatment of semiconductors and other semiconductor components, such as the transistor, references are made to the many books which have been written on this subject. \
Topics covered in this chapter are:
- Electrical properties of solids
- "Doping"
- The pn-junction
- Applications of diodes:
    - Signal "clamping"
    - Rectification
    - Zener stabilization

## Electrical properties of solids
On the basis of their electrical properties, solid materials can be classified into three categories: *conductors, insulators, and semiconductors*. The difference in properties is largely determined by the electrons in the outer shell of the atoms from the material involved, also called *valence electrons*.

### Conductors
Valence electrons of  conductors are the most weakly bound electrons. In the case of metals, they form a cloud of free electrons. When across a metal a voltage is applied, a relatively large electric current will flow.\
Increasing the temperature will increase the number of free electrons to a small extent, while the electrons as a result of the intensive vibrating atoms encounter more resistance. Because the latter effect is much greater than the first, the current will decrease with increasing temperature.

### Insulators
In insulators, such as plastic, the valence electrons are very strongly bound. When across an insulator a voltage is applied, a very small current will flow, because there are hardly any free electrons. Increasing the temperature has, in comparison with a conductor, a relatively greater increase in the number of free electrons as a result. In an insulator, the current will increase as temperature increases. However, in absolute terms, the flow will still be very small.

### Semiconductors
Semiconductors are positioned between insulators and conductors. At low temperatures they act as insulators. At higher temperatures, the number of free electrons grow much stronger than in insulators. Semiconductors then behave a bit like "poor" conductors. Examples of semiconductor materials are silicon, germanium, and gallium arsenide. To understand the operation of semiconductors we look at the structure of silicon. {numref}`fig:diode01` shows the crystal structure of silicon.

```{figure} /Fig-ch5/Diod01.png
---
width: 400px
name: fig:diode01
---
Crystal structure of silicon
```

Silicon has four valence electrons, while the outer electron shell can have eight. Energetically speaking, a fully stocked shell is favorable. The result of this is that every atom will share four valence electrons with four neighboring atoms. forming *covalent bonds*. At low temperatures electrons bound strongly in such a configuration. With increasing temperature, due to the thermal vibration, single bonds are broken, wherein free electrons are created which in turn leave a similar number of holes in the crystal (see {numref}`fig:diode02`).

```{figure} /Fig-ch5/Diod02.png
---
width: 400px
name: fig:diode02
---
Effect of thermal vibrations in the crystal structure of silicon
```

A hole is actually a missing electron and, to that effect, may thus be regarded as a positive charge. Both the free electrons and the holes can move through the lattice. The movement of a hole is caused by filling the gap by an electron from a neighboring situated atom. Applying an electric field across a piece of silicon will cause the negatively charged free electrons move against the field and the positively charged holes along with the field. At room temperature, the number of free electrons and holes in pure silicon is still relatively small and, therefore, a poor conductor. This type of conduction is known as *intrinsic conduction*.

## "Doping"
The number of free charge carriers and, correspondingly, the conductivity of the semiconductor can be considerably increased by addition of small amounts of impurities.
This process is called *"doping"*. When, for example a phosphorus atom, which has five valence electrons, is added to silicon, then four of the valence electrons will join covalent bonds with the surrounding silicon atoms, while the fifth valence electron can not. This electron is therefore weakly bound and behaves basically like an extra free electron. Already a small amount of phosphorus will dramatically increase the number of free electrons. Phosphorus is called a *donor* impurity, because it generates additional free electrons. The doped silicon is referred to as *n-type* semiconductor due to the additional negative free charge carriers.

:::{note}
Although there are free negative charge carriers the total material remains electrically neutral. Addition of the phosphorus atoms, which are electrically neutral, adds no net negative charge.
:::

In addition to the n-type there is also a *p-type* semiconductor. This type is created when an element such as boron, which has three valence electrons, is added to the silicon. The three valence electrons will join covalent bonds with three of the four neighboring silicon atoms. The fourth silicon atom will be left with a hole, which can easily be filled with an electron from another nearby silicon atom. The hole can therefore move freely through the crystal. Positive free charge carriers are created. Boron is called an *accepter* impurity, because it easily accepts electrons. The doped silicon is referred to as p-type semiconductor due to the additional positive free charge carriers. \
The magnitude of the conductivity depends on the degree of dope. This type of conduction is known as *extrinsic conduction*. The free electrons in n-type and the free holes in a p-type semiconductor can be referred to as *majority charge carriers*. As a result of thermal motion there will always be some free holes in n-type and some free electrons in a p-type semiconductors. These are called *minority charge carriers*.

## pn junction
The combination of a p-type and an n-type semiconductor plays a very important role in many electronic components. If a piece of n-type and a piece of p-type semiconductor are connected a so-called *pn-junction* is created. Since the p-type has a high concentration of holes, and the n-type has free electrons, after attaching the two types a strong electrical gradient is present across the pn-junction.

```{figure} /Fig-ch5/Diod03.png
---
width: 500px
name: fig:diode03
---
pn junction
```

As a result of this gradient holes from the p-type will diffuse to the n-type, and electrons of the n-type to the p-type. If free holes and electrons encounter each other they will recombine and no free charge carriers remains. The result is that a thin layer around the junction is created, where free charge carriers are hardly found. This layer is called the *depletion layer*. The *depletion layer* is not electrically neutral. The diffusion of electrons, away from the junction, will leave in the n-type positive ions behind while the diffusion of holes in the p-type will leave behind negative ions. 

Positive and negative space charges are created on either side of the junction (see {numref}`fig:diode03`). These space charges cause an electric field and an associated potential difference. This electric field counteracts on the free electrons that are diffusing from the n-type to the p-type side, as well as the diffusion of the holes from the p-type to n-type. As the potential difference gets larger, a smaller and smaller number of free (majority) charge carriers possess sufficient energy to overcome the potential barrier created and, therefore, the corresponding *diffusion current* decreases.

For the minority charge carriers, the potential difference does not function as a barrier but will actually stimulate the movement across the junction, resulting in a *drift current*. Eventually, the diffusion current and the drift current will be equal to each other and a dynamic equilibrium is reached.

The height of the potential difference at this equilibrium mainly depends on the base material and to a lesser extent on the doping concentration used. For silicon this is about 0.7 V and for germanium 0.3 V.

The height of this potential difference can be influenced by an external electric field.

### Forward bias
When the external field is in opposite direction of the internal field of the diode, the diode is called *forward biased*. In this case, the p-type material is made positive relative to the n-type material.
The applied field neutralizes a portion of the space charge, the depletion layer becomes narrower and the potential barrier decreases. The result is that the number of majority carriers which have sufficient energy to overcome the barrier greatly increases, with the result that the diffusion current is much larger than the drift current. As a result, a current will flow in the direction of the applied field. This situation is shown in {numref}`fig:diode04`.

```{figure} /Fig-ch5/Diod04.png
---
width: 300px
name: fig:diode04
---
Forward biased pn junction
```

On the top of the {numref}`fig:diode04` the symbol for a diode is shown.

### Reversed bias
When the external field has the same direction as the internal field the diode is called *reversed bias*. In this case, the p-type material is made negative relative to the n-type material. The applied field in this case causes an increase of the space charge, the depletion layer becomes wider and the potential barrier increases. The number of majority charge carriers which have sufficient energy to overcome the barrier thereby strongly reduces and, correspondingly, the diffusion current reduces as well. A voltage of about 0.1 V is already sufficient to reduce the diffusion current to almost zero. The drift current will no longer be neutralized by the diffusion current. The result is that now a small current, in fact the drift current, will flow in the opposite direction. 

This situation is shown in {numref}`fig:diode05`.

```{figure} /Fig-ch5/Diod05.png
---
width: 300px
name: fig:diode05
---
Reversed biased pn junction
```

The drift current is determined by the number of minority charge carriers generated in the vicinity of the junction. Since this number depends on the temperature, the current will not be dependent on the applied field.

### Characteristics
The current $I$ through a diode can be approximated by eqn.{eq}`eq:Diod01`:

$$
I=I_{\rm s}\left (\exp\dfrac{eV}{kT} -1 \right ).
$$ (eq:Diod01)

Here $e$ is the charge of an electron, $V$ the applied voltage<sup>[^1]</sup>,  $k$ is  Boltzmann's constant, $T$ is the absolute temperature and $I_{\rm s}$ the magnitude of current at a sufficiently negative voltage. At room temperature $ {e}/{(kT)} $ is approximately equal to $ 40 \, {\rm V}^{-1} $. For voltages larger than - 0.1 V $ exp({eV}/{(kT))} << 1$.\
Then:

$$
I\cong-I_{\rm s}.
$$ (eq:Diod02)

This current is called the *reverse saturation current* and is equal to the drift current. 
For voltages larger than + 0.1 V $ exp({eV}/{(kT))} >> 1$.\
Then:

$$
I \cong I_{\rm s} \left ( \exp\dfrac{eV}{kT} \right) \cong I_{\rm s}\exp(40\cdot V).
$$ (eq:Diod03)

{numref}`fig:diode06` shows the current-voltage characteristic of a pn-junction.

```{figure} /Fig-ch5/Diod06.png
---
width: 300px
name: fig:diode06
---
Current-voltage characteristic of a pn-junction
```

For many applications, it is convenient to use an idealized model of a diode. In that case, the diode is regarded as a resistor of zero Ohm in the forward direction and infinite in the opposite direction. In other words, in one direction the flow is always allowed to pass, while in the other direction no current can flow. The characteristics of an ideal diode is shown in {numref}`fig:diode07`a.

A real diode has a characteristic equal to that of the pn-junction, as shown in {numref}`fig:diode06`. This is shown in {numref}`fig:diode07`b for different materials.

```{figure} /Fig-ch5/Diod07.png
---
width: 500px
name: fig:diode07
---
Diode characteristics
```

### Turn-on voltage
When a continuously increasing positive voltage is applied, at first a very small current will run, which will then increase exponentially. A more realistic diode model has the characteristic that the current is zero for small positive voltages up to a certain value, the so-called *turn-on voltage* $V_{\rm turn \,\, on}$. For higher voltages, the diode characteristic can be approximated by an almost vertical straight line. These approximated characteristics plus the corresponding turn-on voltage values are shown in {numref}`fig:diode07`c for different materials. In an electric circuit this means that when the diode conducts, although the resistance is very small, the diode still causes a voltage drop which is equal to the turn-on voltage. In practice, it is often assumed that the resistance is zero in case of conduction.

### Reverse breakdown
With increasing negative voltage (reverse bias), the current will soon reach the reverse saturation current, which is very small. For silicon, it has a value in the order of 1 nA. However, when the voltage is getting more negative than a certain critical value (*reverse breakdown voltage*) the junction will fail and the current flow will suddenly increase rapidly, which can be due to two possible causes (discussed in the following two subsections).

### Zener diode
The first cause occurs in diodes, where the n- and p-type material is strongly contaminated. Then the transition between the two is very sharp, resulting in a very thin depletion layer of sometimes only a few nm thick. Even a negative voltage of a few volts then delivers electric fields across the depletion layer of several hundreds of mega volts per meter. At such high fields the covalent bound electrons are pulled out of their bonds, causing a sharp increase in the number of free charge carriers and thus the current. This phenomenon is called *Zener breakdown*. If the current is not limited by connected external components around the diode, the diode will be damaged by the occurring heat dissipation. In specially designed so called Zener diodes current-limiting measures have been taken so that the diode is not damaged when it reaches the breakdown voltage. The breakdown voltage of a Zener diode is often indicated by the symbol $V_{\rm z}$. Such diodes are used for example to make a stabilized voltage source, as shown in {numref}`fig:diode08`.

```{figure} /Fig-ch5/Diod08.png
---
width: 400px
name: fig:diode08
---
Voltage stabilization with a Zener diode
```

In this circuit the Zener diode <sup>[^2]</sup> is reversed biased. When the input voltage is larger than $V_{\rm z}$, the diode will reach the break down voltage and will conduct electricity. The voltage across the diode will continue to be equal to $V_{\rm z}$ and the current flow will be large enough to cause a voltage drop across $R$ that is equal to:

$$
V_{\rm R} = I \cdot R = V_{\rm i} - V_{\rm z}.
$$ (eq:Diod04)

Variations in the input voltage $V_{\rm i}$ will, as long as $V_{\rm i}$ is greater than $V_{\rm z}$, not reveal variations in the output voltage $V_0$, but only in the current $I$. $V_{0}$ is always equal to $V_{\rm z}$. If $V_{\rm i}$ is less than $V_{\rm z}$, but larger than  $-V_{\rm turn \,\, on}$ the diode will not conduct and the output voltage $V_{0}$ will follow the input voltage $V_{\rm i}$.

````{admonition} Exercise 5.1
:class: note

- What happens to $V_{0}$ in the circuit of {numref}`fig:diode08` when $V_{\rm i}$ is between 0 and $-V_{\rm turn \,\, on}$.

Assume that $V_{\rm i}$ in {numref}`fig:diode08` is a sinusoidal voltage with a peak amplitude of 8 V and the Zener has a Zener voltage of 4.7 V and a turn on voltage of 0.7 V (silicon).

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Run *Mult 5.1* and explain the behavior of the output signal relative to the input signal.
````

::::{admonition} Answer
:class: dropdown

- When $V_{\rm i}$ becomes smaller than $-V_{\rm turn \; on}$ $V_0 = -V_{\rm turn \; on}$.
- The Zener diode clamps the positive sinusoidal voltage to breakdown voltage of 4.7 V. For negative sinusoidal voltages the Zener diode clamps the voltage to $-V_{\rm turn \; on} = -0.7$ V.

```{figure} /Fig-sol/51.png
---
width: 600px
name: fig-51
---
Voltage stabilization with a Zener diode
```
::::

### Avalanche Diode
The second cause for reverse breakdown occurs when the n-type or p-type, or both are slightly contaminated. In that case, the transition will be less sharp and therefore the depletion layer is much wider. The electric field across the depletion layer caused by the applied negative voltage will then not be large enough to break the covalent bonds. What happens is that free electrons in the electric field will be accelerated. If their kinetic energy is sufficiently high, electrons are able to ionize atoms in the lattice via collisions and the released electrons are then in turn accelerated again. At a certain voltage a kind of avalanche effect occurs, causing the number of free electrons and thus the current to increase sharply. This phenomenon is called *avalanche breakdown*.

## Diode Circuits
In the following paragraphs some examples of circuits with diodes are discussed. For all circuits it is assumed that silicon diodes are used.

### Signal "clamping"
Diodes are often used to limit signals (signal *clamping*). An example of this is the voltage stabilization with a Zener diode (see {numref}`fig:diode08`). In {numref}`fig:diode09` the signal is also limited, but now use is made of an ordinary diode.

```{figure} /Fig-ch5/Diod09.png
---
width: 400px
name: fig:diode09
---
Signal clamping using an ordinary diode
```

````{admonition} Exercise 5.2
:class: note

$V_{\rm i}$ in the circuit of {numref}`fig:diode09` is a sine wave with a voltage amplitude of 8 V.

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Run *Mult 5.2* and explain the behavior of the output signal relative to the input signal.
````

::::{admonition} Answer
:class: dropdown

When the sinusoidal voltage increases to the $V_{\rm turn \; on}$ value of 0.7 V the voltage gets clamped to that value until the sinusoidal voltage drops below 0.7 V. Then the diodes gets a (near) infinite resistance and the sinusoidal voltage is divided across the 5 k$\Omega$ (1/3) and 10 k$\Omega$ resistor. Hence the negative part of the sinusoidal voltage $V_0$ reaches $-8 \cdot \frac{2}{3} = -5.3$ V. 

```{figure} /Fig-sol/52.png
---
width: 600px
name: fig-52
---
Signal clamping using an ordinary diode
```
::::

Using the schematic of {numref}`fig:diode10` it is possible to design a circuit, which limits the output signal within a given voltage range, provided that the Zener diodes are well chosen.

```{figure} /Fig-ch5/Diod10.png
---
width: 400px
name: fig:diode10
---
Schematic to limit a voltage output range
```

````{admonition} Exercise 5.3
:class: note

Assume a sinusoidal input signal with an amplitude of 10 V.

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Design in Multisim a circuit, which limits the amplitude of the output signal to $\pm$5.4 V.
````

::::{admonition} Answer
:class: dropdown

Because of the $V_{\rm turn \; on}$ the break down voltage of the Zener diodes should be a little higher than 4.6 V. The resistor value is just to limit the current. Its value is not so important. The result is shown in the {numref}`fig:53`.

```{figure} /Fig-sol/53.png
---
width: 600px
name: fig:53
---
Using Zener diodes to limit the voltage range to $\pm$ 5.4 V
```
::::







### Single-phase rectifier
Perhaps the most important use of diodes is that of a *rectifier* in *DC* voltage supplies. The simplest form is the *half-wave rectifier*, whose circuit is shown in {numref}`fig:diode11`a. {numref}`fig:diode11`b shows the output signal for a sinusoidal input signal. The dashed lines show the output including the capacitor in the circuit, the solid curve the output without the capacitor.

```{figure} /Fig-ch5/Diod11.png
---
width: 500px
name: fig:diode11
---
Single-phase rectifier: (a) circuit; (b) output signal
```

*Without a capacitor*\
As long as the input voltage is larger than the turn on voltage of the diode, the diode will conduct. The output voltage will then be equal to the input voltage minus the small voltage drop across the diode. The drop is equal to the turn on voltage. If the diode input voltage falls below the turn on voltage (this is the case for the entire negative period of the sine wave and a small portion of the positive period), the diode will not conduct and therefore no current flows through the load resistance $R_{\rm L}$. Therefore the output voltage is zero. 

*With capacitor*\
Including a capacitor, a DC voltage can be realized. As long as the diode conducts, the capacitor will be recharged. When the voltage drop across the diode is less than the turn on voltage, conduction through the diode stops. The capacitor can only lose its charge when a current flows through the resistance $R_{\rm L}$. When this load is not too large ($R_{L}$ not too small) this loss is much slower than the change of the input signal. The output voltage will remain nearly constant. 

The discharge of the capacitor via $R_{\rm L}$ manifests itself as a kind of ripple on the output signal.
The output signal as a function of time is given by the following relation:

$$
V_{0}=V_{c}=V_{\rm max}\cdot \exp^{(-t / RC)}\cong \
V_{max}\cdot \left ( 1-\frac{t}{RC} \right ).
$$ (eq:Diod05)

From {numref}`fig:diode11`b can be seen that the discharge time is almost equal to the time period $T$ of the input signal. To calculate the peak-to-peak value of the ripple, a good approximation is given by:

$$
V_{\rm pp}=V_{\rm max}\cdot T/R_{\rm L}C= V_{\rm max}/ fR_{\rm L}C,
$$ (eq:Diod06)

where $f$ is the frequency of the input signal. Both from {numref}`fig:diode11`  and eqn.{eq}`eq:Diod06` it follows that the ripple size decreases, and thus the stability of the output voltage increases at higher frequency. Furthermore can be seen from {numref}`fig:diode11` that the capacitor is only charged for a small fraction of the positive phase of the signal. In fact, the negative phase is not used.

### Dual rectification
A much more effective method is the full-wave rectification, whose circuit is shown in {numref}`fig:diode12`a. {numref}`fig:diode12`b shows the output signal when a sinusoidal input signal is applied. Again, the solid curve is without capacitor, and the dashed curve with capacitor.

```{figure} /Fig-ch5/Diod12.png
---
width: 500px
name: fig:diode12
---
Dual full-wave rectifier: (a) circuit; (b) output signal
```

:::{note}
As opposed to the single-phase rectification of an alternating voltage source, the voltage source here is not grounded but kept "floating". In general a transformer is used as an AC voltage source with a floating output. The AC input often the 230 V mains.
:::

*Without capacitor*\
During the positive phase of the input signal at terminal $A$ will have a higher voltage than at terminal $B$. The diodes $D_{2}$ and $D_{3}$ will conduct (forward biased), while diodes $D_{1}$ and $D_{4}$ will not (reversed biased). The current flows from $A$ via D$_{2}$ and the load resistor $R_{\rm L}$ via $D_{3}$ back to $B$. This results in a positive output voltage at $V_{0}$. During the negative phase of the input signal $B$ is positive with respect to $A$. Now diodes $D_{1}$ and $D_{4}$ will conduct and the diodes $D_{2}$ and $D_{3}$ do not. In that case, the current flows from $B$ through $D_{4}$ and the load resistance $R_{\rm L}$ through $D_{1}$ back to $A$. The direction of the current through $R_{\rm L}$ remains the same. Both the positive and the negative phase of the input signal give a positive output voltage at $V_{0}$. 

*With capacitor*\
Including a capacitor, just as for the single-phase rectification, results in a DC voltage. The difference now is that the discharge time of the capacitor is halved. In other words eqn. {eq}`eq:Diod06` for the single-phase wave rectifier for a full wave rectifier changes to:

$$
V_{\rm pp}=V_{\rm max}\cdot T/2R_{\rm L}C= V_{\rm max}/ 2fR_{\rm L}C
$$ (eq:Diod07)

## Lab exercises

````{admonition} Exercise 5.4
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```
- Build a wave rectifier, as shown in {numref}`fig:diode12`. Use a 12 V transformer as an AC source (black box to be connected to the mains) with a 1 k$\Omega$ resistor in series. This is needed as the ADC of the NI Elvis II system can only take signals between $\pm$ 10 V. Make sure not to ground the part of the circuit with the transformer! Study first a circuit without a capacitor.
- Include a capacitor and study how the size of the ripple $V_{\rm pp}$ depends on $R_{\rm L}$ and $C$, and show this dependency in a graph (first choose a $C$ - should it be low or high? - and vary $R_{\rm L}$). \
Please note that the 1 k$\Omega$ resistor in the transformer circuit affects the value of $V_{max}$: it will not remain constant. When you do measurements with NI Elvis the oscilloscope will give you $V_{pp}$ and $V_{rms}$. Since $V_{max} = \sqrt{2} \cdot V_{rms}$ you can calculate $V_{max}$. Plot $V_{pp} / V_{max}$ vs $R_L$ and use a fit to check whether eqn. {eq}`eq:Diod07` holds
````

````{admonition} Exercise 5.5
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```
- Build  using the circuit of exercise 5.4 (remove the 1 k$\Omega$ resistor in the transformer circuit) a Zener stabilized voltage supply of 6.8 V. See {numref}`fig:diode08` and {numref}`fig:diode13`.
- Examine how the output voltage depends on the load and explain your findings.
```{figure} /Fig-ch5/Diod13.png
---
width: 400px
name: fig:diode13
---
Full-wave rectifier with Zener stabilization
```
````

[^1]: The voltage is positive when the diode is forward biased.

[^2]: The extra dash at the symbol of the diode indicates that it is a Zener diode.