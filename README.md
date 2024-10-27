# Ultrasonic Distance Indicator Using Raspberry Pi Pico WH

This project measures distance using an ultrasonic sensor and displays the output in Thonny’s console. With a Raspberry Pi Pico WH, the setup provides real-time distance monitoring, and LED indicators show whether objects are within safe, medium, or close proximity.

## Features
- **Distance Measurement**: Measures and displays distance in real-time.
- **LED Indicators**: Visual indication of object distance:
  - **Green LED**: Safe distance.
  - **Yellow LED**: Medium distance.
  - **Red LED**: Close distance.

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


## How It Works
1. **Ultrasonic Sensor**: The sensor sends a sound pulse, calculates the time it takes to bounce back, and determines the distance to the nearest object.
2. **LED Indicators**: Based on the measured distance, the LEDs turn on or off to signal object proximity.
   - **Red LED**: Object very close.
   - **Yellow LED**: Object at medium distance.
   - **Green LED**: Object at a safe distance.

## Thonny: Running Code on the Raspberry Pi Pico WH
Thonny is used to upload and execute the MicroPython script on the Pico WH, and it displays real-time distance output in its console.

### Flashing MicroPython onto the Pico WH
1. Connect the Pico WH to your computer and open Thonny.
2. Choose **MicroPython (Raspberry Pi Pico)** under **Tools > Options > Interpreter**.
3. Flash MicroPython if it’s not already installed.

### Uploading the Code
1. Open the script in Thonny and select **Save As...**.
2. Choose **Raspberry Pi Pico** and save the file as `main.py` to run automatically.

### Running the Code
1. Click **Run** in Thonny to start the script.
2. The Thonny console will display the distance, and the LEDs will indicate object proximity.

## Code Overview

### Measuring Distance with the Ultrasonic Sensor
The code calculates distance based on the time it takes for the ultrasonic pulse to travel to an object and back.

```python
def measure_distance():
    trig.low()
    time.sleep_us(2)
    trig.high()
    time.sleep_us(10)
    trig.low()

    # Measure time for echo
    duration = time_pulse_us(echo, 1)
    distance = (duration * 0.0343) / 2  # cm
    return distance
```
###LED Indicator Logic
This part of the code lights up LEDs based on the measured distance.

```python
def update_leds(distance):
    if distance < 10:
        red_led.on()
        yellow_led.off()
        green_led.off()
    elif 10 <= distance < 20:
        red_led.off()
        yellow_led.on()
        green_led.off()
    else:
        red_led.off()
        yellow_led.off()
        green_led.on()
```

###Main Loop
The main loop continuously measures distance and updates the LEDs.

```python
while True:
    distance = measure_distance()
    print(f"Distance: {distance:.2f} cm")
    update_leds(distance)
    time.sleep(1)

```


