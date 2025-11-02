📌 Gesture-Controlled Robot (Manual + Obstacle Avoidance Mode)

This project is a 4-wheel Arduino robot that can be controlled using hand gestures and also switch to Autonomous Obstacle Avoidance mode.
The gestures are captured using a Basic CNN model, which sends commands to the robot via Bluetooth. An ultrasonic sensor enables autonomous navigation with intelligent obstacle detection.

🚀 Features

✅ Gesture-Based Manual Control
Use hand gestures detected by a CNN model to move the robot:

Gesture/Key	Action
F / Forward Gesture	Move Forward
B / Backward Gesture	Move Backward
L / Left Gesture	Turn Left
R / Right Gesture	Turn Right
S	Stop
M	Switch to Manual Mode
A	Switch to Autonomous Mode

✅ Autonomous Obstacle Avoidance Mode

Uses an ultrasonic sensor to detect obstacles

If obstacle in front → turn right

If right also blocked → turn left

If surrounded → move backward

Automatically resumes forward motion when path is clear

✅ Bluetooth Communication

Commands transmitted via HC-05/HC-06 Bluetooth module

Compatible with mobile apps or Python scripts

✅ Motor Speed Control (Manual)

Speed adjusts using PWM based on how long command is sent

Smooth acceleration and deceleration for realistic control

🧠 Tech Stack
Component	Usage
Arduino Uno / Nano	Main controller
HC-05 / HC-06	Wireless communication
L298N Motor Driver	Controls DC motors
Ultrasonic Sensor (HC-SR04)	Obstacle detection
Python + OpenCV + CNN	Hand-gesture recognition
🔧 Hardware Required
Component	Quantity
Arduino Uno / Nano	1
L298N Motor Driver	1
HC-05/HC-06 Bluetooth Module	1
HC-SR04 Ultrasonic Sensor	1
4 DC Motors + Wheels	4
Battery Pack (7.4V–12V)	1
Chassis	1
Jumper Wires	—
⚙️ Wiring Diagram (Overview)
Arduino Pin	Connected To
D5 (PWM)	Left Motor Enable
D6 (PWM)	Right Motor Enable
D8, D9	Left Motor IN1, IN2
D10, D11	Right Motor IN3, IN4
D2, D3	Ultrasonic Trigger, Echo
RX, TX	Bluetooth TX, RX (cross connection)

Detailed wiring diagram will be added as an image in /docs/.

📂 Project Structure
GESTURE-CONTROLLED-ROBOT/
│
├── code/
│   ├── gesture_robot.ino         # Arduino code
│   └── cnn_gesture_control.py     # Python gesture detection + command sender
│
├── models/
│   └── gesture_cnn_model.h5       # Saved CNN model
│
├── docs/
│   ├── wiring_diagram.png
│   ├── how_it_works.md
│   └── demo_images/
│
├── README.md                      # Project Documentation
└── LICENSE

🏃‍♂️ How to Run
Step 1: Upload Arduino Code

Open the .ino file in Arduino IDE

Select board & COM port

Upload

Step 2: Run Gesture Detection
python cnn_gesture_control.py

Step 3: Control the Robot

Perform hand gestures in front of the camera → robot responds via Bluetooth.

Press A on your keyboard to switch to Auto mode.
Press M to go back to Manual mode.

🧪 Future Enhancements

🚧 Add more gestures (e.g., speed boost, diagonal motion)
🟦 Train a more accurate CNN model
🤖 Add line-following or voice commands
📍 Add PID-based smooth motion

📝 License

This project is open-source under the MIT License.
Feel free to use, modify, or improve the project with attribution.
