#  Gesture Controlled Robot (Manual + Obstacle Avoidance Mode)

This project is a 4-wheel Arduino robot that can be controlled using hand gestures and can also switch to Autonomous Obstacle Avoidance mode. The gestures are detected using a Basic CNN model and sent to the robot via Bluetooth. An ultrasonic sensor enables the robot to avoid obstacles intelligently.


##  Features

###  Manual Gesture Control
Hand gestures are detected using a CNN model and converted into commands:

| Gesture/Key | Action |
|-------------|--------|
| F / Forward Gesture | Move Forward |
| B / Backward Gesture | Move Backward |
| L / Left Gesture | Turn Left |
| R / Right Gesture | Turn Right |
| S | Stop |
| M | Switch to Manual Mode |
| A | Switch to Autonomous Mode |

### Autonomous Obstacle Avoidance
- Detects objects using an ultrasonic sensor
- If obstacle in front → turn right
- If right is also blocked → turn left
- If surrounded → move backward
- Automatically resumes forward movement when path is clear

###  Bluetooth Control
Supports HC-05/HC-06 Bluetooth module  
Compatible with mobile apps or Python script

###  Speed Control (Manual Mode Only)
Uses PWM for smooth speed changes  
Speed increases the longer the command is sent  
Stops when command input stops

---

##  Tech Stack

| Technology | Purpose |
|------------|----------|
| Arduino Uno / Nano | Main controller |
| HC-05/HC-06 | Communication |
| L298N Motor Driver | Motor control |
| Ultrasonic Sensor | Obstacle detection |
| Python + OpenCV + CNN | Gesture detection |

---

##  Hardware Requirements

| Component | Qty |
|-----------|-----|
| Arduino Uno / Nano | 1 |
| L298N Motor Driver | 1 |
| HC-05/HC-06 Bluetooth Module | 1 |
| HC-SR04 Ultrasonic Sensor | 1 |
| 4 DC Motors + Wheels | 4 |
| Battery Pack (7.4V–12V) | 1 |
| Chassis | 1 |
| Jumper Wires | — |

---

##  Wiring Overview

| Arduino Pin | Connected To |
|-------------|-----------------|
| D5 (PWM) | Left Motor Enable |
| D6 (PWM) | Right Motor Enable |
| D8, D9 | Left Motor IN1, IN2 |
| D10, D11 | Right Motor IN3, IN4 |
| D2, D3 | Ultrasonic Trigger, Echo |
| RX, TX | Bluetooth TX, RX (crossed) |

> A detailed wiring diagram is provided in `/docs/`.

---



##  Project Structure
GESTURE-CONTROLLED-ROBOT/
│
├── arduino/
│   ├── gesture_robot.ino                 # Main Arduino code (Manual + Auto Modes)
│   └── constants.h                       # Pin definitions & configuration (optional)
│
├── gesture-model/
│   ├── training/
│   │   ├── dataset/                      # Collected gesture images
│   │   │   ├── forward/
│   │   │   ├── backward/
│   │   │   ├── left/
│   │   │   ├── right/
│   │   │   ├── stop/
│   │   │   └── additional_classes_here/
│   │   ├── train_model.ipynb             # Notebook to train CNN
│   │   ├── model.py                      # Model architecture + training code
│   │   └── requirements.txt              # Python dependencies
│   │
│   ├── models/
│   │   ├── gesture_cnn_model.h5          # Trained model
│   │   └── label_map.json                # Gesture-to-command mapping
│   │
│   └── run/
│       └── cnn_gesture_control.py        # Run model + send commands via Bluetooth
│
├── bluetooth/
│   ├── bt_test.ino                       # Simple BT test code (optional)
│   └── python_bt_sender.py               # Test sending Bluetooth commands (without model)
│
├── docs/
│   ├── wiring_diagram.png                # Block or Fritzing diagram
│   ├── system_architecture.png           # Data + control flow image
│   ├── how_it_works.md                   # Logic explanation
│   ├── setup_steps.md                    # Setup guide for beginners
│   ├── demo_images/                      # Images for README
│   └── demo_videos/                      # Add short videos later
│
├── tests/
│   ├── motor_test.ino                    # Test motors individually
│   ├── ultrasonic_test.ino               # Test ultrasonic sensor
│   └── speed_control_test.ino            # Test PWM speed logic
│
├── .gitignore
├── LICENSE
└── README.md


GESTURE-CONTROLLED-ROBOT/
│
├── code/
│ ├── gesture_robot.ino # Arduino Code
│ └── cnn_gesture_control.py # Python Gesture Detection + Sender
│
├── models/
│ └── gesture_cnn_model.h5 # CNN Model
│
├── docs/
│ ├── wiring_diagram.png
│ ├── how_it_works.md
│ └── demo_images/
│
├── README.md
└── LICENSE

---

##  How to Run

### Upload Arduino Code
- Open `gesture_robot.ino` in Arduino IDE
- Select board and COM port
- Upload

### Run Gesture Detection
```bash
python cnn_gesture_control.py
```
Control the Robot
Show hand gestures to the camera → Robot moves accordingly via Bluetooth.

Press A to switch to Autonomous Mode

Press M to switch back to Manual Mode

Future Enhancements
Add more gestures (diagonal movement, speed boost)

Improve CNN accuracy

Add voice control or line-following

Add PID for smoother motion

 License
This project is open-source under the MIT License.
