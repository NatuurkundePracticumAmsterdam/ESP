(Introduction)=
# Introduction

## Corona measures
We find it important that everyone feels safe and comfortable studying on campus. If you experience any symptoms (coughing, sneezing, a sore throat, congestion or a runny nose) please take a self-test and if you are positive stay at home. If you need to stay at home please inform [Gerrit Kuik](mailto:g.j.kuik@vu.nl). 

## Objective
The objective of the *Electronics \& Signal Processing* lab course is to become familiar with basic concepts of electronics, signal processing and control systems techniques. Electronics is very much a "hands-on" subject. One can gather knowledge through studying literature (which you should certainly do), but only by *doing* electronics the subject can really be mastered.

## Setup of course

The *Electronics \& Signal Processing* course is a combination of lectures, tutorials and labs.  
A number of sessions will start with a lecture where theory discussed in the syllabus will be clarified.
The first six chapters cover basic concepts of electronics. The final chapters cover more advanced topics, utilizing basic concepts covered in the earlier chapters.

## Systems board
Circuits are build on *NI Elvis* system boards. These boards of National Instruments combined with LabVIEW based software offers the possibility of testing and analysis of circuits on a computer.

## Simulation software
Circuits can also be simulated on a computer. For this purpose this course uses the software *Multisim*, which offers a database of about a thousand electronic components for the design of circuits. It also provides several virtual instruments such as voltage and current sources, function generators, oscilloscopes, etc. to generate signals and to perform measurements. *Multisim* offers a wide range of tools to perform analysis on data, including comparison of simulated and 'real' data obtained from circuits on a *NI Elvis* system board.

## Exercises
Each chapter offers exercises sandwiched in between text and at the end.
- Exercises sandwiched in between text are mainly to assess insight, to develop problem solving skills (calculations) and to learn to develop circuits using *Multisim* (tutorial exercises). *Multisim* exercises can be recognized through the icon shown below.

```{figure} /Fig-ch1/multisim.png
---
height: 50px
name: MS-fig
---

```

You do not need to hand in these exercises but you will be asked to show your work during the lab sessions. Model answers will be made available through Canvas. 
- The exercises at the end of each chapter are circuit designs that have to be constructed using the *NI Elvis* system board (lab exercises). The lab exercises you need to hand in (individually) as a digital lab journal (see {ref}`reporting`).

## Test
Two tests are conducted during the course on the basics covered in the first six chapters. The exams are given (a) to encourage students to master the basic concepts needed for the lab exercises, and (b) to assess how well the basic concepts are known. 
The weight of these tests can be compared to a mid-term exam. When you complete the weekly exercises, preparation for these tests should be minimal. 
Unless to unforeseen circumstances (at the discretion of the lecturer) tests cannot be repeated.

## Work schedule
In the lab you will spend 4 half-days per week conducting the circuit design exercises. In order to be able to complete these exercises in time pre-lab preparation is required: studying theory and conducting the tutorial exercises. During classes you will then have sufficient time to ask questions on theory and/or tutorial exercises when needed, and to design and test the circuits. \
Be prepared that during lab exercises calling for assistance usually results in being given hints and referrals to literature to help you discover how to solve the problem yourself: the aim is that you learn to work independently and to develop a research attitude.

(ps)=
## Problem solving

You are bound to run into lab exercises where circuits you built  either do not work or show unexpected behavior. Below some hints are given to prevent problems as much as possible and how to solve them if they still occur.
* Build well organized circuits:
    - Locate inputs on the left of your circuit board and outputs on the right.
    - Use different colors of wires for grounding, positive and negative poles of the power supply, inputs and outputs.
* Power supply: \
Switch on the power only after the circuit is complete, and switch off the power when you make changes to the circuit.
* Non-function circuit: 
    - Check whether the design of the circuit is correct.
    - Locate errors by splitting the overall circuit into smaller parts that can be tested separately (are expected outputs obtained for well defined inputs for the smaller parts?).
    - Next check all connections and check whether components used have the correct values. Check the resistance of wires used when in doubt. 

````{warning} 
Never replace a component without checking whether the connections are correct first. Particularly with the use of integrated circuits (ICs) like operational amplifiers (see {ref}`OpAmps`) often a wire is connected to a wrong pin, which may result in a blown-up IC. Simply replacing the component will result in the next IC being blown-up.
````

* Start all over again: \
If you cannot discover any mistake in (part of) a circuit rebuild it from scratch.
* Draw a schematic of your circuit on paper, and then compare it with your original design. This often quickly leads to tracing errors in the construction of your circuit. 

(reporting)=
## Reporting of lab exercises

You need to hand in three lab journals on Ch. 3-4, on Ch. 5-6 and on Ch. 7-8. The lab journals should contain short reports on the lab exercises at the end of each chapter only. For lab exercises all items listed below should be included. 

* Title
    - Formulate a short concise and clear title, e.g. *Band pass filter*.
    - Start each exercise at the top of a new page in your lab journal.
    
* Objective
    - What are you going to determine/measure? What is your research question. Example: Determine the output impedance of the inverted amplifier.

* Schematic of circuit
    - Give a detailed explanation of your schematic.
    - Clearly label components in your schematic, e.g. R$_1$, R$_2$, C$_1$, etc. Try to use relevant names, like R$_{\rm in}$ for input resistance, V$_{\rm out}$ for output voltage.
    - Specify values of components and voltages that are fixed.
    - Stick to the following conventions:
        - place the input of a circuit on the left and the output on the right
        - DC voltages and currents denoted as (V, I) and AC voltages and currents as (v, i)
        - lowest voltages always at the bottom 

```{figure} /Fig-ch1/ps.png
---
height: 75px
name: ps-fig
---

```

* Theory
    - Either present derivations of formulas or give references to books or the syllabus where derivations can be found.

* Measurements
    - Record data in tables.
    - Specify physical quantities and units, and other relevant parameters (e.g. the frequency setting in an experiment) in table heading.

* Data analysis
    - Refer to the formulas used to determine the final results from measured physical quantities.
    - Show results in graphs if possible.
    - For each graph:
        - include the exercise number (particularly useful when several graphs are presented in one page), units, physical quantities and relevant parameters (e.g. the frequency setting in an experiment).
* Discussion of results \& conclusion
    - Do the results meet your expectation?
    - If not, try to present an explanation.

An example of a report on a lab exercise can be found on Canvas.

## Assessment
You will be graded for this course as follows:
- Test 1 (weight *17\%*) and test 2 (weight *17\%*)
- Average lab journal (3x) (weight *36\%*)
- Average (lab) work covering Ch. 5-6 and Ch. 7-8 (2x) (weight *30\%*)

To pass the course the final grade should be at least 5.5.
