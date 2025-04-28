# Dual DC Motor Driver (L293D) 

Controls two DC motors independently (direction & enable) using an L293D driver IC and a 5V regulated supply.

## Components:

* **U1 (L293D):** Dual H-bridge motor driver IC. This chip contains two independent H-bridge circuits, allowing control of the direction and current flow to two DC motors.
* **U2 (L7805):** 5V voltage regulator. This component takes a higher DC input voltage and provides a stable 5V output to power the L293D's logic and the indicator LED.
* **D1 (LED):** Light Emitting Diode. This visual indicator illuminates when the circuit has a stable 5V power supply.
* **R1 (Resistor):** Current-limiting resistor. This resistor is placed in series with the LED to prevent excessive current flow and potential damage to the LED.
* **J1 (Screw Terminal):** Input connector for the external DC power supply. This is where you connect your power source.
* **J2 (Header):** Connector for control input signals. This header receives signals (typically from a microcontroller) to control the enable and direction of both motors.
* **J3 (Header):** Connector for the first DC motor. Connect the two terminals of your first motor here.
* **J4 (Header):** Connector for the second DC motor. Connect the two terminals of your second motor here.

## Working:

1.  **Power Input:** External DC power is connected to the J1 screw terminal. Ensure correct polarity.
2.  **Voltage Regulation:** The L7805 (U2) steps down and stabilizes the input voltage to a consistent 5V, which is crucial for the proper operation of the L293D and other components.
3.  **Power Indication:** When the 5V regulation is successful, the LED (D1) lights up, indicating that the circuit is powered and ready for motor control.
4.  **Motor Enabling:** To allow a motor to run, a HIGH logic signal (+5V) must be applied to the corresponding enable pin on the J2 header (connected to the EN pins of U1). A LOW signal (0V) on the enable pin will stop the motor.
5.  **Direction Control:** The direction of rotation for each motor is determined by the logic levels applied to the respective direction control pins on the J2 header (connected to the input pins of U1, like 1A, 2A, 3A, 4A). Specific HIGH/LOW combinations on these pins dictate the polarity of the voltage applied across the motor terminals. Consult the L293D datasheet for the exact logic table.
6.  **Motor Driving:** Based on the enable and direction signals received from J2, the L293D (U1) activates its internal H-bridge circuitry to control the flow of current through the motors connected to J3 and J4, causing them to rotate in the desired direction or stop.

## Usage:

1.  Connect your external DC power supply to the J1 screw terminal, paying attention to the positive and negative connections.
2.  Connect your two DC motors to the J3 and J4 headers. The initial direction of rotation might depend on the polarity of the motor connections.
3.  Connect the control output pins of your microcontroller or other control system to the J2 header. Ensure your control signals match the logic levels required by the L293D (typically 0V for LOW and 5V for HIGH).
4.  Control the operation of the motors by manipulating the digital signals sent to the enable and direction control pins on the J2 header. Refer to the L293D datasheet for the specific input logic required to achieve forward, reverse, and brake/coast states for each motor.
