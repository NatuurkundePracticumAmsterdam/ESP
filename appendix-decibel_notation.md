(decibel)=
# Appendix C: Decibel notation

## Decibel notation
The electrical power gain of an amplifier can take on very high values. Values greater then $10^{6}$ are very common. Therefore, the power gain is often shown in a logarithmic form and not in a form of eqn. {eq}`eq:PA`. The unit dB (decibel) is used.

$$
{\rm Power \,\, Gain \,\, (dB)} =10 {}^{10}\log \frac{P_{\rm out}}{P_{\rm in}}
$$ (eq:C1)

An important consequence of the logarithmic notation is that, when a coupling is made with a number of systems after each other, the overall gain can be found as the sum of the individual gain of each systems expressed in decibels.

The power gain of + 3 dB and -3 dB correspond with doubling and halving of the power gain respectively. These two values will turn up in the course regularly.

Using Ohm's law eqn. {eq}`eq:C1` can be written as: 

$$
{\rm Power \,\, Gain\,\, (dB)} = 10 {}^{10} \log \dfrac{ \left( V^{2}_{\rm out} / R_{\rm L} \right)}{ \left( V^{2}_{\rm in} / R_{\rm i} \right)},
$$ (eq:C2)

where $R_{\rm L}$ is the load and $R_{i}$ is the input resistance of the amplifier.
For the special case that $R_{\rm L}$ and $R_{\rm i}$ are equal to each other  eqn. {eq}`eq:C2` can be simplified to:

$$
\begin{split}
{\rm Power \,\, Gain \,\, (dB)} & = 20 {}^{10}\log \frac{V_{\rm out}}{V_{\rm in}} \\
 & = 20 {}^{10} \log ({\rm Voltage \,\, Amplification}).
 \end{split}
$$ (eq:C3)

Although the decibel notation is only applicable to power amplification. in literature, it is very common use it for voltage amplification as well, even when $R_{\rm L}$ and $R_{\rm i}$ are not equal to each other. The voltage gain in decibels is defined as:

$$
{\rm Voltage \,\, Gain \,\, (dB)} = 20 {}^{10} \log \frac{V_{\rm out}}{V_{\rm in}}.
$$ (eq:C4)

A voltage gain of + 3 dB or - 3 dB, means a voltage gain of $\sqrt{2}$ and $\dfrac{1}{2}\sqrt{2}$ respectively.