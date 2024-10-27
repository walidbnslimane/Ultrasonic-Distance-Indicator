## Components 

| Component             | Description                                               | Pin Connection            | Image                                       |
|-----------------------|-----------------------------------------------------------|---------------------------|---------------------------------------------|
| Raspberry Pi Pico WH  | Microcontroller with built-in WiFi                        | GPIO 8, 9, 16, 17, 18  | ![Pico WH](https://github.com/user-attachments/assets/3d182aa3-03d6-452b-a237-287b00e4ef78)  |
| Ultrasonic Sensor (HC-SR04) | Measures distance by emitting and receiving sound waves | Trig to GPIO 9, Echo to GPIO 8 | ![Ultrasonic Sensor](https://github.com/user-attachments/assets/2599ed72-8cf7-478a-8549-72aba8d3638c) |
| Red LED               | Indicates very close distance                             | GPIO 18                   | ![Red LED](https://github.com/user-attachments/assets/265a4442-a139-4051-82f5-eb93e849d90a)  |
| Yellow LED            | Indicates medium distance                                 | GPIO 17                   | ![Yellow LED](https://github.com/user-attachments/assets/24de3840-b46d-4043-a0f1-da4f98be119a)  |
| Green LED             | Indicates safe distance                                   | GPIO 16                   | ![Green LED](https://github.com/user-attachments/assets/130c74d8-a96f-4a34-b5be-614e10a985fb)  |
| Resistors (220Ω)      | Current limiters for LEDs                                 | Series with each LED      | ![Resistor](https://github.com/user-attachments/assets/ce9a677e-3ba4-4b60-9420-2f1fa8915891)  |
| Breadboard            | For easier wiring and connections                         | -                         | ![Breadboard](https://github.com/user-attachments/assets/0b694d76-3eea-4123-a352-6cec240d29b1)  |
| Jumper Wires          | Connects Pico, LEDs, resistors, and sensor                | GPIO pins, GND            | ![Jumper Wires](https://github.com/user-attachments/assets/b21f7fa1-e0f0-46e0-b93c-fa01bac3a849)  |

## Connections Breakdown

| **Pin**       | **Component**       | **Connection**            |
|---------------|---------------------|---------------------------|
| GPIO 9       | Ultrasonic Sensor   | Trig                      |
| GPIO 8       | Ultrasonic Sensor   | Echo                      |
| GPIO 18       | Red LED (Anode)     | Long leg of red LED       |
| GPIO 17       | Yellow LED (Anode)  | Long leg of yellow LED    |
| GPIO 16       | Green LED (Anode)   | Long leg of green LED     |
| GND           | Resistors & LEDs    | Resistor to LED cathode   |
| Resistor end  | LEDs (Cathode)      | Short leg of each LED     |
