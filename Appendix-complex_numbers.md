(complex_numbers)=
# Appendix D: Complex numbers

## Properties of complex numbers
### Imaginary Numbers
The square root of a negative real number is referred to as an imaginary number. So
$\sqrt{-2}$, $\sqrt{-5}$ and $\sqrt{-11}$ are all imaginary numbers. The unit of imaginary numbers is $\sqrt{-1}$ and is usually denoted by the letter $i$. To avoid confusion with the current $i$ in electronics, the letter $j$ is used. So

$$
i = j = \sqrt{-1}.
$$ (eq1)

### Complex numbers
A complex number is a number of the form

$$
z = x + j \cdot y.
$$ (eq2)

where $x$ and $y$ are real numbers. The variables $x$ and $y$ are  the real (Re$z$) and the imaginary (Im$z$) component of $z$ respectively. The complex number $z$ can also be written as:

$$
z = ({\rm Re} \, z,\, {\rm Im} \, z) = (x,\, y).
$$ (eq3)

In fact a complex number has two coordinates and can be graphically displayed as a point in a plane, the complex plane. This rectangular or the Cartesian coordinates are plotted along the real and the imaginary axis (see {numref}`figD1`). 

```{figure} /Fig-app/FigureD1.png
---
width: 400px
name: figD1
---
Complex plane
```

A complex number can also be represented in a polar notation:

$$
z = (|z|,\varphi),
$$ (eq4)

where:

$$
|z| = r = \sqrt{({\rm Re} \, z)^{2}+({\rm Im} \, z)^{2}}
$$ (eq5)

is the length of the vector (${\rm Re } \, z$, ${\rm Im} \, z$), also known as the modulus of $z$, and:

$$
\varphi = \arg z = \tan^{-1} \left( \dfrac{{\rm Im} \, z}{{\rm Re} \, z}\right ) \pm k \cdot \pi
$$ (eq6)

is the angle this vector makes with the positive real axis, with $k$ as an integer, also known as the argument of $z$.

:::{note}
The $\pm  k \cdot \pi$ has to do with the fact that $\varphi$ is a continuous quantity, in principle with a range of $-\infty$ and $+\infty$, while the function $tan^{-1}$ is defined for the interval $-\pi/2$ to + $\pi/2$.
:::

The inverse transformation from polar coordinates to Cartesian coordinates is given by:

$$
\begin{split}
{\rm Re} \, z &= |z|\cos \varphi \\
{\rm Im} \, z &= |z| \sin \varphi.
\end{split}
$$ (eq7)

A third way to express a complex number is to make use of the complex exponential function:

$$
z = |z|\exp^{j\varphi}  = r\exp^{j\varphi},
$$ (eq8)

where:

$$
\exp^{j\varphi} = \cos \varphi +j\sin \varphi.
$$ (eq9)

Using the above definitions, and relationships we can derive some rules.

For addition and subtraction:

$$
\begin{split}
z & = z_{1} \pm z_{2}\Rightarrow \\
{\rm Re} \, z &= {\rm Re} \, z_{1} + {\rm Re} \, z_{2} \\
{\rm Im} \, z & = {\rm Im} \, z_{1} + {\rm Im} \, z_{2};
\end{split}
$$ (eq10)

for multiplication:

$$
\begin{split}
z & = z_{1} \cdot z_{2}\Rightarrow \\
|z| & = |z_{1}| \cdot |z_{2}| \\
\arg z & = \arg z_{1} + \arg z_{2};
\end{split}
$$ (eq:D13)

for division:

$$
\begin{split}
z & = \frac{z_{1}}{z_{2}} \rbrace \Rightarrow \\
|z| & = \frac{|z_{1}|}{|z_{2}|} \\
\arg z & = \arg z_{1} - \arg z_{2}.
\end{split}
$$ (eq:D14)

