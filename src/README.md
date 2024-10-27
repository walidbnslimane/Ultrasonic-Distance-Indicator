```python
import machine
import utime

trig_pin = machine.Pin(9, machine.Pin.OUT)
echo_pin = machine.Pin(8, machine.Pin.IN)
red_pin = machine.Pin(18, machine.Pin.OUT)
yellow_pin = machine.Pin(17, machine.Pin.OUT)
green_pin = machine.Pin(13, machine.Pin.OUT)
                        

def measure_distance():
    trig_pin.off()
    utime.sleep_us(2)
    trig_pin.on()
    utime.sleep_us(10)
    trig_pin.off()

    while echo_pin.value() == 0:
        pass
    start_time = utime.ticks_us()

    while echo_pin.value() == 1:
        pass
    end_time = utime.ticks_us()

    duracion = utime.ticks_diff(end_time, start_time)
    distance = duracion / 58
    print("Distance: {:.1f} cm".format(distance))

    return distance

def turn_on_red():
    red_pin.on()
    yellow_pin.off()
    green_pin.off()

def turn_on_yellow():
    red_pin.off()
    yellow_pin.on()
    green_pin.off()

def turn_on_green():
    red_pin.off()
    yellow_pin.off()
    green_pin.on()

while True:
    distance = measure_distance()

    if distance < 5:
        turn_on_red()
    elif distance < 10:
        turn_on_yellow()
    else:
        turn_on_green()

    utime.sleep(0.2)


