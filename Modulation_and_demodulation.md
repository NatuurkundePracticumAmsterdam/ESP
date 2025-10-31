(modulation_and-demodulation)=
# 8. Modulation and demodulation

In many communication systems, but also in many measurement systems, a form of modulation is used. Modulation is a form of signal conversion where a carrier wave is used. One of the parameters of the carrier wave is depending on the input signal (modulated). Examples are:

- Amplitude Modulation (AM).
- Frequency Modulation (FM).
- Pulse height- and pulse width modulation.
- phase modulation.

A consequence of modulation with a generally much lower carrier frequency, is that signal is shifted towards a frequency range around the carrier frequency. This offers some great advantages.
- *Frequency Multiplexing:*\
By choosing different carrier frequencies for different input signals (e.g. radio signals from different transmitters), these signals can simultaneously be transmitted or sent over a single cable.

- *Elimination of offset and drift:*\
It is very hard to amplify slowly varying or DC signals without suffering from offset and drift. By modulating the signals to a much higher frequency range AC-amplifiers can be used, which do not suffer from offset and drift.

- *Noise suppression and 50 Hz insensitivity*\
Certain forms of noise act much more strongly at low than at high frequencies. By conversion to higher frequencies the influence of noise can be reduced. Many signals are disturbed by picking up the 50 Hz from the mains (230 V). By conversion to much higher frequencies the 50 Hz noise can more easily be filtered out.

```{figure} /Fig-ch8/Modul01.png
---
width: 400px
name: fig:Mod01
---
Signals of different kinds of modulation: a) symbol of a modulator; b) input signal; c) amplitude; d) frequency; e) pulse height; f) pulse width modulation
```

{numref}`fig:Mod01` shows signals $ x_{0} $ of different types of modulation for a given input signal $x_{i}$ and carrier wave $x_{d}$.
This chapter covers the amplitude modulation a little bit more in detail and illustrates its application in a commonly used measurement technique, the lock-in amplifier.

## Amplitude (de)modulation
There are various forms of amplitude modulation possible.

(AMsc)=
### AM with suppressed carrier

In this form of AM the amplitude of the carrier wave is multiplied by the input signal. In the simplest case, both the carrier wave and input signal are sinusoidal. Multiplying means multiplying two cosines (or sines) of different frequency. Multiplication of two cosines yields:

$$
\cos A \cdot \cos B = \dfrac{1}{2} \left[ \cos (A+B) + \cos (A-B) \right].
$$ (eq:Mod01)

Using eqn.{eq}`eq:Mod01` multiplication of the carrier wave frequency $ \omega_{\rm d} $ and input signal frequency $ \omega_{\rm i} $<sup>[^1]</sup> results in an output signal $ x_{0} $ given by:

$$
x_{0}(t) = \dfrac{x_{\rm d}x_{\rm i}}{2} \left[ \cos (\omega_{\rm d}+\omega_{\rm i})t + \cos (\omega_{\rm d}-\omega_{\rm i})t \right]
$$ (eq:Mod02)

where $ x_{\rm d} $ and $ x_{\rm i} $ are the amplitudes of the carrier wave and the input signal respectively.

```{figure} /Fig-ch8/Modul02.png
---
width: 500px
name: fig:Mod02
---
AM without carrier wave: a) time signal; b) frequency spectrum input signals; c) frequency spectrum output signals
```

{numref}`fig:Mod02`a shows the time-modulated signal, {numref}`fig:Mod02`b the frequency spectrum of the input signal and the carrier wave, and {numref}`fig:Mod02`c the frequency spectrum of the modulated output signal. The output signal consists of two components. One has a frequency equal to the sum of the frequencies of the carrier wave and the input signal, also referred to as *upper-side frequency*. The other frequency is equal to the difference of the two frequencies, referred to as *lower-side frequency*. Note that both the frequency of the input signal and the carrier wave are not appearing in the output signal.
The carrier wave is suppressed. Hence the name *suppressed carrier modulation*.

### AM with carrier wave
In standard AM systems, the output signal contains three components, the upper and lower side frequency components and a carrier wave frequency component. The third component is used for the tuning of the receiver (see {numref}`fig:Mod03`).\
In order to achieve this a DC signal is first added to the input signal with a magnitude equal to the amplitude of the carrier wave. The resulting wave signal is multiplied by the carrier wave signal. The output signal is then given by:

$$
\begin{split}
x_{0}(t) &= (x_{d}+x_{i}\cos (\omega_{i}t))x_{d}\cos(\omega_{d}t) \\
&= x_{\rm d}^{2}\cos(\omega_{\rm d}t)+\dfrac{x_{\rm d}x_{\rm i}}{2} [ \cos (\omega_{\rm d}+\omega_{\rm i})t \\
& + \cos (\omega_{\rm d}-\omega_{\rm i})t ].
\end{split}
$$ (eq:Mod03)


```{figure} /Fig-ch8/Modul03.png
---
width: 500px
name: fig:Mod03
---
AM with carrier wave: a) time signal; b) frequency spectrum
```

### Amplitude modulation with an arbitrary input signal
Until now the input signal is sinusoidal. In general this is not the case.
For example, in the event that the input signal is a sound or a voice, the input signal will be a multiple of sinusoidal components within a frequency range of about 20 Hz to 20 kHz.
After modulation each frequency component will give rise to an upper and a lower side band frequency component in the output signal, and sometimes also a carrier wave component. The total input signal after modulation will constitute an upper and lower side frequency band. The width of these frequency bands is equal to the bandwidth of the input signal.

````{admonition} Example 
:class: tip

Suppose an audio signal is limited to a frequency range of 10-4000 Hz. The carrier wave has a frequency of 1 MHz. The modulated signal is then divided into two frequency bands:
* lower sideband 996.00 - 999.99 kHz
* the upper sideband 1000.01 - 1004.00 kHz

{numref}`fig:Mod04` shows the frequency spectrum of the output signal. 

```{figure} /Fig-ch8/Modul04.png
---
width: 400px
name: fig:Mod04
---
Example of a frequency spectrum of an audible signal with amplitude modulation
```
````

````{admonition} Example 
:class: tip

If the objective is to get a hundred different radio channels using AM in a specified frequency band and the highest frequency in the original audio signal is 20 kHz, then the width of this frequency band must be at least (20 kHz x 2) x 100 = 4 MHz.  
````

### Amplitude modulation techniques

As is apparent from what is covered so far, multiplication plays an important role in the amplitude modulation. The most direct way to achieve multiplication is to make use of an analog multiplier, such as the AD 532 (OpAmp), as we will do in the Lab Exercises. For the mixing of the carrier wave signal an adder circuit can be used, which is described in section 6.4.4. 

*'Switch modulator'* \
Another way to mix the carrier wave signal is the switch modulator. In this technique the input signal is switched alternately on and off with the aid of a switch. The frequency with which this happens is the frequency of the carrier wave. This process can be described as multiplication of the input signal $ x_{\rm i}(t) $, and the switch signal $ s(t) $, where $ s(t) $ is equal to 1 when the switch is closed and 0 when the switch is open. {numref}`fig:Mod05`b shows $ s(t) $, where $ T=\dfrac{2\pi}{\omega_{\rm d}}$, the time period.


```{figure} /Fig-ch8/Modul05.png
---
width: 400px
name: fig:Mod05
---
a) Switch Modulator; b) Switch signal
```

The Fourier development of the switch signal in {numref}`fig:Mod05`b is:

$$
s(t) = \dfrac{1}{2}+\dfrac{2}{\pi}(\sin \omega_{\rm d}t+\dfrac{1}{3}\sin 3 \omega_{\rm d}t+\dfrac{1}{5}\sin 5 \omega_{\rm d}t+...).
$$ (eq:Mod04)

The output signal $ x_{0}(t) $ is given by:

$$
\begin{split}
& x_{0}(t) = x_{i}(t) \cdot s(t) \\
 &= x_{\rm i} \left ( \dfrac{1}{2}+\dfrac{2}{\pi} \sum\limits_{1}^\infty \dfrac{1}{n} \sin n\omega_{\rm d}t \right ) \cos\omega_{\rm i}t \; (n = {\rm odd}) \\
 & =\dfrac{1}{2}x_{\rm i}\cos\omega_{ \rm i}t \, +
\dfrac{x_{\rm i}}{\pi} [ \sin( \omega_{\rm d}+\omega_{i})t \\
& + \sin( \omega_{\rm d}-\omega_{\rm i})t \, +  \dfrac{1}{3}(\sin(3 \omega_{\rm d}+\omega_{\rm i})t \\
&+ \sin(3 \omega_{\rm d}-\omega_{\rm i})t )]
\end{split}
$$ (eq:Mod05)

The spectrum of this signal is shown in {numref}`Fig:Mod06`.

```{figure} /Fig-ch8/Modul06.png
---
width: 400px
name: fig:Mod06
---
Spectrum of the switch modulator
```

This modulated signal contains a large number of side band pairs around the carrier wave frequency and around all odd multiples of this frequency. The component containing the frequency of the original input signal is the result of multiplication by the mean of $s(t)$, which is equal to $\dfrac{1}{2}$.\
This low-frequency component, and all components having frequencies around $ 3\omega_{\rm d} $ and higher can be removed with the aid of a band-pass filter. The resulting signal then is an AM signal with suppressed carrier wave.\
The advantage of the switch modulator with respect to the analog multiplier is its simplicity and better accuracy.

### AM Demodulation in the case of carrier wave
Inspection of {numref}`fig:Mod03`b shows the correspondence between the original signal and the envelope of the modulated signal. By determining the envelope of the modulated signal the original signal can be reconstruct. The envelope can be determined by rectifying the signal of {numref}`fig:Mod03`b by a single or better double-sided rectifier followed by a low pass filter. The result can be seen in {numref}`fig:Mod07`.

```{figure} /Fig-ch8/Modul07.png
---
width: 500px
name: fig:Mod07
---
(a) Single and (b) Full-wave rectified AM signal $v_{\rm i}$ followed by a low-pass filter. The resulting signal is $v_{0}$
```

With a properly selected time constant of the low pass filter the output signal $v_{0}$ will be proportional to the average of the rectified signal and follows exactly the original input signal.

(AMdm)=
### AM Demodulation in case of suppressed carrier wave

As is obvious in {numref}`fig:Mod02` the envelope of the output signal, in the case of a suppressed carrier wave, bears no similarity with the original input signal. In order to reconstruct the original signal the technique of rectifying can not be applied. The technique applied in this case (which can also be used by AM modulation with a carrier wave) is called *synchronous detection*. 

*Synchronous detection* \
In the case of synchronous detection, the modulated signal is multiplied by a signal with the same frequency as the carrier wave signal, and is then sent through a low pass filter (see {numref}`fig:Mod08`).

```{figure} /Fig-ch8/Modul08.png
---
width: 500px
name: fig:Mod08
---
Synchronous detector
```

In order to see the result of these operations we make again use of eqn. {eq}`eq:Mod01` were the multiplication of two sinusoidal signals with frequencies $ \omega_{1} $ and $ \omega_{2} $ result in a signal containing two frequency components: the sum frequency $ \omega_{1}+\omega_{2} $ and difference frequency $ \omega_{1}-\omega_{2} $.\
An AM signal with suppressed carrier wave contains, as shown in {numref}`fig:Mod02`c, two frequency components $ \omega_{\rm d}+\omega_{\rm i} $ and $ \omega_{\rm d}-\omega_{\rm i} $. Multiplication with a signal $ x_{s}(t)=x_{\rm s}\cos(\omega_{\rm d}t+\phi) $, which is synchronous with the carrier wave signal, will result in a signal with three frequency components: $\omega_{\rm i}$,
$2\omega_{\rm d}-\omega_{\rm i} $, $2\omega_{\rm d}+\omega_{\rm i} $. $ \phi $ is important when there is a phase shift between the two carrier waves used for the modulation and for demodulation. \
Using eqn.(\ref{eq:Mod02}) the result can be expressed as:

$$
\begin{split}
x_{0}(t)  & = \dfrac{x_{\rm s}x_{\rm d}x_{\rm i}}{2} [ \cos (\omega_{\rm i}t) \cos \phi  \\
+ & \dfrac{1}{2} ( \cos \left( (2 \omega_{\rm d} + \omega_{\rm i} ) t + \phi \right) \\
+ & \cos \left( ( 2 \omega_{\rm d} - \omega_{\rm i} ) t + \phi \right) ) ].
\end{split}
$$ (eq:Mod06)

With the aid of a suitably chosen low pass filter the two frequency components nearby $ 2 \omega_{\rm d} $ can be filtered out and only the component with the original frequency $ \omega_{\rm i} $ remains. This component is proportional to $\cos \phi$ and has a maximum for $ \phi=0 $, and a minimum for $ \phi=\frac{\pi}{2} $. Thus, by choosing the phase of the synchronous signal  properly the demodulated signal can be maximized.

````{admonition} Exercise 8.1
:class: note

A signal with a highest frequency component of 400 Hz is sent as an AM signal with suppressed carrier wave. The carrier frequency is 10 kHz. Prior to the signal demodulation, a disturbance of 1 kHz is picked up. The amplitude of both the signal and the disturbance is 1 V and the amplitude of the carrier wave is 2 V.
- Explain which frequencies are present at the following moments in the whole process:
  - before modulation
  - before demodulation
  - during demodulation, but before the low pass filter
  - after the low pass filter

```{figure} /Fig-ch1/multisim.png
---
width: 50px
name: fig-multisim
align: right
---

```
- Open *Mult 8.1* and check your results.
- Set $ \omega_{3 \, {\rm dB}} $ of the low pass filter such that the original signal can pass nearly undisturbed.
- How many dB are the frequency components in the output signal, due to the disturbance of 1 kHz, at this value of $ \omega_{3 \, {\rm dB}} $ theoretically suppressed?
````

::::{admonition} Answer
:class: dropdown

A signal with a highest frequency component of 400 Hz is sent as an AM signal with suppressed carrier wave. The carrier frequency is 10 kHz. Prior to the signal demodulation, a disturbance of 1 kHz is picked up. The amplitude of both the signal and the disturbance is 1 V and the amplitude of the carrier wave is 2 V (see {numref}`fig:91_mod_demod_circuit`). 

```{figure} /Fig-sol/91_mod_demod_circuit.png
---
width: 600px
name: fig:91_mod_demod_circuit
---
The modulation/demodulation circuit
```

The frequencies present were studied for different parts of the total process:
- Before modulation, the two input frequencies are present in the signal: $f_i = 400$ Hz and $f_d = 10$ kHz.
- After modulation, the two input signals behave like an AM signal with a suppressed carrier wave (see eqn. {eq}`eq:Mod02`): $f_d - f_i = 9.6$ kHz and $f_d + f_i = 10.4$ kHz (see {numref}`fig:91_after_mod`).
```{figure} /Fig-sol/91_after_mod.png
---
width: 600px
name: fig:91_after_mod
---
The signal after modulation
```
- Before the demodulation a disturbance frequency $f_s$ of 1 k Hz is added. So during the modulation, but before the low-pass filter the output signal has 3 frequencies: $f_d - f_i = 9.6$ kHz, $f_d + f_i = 10.4$ kHz and $f_s = 1$ kHz.
- After the demodulation but before the low-pass filter, the behavior of the frequency is given by eqn. (8.6), resulting in: $f_i = 400$ Hz, $f_d - fs = 9$ kHz, $f_d + fs = 11$ kHz, $2f_d - f_i = 19.6$ kHz and $2f_d + f_i = 20.4$ kHz (see {numref}`fig:91_after_demo_before_LPF`).
```{figure} /Fig-sol/91_after_demo_before_LPF.png
---
width: 600px
name: fig:91_after_demo_before_LPF
---
The signal after demodulation before the low-pass filter
```
- Using a low-pass filter with $R = 2.6 \; {\rm k}\Omega$ and $C = 100$ nF ($\omega_{3 \; {\rm dB}} = 3846 \; {\rm rad/s}$, so $f_{3 \; {\rm dB}} = 612$ Hz) higher frequencies can be filtered out and only the original input signal $f_i = 400$ Hz is obtained (see {numref}`fig:91_after_lpf`).
```{figure} /Fig-sol/91_after_lpf.png
---
width: 600px
name: fig:91_after_lpf
---
The signal after demodulation after the low-pass filter
```
::::

### Multiplier Lab Exercises
In the following lab exercises an analog multiplier the AD 532 is used. This IC is placed in a box together with a light sensitive circuit (see {numref}`fig:Mod09`).

```{figure} /Fig-ch8/Modul09.png
---
width: 500px
name: fig:Mod09
---
Box BPX 25 + amplifier and multiplier
```

To use the multiplier you must first connect the power connections (+ and - 15V and GND). (Before connection turn off the power supply of the NI Elvis system and pay attention to the polarity!).
For the multiplier the specifications in the data-sheet apply, however with the following modifications:
- The output impedance is 1 k$\Omega$.
- The "-" input of the Y input is connected to the ground.
- The "-" input of the X input has an input impedance of 1 k$\Omega$.

````{admonition} Exercise 8.2: Modulation
:class: note
:name: ex82

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Check the specifications of the AD 532 integrated multiplier. (The data-sheet can be found on the internet.)
- Build a multiplier and multiply two sine signals of 10 kHz and 1 kHz with each other. In NI-Elvis the analysis can be done with the Dynamic Signal Analyzer.
- Check eqn. {eq}`eq:Mod02` by measuring the sum and difference frequencies of the modulated signal. Ensure that sum and difference frequencies are well distinguishable.
- If more significant frequency peaks are observed, try to give an explanation.
- Use this setup in the next exercise.
````

````{admonition} Exercise 8.3: Demodulation
:class: note
:name: ex83

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Describe the operation of a synchronous detector.
- Build a synchronous detector with a low-pass filter a $ \omega_{3 \, {\rm dB}}$ of about 1 kHz. Take as the input of the synchronous detector the modulated signal of the previous [Exercise 8.2](#ex82) with 400 Hz (instead of 1 kHz) as an input signal and 10 kHz as the reference signal. Which frequencies are observed in the output signal just before the low pass filter of the synchronous detector?
- Give an explanation of all the significant frequency peaks you observe!
- Keep the frequency of the reference signal constant and study the frequency characteristic after the low pass filter (look only at the amplitude).
- Give an explanation of all the significant frequency ranges you observe!
````

## An application of a synchronous detector: the Lock-in Detector

### Principle
In many setups of physics experiments small voltages or currents are measured in very interference rich environment (pumps, electronics, outdoor light, fellow students, etc.). A method that can be applied in order to minimize the influence of the disturbance is to make use of a so-called *Lock In Amplifier* (LIA). In this technique, a reference signal (a square wave or something similar) is modulated with the signal that you want to measure. A LIA will only respond to input signals which have the same frequency as the reference signal, and are therefore insensitive to interference signals that have arbitrary (other) frequencies.
The principle of the LIA is shown in {numref}`fig:Mod10` and is based on synchronous detection (see {ref}`AMdm`).

```{figure} /Fig-ch8/Modul10.png
---
width: 600px
name: fig:Mod10
---
Principle of a Lock-in amplifier
```

The LIA has two inputs: the signal input and the reference input. The input signal is amplified if necessary. Usually, this is done by an AC amplifier, with a possible DC component in the input signal already filtered out. For the reference connection and modulation of the measuring signal the same reference signal is used.
The box with $ \phi $ is a phase shifter, which allows the phase of $ V_{ref} $ to be adjusted. The signals are then connected to a synchronous detector with the variable low pass filter. Only when $ f_{\rm ref} - f_{\rm in} $ is small enough there will be a signal from the synchronous detector.

What exactly happens in the entire system? \
Modulation of the reference signal with the measured signal $ x(t) $ provides a signal $x(t) \cos ( \omega_{\rm ref} \cdot t )$. Suppose two interference signals are mixed before the signal reaches the LIA. One is a DC-offset of $ a $ and the other a signal with frequency $ f_{2} $. The input signal $ V_{\rm in} $ is then given by:

$$
V_{in}=x(t) \cos (\omega_{\rm ref}t)+a+b \cos (\omega_{2} t).
$$ (eq:Mod07)

The DC offset is filtered out by the AC amplifier. After multiplication in the synchronous detector with the reference signal $ \cos (\omega t + \phi ) $, the signal looks like:

$$
\begin{split}
 x_{0}(t)  & = \dfrac{x(t)}{2}( \cos \phi + \cos (2 \omega_{\rm ref}t + \phi )) \\
+ & \dfrac{b}{2} ( \cos ( (\omega_{\rm ref} + \omega_{2})t + \phi ) \\
+ & \cos ( (\omega_{\rm ref} - \omega_{2})t + \phi )).
\end{split}
$$ (eq:Mod08)

The low pass filter passes through only the term $ \dfrac{x(t)}{2} \cos \phi $.

:::{note}
Note that the lock-in technique is in fact nothing else than demodulation of a signal with suppressed carrier wave (see {ref}`AMdm` and [Exercise 8.3](ex83)).
:::

Using the phase shifter in the reference channel, this term, which is proportional to the original measurement signal, can be maximized.\
It is important to make the low pass filter very narrow in order to filter out noise as much as possible. However, not so narrow that also frequency components which are present in the measurement signal are also filtered out.

````{admonition} Example 
:class: tip

The lock-in technique is often used in optical experiments involving interference from other light sources, such as the fluorescence light in the lab (100 Hz), daylight, etc. {numref}`fig:Mod11` shows a schematic diagram of an optics experiment, making use of the lock-in technique.

```{figure} /Fig-ch8/Modul11.png
---
width: 600px
name: fig:Mod11
---
Optical experiment with lock-in detector
```
````

Light of a lamp with constant intensity $ I_{0} $ shines on a rotating disk (chopper) with a angular velocity $\omega$. The disk contains holes. Behind the chopper, the intensity of the light will vary with frequency $ \omega $. The resulting carrier wave is then modulated by the experiment measurement signal $ x(t) $.
When light from a fluorescent lamp (frequency 100Hz) disturbs the measurement signal, the detector apart from the $ \omega $ component will also detect a $ 200\pi $ component. The lock-in amplifier with a suitably chosen low pass filter will filter out the $ 200\pi $ component and produce an output signal which is proportional to $ x(t) $.

### Simulation experiment with a Lock-In

In the following exercises a simple experiment is presented with a lock-in.

The diagram of the setup is illustrated in {numref}`fig:Mod12`. The modulated signal is made by driving a LED with a square wave (see {numref}`fig:Mod13`). The detected signal is measured by a photo diode, then amplified, and with the aid of a synchronous detector (see {ref}`AMsc`) compared with the reference frequency. In the reference channel no phase shifter is used.


```{figure} /Fig-ch8/Modul12.png
---
width: 600px
name: fig:Mod12
---
Diagram optics setup with a lock-in amplifier. For synchronous detector see {numref}`fig:Mod08`.
```

In order to detect the modulated signal, we use a light-sensitive diode, the BPX 25. The operation of this photo diode is basically the same as that of the ordinary diode. The free charge carriers in the base are in this case released by incident photons instead of an applied voltage.\
The BPX 25 and associated amplifier (see {numref}`fig:Mod09`) are placed together with the multiplier in a single box. Pay attention again to connect the box properly! Also check out the data sheets.

````{admonition} Exercise 8.4
:class: note

```{figure} /Fig-ch3/Lexercise.png
---
width: 50px
align: right
name: fig-Lexercise
---

```

- Build the circuit shown in figure 9.14 to create a modulated light signal. The maximum current through the LED must remain below 20 mA. Use a square wave with a frequency of about 1 kHz, about 3 $V_{p-p}$ with an offset such that $V_{min} \geq 0$ V.
```{figure} /Fig-ch8/Modul13.png
---
width: 400px
name: fig:Mod13
---
A modulated light source
```
- We will investigate a LIA set up according to the general diagram of figure 9.12. We will not include an optical setup so that part can be left out. Before you investigate the circuit experimentally first derive what signals you expect to observe. Use 
$ 
\begin{split}
\\
&\sin A \cdot \sin B = \frac{1}{2} \left[ \cos (A - B) - cos (A + B)\right], \\
\\
&V_{in} = I_o \cdot \left[ \frac{1}{2} + \frac{2}{\pi} \left( \sin \omega_r t + \frac{1}{3} \sin (3 \omega_r t) \right) \right] \; {\rm and} \\
\\
&V_{ref} = \left[ \frac{1}{2} + \frac{2}{\pi} \left( \sin \omega_r t + \frac{1}{3} \sin (3 \omega_r t + \phi) \right)  \right]. \\
\\
\end{split}
$ 
- Construct the LIA circuit, including the low-pass filter after the synchronous detector.
- Measure the variation in the amplitude of $ V_{out} $ due to frequency variations of the light signal after the LPF. Do so using an oscilloscope recording both the input and output signal of the synchronous detector for 5 frequencies of the LED below 1 kHz and 5 frequencies above 1 kHZ (up to about 10 kHz). Show the results (amplitude function) in a manually generated Bode plot (using a dB scale).
- Using the frequency analyser of NI-Elvis investigate the output voltage *before* the LPF. Explain the observations.
- In this setup an experiment is situated between the LED and the photo diode: place an electric fan between the LED and the photodiode. The electric fan runs after applying a voltage of about 5 V (use the variable voltage supply of NI-Elvis). When set to manual you can use the dial on the right top of the NI-Elvis board to adjust the voltage. What component of the output frequency signal in $ V_{out} $ is due to this experiment? Determine this frequency. Hint: you should probably increase the $\omega_r$ for this experiment.

The last three tasks may not work in S5.29 due to grounding problems. If you have time left give it a try!
- For a disturbance we use a second LED. Place this LED next to the first one. Connect this LED to a second signal generator.
- Study the influence of the frequency and the light intensity of the second LED on the output voltage.
- Explain what happens when $ f_{{\rm LED}_1} \approx f_{{\rm LED}_2} $. Make a graph around this frequency.
````

[^1]: Caution! In this situation angular frequencies are used rather than frequencies, but the reference to 'angle' is usually omitted.

