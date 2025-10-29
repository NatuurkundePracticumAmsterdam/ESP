(measuring_systems)=
# 2. Measuring systems

A measuring system is a system designed to collect data on a certain physical process and to present this data in a useful and accessible form  to an observer and/or to another system. 

In this chapter a number of basic principles of measuring systems are covered. Whether a system meets the demands of a user depends on the specifications of the system.

## System components
In a measuring system three important components can be distinguished (see {numref}`fig-system_components`).

```{figure} /Fig-ch2/components_ms.png
---
width: 600px
name: fig-system_components
---
Main components of a measuring system
```
	
* *Data acquisition:* data collected by measuring devices (electrical signals) need to be converted into digital data.
* *Data processing:* the digital data needs to be processed through a predefined protocol (usually by a program running on a computer).
* *Data distribution:* the processed measured data is passed on to one or several output systems.

The data acquisition can be split into three sub-components (see {numref}`fig-dac`).

```{figure} /Fig-ch2/dac.png
---
width: 600px
name: fig-dac
---
Sub-components of data acquisition
```

* *Sensor:* Most physical measurable quantities are not of an electrical nature. The sensor is responsible to convert physical quantities into electric signals suitable for electronic processing. E.g. a thermocouple converts a temperature into a voltage. 
* *S(ignal) C(onditioning):* In many cases the signal given by a sensor is not (optimally) suitable as an input for the ADC. Making a signal suitable as an ADC input is called signal conditioning. Examples of signal conditioning are:
    - Amplification: an ADC requires an input range of voltages (e.g. 0 V to 10 V). Through amplification a sensor output signal can be amplified to cover the whole ADC input range, increasing the accuracy of the sensor signal.
    - Filtering: unwanted signal components can be removed from the sensor output signal before signal conversion is done by the ADC.
    - Modulation: by adjusting the shape of the signal it becomes possible to transfer signals across large distances and make them less sensitive to noise and disturbances (like 50 Hz).

* *A(nalog) to D(igital) C(onversion):* Most sensors produce analog signals. Analog signals are signals that vary in amplitude and time continuously. Digitizing the signal will result in some data loss. Whether this is relevant depends on the properties of the signal measured or of the system that needs to be controlled.

With data distribution the opposite process of data acquisition occurs. First, the digital signal is converted to an analog signal using a DAC. Usually this is followed by signal conditioning. Finally the electrical output signal is converted to a desired non-electrical effect using an actuator or transducer. E.g. an (electrical) audio signal is converted into sound by a loudspeaker.

## Systems specification
To determine whether a measuring system is suitable for measuring a physical quantity the properties (specifications) of a system should be known.

(transfer_function)=
### Transfer function

The most important property of a system is the transfer function A, which describes the relation between the input signal x and the output signal y of the system (see {numref}`fig-transfer`). 

```{figure} /Fig-ch2/transfer.png
---
width: 400px
name: fig-transfer
---
Transfer function A
```

````{admonition} Example *transfer function*
:class: tip

The transfer function of a resistor thermometer could be:

$$
R = 100 + 0.4 T,
$$ (eq:ch2-1)

where $R$ is the resistance in $\Omega$ and $T$ the temperature in $^{\rm o}$C.
````

