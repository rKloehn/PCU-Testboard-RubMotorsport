# PCU-Testboard-RubMotorsport

## Overview
The Powertrain Control Board test board (PCU test board for short) was developed in 2020 for the Drivetrain assembly in order to test the functions for the pneumatic switching and coupling of the RUB20 in advance. For this reason, the board contains all the necessary peripherals and connections required for the switching and coupling of the RUB20. The board is supplied with a 12V power supply (like the real PCU in the vehicle). On the board there are connections for two 24V solenoid valves and one proportional valve. Furthermore two sensors with 5V supply voltage each can be connected and the current value of the proportional valve can be read out. For testing the functionality of the switching and coupling process, three push buttons and an adjustment potentiometer are available. All mentioned components were fixed on the board. The control and regulation tasks are performed by a STM32F405RG. The microcontroller can be programmed via the SWD interface on the board. 
<p align="center">
	<img src="img/frontside_testboard.jpg" width="350">
</p>


### Sensors
The drivetrain assembly has two sensors specified, which are required for a displacement control of the clutch. A Hall displacement transducer and a pressure sensor are used. The Hall displacement sensor is from the Novotechnik and is sponsored. The sensor is the TFD-4000 series (data sheet TDF-4000). The exact designation of the ordered sensor is: TFD-4021-624-211-401. This sensor has a measuring range of 24mm and a supply voltage of 5V (4.5...5V). The output signal is in the range of 0.25...4.75V and behaves ratiometrically to Ub. The characteristic curve is rising and the sensor is single-channel. Further characteristics can be taken from the data sheet. It is purchased from the company ADZ Nagano. The pressure sensor has a measurable pressure range of FILL IN DATA HERE and requires a supply voltage of 5V. The output signal, similar to the displacement sensor, is ratiometric and is in the range 0.5...4.5V. The sensor has three conductors and a rising characteristic. Further data can be taken from the data sheet (data sheet ADZ-SME).
<p align="center">
	<img src="img/Sensors.png" width="350">
</p>


### Actuators
The actuator system to be controlled by the test board consists of two 24V solenoid valves and one proportional valve. The 24V solenoid valves are from the company FESTO and have the following type description: VUVG-L10-P53E-T-M5_1P3. These are 5/3 [exhausted] valves with a switch-on time of 10ms, a switch-off time of 30ms and a switch-over time of 16ms. The coil is operated with 24V DC with 1W. Further values can be taken from the data sheet (data sheet solenoid valve). The proportional valve is also from the company FESTO and has the type description: VEAA-L-3-D11-Q4-A4-1-R1. The flow valve is controlled by setting the current from 4-20mA. The operating voltage is 24V DC and the electrical connection is a 4-pin M8 connector. Further data can be found in the data sheet.

### User interface
The aim of the test board is to check whether the intended path control and control of the circuit/clutch works. In order for this to happen early in the development process, the board must function completely independently of other boards (e.g. power supply board) or the steering wheel. Thus, it is necessary that the user has a possibility to simulate the actuation of the clutch or the start of a shifting process. For this reason, there are three push buttons on the board, two buttons for upshifting and downshifting and one button for venting the system at the push of a button. A rotary potentiometer also allows the on/off coupling of the motor gearbox. For programming, as mentioned above, the SWD interface is available to the user. The push buttons are all debounced with a corresponding circuit on the board. 

<p align="center">
	<img src="img/userinterface.png" width="350">
</p>

### Power supply
Several circuits are required for the power supply of the board. In total, exactly three voltage levels are available on the entire PCU test board. The input voltage of the board is 12V DC, which can be provided by a battery or power supply unit. The required current ranges from 0.1A to 0.3A, depending on which peripherals are used. The first voltage level of 5V is achieved by a UA78M05CDCY stepdown converter. The 5V voltage is then either used by the sensors or forms the input voltage for the 5V-3.3V voltage converter. Here a LM2937IMP is used. The 3.3V voltage circuit provides the supply voltage for the microcontroller. The 24V voltage circuit is realized by a StepUp circuit with the MC33063ADG. The 24V are used for the two valves. 





