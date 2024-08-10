Automatic Railway Gate Control System
This project is an implementation of an automatic railway gate control system using Arduino. The system uses IR sensors to detect the approach and passage of a train, and controls the gates using servo motors.
Components
•	Arduino Uno
•	2x Servo Motors
•	2x IR Sensors
•	Jumper Wires
•	Breadboard
Circuit Diagram
[Include an image of your circuit diagram here.]
Code
The code for this project is written in Arduino C. Below is an overview of the code:
- The `Servo` library is used to control the servo motors.
- Two servos (`servoGate1` and `servoGate2`) are used to control the gates.
- Two IR sensors are connected to pins 2 and 3 of the Arduino to detect the train.
- The gates are initially set to the closed position.
- The `loop()` function checks the state of the IR sensors to determine if the gates should be opened or closed.
Code Explanation

#include <Servo.h>

Servo servoGate1; // Servo motor for the gate
Servo servoGate2; // Servo motor for gate 2

void setup() {
  servoGate1.attach(9); // Attach the servo motor to pin 9
  servoGate2.attach(10); // Attach the servo motor to pin 10
  servoGate1.write(90); // Initialize gate to closed position
  servoGate2.write(90);
  pinMode(2, INPUT); // IR sensor for train approaching
  pinMode(3, INPUT); // IR sensor for train passing
  delay(1000); // Delay for stability
}

void loop() {
  if (digitalRead(3) == LOW && digitalRead(2) == HIGH) {
    closeGate(); // Close the gate if a train is approaching
    delay(200);
  }
  if (digitalRead(2) == LOW && digitalRead(3) == HIGH) {
    openGate(); // Open the gate if a train has passed
    delay(200);
  }
  if (digitalRead(2) == LOW && digitalRead(3) == LOW) {
    // Do nothing when both sensors are low
    delay(200);
  }
}

void closeGate() {
  servoGate1.write(0); // Close the gate by moving the servo to 0 degrees
  servoGate2.write(0); 
}

void openGate() {
  servoGate1.write(90); // Open the gate by moving the servo to 90 degrees
  servoGate2.write(90);
}

Installation
1. Clone this repository to your local machine.
```bash
git clone https://github.com/Rohan3177/Automatic-Railway-Gate-Control.git
```
2. Open the `.ino` file in the Arduino IDE.
3. Connect your Arduino board to your computer.
4. Upload the code to the Arduino board.
Usage
1. Set up the circuit as per the circuit diagram.
2. Power on the Arduino.
3. The gates will automatically open and close based on the train's presence detected by the IR sensors.
Acknowledgements
[Arduino](https://www.arduino.cc/) for the development platform
Contributing
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.
Contact
For any inquiries or issues, please contact [Rohan]
