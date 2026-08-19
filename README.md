# EXPERIMENT-01-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython


 
## NAME: SHIVRAJ R 

## DEPARTMENT: CSE(IOT)

## ROLL NO: 212223110051

## DATE OF EXPERIMENT: 17.08.2026

## AIM

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

1. Raspberry Pi Pico - 1

2. Push Button Switches - 2

3. LEDs (Light Emitting Diodes) -3

4. Buzzer - 1

5. 330Ω Resistors -3

6. Breadboard

7. Jumper Wires

8. USB Cable

## THEORY

<img width="474" height="407" alt="image" src="https://github.com/user-attachments/assets/df0155b7-5b06-4276-aad3-0e114260605d" />

## FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

## WORKING PRINCIPLE

## Experiment 1A:
1. The LEDs are connected as outputs in any three GPIO pins.

2. The Buzzer connected as output in any one LED connected GPIO pins.

3. A MicroPython script reads the switch states and controls the LEDs accordingly.

## Experiment 1B:

1. The switches are connected as inputs to GPIO pins of the Pico.

2. The LEDs are connected as outputs.

3. A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
## Experiment 1A

<img width="710" height="507" alt="image" src="https://github.com/user-attachments/assets/6bc88cc6-578c-4c45-a346-17d4804816ae" />

## FIGURE-02:  Circuit Diagram of Digital Output Interface 

1. Connect LED 1 to GPIO 0 via a 330Ω resistor, LED 2 to GPIO 2 via a 330Ω resistor and LED 3 to GPIO 4 via a 330Ω resistor.

2. Connect the Buzzer positive to either one pins GPIO 0 or GPIO 2 or GPIO 4.

3. Connect the other terminals of the LEDs and Buzzer to GND.

## Experiment 1B

<img width="940" height="576" alt="image" src="https://github.com/user-attachments/assets/6fc9a95f-28d4-4793-bf72-f60e34877c33" />

## FIGURE-03:  Circuit Diagram of Digital Input and Output Interface 


1. Connect switch 1 to GPIO 2 and switch 2 to GPIO 3.

2. Connect LED 1 to GPIO 13 via a 330Ω resistor.

3. Connect LED 2 to GPIO 16 via a 330Ω resistor.

4. Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython)
''''

## Experiment 1A:
```
from machine import Pin
import time
print("Pi Pico")
led1 = Pin(0, Pin.OUT)
led2 = Pin(2, Pin.OUT)
led3 = Pin(4, Pin.OUT)
buzzer=Pin(4,Pin.OUT)
while True:
    led1.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led1.value(0)  
    print("LED is OFF")
    time.sleep(1)
    led2.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led2.value(0)  
    print("LED is OFF")
    time.sleep(1)
    led3.value(1) 
    print("LED is ON")
    time.sleep(1) 
    led3.value(0)  
    print("LED is OFF")
    time.sleep(1)
    buzzer.value(1) 
    print("Buzzer is ON")
    time.sleep(1) 
    buzzer.value(0)  
    print("Buzzer is OFF")
    time.sleep(1)
```



## Experiment 1B:

```
from machine import Pin
import time import sleep 
switch1=Pin(2,Pin.IN)
switch2=Pin(3,Pin.IN)
led1=Pin(13,Pin.OUT)
led2=Pin(16,Pin.OUT)
while True:
    sw1_state=switch1.value()
    sw2_state=switch2.value()
    print("Switch 1 State", sw1_state)
    print("Switch 2 State", sw2_state)
    led1.value(0)
    if sw1_state==1 and sw2_state==1:
        led1.value(0)
        led2.value(0)
    elif sw1_state==1:
        led1.value(1)
        sleep(0.5)
        led1.value(0)
        led2.value(0)
    elif sw2_state==1:
        led1.value(0)
        led2.value(1)
        sleep(0.5)
        led2.value(0)
    sleep(0.5)
```

## OUTPUT


## Experiment 1A:


## FIGURE-04: CIRCUIT CONNECTION
<img width="797" height="420" alt="image" src="https://github.com/user-attachments/assets/a32c6964-b51e-47ea-8403-92cc7b16e145" />




## FIGURE-05: CODE EXECUTION OUTPUT
<img width="923" height="805" alt="EXP1_!" src="https://github.com/user-attachments/assets/bb30bbe4-85d3-418f-9785-27a1a0bfee93" />


## FIGURE-06: LED AND BUZZER STATUS
<img width="941" height="811" alt="2" src="https://github.com/user-attachments/assets/b7789f23-c3cb-4b0b-acd0-4ab4535d65b2" />

<img width="1022" height="907" alt="image" src="https://github.com/user-attachments/assets/b838b0a3-ebd9-46bb-9cfd-1280de15cae8" />



## Experiment 1B:


## FIGURE-07: CIRCUIT CONNECTION

<img width="1053" height="555" alt="image" src="https://github.com/user-attachments/assets/42e4f0aa-4e0c-4789-9777-5e8a5cd0ce44" />


## FIGURE-08: CODE EXECUTION OUTPUT
<img width="938" height="803" alt="image" src="https://github.com/user-attachments/assets/afc37147-cb39-48e1-aea3-c61cd21dfd4d" />

<img width="942" height="778" alt="image" src="https://github.com/user-attachments/assets/2e33f39a-1490-4a5c-83c4-c640a4db564b" />


## FIGURE-09: LED STATUS BASED ON SWITCH INPUTS
<img width="938" height="799" alt="image" src="https://github.com/user-attachments/assets/b168f6bb-7a16-4c41-8240-df8099d1bb6a" />


## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

