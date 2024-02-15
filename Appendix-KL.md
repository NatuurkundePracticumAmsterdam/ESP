(Kirchhoff)=
# Appendix B: Kirchhoff's laws, voltage and current sources

## Kirchhoff's laws
### Nodes, branches and circles
- A node is a point in a circuit where two or more electronic elements are coupled to each other.
- A branch is the path between two nodes consisting of one single element.
- A circle is a closed path in a circuit along random branches, in which no nodes are crossed more than once.

```{figure} /Fig-app/FigureB1.png
---
width: 400px
name: fig:FigB1
---
Nodes, branches and circles
```

The circuit in {numref}`fig:FigB1` has  three nodes: a, b and c, four branches: a-b, a-c and two b-c branches and three loops: one loop consisting of a voltage source V, and resistors $R_{1}$ and $R_{2}$, one consisting of the voltage source V, resistor $R_{1}$ and current source $I$, and one loop consisting of resistor $R_{2}$ and current source $I$.

### Kirchhoff's Voltage Law

> In a closed loop the sum of all voltages is zero.

The following rules apply:
- Take the voltage change positive when in a loop the negative voltage terminal enters a voltage source.
- Take the voltage change negative when the loop and the current go in the same direction through the resistor.

A very frequently used circuit is the voltage divider shown in {numref}`fig:FigB2`.

```{figure} /Fig-app/FigureB2.png
---
width: 400px
name: fig:FigB2
---
Voltage divider
```

With the help of Kirchhoff's voltage law and Ohm's law for the circuit of {numref}`fig:FigB2` we obtain:

$$
V_{2}=\dfrac{R_{2}}{R_{1}+R_{2}} \cdot V
$$ (eq1)

### Kirchhoff's Current Law

> The sum of all currents flowing towards and from a node is zero.

The following rules apply:
- Take the current flowing towards a node positive and away from a node negative.

The Kirchhoff's current law is often used in circuits with parallel flows, such as shown in {numref}`fig:FigB3`.

```{figure} /Fig-app/FigureB3.png
---
width: 400px
name: fig:FigB3
---
Parallel flows
```

For the circuit shown in {numref}`fig:FigB3` the current $I_2$ is given by:

$$
I_{2}=\dfrac{R_{1}}{R_{1}+R_{2}} \cdot I.
$$ (eq2)

## Voltage and current source
### Voltage sources
Every real voltage source has an internal resistance. If the voltage source is connected to an external circuit, a certain current will flow and causes a voltage drop across the internal resistance, with the result that the voltage across the external load is lower than the original voltage of the source. This effect will be smaller as the internal resistance is smaller. A ideal voltage source is therefore a voltage source with zero internal resistance.\
A real voltage source can be understood as an ideal voltage source $V$ in series with a source resistor $R_{\rm s}$. (see {numref}`fig:FigB4`). $R_{\rm s}$ is often called the internal or output resistor.

```{figure} /Fig-app/FigureB4.png
---
width: 350px
name: fig:FigB4
---
Real voltage source
```

Without a load the voltage $V_{\rm AB}$ across the output is equal to $V$, because no current flows through $R_{\rm s}$

```{figure} /Fig-app/FigureB5.png
---
width: 400px
name: fig:FigB5
---
Real voltage source with a load
```

For {numref}`fig:FigB5`), with a voltage source  connected to a resistor $R_{\rm L}$ the output or terminal voltage $V_{\rm AB}$, using eqn. {eq}`eq1`, is given by:

$$
V_{\rm AB}=\dfrac{R_{\rm L}}{R_{\rm s}+R_{\rm L}} \cdot V
$$ (eq3)

$V_{\rm AB}$ will approach $V$ better if $R_{\rm s}$ becomes smaller or $R_{\rm L}$ larger.\
For an ideal voltage source the output voltage $V_{\rm AB}$ is constant, regardless the magnitude of the current $I$ and therefore independent of load $R_{\rm L}$. For an ideal voltage source $R_{\rm s}$ equals zero must apply.

### Current sources
For current sources there is a similarity. An ideal voltage source has an output voltage independent of the current supplied by the voltage source. An ideal current source has an output  current independent of the voltage between the connection terminals. A realistic power source can be interpreted as an ideal current source $I$, in parallel with an internal source resistance $R_{\rm s}$, as shown in the circuit in {numref}`fig:FigB6`.

```{figure} /Fig-app/FigureB6.png
---
width: 400px
name: fig:FigB6
---
Real current source
```

When there is no load between a and b, the full current $I$ will pass through the internal resistance $R_{\rm s}$.

```{figure} /Fig-app/FigureB7.png
---
width: 400px
name: fig:FigB7
---
Real current source with load $R_{\rm L}$
```

A resistor $R_{\rm L}$ connected to a current source (see {numref}`fig:FigB7`) will have an output current $I_{\rm L}$ (using eqn. {eq}`eq2`) equal to:

$$
I_{L}=\dfrac{R_{\rm s}}{R_{\rm s}+R_{\rm L}} \cdot I.
$$ (eq4)

$I_{\rm L}$ will approach $I$ better as $I_{\rm s}$ gets smaller.
This is the case when $R_{\rm s}$ becomes larger or $R_{\rm L}$ smaller.

In an ideal current source $R_{\rm s}$ must be infinitely large, just the opposite to an ideal voltage source, where $R_{\rm s}$ must be equal to zero.