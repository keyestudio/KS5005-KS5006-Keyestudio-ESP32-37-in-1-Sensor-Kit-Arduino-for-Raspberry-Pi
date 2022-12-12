# **KS5005(KS5006)Keyestudio ESP32 37 in 1 Sensor Kit**

You need to look through the file“Preparation before class for C”first
before get started with this kit.

![](media/0a7bf48106d3e6f6be919d08bf5b52c5.png)

## 1. Description：

The Keyestudio ESP32 37 in 1 sensor kit mainly contains 37 commonly used
sensors and modules, an ESP32 board, an ESP32 expansion board and Dupont
wires.

All sensors and modules are fully compatible with the ESP32 expansion
board. You only need to stack the ESP32 mainboard onto the ESP32
expansion Board, and hook up them with Dupont wires, which is simple and
convenient.

To make you master the electronic knowledge, detailed tutorials (Arduino
C), schematic diagrams, wiring methods and test code are included.
Through these projects, you will have a better understanding about
programming, logic and electronics.


## 3. Arduino C library and set up the ESP32 environment:

The Arduino C is in the folder Arduino Libraries, and you can refer to
Preparation before class for C(Raspberry Pi) to set the ESP32
environment

If the Arduino C is added, just skip this part.

![](media/ec21944fe80dc788f2dc93d963b95298.png)

![](media/4fa68af346cd73bc657a2cda18c70fd0.png)

## Projects：

There are 37 sensors and modules in this kit. Next, we will analyze and
introduce how they work step by step. Interface sensors with the ESP32
board and its expansion board, run test codes and observe experimental
phenomenon.

**Note: please wire up components according to the given connection
diagrams.**

**What’s more, wire up the power and signals correctly, otherwise,
sensors or modules will get damaged or no test results will be shown.**

### Project 1: Hello World

**Overview**

In this project, we will make an experiment to light up the white LED
module. The high and low levels can be controlled by programming, then
the state of the LED can be controlled.


**Wire Up：**

Connect the ESP32 to Raspberry Pi

![](media/56053f7126905c6def63919c661d5c0a.jpeg)

**Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Hello World</p>
<p>* Description : Enter the letter R,and the serial port displays"Hello World".</p>
<p>* Auther :http//www.Keyestudio.com</p>
<p>*/</p>
<p>char val;// defines variable "val"</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>}</p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

Before uploading the test code to the
ESP32，click“Tools”→“Board”，select“ESP32 Wrover Module”.

![](media/10c7078bdcf9dd4c228c81faec39a736.png)

Select the correct serial port

![](media/dc1b74b0a57bc1765a552af01647d0da.png)

![](media/97f4ac2f7d2aac69f5b5cd558668b307.png)

Click ![](media/b0d41283bf5ae66d2d5ab45db15331ba.png) to upload the test code to the ESP32.

![](media/5a15050cdeb4d29af99cb5312419276d.png)

Note: If uploading code fails, you can press and hold the Boot button on
the ESP32 after clicking![](media/d09c4a31563f04a42d451e7bc1a5fb8a.png)and release the Boot
button after the percentage of uploading progress
appears.![](media/dc77bfcf5851c8f43aab6cbe7cec7920.png), as shown below:  

![](media/080186e49751f61bf8ac092a6bac9f70.png)

The code is uploaded successfully

![](media/6ace2a69565bd42a80d538ce59f38b17.png)

**5. Test Result**

After uploading successfully，we will use a USB cable to power
on，click![](media/2f6bca56f724e45a855335cb53ae9b4e.png), set the baud rate to 9600，we need to
press the reset button on the ESP32 motherboard and enter the
letter“R”，click“Send”，then the serial monitor prints“Hello
World\!”.

![](media/2d8f587df34800330465779a3daed987.png)

### Project 2: Lighting up LED

![](media/ce8d61c97eb89c94c05cc1f6299316b5.jpeg)

1.  **Overview**

In this kit, we have a Keyestudio Purple Module, which is very simple to
control. If you want to light up the LED, you just need to make a
certain voltage across it.

In the project, we will control the high and low level of the signal end
S through programming, so as to control the LED on and off. 

2.  **Working Principle**

The two circuit diagrams are given.

The left one is wrong wiring-up diagram. Why? Theoretically, when the S
terminal outputs high levels, the LED will receive the voltage and light
up.

Due to limitation of IO ports of ESP32 board, weak current can’t make
LED brighten.

The right one is correct wiring-up diagram. GND and VCC are powered up.
When the S terminal is a high level, the triode Q1 will be connected and
LED will light up(note: current passes through LED and R3 to reach GND
by VCC not IO ports). Conversely, when the S terminal is a low level,
the triode Q1 will be disconnected and LED will go off.

![](media/d205e9ad7c33cc55909cb1d652d42ad7.png)

**4.Wiring Diagram：**

![](media/fed849dd5952f3b94a591d5bc5e64267.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Blink</p>
<p>* Description : led Flashing 1 s</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int ledPin = 0; //Define LED pin connection to GPIO0</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

1.  **Code Explanation**

1\. PinMode(pin,mode): Pin is the ESP32 GPIO pin number used to set the
mode, here we set pin 0 as output mode.

2\. DigitalWrite(pin, value): Pin is the GPIO pin, which is defined GP0
here. Valueis the digital level that we will output（HIGH/LOW）. If the
pin is configured to OUTPUT using pinMode(), its voltage is set to the
corresponding value: 3.3V is HIGH,low level is 0V (ground). When connect
the LEDs to the pins, using the digitalWrite（HIGH）, the LEDs will get
dim.

3\. Setup() executes once, while loop() executes all the time. Delay
(ms) is delay function, ms is the number of milliseconds to pause. Data
type: unsigned long（range 0\~ 4,294,967,295 (2^32 - 1)）.

Firstly, we connect the module signal to ledPIN, namely GP0, and set it
to a high level to light the LEDs on the module. Then delay 1000 ms,
controlling the LEDs on the module light up for 1s and off for 1s to
achieve the flashing effect. 

7.  **Test Result**

Wire up, power on, compile and upload the code to the ESP32. After
uploading successfully, we will use a USB cable to power on，we will see
that the LED in the circuit will flash alternately.

### Project 3: Traffic Lights Module

![](media/e191c790f251715b418bcfd39a32917f.jpeg)

**Overview**

In this lesson, we will learn how to control multiple LED lights and
simulate the operation of traffic lights.

Traffic lights are signal devices positioned at road intersections,
pedestrian crossings, and other locations to control flows of traffic.

In this kit, we will use the traffic light module to simulate the
traffic light.

**Working Principle**

In previous lesson, we already know how to control an LED. In this part,
we only need to control three separated LEDs. Output high levels to the
signal R(3.3V), then the red LED will be on.

![](media/1479f32d51a02c2230cb535197093d4c.png)



**4.Wiring Diagram：**

![](media/cecade99c652fe14ea7547b80849f5b7.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Traffic_Light</p>
<p>* Description : Simulated traffic lights</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int redPin = 15; //Red LED connected to GPIO15</p>
<p>int yellowPin = 2; //Yellow LED connected to GPIO2</p>
<p>int greenPin = 0; //Green LED connected to GPIO0</p>
<p>void setup() </p>
<p>void loop() </p>
<p>digitalWrite(redPin, HIGH); //Lighting red LED</p>
<p>delay(5000); //Delay5s</p>
<p>digitalWrite(redPin, LOW); //Turn off red LED</p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

We use the function for(). for (int i = 1; i \<= 3; i = i + 1)
represents the variable i adds 1 fir each time from 1 to 3.

The function for (int i = 255; i \>= 0; i = i - 1) indicates that i
reduces by 1 each time. When i\<0, exit the for() loop and execute 256
times

**Test Result**

Upload the code, the green LED will be on for 5s then off, the yellow
LED will flash for 3s then go off and the red one will be on 5s then
off.

### Project 4: Laser Sensor

![](media/d5d84e9d26d2cc89772a05eed6340bc0.jpeg)

**Description**

Lasers are widely used to cut, weld, surface treat, and more on specific
materials. The energy of the laser is very high. The toy laser pointer
may cause glare to the human eye, and it may cause retinal damage for a
long time. my country also prohibits the use of laser to illuminate the
aircraft.

**Working Principle**

The laser head sensor module is mainly composed of a laser head with a
light-emitting die, a condenser lens, and a copper adjustable sleeve.

We can see the circuit schematic diagram of this module which is very
similar to the LED we have learned. They are all driven by triodes. A
high-level digital signal is directly input at the signal end, then the
sensor will start to work; if inputting low levels, the sensor won’t
work


**4.Wiring Diagram：**

![](media/73060fc0934dd3d40c8fd7062b6173c9.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Laser sensor</p>
<p>* Description : Laser light flashing</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int laserPin = 0; //Define the laser pin as GPIO 0</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Results**

Upload the test code successfully and power on, the laser module will
emit red laser signals for 2 seconds and stop emitting signals for 2
seconds.

### Project 5: Breathing LED

![](media/25107e92a36e701f271b2371359f2679.jpeg)

**Overview**

A“breathing LED”is a phenomenon where an LED's brightness smoothly
changes from dark to bright and back to dark, continuing to do so and
giving the illusion of an LED“breathing. This phenomenon is similar to a
lung breathing in and out. So how to control LED’s brightness? We need
to take advantage of PWM.

**3.Wiring Diagram：**

![](media/fed849dd5952f3b94a591d5bc5e64267.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Breathing Led</p>
<p>* Description : Make led light fade in and out, just like breathing.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_LED 0 //define the led pin</p>
<p>#define CHN 0 //define the pwm channel</p>
<p>#define FRQ 1000 //define the pwm frequency</p>
<p>#define PWM_BIT 8 //define the pwm precision</p>
<p>void setup() </p>
<p>void loop() </p>
<p>for (int i = 255; i &gt; -1; i--) </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

5.  **Test Result**

Wire up, power on, compile and upload the code to the ESP32. After
uploading successfully，we will use a USB cable to power on，we will see
that the LED on the module gradually gets dimmer then brighter,
cyclically, like human breathe.

### Project 6: RGB Module

![](media/b3515a7e0340f391bef256c9ed6ccd4b.jpeg)

1.  **Overview**

Among these modules is a RGB module. It adopts a F10-full color RGB
foggy common cathode LED. We connect the RGB module to the PWM port of
MCU and the other pin to GND(for common anode RGB, the rest pin will be
connected to VCC). So what is PWM?

PWM is a means of controlling the analog output via digital means.
Digital control is used to generate square waves with different duty
cycles (a signal that constantly switches between high and low levels)
to control the analog output.In general, the input voltages of ports are
0V and 5V. What if the 3V is required? Or a switch among 1V, 3V and
3.5V? We cannot change resistors constantly. For this reason, we resort
to PWM.

![](media/bbcfcb9ae56abb7e80ee587246fc4be9.GIF)

For Arduino digital port voltage outputs, there are only LOW and HIGH
levels, which correspond to the voltage outputs of 0V and 5V
respectively. You can define LOW as“0”and HIGH as“1’, and let the
Arduino output five hundred‘0’or“1”within 1 second. If output five
hundred‘1’, that is 5V; if all of which is‘0’,that is 0V; if output 250
01 pattern, that is 2.5V.

This process can be likened to showing a movie. The movie we watch are
not completely continuous. Actually, it generates 25 pictures per
second, which cannot be told by human eyes. Therefore, we mistake it as
a continuous process. PWM works in the same way. To output different
voltages, we need to control the ratio of 0 and 1. The more‘0’or‘1’
output per unit time, the more accurate the control.

2.  **Working Principle**

For our experiment, we will control the RGB module to display different
colors through three PWM values.

![](media/71e990d503b6f1822379091a37f58a6b.jpeg)


**4.Wiring Diagram：**

![](media/e684c10368af661546702f94e0a495f3.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : RGB LED</p>
<p>* Description : Use RGBLED to show random color.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>int red, green, blue;</p>
<p>void setup() </p>
<p>}</p>
<p>void loop() </p>
<p>void setColor(byte r, byte g, byte b) </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Wire up, power on, compile and upload the code to the ESP32. After
uploading successfully，we will use a USB cable to power on，we will see
that the RGB LED on the module starts to display random colors.

### Project 7: Button Sensor

![](media/4d5f6ea741d1e346e03f6efe7cfc9d2d.jpeg)

**Overview**

In this kit, there is a Keyestudio single-channel button module, which
mainly uses a tact switch and comes with a yellow button cap.

In previous lessons, we learned how to make the pins of our single-chip
microcomputer output a high level or low level. In this experiment, we
will read the high level (3.3V) and low level (0V).

We can determine whether the button on the sensor is pressed by reading
the high and low level of the S terminal on the sensor.

**Working Principle**

The button module has four pins. The pin 1 is connected to the pin 3 and
the pin 2 is linked with the pin 4. When the button is not pressed, they
are disconnected. Yet, when the button is pressed, they are connected.
If the button is released, the signal end is high level.

![](media/a51debfc8a38d0d5729d1da394f95ca5.png)

**4.Wiring Diagram：**

![](media/395caba95f49d582d7fd36cacbf44a7c.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : button</p>
<p>* Description : Read key value</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0; //Useto store key values</p>
<p>int button = 15; //The pin of the button is connected to GP15</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

**1. pinMode(button, INPUT)**; set the pin of the button module to GP15
and INPUT.

Configure INPUT through pinMode(). INPUT must use the pull-up or
pull-down resistor(ours module has the pull-up resistor RI).

**2. Serial.begin(9600)**: Initialize serial communication and set the
baud rate to 9600.

**3. digitalRead(button)**: read the digital level of the button(HIGH or
LOW). If this pin is not connected to pins, the digitalRead() will
return HIGH or LOW.

**4. if..else..**：if the logic behind () is true, execute the code of
(); otherwise execute the code of **else**.

5\. If the button is pressed, the signal end is low level, GP15 is low
level and Val is 0. Then the monitor will show the corresponding value
and characters; otherwise, the sensor is released, val is 1 and monitor
will show 1 and other characters

**Test Result**

Upload the test code successfully. After powering on the USB cable, open
the serial monitor and set the baud rate to 9600. Press the reset button
on the ESP32 board. The serial monitor will display the corresponding
data and characters. When the button is pressed, val is 0, the monitor
will show“Press the button”；when the button is released, val is 1，the
monitor will show“Loosen the button”; as shown below

![](media/7045e31571bac203864ccfcc4dafac7c.png)

### Project 8: Capacitive Sensor

![](media/794f73317cd5349345e92cebb5ccb410.jpeg)

**Description**

In this kit, there is a capacitive touch module which mainly uses a
TTP223-BA6 chip. It is a touch detection chip, which provides a touch
button, and its function is to replace the traditional button with a
variable area button. When we power on, the sensor needs about 0.5
seconds to stabilize. Do not touch the keys during this time period. At
this time, all functions are disabled, and self-calibration is always
performed. The calibration period is about 4 seconds. We display the
test results in the shell.

**Working Principle**

![](media/7fe7f9d2bdf7b9b25e708c52d7dda66d.png)

When our fingers touch the module, the signal S outputs high levels, the
red LED on the module flashes. We can determine if the button is pressed
or not by reading high and low levels on the sensor.


**4.Wiring Diagram：**

![](media/56ba673521d6b8e398b321382b402732.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Touch sensor</p>
<p>* Description : Reading touch value</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>int touch = 15; //The key of PIN</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

When we touch the sensor, the monitor will show“You pressed the
button\!”, if not,“You loosen the button\!”will be shown on the
monitor.

**Test Result**

Wire up, upload the code, open the monitor and set baud rate to 9600.
Press the reset button on the ESP32 board. The monitor shows
corresponding data and characters. In the experiment, when the button is
pressed, the red LED lights up and val is 1. Then the shell shows “You
pressed the button\!”; if the button is released, the red LED is off and
val is 0,“You loosen the button\!”will be displayed

![](media/5fc0643db935a176f614c248282ab4cd.png)

### Project 9: Obstacle Avoidance Sensor

![](media/e6dda88bb6faf8fc06d81361b7f48a3d.jpeg)

**Overview**

In this kit, there is a Keyestudio obstacle avoidance sensor, which
mainly uses an infrared emitting and a receiving tube. In the
experiment, we will determine whether there is an obstacle by reading
the high and low level of the S terminal on the sensor.

**Working Principle**

NE555 circuit provides IR signals with frequency to the emitter TX, then
the IR signals will fade with the increase of transmission distance. If
encountering the obstacle, it will be reflected back.

When the receiver RX meets the weak signals reflected back, the
receiving pin will output high levels, which indicates the obstacle is
far away. On the contrary, it the reflected signals are stronger, low
levels will be output, which represents the obstacle is close. There are
two potentiometers on the module, and one is for adjusting emission
power, another one is for receiving frequency.

![](media/f32ebd19bd8e893ab6c865f83b274900.png)


**4.Wiring Diagram：**

![](media/1c80fc2e1d7c038f0e105164090b97da.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : obstacle avoidance sensor</p>
<p>* Description : Reading the obstacle avoidance value</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Note:**

Upload the test code and wire up according to the connection diagram.
After powering on, we start to adjust the two potentiometers to sense
distance.

1.  Adjust the potentiometer transmitting power. Make the P LED at the
    critical point of ON and OFF states.

2\. Adjust the potentiometer receiving frequency. Rotate it clockwise,
the frequency will increase. Make the S LED at the critical point of ON
and OFF states, then the 38KHz square wave can be produced.

**Test Result**

Upload the code power up by a USB cable, open the serial monitor and set
baud rate to 9600. Press the reset button on the ESP32 board. When the
sensor detects the obstacle, the monitor will show“There are obstacles”;
if the obstacle is not detected,“All going well”will be shown.

![](media/a3911f5605c806be10f8c15bae032fd2.png)

### Project 10: Line Tracking Sensor

![](media/deac96f3f54b7bedea5399a3aca20c71.jpeg)

**Description**

In this kit, there is a DIY electronic building block single-channel
line tracking sensor which mainly uses a TCRT5000 reflective black and
white line recognition sensor element.

In the experiment, we judge the color (black and white) of the object
detected by the sensor by reading the high and low levels of the S
terminal on the module; and display the test results on the shell.

**Working Principle**

![](media/b4bec738ca3565a2ce3a274bfec4a57a.png)

When a black or no object is detected, the signal terminal will output
high levels; when white object is detected, the signal terminal is low
level; its detection height is 0-3cm. We can adjust the sensitivity by
rotating the potentiometer on the sensor. When the potentiometer is
rotated, the sensitivity is best when the red LED on the sensor is at
the critical point between off and on.


**4.Wiring Diagram：**

![](media/8bf3cd4119768830839818cb8b9cee54.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : line tracking</p>
<p>* Description : Reading the tracking sensor value</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload test code, wire up, open the monitor and set baud rate to 9600.
Press the reset button on the ESP32 board.

In the experiment, when the sensor doesn’t detect an object or detects a
black object, the val is 1, and the monitor will display "Black" ; when
a white object (can reflect light) is detected, the val is 0, and the
monitor will display "White" ;

![](media/62d1d97ba7dff77a495a893774d81068.png)

### Project 11: Photo Interrupter

![](media/20519af325d65d055bd8b70c1475438e.jpeg)

**Description**

This kit contains a photo interrupter which mainly uses 1 ITR-9608
photoelectric switch. It is a photoelectric switch optical switch
sensor.

**Working Principle**

When the paper is put in the slot, C is connected with VCC and the
signal end S of the sensor are high levels; then the red LED will be
off. Otherwise, the red LED will be on.

![](media/95c79c5260ec5e7d4de31094ea608767.png)


**4.Wiring Diagram：**

![](media/8444b72b5a68234acc69a6a3e16b8449.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Photo_Interrupt</p>
<p>* Description : Light snap sensor counting</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int PushCounter = 0; //The count variable is assigned an initial value of 0</p>
<p>int State = 0; //Store the current state of the sensor output</p>
<p>int lastState = 0; //Stores the state of the last sensor output</p>
<p>void setup() </p>
<p>void loop() </p>
<p>}</p>
<p>lastState = State;//Update state</p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Logic setting:

<table>
<tbody>
<tr class="odd">
<td>Initial Setting</td>
<td>Set PushCounter to 0</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Set State to 0 (value of the sensor)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Set lastState to 0</td>
<td></td>
</tr>
<tr class="even">
<td>when an object enters the slot</td>
<td>lastState is 0，State turns into 1; lastState turns into 1</td>
<td><p>Set PushCounter to PushCounter+1</p>
<p>print the value of PushCounter</p></td>
</tr>
<tr class="odd">
<td>when the object leaves the slot</td>
<td>lastState is 1，State becomes 0，two data are not equal，lastState turns into 0.</td>
<td><p>PushCounterdoesn’t change;</p>
<p>Don’t print the value of PushCounter</p></td>
</tr>
<tr class="even">
<td>When the object goes through this slot again</td>
<td>lastState is 0, State becomes 1，two data are not equal，lastState turns into 1.</td>
<td><p>Set PushCounter to PushCounter+1</p>
<p>And print the value of PushCounter</p></td>
</tr>
<tr class="odd">
<td>When the object leaves this slot again</td>
<td>lastState is 1，State turns into 0，two data are not equal lastState turns into 0</td>
<td><p>PushCounter doesn’t change;</p>
<p>Don’t print the PushCounter value</p></td>
</tr>
</tbody>
</table>

**Test Result**

Wire up, upload test code, open monitor and set baud rate to 9600. Press
the reset button on ESP32 board. The shell displays the PushCounter
data. Every time when the object passes through the slot of the sensor,
the PushCounter data will increase by 1 continuously, as shown below;

![](media/f5aed8756c76a09f839629f8f3692755.png)

### Project 12: Tilt Module

![](media/9d4fcf498d8943539935d0f9638f22eb.jpeg)

**Overview**

In this kit, there is a Keyestudio tilt sensor. The tilt switch can
output signals of different levels according to whether the module is
tilted. There is a ball inside. When the switch is higher than the
horizontal level, the switch is turned on, and when it is lower than the
horizontal level, the switch is turned off. This tilt module can be used
for tilt detection, alarm or other detection.

**Working Principle**

![](media/7b5da31ecdd90419d5b3326eebdb14e7.png)

The working principle is pretty simple. When pin 1 and 2 of the ball
switch P1 are connected, the signal S is low level and the red LED will
light up; when they are disconnected, the pin will be pulled up by the
4.7K R1 and make S a high level, then LED will be off.


**4.Wiring Diagram：**

![](media/0303daa7c70c79e2e1784f9e23693425.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Tilt switch</p>
<p>* Description : Reading the tilt sensor value</p>
<p>* Auther :http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val; //Store the level value output by the tilt sensor</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the code power up by a USB cable, open the serial monitor and set
baud rate to 9600. Press the reset button on the ESP32 board.

Make the tilt module incline to one side, the red LED on the module will
be off and the monitor will display“1”. In contrast, if you make it
incline the other side, the red LED will light up and the monitor will
display“0”.

![](media/d6446d1bb182db07788217a0d71bcd82.png)

### Project 13: Hall Sensor

![](media/3fa2bf365868256a8c9fe4f32c883c91.jpeg)

**Description**

In this kit, there is a Hall sensor which mainly adopts a A3144 linear
Hall element. The element P1 is composed of a voltage regulator, a Hall
voltage generator, a differential amplifier, a Schmitt trigger, a
temperature compensation circuit and an open-collector output stage. In
the experiment, we use the Hall sensor to detect the magnetic field and
display the test results on the shell.

**Working Principle**

When the sensor detects no magnetic field or a north pole magnetic
field, the signal terminal will be high level; when it senses a south
pole magnetic field, the signal terminal will be low levels.

The stronger the magnetic field strength is, induction distance is
longer.

![](media/e9dcd0f7f384f9233a0f227c7a8d3744.png)

**4.Wiring Diagram：**

![](media/335c913c8869defe1f0c8e8d3a801913.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Hall magnetic</p>
<p>* Description : Reading the value of hall magnetic sensor</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>int hallPin = 15; //Hall sensor pin is connected to GPIO15</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the test code, open the monitor and set baud rate to 9600. Press
the reset button on the ESP32 board.

when the sensor detects no magnetic fields or the north pole magnetic
field, the monitor l will show“1 Just be all normal\!”and the LED on the
sensor will be off; When it detects the south pole magnetic field,“0 The
magnetic field at the South Pole\!”and the LED on the sensor will be on.

![](media/84a5a91f49e4f8591e9e9809875dab24.png)

### Project 14: Reed Switch Module

![](media/2a699e913fa52d9acff4b0e4a8188540.png)

**Overview**

In this kit, there is a Keyestudio reed switch module, which mainly uses
a MKA10110 green reed component.

The reed switch is the abbreviation of the dry reed switch. It is a
passive electronic switch element with contacts.

It has the advantages of simple structure, small size and easy control.

Its shell is a sealed glass tube with two iron elastic reed electric
plates.

In the experiment, we will determine whether there is a magnetic field
near the module by reading the high and low level of the S terminal on
the module; and, we display the test result in the shell.

![](media/a4a9a00f86be808be0a9c784a6960cd6.jpeg)

**Working Principle**

Reed switch is an abbreviation of the dry reed contacts a passive

electronic switching elements, and has the advantages of simple
structure, small size and ease of control, its shell is a sealed glass
tube, the tubes are installed two iron elastic reed plate, but also
filling called rhodium metal inert gas. In peacetime, the glass tube in
the two reeds made of special materials are separated. When a magnetic
substance close to the glass tube, in the role of the magnetic field
lines, the pipe within the two reeds are magnetized to attract each
other in contact, the reed will suck together, so that the junction
point of the connected circuit communication. After the disappearance of
the outer magnetic reed because of their flexibility and separate, the
line is disconnected. Therefore, as a use of the magnetic field signals
to control the line switching device, reed tube can be used as a sensor
for counting the number, spacing, etc., and also are widely used in a
variety of communication devices.


**4.Wiring Diagram：**

![](media/45cb30739b7c6518fe1591142aabbf2f.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Reed Switch</p>
<p>* Description : Read the value of the reed sensor</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>int reedPin = 15; //Define dry reed module signal pin connected to GPIO15</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the code power up by a USB cable, open the serial monitor and set
baud rate to 9600. Press the reset button on the ESP32 board. When the
sensor detects a magnetic field, val is 0 and the red LED of the module
lights up, "A magnetic field" will be displayed; when no magnetic field
is detected, val is 1, and the LED on the module goes out, "There is no
magnetic field" will be shown, as shown below.

![](media/a97a8adedf3e80eb7f9c7c4f554a73cb.png)

### Project 15: PIR Motion Sensor

![](media/d58ba7b9b4a0115b07cbb1c871ef8ec9.jpeg)

**Overview**

In this kit, there is a Keyestudio PIR motion sensor, which mainly uses
an RE200B-P sensor elements. It is a human body pyroelectric motion
sensor based on pyroelectric effect, which can detect infrared rays
emitted by humans or animals, and the Fresnel lens can make the sensor's
detection range farther and wider.

In the experiment, we determine if there is someone moving nearby by
reading the high and low levels of the S terminal on the module. The
detected results will be displayed on the Shell.

**Working Principle**

The upper left part is voltage conversion(VCC to 3.3V). The working
voltage of sensors we use is 3.3V, therefore we can’t use 5V directly.
The voltage conversion circuit is needed.

When no person is detected or no infrared signal is received, and pin 1
of the sensor outputs low level. At this time, the LED on the module
will light up and the MOS tube Q1 will be connected and the signal
terminal S will detect Low levels.

When one is detected or an infrared signal is received, and pin 1 of the
sensor outputs a high level. Then LED on the module will go off, the MOS
tube Q1 is disconnected and the signal terminal S will detect high
levels.

![](media/e62f4d614ab7e67ac373576d7ff96fee.png)


**4.Wiring Diagram：**

![](media/6e57df420ca5d0dcc6f87467bb0295db.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : PIR motion</p>
<p>* Description : Reading the value of the human body infrared sensor</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int val = 0;</p>
<p>int pirPin = 15; //The pin of PIR motion sensor is defined as GPIO15</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the code power up by a USB cable, open the serial monitor and set
baud rate to 9600. Press the reset button on the ESP32 board. When the
sensor detects someone nearby, value is 1, the LED will go off and the
monitor will show“Somebody is in this area\!”. In contrast, the value is
0, the LED will go up and“0 No one\!”will be shown.

![](media/f63fe3ac6e6ea86f116a9afd6b7a4850.png)

### Project 16: Active Buzzer

![](media/f4cc23dc8ed28d408e5a119855e19aa2.jpeg)

**Overview**

In this kit, it contains an active buzzer module and a power amplifier
module (the principle is equivalent to a passive buzzer). In this
experiment, we control the active buzzer to emit sounds. Since it has
its own oscillating circuit, the buzzer will automatically sound if
given large voltage.

**Working Principle**

![](media/458b66a2a23d6e135e7cf9975fe27507.png)

From the schematic diagram, the pin of buzzer is connected to a resistor
R2 and another port is linked with a NPN triode Q1. So, if this triode
Q1 is powered, the buzzer will sound.

If the base electrode of the triode connected to the R1 resistor is a
high level, the triode Q1 will be connected.If the base electrode is
pulled down by the resistor R3, the triode is disconnected.

When we output a high level from the IO port to the triode, the buzzer
will emit sounds; if outputting low levels, the buzzer won’t emit
sounds.


**4.Wiring Diagram：**

![](media/44508746060c5df3544ab2d84b2482bf.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Active buzzer</p>
<p>* Description : An active buzzer produces sound</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>int buzzer = 15; //Define buzzer receiver pin GPIO15</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

In the experiment, we set the pin number to GPIO15. When setting to
high, the active buzzer will beep; when setting to low, the active
buzzer will stop emitting sounds

**Test Result**

Upload the code and power on. The active buzzer will emit sound for 1
second, and stop for 1 second.

### Project 17: 8002b Audio Power Amplifier

![](media/6e8569df97b72e866488a6f414f9e392.jpeg)

**Overview**

In this kit, there is a Keyestudio 8002b audio power amplifier. The main
components of this module are an adjustable potentiometer, a speaker,
and an audio amplifier chip;

The main function of this module is: it can amplify the output audio
signal, with a magnification of 8.5 times, and play sound or music
through the built-in low-power speaker, as an external amplifying device
for some music playing equipment.

In the experiment, we used the 8002b power amplifier speaker module to
emit sounds of various frequencies.

**Working Principle**

In fact, it is similar to a passive buzzer. The active buzzer has its
own oscillation source.Yet, the passive buzzer does not have internal
oscillation. When controlling the circuit, we need to input square waves
of different frequencies to the positive pole of the component and
ground the negative pole to control the buzzer to chime sounds of
different frequencies.

![](media/f5f372e0713df6439a7cc52f5caf1cad.png)


**4.Wiring Diagram：**

![](media/c6e67388d17aae690f538a4c61f9fd9f.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Passive Buzzer</p>
<p>* Description : Passive Buzzer sounds the alarm.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define LEDC_CHANNEL_0 0</p>
<p>// LEDC timer uses 13 bit accuracy</p>
<p>#define LEDC_TIMER_13_BIT 13</p>
<p>// Define tool I/O ports</p>
<p>#define BUZZER_PIN 15</p>
<p>//Create a musical melody list, Super Mario</p>
<p>int melody[] = ;</p>
<p>//Create a list of tone durations</p>
<p>int noteDurations[] = ;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>}</p>
<p>//**********************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the test code successfully and power on. The power amplifier
module will play a song.

### Project 18: 130 Motor

![](media/6c4e0d18c7c1867e27c0bac8e1c6412b.jpeg)

**Description**

The 130 motor driver module is compatible with servo motors, which has
high efficiency and good quality fans.

It adopts a HR1124S motor control chip. HR1124S is a single-channel
H-bridge driver chip for DC motor solutions. In addition, this chip has
low standby current and low quiescent current.

The module is compatible with various single-chip control boards. In the
experiment, we can control the rotation direction of the motor by
outputting the voltage directions of the two signal terminals IN+ and
IN- to make the motor rotate.

**Working Principle**

The chip is used to help drive the motor.

We can’t drive it with a triode or an IO port due to its a large current
of need. It is very simple to make the motor rotate. Just apply voltage
to both ends of the motor. The direction of the motor is different in
different voltage directions. Within the rated voltage, the higher the
voltage, the faster the motor rotates; on the contrary, the lower the
voltage, the slower the motor rotates, or even unable to rotate.

So we can use the PWM port to control the speed of the motor. We haven't
learned PWM here, so we use the high and low levels to control the motor
first.

![](media/5ea2e4d2b18f87ffa9a31e834764ec4b.png)


Note: the motor is separated with its fan, you need to assemble them
together first.

**4.Wiring Diagram：**

<table>
<tbody>
<tr class="odd">
<td>130 Motor</td>
<td>ESP32 Expansion Board</td>
</tr>
<tr class="even">
<td>G</td>
<td>G</td>
</tr>
<tr class="odd">
<td>V</td>
<td>5V</td>
</tr>
<tr class="even">
<td>IN+</td>
<td>IO15</td>
</tr>
<tr class="odd">
<td>IN-</td>
<td>IO4</td>
</tr>
</tbody>
</table>

![](media/bbe7e2090eaae8cea355349c9484289b.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : 130DC Fan motor</p>
<p>* Description : Motor positive and negative rotation</p>
<p>* Auther : http://www.Keyestudio.com</p>
<p>*/</p>
<p>//Define two pins interfaces of the motor, respectively 15 and 4</p>
<p>int INA = 15; //INA corresponds to IN+</p>
<p>int INB = 4; //INB corresponds to IN-</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Set pins to 14 and 15, when the pin 14 outputs high levels and the pin
15 outputs low levels, the motor will rotate counterclockwise; when both
pins are set to low, the motor stops rotating.

**Test Result**

Wire up, upload test code, power up and turn the DIP switch to ON on the
ESP32 board. The fan will rotate counterclockwise for 2 seconds, stop
for 1 second; and rotate clockwise for 2 seconds and stop for 1 second;
cycle alternately.

### Project 19: Potentiometer

![](media/fe92a4f36758bc236d94290478fe5eac.jpeg)

1.  **Overview**

The following we will introduce is the Keyestudio rotary potentiometer
which is an analog sensor.

The digital IO ports can read the voltage value between 0 and 3.3V and
the module only outputs high levels. However, the analog sensor can read
the voltage value through 16 ADC analog ports on the ESP32 board. In the
experiment, we will display the test results on the Shell.

It uses a 10K adjustable resistor. We can change the resistance by
rotating the potentiometer. The signal S can detect the voltage
changes(0-3.3V) which are analog quantity.

**ADC:** The more bits an ADC has, the denser the partitioning of the
simulation, the higher the accuracy of the final conversion.

![](media/f6c45550f4adf8373d7f1d01daec2c64.png)

The conversion formula is as follows:

**DAC：**The higher the precision of DAC, the higher the precision of the
output voltage value.  

The conversion formula is as follows:  

**ADC on ESP32：**

The ESP32 has 16 pins that can be used to measure analog signals.  GPIO
pin serial numbers and analog pin definitions are shown below:  

<table>
<tbody>
<tr class="odd">
<td>ADC number in ESP32</td>
<td>ESP32 GPIO number</td>
</tr>
<tr class="even">
<td>ADC0</td>
<td>GPIO 36</td>
</tr>
<tr class="odd">
<td>ADC3</td>
<td>GPIO 39</td>
</tr>
<tr class="even">
<td>ADC4</td>
<td>GPIO 32</td>
</tr>
<tr class="odd">
<td>ADC5</td>
<td>GPIO33</td>
</tr>
<tr class="even">
<td>ADC6</td>
<td>GPIO34</td>
</tr>
<tr class="odd">
<td>ADC7</td>
<td>GPIO 35</td>
</tr>
<tr class="even">
<td>ADC10</td>
<td>GPIO 4</td>
</tr>
<tr class="odd">
<td>ADC11</td>
<td>GPIO0</td>
</tr>
<tr class="even">
<td>ADC12</td>
<td>GPIO2</td>
</tr>
<tr class="odd">
<td>ADC13</td>
<td>GPIO15</td>
</tr>
<tr class="even">
<td>ADC14</td>
<td>GPIO13</td>
</tr>
<tr class="odd">
<td>ADC15</td>
<td>GPIO12</td>
</tr>
<tr class="even">
<td>ADC16</td>
<td>GPIO14</td>
</tr>
<tr class="odd">
<td>ADC17</td>
<td>GPIO27</td>
</tr>
<tr class="even">
<td>ADC18</td>
<td>GPIO25</td>
</tr>
<tr class="odd">
<td>ADC19</td>
<td>GPIO26</td>
</tr>
</tbody>
</table>

**DAC on ESP32：**

The ESP32 has two 8-bit digital-to-analog converters connected to GPIO25
and GPIO26 pins, which are immutable, as shown below :

<table>
<tbody>
<tr class="odd">
<td>Simulate pin number</td>
<td>GPIO number</td>
</tr>
<tr class="even">
<td>DAC1</td>
<td>GPIO25</td>
</tr>
<tr class="odd">
<td>DAC2</td>
<td>GPIO26</td>
</tr>
</tbody>
</table>


**4.Wiring Diagram：**

![](media/ce7b953cd508fd8f2f9aafb805fae1f6.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Rotary_potentiometer</p>
<p>* Description : Read the basic usage of ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the Potentiometer</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

1\. analogVal means analog value. The rotary potentiometer outputs
analog values(0\~4095), therefore, we set pins to analog ports. For
example, we connect to GPIO34.

2\. analogRead(pin): read the value of the specified analog pin. The
ESP32 contains a multi-channel, 12-bit converter. This means that it
will map the input voltage between 0 and the working voltage (5V or 3.3V
) to an integer value between 0 and 4095. For example, this will produce
a resolution among readings: 3.3V/4096 stands for 0.0008V per unit.

3\. The map() function converts this 12-bit DAC value to an 8-bit DAC
value.  

4\. Pin: the name of analog input pin.

5\. The serial monitor displays the values of adcVal, dacVal, voltage,
the baud rate must be set before display (we default to 9600,which can
be changed).  

**7. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on, open the serial
monitor and set the baud rate to 9600. We need to press the reset button
on the ESP32, then the serial monitor will display the potentiometer's
ADC value, DAC value and voltage value. Rotate the potentiometer handle,
the analog values will change.

![](media/ac163a6854fe84ab39de2e9efcef76ee.png)

### Project 20: Steam Sensor

![](media/0062e47b90828244595c1fb93c45f1d5.jpeg)

1.  **Description**

This is a DIY electronic building block water drop sensor. It is an
analog (digital) input module, also called rain, rain sensor. It can be
used to monitor various weather conditions, detect whether it is raining
and the amount of rain, convert it into digital signal (DO) and analog
signal (AO) output, and is widely used in Arduino robot kits, raindrops,
rain sensors, and can be used for various It can monitor various weather
conditions, and convert it into digital signal and AO output, and can
also be used for automobile automatic wiper system, intelligent lighting
system and intelligent sunroof system.

In the experiment, we input the sensor signal terminal (S terminal) to
the analog port of the ESP32 development board, sense the change of the
analog value, and display the corresponding analog value on the shell.

**2. Working Principle**

Its principle is to detect the amount of water through the exposed
printed parallel lines on the circuit board. The more water there is,
the more wires will be connected, and the conductive contact area
increases. The voltage output by pin 2 will gradually increase. The
larger the analog value detected by the signal terminal S is.

It can also detect steam in the air. Two position holes are used to
install on the other devices.

![](media/790270169035ee740b28c49c4b1dde47.png)


**4.Wiring Diagram：**

![](media/c4eb7a1f583dc8b99775578cd7cd4674.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Steam sensor</p>
<p>* Description : Read the basic usage of ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the Steam sensor</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully，power on, open the serial monitor and set the baud rate to
9600. We need to press the reset button on the ESP32, then the serial
monitor will display ADC value, DAC value and voltage value. When a few
drops of water are placed in the sensing area, the values will change.
The more water volume, the greater the output voltage value , ADC value
and the DAC value .

![](media/ac163a6854fe84ab39de2e9efcef76ee.png)

### Project 21: Sound Sensor

![](media/c4d4961f71c7e91bae04507f72cb56eb.jpeg)

1.  **Overview**

In this kit, there is a Keyestudio DIY electronic block and a sound
sensor. In the experiment, we test the analog value corresponding to the
sound level in the current environment with it. The louder the sound,
the larger the ADC, DAC and the voltage value, and the “shell”window
will display the test results.

**2. Working Principle**

It uses a high-sensitive microphone component and an LM386 chip. We
build the circuit with the LM386 chip and amplify the sound through the
high-sensitive microphone. In addition, we can adjust the sound volume
by the potentiometer. Rotate it clockwise, the sound will get louder.

![](media/d55fc5234be47e7727c0bf48c049e341.jpeg)


**4.Wiring Diagram：**

![](media/7a5b741aba98560eddadc3b7788325d9.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : MicroPhone</p>
<p>* Description : Read the basic usage of ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the Sound Sensor</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully, we will use a USB cable to power on, open the serial
monitor and set the baud rate to 9600. We need to press the reset button
on the ESP32, then the serial monitor will display the sound sensor’s
ADC value, DAC value and voltage value. Rotate clockwise the
potentiometer and speak at the MIC. Then you can see the analog value
get larger, as shown below:

![](media/73bf0aa43b2eaa134fe43495206a8817.png)

### Project 22: Photoresistor

![](media/37bb57bcf72ba62056bbc61164185f0a.png)

1.  **Description**

In this kit, there is a photoresistor which consists of photosensitive
resistance elements. Its resistance changes with the light intensity.
Also, it converts the resistance change into a voltage change through
the characteristic of the photosensitive resistive element. When wiring
it up, we interface its signal terminal (S terminal) with the analog
port of ESP32 , so as to sense the change of the analog value, and
display the corresponding analog value in the shell.

**2. Working Principle**

If there is no light, the resistance is 0.2MΩ and the detected voltage
at the terminal 2 is close to 0. When the light intensity increases, the
resistance of photoresistor and detected voltage will diminish.

![](media/0a804f6b1ccb475325301d7c9c94f38d.png)


**4.Wiring Diagram：**

![](media/0b880c099cb70864881c501c9a3a8dbb.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Photoresistance</p>
<p>* Description : Read the basic usage of ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the Photoresistance</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on, open the serial monitor and set the baud
rate to 9600. We need to press the reset button on the ESP32, then the
serial monitor will display the photoresistor’s ADC value, DAC value and
voltage value. When the light intensity gets stronger, the analog values
will get larger, as shown below:

![](media/ac163a6854fe84ab39de2e9efcef76ee.png)

### Project 23: NTC-MF52AT Thermistor

![](media/868d93395d983645baab872091991403.jpeg)

1.  **Overview**

In the experiment, there is a NTC-MF52AT analog thermistor. We connect
its signal terminal to the analog port of the ESP32 mainboard and read
the corresponding ADC value, voltage value and thermistor value.

We can use analog values to calculate the temperature of the current
environment through specific formulas. Since the temperature calculation
formula is more complicated, we only read the corresponding analog
value.

**2. Working Principle**

![](media/84a67bb2b90b4740c09d914dc6402f48.png)

NTC-MF52AT thermistor elements. The NTC-MF52AT thermistor element can
sense the changes of the surrounding environment temperature. Resistance
changes with the temperature, causing the voltage of the signal terminal
S to change.

This sensor uses the characteristics of NTC-MF52AT thermistor element to
convert resistance changes into voltage changes.

**4.Wiring Diagram：**

![](media/7fba5e360e5bcc3e60ef27a77b3362d1.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Temperature sensor</p>
<p>* Description : Making a thermometer by thermistor.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on, open the serial monitor and set the baud
rate to 9600. We need to press the reset button on the ESP32, then the
serial monitor will display the thermistor’s ADC value, voltage value
and temperature value, as shown below:

![](media/b4f9c5e44e41d6624fbd81dab49781e4.png)

### Project 24: Thin-film Pressure Sensor

![](media/a9ae2963fc87b3502703f7dd5eb208ec.jpeg)

1.  **Overview**

In this kit, there is a Keyestudio thin-film pressure sensor. The
thin-film pressure sensor composed of a new type of nano
pressure-sensitive material and a comfortable ultra-thin film substrate,
has waterproof and pressure-sensitive functions.

In the experiment, we determine the pressure by collecting the analog
signal on the S end of the module. The smaller the ADC value, DAC value
and voltage value, the greater the pressure; and the displayed results
will shown on the Shell.

![](media/520fa537602873d2a337731318668348.png)**2. Working Principle**

When the sensor is pressed by external forces, the resistance value of
sensor will vary. We convert the pressure signals detected by the sensor
into the electric signals through a circuit. Then we can obtain the
pressure changes by detecting voltage signal changes.


**4.Wiring Diagram：**

![](media/a461b6b0227b4430b64da6e80be8d898.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Film pressure sensor</p>
<p>* Description : Read the basic usage of ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the Film pressure sensor</p>
<p>void setup() </p>
<p>//In loop()，the analogRead() function is used to obtain the ADC value,</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on, open the serial monitor and set baud rate
to 9600. We need to press the reset button on the ESP32 board, then the
serial monitor will display the thin-film’s ADC value, DAC value and
voltage value, when the thin-film is pressed by fingers, the analog
value will decrease, as shown below;

![](media/ac163a6854fe84ab39de2e9efcef76ee.png)

### Project 25: Flame Sensor

![](media/6d2b8c5a00f805cd790af7c7fd1abd40.jpeg)

1.  **Description**

In daily life, it is often seen that a fire broke out without any
precaution. It will cause great economic and human loss. So how can we
avoid this situation? Right, install a flame sensor and a speaker in
those places that easily break out a fire. When the flame sensor detects
a fire, the speaker will alarm people quickly to put out the fire.

So in this project, you will learn how to use a flame sensor and an
active buzzer module to simulate the fire alarm system.

**2. Working Principle**

This flame sensor can be used to detect fire or other light sources with
wavelength stands at 700nm \~ 1000nm. Its detection angle is about 60°.
You can rotate the potentiometer on the sensor to control its
sensitivity. Adjust the potentiometer to make the LED at the critical
point between on and off state. The sensitivity is the best.

From the below figure, power up. When detecting fire, the digital pin
outputs low levels, the red LED2 will light up first, the digital signal
terminal D0 outputs a low level, and the red LED1 will light up. The
stronger the external infrared light, the smaller the value; the weaker
the infrared light, the larger the value.

![](media/01f69822915149445858a471784ebddf.png)


**4.Wiring Diagram：**

![](media/1f2a3bd0f40c2c14162e1c148044ab22.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Flame sensor</p>
<p>* Description : Read the basic usage of Digital，ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>//Flame sensor two pins 13, 34, respectively</p>
<p>#define PIN_ANALOG_IN 34</p>
<p>int digitalPin = 13;</p>
<p>//The following two variables hold the digital signal and adc values respectively</p>
<p>int analogVal = 0;</p>
<p>int adcVal = 0;</p>
<p>void setup() </p>
<p>//In loop()，the digitalRead()function is used to obtain the digital value,</p>
<p>//the analogRead() function is used to obtain the ADC value.</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**7. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Rotating the potentiometer on the sensor,
we can adjust the red LED bright and not bright critical point. The red
LED2 on the sensor module is lit, while the red LED1 is not. Open the
monitor and set baud rate to 9600.

We need to press the reset button on the ESP32, then the monitor will
display the digital value, ADC value, DAC value and voltage value of the
flame sensor. When fire is detected, the LED1 will be on and the digital
value will change from 1 to 0, and the analog value will become
smaller, as shown below.

![](media/6364acee04ac771eb13df0e2f538b3b4.png)

### Project 26: MQ-2 Gas Sensor

![](media/f712788d3997805df25abe4a99d42461.GIF)

1.  **Description**

This analog gas sensor - MQ2 is used in gas leakage detecting equipment
in consumer electronics and industrial markets.

This sensor is suitable for detecting LPG, I-butane, propane, methane,
alcohol, Hydrogen and smoke. It has high sensitivity and quick response.

In addition, the sensitivity can be adjusted by rotating the
potentiometer.

In the experiment, we read the analog value at the A0 port and the D0
port to determine the content of gas.

**2. Working Principle**

The greater the concentration of smoke, the greater the conductivity,
the lower the output resistance, the greater the output analog signal.

When in use, the A0 terminal reads the analog value of the corresponding
gas; the D0 terminal is connected to an LM393 chip (voltage comparator),
we can adjust the alarm threshold of the measured gas through the
potentiometer, and output the digital value at D0. When the measured gas
content exceeds the critical point, the D0 terminal outputs a low level;
when the measured gas content does not exceed the critical point, the D0
terminal outputs a high level.

![](media/c55edbe71237172f6b80877504a9debb.png)


**4.Wiring Diagram：**

![](media/9421fdc1d7de9566b377f1bcd9e060a8.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : MQ2</p>
<p>* Description : Read the basic usage of Digital, ADC，DAC and Voltage</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>//MQ_2 two pins 13, 34, respectively</p>
<p>#define PIN_ANALOG_IN 34</p>
<p>int digitalPin = 13;</p>
<p>//The following two variables hold the digital signal and adc values respectively</p>
<p>int analogVal = 0;</p>
<p>int adcVal = 0;</p>
<p>void setup() </p>
<p>//In loop()，the digitalRead()function is used to obtain the digital value,</p>
<p>//the analogRead() function is used to obtain the ADC value.</p>
<p>//and then the map() function is used to convert the value into an 8-bit precision DAC value.</p>
<p>//The input and output voltage are calculated according to the previous formula,</p>
<p>//and the information is finally printed out.</p>
<p>void loop() </p>
<p>else </p>
<p>delay(100); //Delay time 100 ms</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Rotating the potentiometer on the sensor,
we can adjust the red LED bright and not bright critical point. Open the
monitor , set baud rate to 9600.

We need to press the reset button on the ESP32, then the monitor
displays the corresponding data and characters. When the sensor detects
the smoke or combustible gas, the red LED lights up and the digital
value changes from 1 to 0, the ADC value, DAC value and voltage value
increase, as shown below.

![](media/46ef0317258657030ac4afadcec8b21e.png)

### Project 27: Joystick Module

![](media/a28a09d0d9103cc8b93f2ae71f98482a.jpeg)

**1. Overview**

Game handle controllers are ubiquitous.

It mainly uses PS2 joysticks. When controlling it, we need to connect
the X and Y ports of the module to the analog port of the single-chip
microcomputer, port B to the digital port of the single-chip
microcomputer, VCC to the power output port(3.3-5V), and GND to the GND
of the MCU. We can read the high and low levels of two analog values and
one digital port) to determine the working status of the joystick on the
module.

In the experiment, two analog values(x axis and y axis) will be shown on
Shell.

**2. Working Principle**

![](media/efcb8ed421ab3572af890d73788a8c01.jpeg)

In fact, its working principle is very simple. Its inside structure is
equivalent to two adjustable potentiometers and a button. When this
button is not pressed and the module is pulled down by R1, low levels
will be output ; on the contrary, when the button is pressed, VCC will
be connected (high levels), When we move the joystick, the internal
potentiometer will adjust to output different voltages, and we can read
the analog value.


**4.Wiring Diagram：**

![](media/c1838e7013bc930e997d7684229bcea3.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Joystick</p>
<p>* Description : Read data from Rocker.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int xyzPins[] = ; //x,y,z pins</p>
<p>void setup() </p>
<p>// In loop(), use analogRead () to read the value of axes X and Y</p>
<p>//and use digitalRead () to read the value of axis Z, then display them.</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

In the experiment, according to the wiring diagram, the x pin is set to
GPIO34, the y pin is set to GPIO35 and the pin of the joystick is set to
GPIO13.

**7. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Open the serial monitor and set baud rate
to 9600.

We need to press the reset button on the ESP32, then the serial monitor
will show the corresponding value. Moving the joystick or pressing it
will change the analog and digital values in the serial monitor .

![](media/06a9de681779df5cfc7e6bc24a928a3a.jpeg)

![](media/11a4bebde80c1429a9c219adde1ebf98.png)

### Project 28: Relay Module

1.  **Overview**

In our daily life, we usually use communication to drive electrical
equipment, and sometimes we use switches to control electrical
equipment. If the switch is connected directly to the ac circuit,
leakage occurs and people are in danger. Therefore, from the perspective
of safety, we specially designed this relay module with NO(normally
open) end and NC(normally closed) end.  

**2. Working Principle**

Relay is compatible with a variety of microcontroller control board,
such as Arduino series microcontroller, which is a small current to
control the operation of large current "automatic switch".  

Input Voltage：3.3V-5V

![](media/be1c90d2b52fc2489590e3f702a087bf.emf)

It can let the MCU control board drive 3A load, such as an LED lamp
belt, a DC motor, a micro water pump and a solenoid valve plugable
interface design, which is easy to use.  



**4.Wiring Diagram：**

![](media/b70c5d14c6a3d8820881af0bf8988848.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Relay</p>
<p>* Description : Relay turn on and off.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define Relay 15 // defines digital 15</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. The relay will turn on 1 second, off for 1
second. At the same time, you can hear the sound of the relay on and off
as well as see the change of the indicator light on the relay.

### Project 29: SK6812 RGB Module

![](media/effda831f7c06cea2c443d8352f1a693.jpeg)

1.  **Overview**

In previous lessons, we learned about the plug-in RGB module and used
PWM signals to color the three pins of the module.

There is a Keyestudio 6812 RGB module whose the driving principle is
different from the plug-in RGB module. It can only control with one pin.
This is a set. It is an intelligent externally controlled LED light
source with the control circuit and the light-emitting circuit. Each LED
element is the same as a 5050 LED lamp bead, and each component is a
pixel. There are four lamp beads on the module, which indicates four
pixels.

In the experiment, we make different lights show different colors.

**2. Working Principle**

From the schematic diagram, we can see that these four pixel lighting
beads are all connected in series. In fact, no matter how many they are,
we can use a pin to control a light and let it display any color. The
pixel point contains a data latch signal shaping amplifier drive
circuit, a high-precision internal oscillator and a 12V high-voltage
programmable constant current control part, which effectively ensures
the color of the pixel point light is highly consistent.

The data protocol adopts a single-wire zero-code communication method.
After the pixel is powered up and reset, the S terminal receives the
data transmitted from the controller. The first 24bit data sent is
extracted by the first pixel and sent to the data latch of the pixel.

![](media/f0d824a10a88aa0fbabfb685634672fc.png)



**4.Wiring Diagram：**

![](media/c24ec4320937c7115802a2937180f703.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : sk6812 RGB LED</p>
<p>* Description : turn on sk6812 RGB LED</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Adafruit_NeoPixel.h&gt;</p>
<p>#define PIN 15</p>
<p>// Parameter 1 = number of pixels in strip</p>
<p>// Parameter 2 = Arduino pin number (most are valid)</p>
<p>// Parameter 3 = pixel type flags, add together as needed:</p>
<p>// NEO_KHZ800 800 KHz bitstream (most NeoPixel products w/WS2812 LEDs)</p>
<p>// NEO_KHZ400 400 KHz (classic 'v1' (not v2) FLORA pixels, WS2811 drivers)</p>
<p>// NEO_GRB Pixels are wired for GRB bitstream (most NeoPixel products)</p>
<p>// NEO_RGB Pixels are wired for RGB bitstream (v1 FLORA pixels, not v2)</p>
<p>Adafruit_NeoPixel strip = Adafruit_NeoPixel(60, PIN, NEO_GRB + NEO_KHZ800);</p>
<p>// IMPORTANT: To reduce NeoPixel burnout risk, add 1000 uF capacitor across</p>
<p>// pixel power leads, add 300 - 500 Ohm resistor on first pixel's data input</p>
<p>// and minimize distance between Arduino and first pixel. Avoid connecting</p>
<p>// on a live circuit...if you must, connect GND first.</p>
<p>void setup() </p>
<p>void loop() </p>
<p>// Fill the dots one after the other with a color</p>
<p>void colorWipe(uint32_t c, uint8_t wait) </p>
<p>}</p>
<p>void rainbow(uint8_t wait) </p>
<p>strip.show();</p>
<p>delay(wait);</p>
<p>}</p>
<p>}</p>
<p>// Slightly different, this makes the rainbow equally distributed throughout</p>
<p>void rainbowCycle(uint8_t wait) </p>
<p>strip.show();</p>
<p>delay(wait);</p>
<p>}</p>
<p>}</p>
<p>//Theatre-style crawling lights.</p>
<p>void theaterChase(uint32_t c, uint8_t wait) </p>
<p>strip.show();</p>
<p>delay(wait);</p>
<p>for (int i=0; i &lt; strip.numPixels(); i=i+3) </p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>//Theatre-style crawling lights with rainbow effect</p>
<p>void theaterChaseRainbow(uint8_t wait) </p>
<p>strip.show();</p>
<p>delay(wait);</p>
<p>for (int i=0; i &lt; strip.numPixels(); i=i+3) </p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>// Input a value 0 to 255 to get a color value.</p>
<p>// The colours are a transition r - g - b - back to r.</p>
<p>uint32_t Wheel(byte WheelPos)  else if(WheelPos &lt; 170)  else </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**7. Test Code**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Then we can see the four RGB LEDs show red,
green, blue and white color ; as shown below;

### Project 30: Rotary Encoder

![](media/ec37b336b8f5620b62b04224b132840a.jpeg)

1.  **Overview**

In this kit, there is a Keyestudio rotary encoder, dubbed as switch
encoder. It is applied to automotive electronics, multimedia audio,
instrumentation, household appliances, smart home, medical equipment and
so on.

In the experiment, it it used for counting. When we rotate the rotary
encoder clockwise, the set data falls by 1; if you rotate it
anticlockwise, the set data is up 1; and when the middle button is
pressed, the value will be show in the serial monitor.

**2. Working Principle**

![](media/2fb56ec6fa69e66fcca4243617d4b18c.jpeg)  

The incremental encoder converts the displacement into a periodic electric signal, and then converts this signal into a counting pulse, and the number of pulses indicates the size of the displacement.This module mainly uses 20-pulse rotary encoder components. It can calculate the number of pulses output during clockwise and reverse rotation. There is no limit to count rotation. It resets to the initial state, that is, starts counting from 0.


**4.Wiring Diagram：**

![](media/add429af09e0e3d449fba9b17b3d0af4.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Encoder</p>
<p>* Description : Rotary encoder module counting.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>//Interfacing Rotary Encoder with Arduino</p>
<p>//Encoder Switch -&gt; pin 27</p>
<p>//Encoder DT -&gt; pin 14</p>
<p>//Encoder CLK -&gt; pin 12</p>
<p>int Encoder_DT = 14;</p>
<p>int Encoder_CLK = 12;</p>
<p>int Encoder_Switch = 27;</p>
<p>int Previous_Output;</p>
<p>int Encoder_Count;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>else</p>
<p></p>
<p>}</p>
<p>Previous_Output = digitalRead(Encoder_DT);</p>
<p>if (digitalRead(Encoder_Switch) == 0)</p>
<p></p>
<p>}</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Set CLK to GPIO12 and DAT to GPIO14.

This code is set well in the library file. When CLK descends, read the
voltage of DAT, when DAT is a HIGH level, the value of the rotary
encoder is added by 1; when DAT is a LOW level, the value of the rotary
encoder is cut down 1.

Set the pin of the button(GPIO27) to LOW ans print.

**Test Result**

Upload the code power up by a USB cable, open the serial monitor and set
baud rate to 9600. Rotate the knob on the rotary encoder clockwise, the
displayed data will decrease; on the contrary, in anticlockwise way, the
data will rise. Equally, press the button on the rotary encoder,“Switch
pressed”will be shown.

![](media/15ea201b58012e593d7133bfcfb778d9.png)

### Project 31: Servo Control

![](media/165f16e47a832fc4dcaea6e4a1c11194.jpeg)

**1. Overview**

Servo motor is a position control rotary actuator. It mainly consists of
a housing, a circuit board, a core-less motor, a gear and a position
sensor. Its working principle is that the servo receives the signal sent
by MCU or receiver and produces a reference signal with a period of 20ms
and width of 1.5ms, then compares the acquired DC bias voltage to the
voltage of the potentiometer and obtain the voltage difference output.

In general, servo has three lines in brown, red and orange. The brown
wire is grounded, the red one is a positive pole line and the orange one
is a signal line.

![](media/4b15604cd8a82aeb39497c7544b39f93.emf)

**Working Principle**

When the motor speed is constant, the potentiometer is driven to rotate
through the cascade reduction gear, which leads that the voltage
difference is 0, and the motor stops rotating. Generally, the angle
range of servo rotation is 0° --180 °

The rotation angle of servo motor is controlled by regulating the duty
cycle of PWM (Pulse-Width Modulation) signal. The standard cycle of PWM
signal is 20ms (50Hz). Theoretically, the width is distributed
between 1ms-2ms, but in fact, it's between 0.5ms-2.5ms. The width
corresponds the rotation angle from 0° to 180°. But note that for
different brand motors, the same signal may have different rotation
angles. 

![](media/b4993212773e13b1a4424b3d7ef41ab6.png)



**4.Wiring Diagram：**

![](media/53dbdf43b364542bedb39e45132a2af9.png)

**5.Test Code 1：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Servo_1</p>
<p>* Description : Steering gear rotation Angle 0-90-180, repeatly</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int servoPin = 4;//steering gear PIN</p>
<p>void setup() </p>
<p>void loop() </p>
<p>void servopulse(int pin, int myangle) </p>
<p>}</p>
<p>//**********************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation 1**

**1.** map(value, fromLow, fromHigh, toLow, toHigh)；

Value is the value we map. fromLow, fromHigh is the maximum and minimum
value；

toLow, toHigh are the upper limit and lower limit we map. For example,
map(myangle, 0, 180, 500, 2500) means that an angle value myangle
(0°-180°）the mapping range is from 500us to 2500us.

We use the function servopulse() to make the servo move. We also make
the servo rotate 0°, 90°and 180°cyclically.

8.  **Test Result 1：**

Wire up, upload the code to the ESP32 and power up. The servo will
rotate 0°， 90° and 180°.

**8.Test Code 2：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Servo Sweep</p>
<p>* Description : Control the servo motor for sweeping</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>Servo myservo; // create servo object to control a servo</p>
<p>int posVal = 0; // variable to store the servo position</p>
<p>int servoPin = 4; // Servo motor pin</p>
<p>void setup() </p>
<p>void loop() </p>
<p>for (posVal = 180; posVal &gt;= 0; posVal -= 1) </p>
<p>}</p>
<p>//********************************************************************************</p></td>
</tr>
</tbody>
</table>

**9. Code Explanation 2**

myservo. write (pos) is the rotation angle to POS.  myservo. read ()
reads the current angle value of the servo.  

**10. Test Result 2**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on, the servo will rotate from 0° to 180° by
moving 1° for each 15ms.

### Project 32: Ultrasonic Sensor

![](media/8f99fc89502d1ae2543839b4950da5b6.jpeg)

Bats and some marine animals are able to use high frequencies of sound
for echolocation or communication. They can emit ultrasonic waves from
the larynx through the mouth or nose and use the sound waves that bounce
back to orient and determine the position, size and whether nearby
objects are moving. Ultrasonic is a frequency higher than 20000 Hz sound
wave, which has a good direction, a strong penetration ability, and is
easy to obtain more concentrated sound energy as well as spread far in
the water. It can be used for ranging, speed measurement, cleaning,
welding, gravel, sterilization and disinfection. What‘s more, it has
many applications in medicine, military, industry and agriculture.

1.  **Overview**

In this kit, there is a keyes HC-SR04 ultrasonic sensor, which can
detect obstacles in front and the detailed distance between the sensor
and the obstacle. Its principle is the same as that of bat flying. It
can emit the ultrasonic signals that cannot be heard by humans. When
these signals hit an obstacle and come back immediately. The distance
between the sensor and the obstacle can be calculated by the time gap of
emitting signals and receiving signals.

In the experiment, we use the sensor to detect the distance between the
sensor and the obstacle, and print the test result.

**2. Working Principle**

The most common ultrasonic ranging method is the echo detection. As
shown below; when the ultrasonic emitter emits the ultrasonic waves
towards certain direction, the counter will count. The ultrasonic waves
travel and reflect back once encountering the obstacle. Then the counter
will stop counting when the receiver receives the ultrasonic waves
coming back.

The ultrasonic wave is also sound wave, and its speed of sound V is
related to temperature. Generally, it travels 340m/s in the air.
According to time t, we can calculate the distance s from the emitting
spot to the obstacle.

s=340t/2.

The HC-SR04 ultrasonic ranging module can provide a non-contact distance
sensing function of 2cm-400cm, and the ranging accuracy can reach as
high as 3mm; the module includes an ultrasonic transmitter, receiver and
control circuit. Basic working principle:

1\. First pull down the TRIG, and then trigger it with at least 10us
high level signal;

2\. After triggering, the module will automatically transmit eight 40KHZ
square waves, and automatically detect whether there is a signal to
return.

3\. If there is a signal returned back, through the ECHO to output a
high level, the duration time of high level is actually the time from
emission to reception of ultrasonic.

Test distance = high level duration \* 340m/s \* 0.5.

![](media/686176f637ba288e3b20d63bb1054477.png)



**4.Wiring Diagram:**

![](media/07eb56920ed1cb9b55deab51b7c61d8d.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Ultrasonic</p>
<p>* Description : Use the ultrasonic module to measure the distance.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>const int TrigPin = 13; // define TrigPin</p>
<p>const int EchoPin = 14; // define EchoPin.</p>
<p>int duration = 0; // Define the initial value of the duration to be 0</p>
<p>int distance = 0;//Define the initial value of the distance to be 0</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set baud rate to 9600.

We need to press the reset button on the ESP32, then the serial monitor
will print the distance between the ultrasonic sensor and the object.

![](media/831ae3263f1653c04c2c2b598ba20f65.png)

### Project 33: IR Receiver Module

![](media/80e8f8d8ddc35df9425032ec4ef783ee.png)

**1. Overview**

There is no doubt that infrared remote control is ubiquitous in daily
life. It is used to control various household appliances, such as TVs,
stereos, video recorders and satellite signal receivers. Infrared remote
control is composed of infrared transmitting and infrared receiving
systems, that is, an infrared remote control and infrared receiving
module and a single-chip microcomputer capable of decoding.​    

In this experiment, we need to know how to use the infrared receiving
sensor. The infrared receiving sensor mainly uses the VS1838B infrared
receiving sensor element. It integrates receiving, amplifying, and
demodulating. The internal IC has already completed the demodulation,
and the output is a digital signal. It can receive 38KHz modulated
remote control signal.

In the experiment, we use the IR receiver to receive the infrared signal
emitted by the external infrared transmitting device, and display the
received signal in the shell.

**2. Working Principle**

The main part of the IR remote control system is modulation,
transmission and reception. The modulated carrier frequency is generally
between 30khz and 60khz, and most of them use a square wave of 38kHz and
a duty ratio of 1/3. A 4.7K pull-up resistor R3 is added to the signal
end of the infrared receiver.



**4.Wiring Diagram：**

![](media/f54763e2701fefc503f275dcb9410ad0.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : IR Receiver</p>
<p>* Description : Decode the infrared remote control and print it out through the serial port.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;IRremoteESP8266.h&gt;</p>
<p>#include &lt;IRrecv.h&gt;</p>
<p>#include &lt;IRutils.h&gt;</p>
<p>const uint16_t recvPin = 15; // Infrared receiving pin</p>
<p>IRrecv irrecv(recvPin); // Create a class object used to receive class</p>
<p>decode_results results; // Create a decoding results class object</p>
<p>void setup() </p>
<p>void loop() </p>
<p>delay(1000);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set baud rate to 9600.

We need to press the reset button on the ESP32, then find the infrared
remote control, pull out the insulating sheet, and press the button at
the receiving head of the infrared receiving sensor. After receiving the
signal, the LED on the infrared receiving sensor also starts to flash,
as shown in the figure below.

![](media/9fb318b17172922762a3fe2440bf3fd9.png)

The key code value of each key is shown below:

![](media/ebcf0cb2055f7784505f76ceeaef9f47.jpeg)

### Project 34: DS18B20 Temperature Sensor

![](media/29c66f83d6ea8bbc378b0508e78d5f3b.png)

1.  **Description**

In this kit, there is a DS18B20 temperature sensor, which is from maxim.
The MCU can communicate with the DS18B20 through 1-Wire protocol, and
finally read the temperature.  In this experiment, we will use this
temperature sensor to measure the temperature in the current
environment. The test result is **℃**, ranging from -55**℃** to
+125**℃**. We will display the test result on shell.

**2. Working Principle**

![](media/eef2d84a2ad003d15575726341de52bf.png)

The hardware interface of the 1-Wire bus is very simple, just connect
the data pin of the DS18B20 to an IO port of the microcontroller. The
timing of the 1-Wire bus is relatively complex. Many students can’t
understand the timing diagram independently here. We have encapsulated
the complex timing operations in the library, and you can use the
library functions directly.

Schematic Diagram of DS18B20

This can save up to 12-bit temperature vale. In the register, save in
code complement. As shown below;

![](media/bffba8c519ff6e0310882d0712be9177.png)

A total of 2 bytes, LSB is the low byte, MSB is the high byte, where MSb
is the high byte of the byte, LSb is the low byte of the byte. As you
can see, the binary number, the meaning of the temperature represented
by each bit, is expressed. Among them, S represents the sign bit, and
the lower 11 bits are all powers of 2, which are used to represent the
final temperature. The temperature measurement range of DS18B20 is from
-55 degrees to +125 degrees, and the expression form of temperature
data, S represents positive and negative temperature, and the resolution
is 2﹣⒋, which is 0.0625.



**4.Wiring Diagram：**

![](media/f605610384d05ff2877e58474a0d6f81.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : ds18b20</p>
<p>* Description : Read the temperature of ds18B20</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;DS18B20.h&gt;</p>
<p>//ds18b20 pin to 15</p>
<p>DS18B20 ds18b20(15);</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

1\. We set the pin to GPIO15 and obtain the temperature in the unit of
℃.  

2\. Set a double decimal variable to temp, and assign the measured
result to temp.

3\. The serial monitor displays the temp value, and the baud rate needs
to be set before displaying (our default setting is 9600, which can be
changed).

4\. We add the unit behind the data. If the unit is directly set to °C,
the test result will be garbled. So we directly replace ℃ with C.

**7. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set baud rate to 9600. We need to press the reset button on
the ESP32, then the monitor will display the temperature of the current
environment, as shown below.

![](media/4fe3fbb24af6789b35ee6531e920b71e.png)

### Project 35: XHT11 Temperature and Humidity Sensor

![](media/1153b275e0f6c086c9e4225084acf246.png)

**1. Description**

This DHT11 temperature and humidity sensor is a composite sensor which
contains a calibrated digital signal output of the temperature and
humidity.

DHT11 temperature and humidity sensor uses the acquisition technology of
the digital module and temperature and humidity sensing technology,
ensuring high reliability and excellent long-term stability.

It includes a resistive element and a NTC temperature measuring device.

![](media/ac0d6049bc0a5ae8cc515d23b85ecad0.png)

**2. Working Principle**

The communication and synchronization between the single-chip
microcomputer and XHT11 adopts the single bus data format. The
communication time is about 4ms. The data is divided into fractional
part and integer part.

Operation process: A complete data transmission is 40bit, high bit first
out. Data format: 8bit humidity integer data + 8bit humidity decimal
data + 8bit temperature integer data + 8bit temperature decimal data +
8bit checksum

8-bit checksum: 8-bit humidity integer data + 8-bit humidity decimal
data + 8-bit temperature integer data + 8-bit temperature decimal data
"Add the last 8 bits of the result.


**4.Wiring Diagram：**

![](media/7e2c1d38e5a419a5df8489869a94d21c.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : xht11</p>
<p>* Description : Read the temperature and humidity values of XHT11.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include "xht11.h"</p>
<p>//gpio15</p>
<p>xht11 xht(15);</p>
<p>unsigned char dht[4] = ;//Only the first 32 bits of data are received, not the parity bits</p>
<p>void setup() </p>
<p>void loop()  else </p>
<p>delay(1000); //It takes 1000ms to wait for the device to read</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

1.  We set the pin to GPIO15, and store the detected temperature and
    humidity data in the dht\[4\] array.

3\. We add units behind the data. If the temperature unit is directly
set to °C, the test results may be wrong, so we directly replace °C with
C; the humidity unit is directly set to %.

**7. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully, we will use a USB cable to power on. Open the serial
monitor and set baud rate to 9600. We need to press the reset button on
the ESP32, then the monitor will display the temperature and humidity
data of the current environment, as shown below.

![](media/8b012c9137d84abac53407dad46a8106.png)

### Project 36: DS1307 Clock Module

![](media/949abbbea3c8d8b36463768a39a07b51.png)

1.  **Overview**

This module mainly uses the real-time clock chip DS1307, which is the
I2C bus interface chip that has second, minute, hour, day, month, year
and other functions as well as leap year automatic adjustment function
introduced by DALLAS. It can work independently of CPU, and won‘t’
affected by the CPU main crystal oscillator and capacitance as well as
keep accurate time. What‘s more, monthly cumulative error is generally
less than 10 seconds.The chip also has a clock protection circuit in
case of main power failure and runs on a back-up battery that denies the
CPU read and write access. At the same time, it contains automatic
switching control circuit of standby power supply, so it can guarantee
the accuracy of system clock in case of power failure of main power
supply and other bad environment.

Going forward, the DS1307 chip internal integration has a certain
capacity, with power failure protection characteristics of static RAM,
which can be used to save some key data. 

In the experiment, we use the DS1307 clock module to obtain the system
time and print the test results.  

![](media/92b8dc82b0c2887539bd506639cfbfc0.png)

**2. Working Principle**

Serial real-time clock records year, month, day, hour, minute, second
and week; AM and PM indicate morning and afternoon respectively; 56
bytes of NVRAM store data; 2-wire serial port; programmable square wave
output; power failure detection and automatic switching circuit; battery
current is less than 500nA.

Pins description：X1, 32.768kHz crystal terminal ;

VBAT:X2：+3V input;

SDA：serial data;

SCL：serial clock;

SQW/OUT：square waves/output drivers



**4.Wiring Diagram：**

![](media/de4d2418a1b8ed0ae1c466747103a440.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : DS1307 Real Time Clock</p>
<p>* Description : Read the year/month/day/hour/minute/second/week of DS1307 clock module</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Wire.h&gt;</p>
<p>#include "RtcDS1307.h" //DS1307 clock module library</p>
<p>RtcDS1307&lt;TwoWire&gt; Rtc(Wire);//i2cport</p>
<p>void setup()</p>
<p>void loop()</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

Rtc.GetDateTime(): the obtained current time and date.

**Rtc.Begin();**enable DS1307 real-time clock

**Rtc.SetIsRunning(true);** run the DS1307 real-time clock, if true
changes into false, time will stop.

**Rtc.SetDateTime()；**set time

**Rtc.GetDateTime().Year()** return year

**Rtc.GetDateTime().Month()** return month

**Rtc.GetDateTime().Day()**return date

**Rtc.GetDateTime().Hour()**return hour

**Rtc.GetDateTime().Minute()**return minute

**Rtc.GetDateTime().Second()**return second

**Rtc.GetDateTime().DayOfWeek() return week**

**7. Test Result**

Wire up, attach the DS1307 sensor to a battery, compile and upload the
code to the ESP32. After uploading successfully，we will use a USB cable
to power on. Open the serial monitor and set baud rate to 9600. We need
to press the reset button on the ESP32, then we can see the displayed
year, month, day, hour, minute, second and week on themonitor, and set
the time and date to refresh every second, as shown below:

![](media/49894e3ce876ac5c2f4b52087a4f8dbe.png)

### Project 37: TM1650 4-Digit Tube Display

![](media/f698ea56391906278b7c8064fca42bb3.jpeg)

**1. Overview**

This module is mainly composed of a 0.36 inch red common anode 4-digit
digital tube, and its driver chip is TM1650. When using it, we only need
two signal lines to make the single-chip microcomputer control a
4-bitdigit tube, which greatly saves the IO port resources of the
control board.

TM1650 is a special circuit for LED (light emitting diode display) drive
control. It integrates MCU input and output control digital interface,
data latch, LED drivers, keyboard scanning, brightness adjustment and
other circuits.

TM1650 has stable performance, reliable quality and strong
anti-interference ability.

It can be applied to the application of long-term continuous working for
24 hours.

TM1650 uses 2-wire serial transmission protocol for communication (note
that this data transmission protocol is not a standard I2C protocol).
The chip can drive the digital tube and save MCU pin resources through
two pins and MCU communication.

**2. Working Principle**

TM1650 adopts IIC treaty, which uses DIO and CLK buses.

![](media/c7b895791863dfc2663800ce90f61c89.png)

**Data command setting**: 0x48 means that we light up the digital tube,
instead of enable the function of key scanning

![](media/09585b52bed3d4112d59a611c3c3f262.png)

**Command display setting:**

bit\[6:4\]: set the brightness of tube display, and 000 is brightest

bit\[3\]: set to show decimal points

bit\[0\]: start the display of the tube display


**4.Wiring Diagram：**

![](media/08a0d34d55b5e4215c77fbf8f656c9a9.png)

1.  **Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : TM1650 Four digital tube</p>
<p>* Description : TM1650 Four Digital Tube shows 0-9999</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include "TM1650.h"</p>
<p>#define CLK 22 //pins definitions for TM1650 and can be changed to other ports</p>
<p>#define DIO 21</p>
<p>TM1650 DigitalTube(CLK,DIO);</p>
<p>void setup()</p>
<p>// DigitalTube.displayDot(1,true); //Bit0 display dot. Use before displayBit().</p>
<p>DigitalTube.displayBit(1,0); //DigitalTube.Display(bit,number); bit=0---3 number=0---9</p>
<p>}</p>
<p>void loop()</p>
<p>}</p>
<p>void displayFloatNum(float num)</p>
<p>if(dat%10000/1000 != 0)</p>
<p>if(dat%1000/100 != 0)</p>
<p>DigitalTube.clearBit(1);</p>
<p>DigitalTube.clearBit(2);</p>
<p>DigitalTube.clearBit(3);</p>
<p>DigitalTube.displayBit(4, dat%100/10);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Similarly, we need to import the library file of the TM1650 module
first. Here are some commonly used function interfaces:

**.init(); Initialize** TM1650

**.clear();**clear up the tube display

**.displayString(char \*aString);**Display character string，

**.displayString(String sString);** Display string ，sString is character
string

**.displayString(float value);Display decimal, the content is float
type**

**.displayString(double value);Display decimal, the content is double
type**

**.displayString(int value); Display integer, the content is int type**

**.displayOn();**open the tube display

**.displayOff();** turn off the tube display，in comparison with
.clear，once turning off, the function .displayOn() must be used;

**.setDot(unsigned int aPos, bool aState);** display decimal point, aPos
is the location of decimal point (0\~3) corresponds to (1\~4)，aState is
the display status:1（true）lights up，2（false）goes off.

**.setBrightness(unsigned int iBrightness);** set the brightness of the
tube display

iBrightness: the brightness value（1\~8, type is unsigned int，

**Test Result**

Run the test code, wire up and power on. 4-digit tube display will show
integer from 0 to 99999, add 1 for each 10ms. Increase to 9999 then
start from 0

### Project 38: HT16K33\_8X8 Dot Matrix Module

![](media/431b6c4abd63b99219658a03d24de991.jpeg)

1.  **Overview**

What is the dot matrix display?

The 8X8 dot matrix is composed of 64 light-emitting diodes, and each
light-emitting diode is placed at the intersection of the row line and
the column line. When the corresponding row is set to 1 level, and a
certain column is set to 0 level, the corresponding diode will light up.

**2. Working Principle**

As the schematic diagram shown, to light up the LED at the first row and
column, we only need to set C1 to high level and R1 to low level. To
turn on LEDs at the first row, we set R1 to low level and C1-C8 to high
level.

16 IO ports are needed, which will highly waste the MCU resources.

Therefore, we designed this module, using the HT16K33 chip to drive an
8\*8 dot matrix, which greatly saves the resources of the single-chip
microcomputer.

![](media/0b38b92f282143bf7605fbc7db294c31.png)

There are three DIP switches on the module, all of which are set to I2C
communication address. The setting method is shown below. A0，A1 and A2
are grounded, that is, the address is 0x70

<table>
<tbody>
<tr class="odd">
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
</tr>
<tr class="even">
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>1（ON）</td>
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>1（ON）</td>
<td>0（OFF）</td>
</tr>
<tr class="odd">
<td>OX70</td>
<td>OX71</td>
<td>OX72</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
</tr>
<tr class="odd">
<td>1（ON）</td>
<td>1（ON）</td>
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>0（OFF）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>0（OFF）</td>
<td>1（ON）</td>
</tr>
<tr class="even">
<td>OX73</td>
<td>OX74</td>
<td>OX75</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td>A0（1）</td>
<td>A1（2）</td>
<td>A2（3）</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>0（OFF）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>OX76</td>
<td>OX77</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

<table>
<tbody>
<tr class="odd">
<td>0（OFF）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td>1（ON）</td>
<td></td>
</tr>
<tr class="even">
<td>OX76</td>
<td>OX77</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


**4.Wiring Diagram：**

![](media/d3f2f2968ff861d04e909cf330986652.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : 8×8 Dot-matrix Display</p>
<p>* Description : 8x8 LED dot matrix display“Heart” pattern.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include "HT16K33_Lib_For_ESP32.h"</p>
<p>#define SDA 21</p>
<p>#define SCL 22</p>
<p>ESP32_HT16K33 matrix = ESP32_HT16K33();</p>
<p>//The brightness values can be set from 1 to 15, with 1 darkest and 15 brightest</p>
<p>#define A 15</p>
<p>byte result[8][8];</p>
<p>byte test1[8] = ;</p>
<p>void setup()</p>
<p></p>
<p>void loop()</p>
<p></p>
<p>for (int i = 7; i &gt; 0; i--)</p>
<p></p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

First we need to import the library file.

1.  The pattern in our code is an array of byte data type, which is
    shown in the table below. We convert
     into binary, and fill in
    the 8\*8 form below to make it clear. 1 means on, 0 means off. Then
    we can see that it is a smile shape.

<table>
<tbody>
<tr class="odd">
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
</tr>
<tr class="odd">
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="odd">
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr class="odd">
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr class="even">
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
</tbody>
</table>

**7. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Then the dot matrix displays a “ smile
”pattern.

### Project 39: RFID Module

![](media/75003b61112e3495f213629e49f26185.jpeg)

1.  **Description**

RFIDRFID-RC522 radio frequency module adopts a Philips MFRC522 original
chip to design card reading circuit, easy to use and low cost, suitable
for equipment development and card reader development and so on.

RFID or Radio Frequency Identification system consists of two main
components, a transponder/tag attached to an object to be identified,
and a transceiver also known as interrogator/Reader.

In the experiment, the data read by the card swipe module is 4
hexadecimal numbers, and we print these four hexadecimal numbers as
strings. For example, we read the data of the IC card below:
0xED、0xF7、0x94、0x5A and the information string displayed in the
serial monitor is ED F7 94 5A ; the data read from the keychain is:
0x4C、0x09、0x6B、0x6E . Different IC cards and different key chains have
diverse data.

**2. Working Principle**

Radio frequency identification, the card reader is composed of a radio
frequency module and a high-level magnetic field. The Tag transponder is
a sensing device, and this device does not contain a battery. It only
contains tiny integrated circuit chips and media for storing data and
antennas for receiving and transmitting signals. To read the data in the
tag, first put it into the reading range of the card reader. The reader
will generate a magnetic field, and because the magnetic energy
generates electricity according to Lenz's law, the RFID tag will supply
power, thereby activating the device.

![](media/8f1b325813b0fe4f6b0fd1e6f02a9405.png)



**4.Wiring Diagram：**

![](media/33c691a71bc8a173a6b775b86c2c2f02.png)

**5.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : RFID</p>
<p>* Description : RFID reader UID</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Wire.h&gt;</p>
<p>#include "MFRC522_I2C.h"</p>
<p>// IIC pins default to GPIO21 and GPIO22 of ESP32</p>
<p>// 0x28 is the i2c address of SDA, if doesn't match，please check your address with i2c.</p>
<p>MFRC522 mfrc522(0x28); // create MFRC522.</p>
<p>void setup() </p>
<p>void loop() </p>
<p>// select one of door cards. UID and SAK are mfrc522.uid.</p>
<p>// save UID</p>
<p>Serial.print(F("Card UID:"));</p>
<p>for (byte i = 0; i &lt; mfrc522.uid.size; i++) </p>
<p>Serial.println();</p>
<p>}</p>
<p>void ShowReaderDetails() </p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Code Explanation**

**Wire.begin();** The module we use is the IIC interface, so we first
initialize the IIC

**mfrc522.PCD\_Init(); initialize** MFRC522

**String(mfrc522.uid.uidByte\[i\], HEX);** A string to convert the value
read into hexadecimal format.

**7. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Open the serial monitor and set baud rate
to 115200. We need to press the reset button on the ESP32, when we make
the IC card close to the RFID module, the information will be printed
out, as shown in the figure below.

![](media/fd497570f812e364d8d4f0e520624898.png)

**5. Comprehensive Experiments**

The previous projects are related to single sensor or module. In the
following part, we will combine various sensors and modules to create
some comprehensive experiments to perform special functions.

### Project 40: Button-controlled LED

![](media/50740b22d16151d490b8494b0bff4f6e.jpeg)

**Overview**

In this lesson, we will make an extension experiment with a button and
an LED. When the button is pressed and low levels are output, the LED
will light up; when the button is released, the LED will go off. Then we
can control a module with another module.


**3.Wiring Diagram：**

![](media/378de9cb95275a6a1dec9adbf2f15eaa.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : button_control_LED</p>
<p>* Description : Make a table lamp.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_LED 4</p>
<p>#define PIN_BUTTON 15</p>
<p>bool ledState = false;</p>
<p>void setup() </p>
<p>// the loop function runs over and over again forever</p>
<p>void loop() </p>
<p>while (digitalRead(PIN_BUTTON) == LOW);</p>
<p>}</p>
<p>}</p>
<p>void reverseGPIO(int pin) </p>
<p>//**********************************************************************</p></td>
</tr>
</tbody>
</table>

**Test Result**

Upload the code wire up and power up with a USB cable. When the button
is pressed, the LED will light up; when pressed again, the LED will go
off

### Project 41: Alarm Experiment

![](media/6db3cb7d3a91e700a3b651c1f0edb7a5.jpeg)

**Overview**

In the previous experiment, we control an output module though an input
module. In this lesson, we will make an experiment that the active
buzzer will emit sounds once an obstacle appears.


**3.Wiring Diagram：**

![](media/e37efdec9676d47eaf8dabd2da41759a.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Avoiding alarm</p>
<p>* Description : Obstacle avoidance sensor controls the buzzer</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int item = 0;</p>
<p>void setup() </p>
<p>void loop()  else </p>
<p>delay(100);//Delay 100ms</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

Set IO ports according to connection diagram then configure pins mode

The value is 0 when pressing the button, So, we can determine the key
value(0）through if (item == 0) and make the buzzer beep digitalWrite(16,
HIGH).

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. If the obstacle is detected, the active
buzzer will chime; if not, it won’t beep.

### Project 42: Intrusion Detection

![](media/b7828b9e5ee615a151567e20d35db90f.png)

1.  **Description**

In this experiment, we use a PIR motion sensor to control an active
buzzer to emit sounds and the onboard LED to flash rapidly.


**3.Wiring Diagram：**

![](media/07ded8ae2b9b12d7d399422cae6b8c5a.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : PIR alarm</p>
<p>* Description : PIR control buzzer</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int item = 0;</p>
<p>void setup() </p>
<p>void loop()  else </p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Test Result**

Wire up, compile and upload the code to the ESP32. After uploading
successfully, we will use a USB cable to power on. If the sensor detects
people moving, the buzzer will emit an alarm , and the LED will flash
continuously.

### Project 43: Extinguishing Robot

![](media/a3ccd8168b26f2a183fa9feda1b015f3.jpeg)

1.  **Description**

Today we will use Arduino simulation to build an extinguishing robot
that will automatically sense the fire and start the fan. In this
project we will learn how to build a very simple robot using ESP32,
(detecting flames with a flame sensor, blowing out candles with a fan)
can teach us basic concepts about robotics. Once you understand the
basics below, you can build more complex robots.


**3.Wiring Diagram：**

![](media/68f8fee9c39dad76e1eb3e783ddc1c37.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Fire-fighting robot</p>
<p>* Description : Flame sensor controls the 130 fan module</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>int item = 0;</p>
<p>void setup() </p>
<p>void loop()  else </p>
<p>delay(100);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

In the code, we set the threshold value to 30000. When the analog value
detected by the flame sensor is lower than the threshold value, the fan
will be automatically turned on; otherwise, it will be turned off. For
the driving method of the fan, please refer to the 130 Motor.

**Test Result**

Wire up and upload the test code，power up and turn the DIP switch to ON
on the ESP32 board and press the rest button. The monitor shows the
flame value. When this value is less than 30000, the fan will blow out
the fire. Basically, the flame value can be set by yourself.

![](media/7a7aaa38c5391a2ce6ce88defb1ff574.png)

### Project 44: Rotary Encoder control RGB

![](media/c6b4f1cedef06ed68d1c2e5ccf5c17d2.jpeg)

1.  **Introduction**

In this lesson, we will control the LED on the RGB module to show
different colors through a rotary encoder.

When designing the code, we need to divide the obtained values by 3 to
get the remainders. The remainder is 0 and the LED will become red. The
remainder is 1, the LED will become green. The remainder is 2, the LED
will turn blue.



**3.Wiring Diagram：**

![](media/c88ef3fa9019777e0697e242d0b41c4c.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Encoder control RGB</p>
<p>* Description : Rotary encoder controls RGB to present different effects</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>//Interfacing Rotary Encoder with Arduino</p>
<p>//Encoder Switch -&gt; pin 27</p>
<p>//Encoder DT -&gt; pin 14</p>
<p>//Encoder CLK -&gt; pin 12</p>
<p>int Encoder_DT = 14;</p>
<p>int Encoder_CLK = 12;</p>
<p>int Encoder_Switch = 27;</p>
<p>int Previous_Output;</p>
<p>int Encoder_Count;</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>int red, green, blue;</p>
<p>int val;</p>
<p>void setup() </p>
<p>}</p>
<p>void loop() </p>
<p>else</p>
<p></p>
<p>}</p>
<p>Previous_Output = digitalRead(Encoder_DT);</p>
<p>if (digitalRead(Encoder_Switch) == 0)</p>
<p></p>
<p>}</p>
<p>if (val == 0)  else if (val == 1)  else </p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

3.  **Code Explanation**

<!-- end list -->

1.  In the experiment, we set the val to the remainder of Encoder\_Count
    divided by 3. Encoder\_Count is the value of the encoder. Then we
    can set pin GPIO0 (red), GPIO2 (green) and GPIO15 (blue) according
    to remainders.
    
    2\. Referring to the control method learned in the previous
    experiment, use the LED on the remainder control module to display
    the corresponding light color. The value obtained by taking the
    remainder of 3 for any number is 0 or 1 or 2. We use these three
    values to judge, and display the corresponding color.
    
    **Test Result**
    
    Wire up, run the code and open the serial monitor. Power up, open
    the monitor and set baud rate to 9600. Press the reset button and
    rotate the knob of the rotary encoder to display the reminders,
    which can control colors of LED.

### Project 45: Rotary Potentiometer

![](media/f71165ab140ae6b2aac093dc75785c96.jpeg)

1.  **Introduction**

In the previous courses, we did experiments of breathing light and
controlling LED with button. In this course, we do these two experiments
by controlling the brightness of LED through an adjustable
potentiometer. The brightness of LED is controlled by PWM values, and
the range of analog values is 0 to 4095 and the PWM value range is
0-255.

After the code is set successfully, we can control the brightness of the
LED on the module by rotating the potentiometer.

**3.Wiring Diagram：**

![](media/7f24723673e622d23fbe0a3cdbd21d69.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : adjust the light</p>
<p>* Description : Controlling the brightness of LED by potentiometer.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#define PIN_ANALOG_IN 34 //the pin of the potentiometer</p>
<p>#define PIN_LED 15 // the pin of the LED</p>
<p>#define CHAN 0</p>
<p>void setup() </p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

In the experiment, the mapping function maps adcVal from the range of
0-4095 to 0-255, and assigns it to pwmVal.

**6. Test Result**

Wire up, power up, compile and upload the code to the ESP32. After
uploading successfully，we will use a USB cable to power on. Rotating the
potentiometer on the module can adjust the brightness of the LED on the
LED module.

### Project 46: Smart Windows

![](media/fd7384d737b0393e91d42523f4d65b07.jpeg)

1.  **Description**

In life, we can see all kinds of smart products, such as smart home.
Smart homes include smart curtains, smart windows, smart TVs, smart
lights, and more. In this experiment, we use a steam sensor to detect
rainwater, and then achieve the effect of closing and opening the window
by a servo.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/b64cdb5749df7d2b7dd3719216c7aff3.png" style="width:0.91458in;height:0.65417in" alt="KS6048 水滴水蒸气传感器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/b9a96e60ed3aee985db5d4dcaf9bf38b.png" style="width:1.05833in;height:1.05069in" alt="舵机" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94722in;height:0.41875in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Keyestudio Steam Sensor*1</td>
<td>Servo*1</td>
<td>3P Dupont Wire*1</td>
<td>Micro USB*1</td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/8683e9990285f9eef82368857cb5b6a6.png)

3.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : smart window</p>
<p>* Description : Water drop sensor controls steering gear rotation.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;ESP32Servo.h&gt;//Import the steering gear library file</p>
<p>int adcVal = 0;//A variable that holds the ADC value output by the droplet sensor</p>
<p>int servoPin = 15; // Define the servo pin</p>
<p>Servo myservo;//Defines an instance of the steering gear class</p>
<p>#define PIN_ADC 34 //the pin of the Water drop sensor</p>
<p>void setup()</p>
<p>void loop() else </p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

We can control a servo to rotate by a threshold.

**6. Test Result**

Wire up, power on and compile and upload the code to the ESP32. After
uploading successfully，we will use a USB cable to power on. When the
sensor detects a certain amount of water, the servo rotates to achieve
the effect of closing or opening windows.

### Project 47: Sound Activated Light

![](media/f3ddb58e83a92a888d3e1d66f7456170.png)

1.  **Introduction**

In this lesson, we will make a smart sound activated light using a sound
sensor and an LED module. When we make a sound, the light will
automatically turn on; when there is no sound, the lights will
automatically turn off. How it works? Because the sound-controlled light
is equipped with a sound sensor, and this sensor converts the intensity
of external sound into a corresponding value. Then set a threshold, when
the threshold is exceeded, the light will turn on, and when it is not
exceeded, the light will go out.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/cf7b54ba090f4e34025101cf9ece26d1.png" style="width:0.60903in;height:0.8125in" alt="声音传感器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/f0ef7a5a2e7eebb09e91f73cb2a6caf3.png" style="width:0.62153in;height:0.82847in" alt="白色LED模块" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94583in;height:0.44375in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Keyestudio Sound Sensor*1</td>
<td>Keyestudio Purple LED Module*1</td>
<td>3P Dupont Wire*2</td>
<td>Micro USB*1</td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/e54db9c861847ce0145accb574467c95.png)

**4.Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : sound-controlled lights</p>
<p>* Description : Sound sensor controls LED on and off</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>int ledPin = 15;//LED is connected to GP15</p>
<p>int microPin = 34;//Sound sensor is connected to GPIO34</p>
<p>void setup() </p>
<p>void loop() else</p>
<p>delay(100);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Wire up, power on and compile and upload the code to the ESP32. After
uploading successfully, we will use a USB cable to power on. Open the
serial monitor and set the baud rate to 9600.

We need to press the reset button on the ESP32, then the corresponding
volume ADC value will be displayed. When the analog value of sound is
greater than 600, the LED on the LED module will light up, otherwise it
will go off.

![](media/dbfc7cb1efd260243534ea96adc9cbe1.png)

### Project 48: Fire Alarm

![](media/e6971103aaa858036b51f3165e0ccb32.jpeg)

**1. Description**

In this experiment, we will make a fire alarm system. Just use a flame
sensor to control an active buzzer to emit sounds.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/a5e355d0fd3c9b18c7684a9a2b99f0a5.png" style="width:0.70625in;height:0.94167in" alt="有源蜂鸣器模块" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Keyestudio Active Buzzer*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/4ecedf84c69e9264059ffd14b02592bd.png" style="width:0.95278in;height:0.57153in" alt="火焰传感器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94722in;height:0.41875in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
</tr>
<tr class="even">
<td>keyestudio Flame Sensor*1</td>
<td>Micro USB*1</td>
<td>3P Dupont Wire*2</td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/2c25672935b822ed775e665e05f72980.png)

**4.Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Flame Alarm</p>
<p>* Description : Controlling the buzzer by flame sensor.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>int item = 0;</p>
<p>void setup() </p>
<p>void loop()  else </p>
<p>delay(100);//Delay 100ms</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

This flame sensor uses an analog pin and a digital pin. When a flame is
detected, the digital pin outputs a low level. In this experiment we
will use the digital port.

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. When the sensor detects the flame, the
external active buzzer will emit sounds, otherwise the active buzzer
will not emit sounds.

### Project 49: Smoke Alarm

![](media/a1f72c7aa7fd3609401a1f1176b426ec.jpeg)

1.  **Description**

In this experiment, we will make a smoke alarm by a TM16504-Digit
segment module, a gas sensor and an active buzzer.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/a5e355d0fd3c9b18c7684a9a2b99f0a5.png" style="width:0.70625in;height:0.94167in" alt="有源蜂鸣器模块" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/f47b077303226cce504ea7734826dfc9.png" style="width:0.94514in;height:0.52569in" alt="四位数码管模块" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Keyestudio Active Buzzer*1</td>
<td>Keyestudio TM1650Segment Module*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/ee4483f37a6f3609acdb661095f4b706.png" style="width:1.04167in;height:0.52708in" alt="KS6029 MQ-2 模拟气体传感器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/269c154eda332be03643bada56070124.jpeg" style="width:0.91458in;height:0.35625in" alt="4p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94722in;height:0.41875in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>keyestudio Analog Gas Sensor*1</td>
<td>3P Dupont Wire*2</td>
<td>4P Dupont Wire*1</td>
<td>Micro USB*1</td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/ae8b397c9acaba3e10da3e2028797197.png)

4.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : smoke alarm</p>
<p>* Description : MQ2 controls a buzzer and a four-digit analog smoke tester</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "TM1650.h" //Import the TM1650 library file</p>
<p>int adcVal = 0; //display ADC value</p>
<p>//the interfaces are GPIO21 and GPIO22</p>
<p>#define DIO 21</p>
<p>#define CLK 22</p>
<p>TM1650 DigitalTube(CLK,DIO);</p>
<p>void setup() </p>
<p>// DigitalTube.displayDot(1,true); //Bit0 display dot. Use before displayBit().</p>
<p>DigitalTube.displayBit(1,0); //DigitalTube.Display(bit,number); bit=0---3 number=0---9</p>
<p>pinMode(15, OUTPUT);//the buzzer is connected to GPIO15</p>
<p>}</p>
<p>void loop()  else </p>
<p>delay(100);//delay 100ms</p>
<p>}</p>
<p>void displayFloatNum(float adcVal)</p>
<p>if(dat%10000/1000 != 0)</p>
<p>if(dat%1000/100 != 0)</p>
<p>DigitalTube.clearBit(1);</p>
<p>DigitalTube.clearBit(2);</p>
<p>DigitalTube.clearBit(3);</p>
<p>DigitalTube.displayBit(4, dat%100/10);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Define an integer variable val to store the analog value of the smoke
sensor, and then we display the analog value in the four-digit digital
tube, and then set a threshold, and when the threshold is reached, the
buzzer will sound.

**Test Result**

Wire up, power on, compile and upload the code to the ESP32. After
uploading successfully，we will use a USB cable to power on. When the
concentration of combustible gas exceeds the standard, the active buzzer
module will give an alarm, and the four-digit digital tube will display
the concentration value.

### Project 50: Ultrasonic Radar

![](media/19a7c30e24f0ec39da94912c5535b791.png)

1.  **Description**

![](media/38037219a4908755dbedc422be1ab61b.jpeg)We know that bats use echoes to determine the
direction and the location of their preys. In real life, sonar is used
to detect sounds in the water. Since the attenuation rate of
electromagnetic waves in water is very high, it cannot be used to detect
signals, however, the attenuation rate of sound waves in the water is
much smaller, so sound waves are most commonly used underwater for
observation and measurement.In this experiment, we will use a speaker
module, an RGB module and a 4-digit tube display to make a device for
detection through ultrasonic.



**3.Connection Diagram**

![](media/3d6e86b75df96354e05447244d2fee68.png)

**4.Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Ultrasonic radar</p>
<p>* Description : Ultrasonic control four digit tube, buzzer and RGB analog ultrasonic radar.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "TM1650.h" //Import the TM1650 library file</p>
<p>//the interfaces are GPIO21 and GPIO22</p>
<p>#define DIO 21</p>
<p>#define CLK 22</p>
<p>TM1650 DigitalTube(CLK,DIO);</p>
<p>int beeppin = 18; //Define the horn pin as GPIO18</p>
<p>int TrigPin = 13; //Set the Trig pin to GPIO13</p>
<p>int EchoPin = 14; //Set the Echo pin to GPIO14</p>
<p>int distance;//Distance measured by ultrasound</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>float checkdistance() </p>
<p>void setup() </p>
<p>// DigitalTube.displayDot(1,true); //Bit0 display dot. Use before displayBit().</p>
<p>DigitalTube.displayBit(1,0); //DigitalTube.Display(bit,number); bit=0---3 number=0---9</p>
<p>pinMode(TrigPin, OUTPUT);//Sets the Trig pin as output</p>
<p>pinMode(EchoPin, INPUT); //Set the Echo pin as input</p>
<p>ledcSetup(3, 1000, 8);//setup the pwm channels,1KHz,8bit</p>
<p>ledcAttachPin(18, 3);</p>
<p>for (int i = 0; i &lt; 3; i++) </p>
<p>}</p>
<p>void loop()  else if (distance &gt; 10 &amp;&amp; distance &lt;= 20)  else </p>
<p>}</p>
<p>void displayFloatNum(float distance)</p>
<p>if(dat%10000/1000 != 0)</p>
<p>if(dat%1000/100 != 0)</p>
<p>DigitalTube.clearBit(1);</p>
<p>DigitalTube.clearBit(2);</p>
<p>DigitalTube.clearBit(3);</p>
<p>DigitalTube.displayBit(4, dat%100/10);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

We set sound frequency and light color by adjusting different distance
range.

We can adjust the distance range in the code.

**6. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. When the ultrasonic sensor detects
different distances, the buzzer will produce different frequencies of
sound, the RGB will show different colors, and the measured distances
are displayed on the 4-digit tube display.

### Project 51: IR Remote Control

![](media/6e823de7db355fde0bc5fcb7c1cdc705.jpeg)

1.  **Introduction**

In the previous experiments, we learned to turn on or turn off the LED,
adjust the brightness of a light through PWM, and how to use the
infrared receiver module. So in this experiment, we use an infrared
remote control to control an LED module.

When we receive a value, we set the PWM value by the corresponding
button value, thus you can adjust the brightness. Control the LED to
turn on or turn off is in the same way. If we want to use the same
button to control the LED to turn on or turn off, we can achieve it
through the code.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/f0ef7a5a2e7eebb09e91f73cb2a6caf3.png" style="width:0.67361in;height:0.89792in" alt="白色LED模块" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d2903250f8e18898973c545ca497393.png" style="width:0.67639in;height:0.89375in" alt="红外接收模块" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td><p>Keyestudio</p>
<p>Purple LED Module*1</p></td>
<td>Keyestudio IR Receiver*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94583in;height:0.44375in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/10ccf14d80feba64bba0c1eacd02b09d.png" style="width:1.3in;height:0.62847in" alt="遥控器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
<td></td>
</tr>
<tr class="even">
<td>Micro USB*1</td>
<td>IR Remote Control*1</td>
<td>3P Dupont Wire*2</td>
<td></td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/e00f371661e0fa08c98e84d3d22a110c.png)

**4.Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : IR Control LED</p>
<p>* Description : Remote controls LED on and off</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;IRremoteESP8266.h&gt;</p>
<p>#include &lt;IRrecv.h&gt;</p>
<p>#include &lt;IRutils.h&gt;</p>
<p>const uint16_t recvPin = 15; // Infrared receiving pin 15</p>
<p>IRrecv irrecv(recvPin); // Create a class object used to receive class</p>
<p>decode_results results; // Create a decoding results class object</p>
<p>int led = 4;//LED connect to GP4</p>
<p>void setup() </p>
<p>////////////////////</p>
<p>void loop() </p>
<p>}</p>
<p>void handleControl(unsigned long value) </p>
<p>else if (value == 0xFF9867) // Receive the number '2'</p>
<p></p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Code Explanation**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully, we will
use a USB cable to power on. Open the serial monitor and set the baud
rate to 9600. We need to press the reset button on the ESP32, then press
the button 1 of the remote, which will be displayed on the monitor, and
the LED will be on. Similarly, press the button 2 , the LED will be off.

![](media/f3fdb954551ed5006b6b67cee76c466d.png)

### Project 52: Heat Dissipation Device

![](media/24a7a2d97a50c2f3fc4ab893d3aee394.jpeg)

**1. Description**

We will use a temperature sensor and some modules to make a smart
cooling device in this experiment. When the ambient temperature is
higher than a certain value, the motor is turned on, thereby reducing
the ambient temperature and achieving the heat dissipation effect. Then
display the temperature value in the four-digit segment display.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6c2548137a8c675141b83227beeb2eb9.png" style="width:0.82917in;height:0.70694in" alt="KS6038 130电机驱动模块" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/f47b077303226cce504ea7734826dfc9.png" style="width:0.94514in;height:0.52569in" alt="四位数码管模块" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Keyestudio 130 Motor*1</td>
<td>Keyestudio TM1650Segment Display*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/d892bdfa25f3544ae28aa16d8b1b3c50.png" style="width:0.98056in;height:0.73542in" alt="18B20温度传感器" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.98958in;height:0.36042in" alt="3p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/269c154eda332be03643bada56070124.jpeg" style="width:0.91458in;height:0.35625in" alt="4p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94722in;height:0.41875in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>Keyestudio 18B20 Temperature Sensor*1</td>
<td>3P Dupont Wire*1</td>
<td>4P Dupont Wire*2</td>
<td>Micro USB*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/b65d826ca481982fed0212dba2957c7c.jpeg" style="width:1.57361in;height:1.13611in" alt="123" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/a815c48437199c6ab79d74cd2d583de0.png" style="width:0.44792in;height:2.0625in" /></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>6 AA Battery Holder*1</td>
<td>AA Battery(not included)*6</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/ab795f487c4b10fe6ff36a82e075475a.png)

**4.Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : heat abstractor</p>
<p>* Description : DS18B20 controls a four digit tube and a motor that simulates Heat Abstractor</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;DS18B20.h&gt;</p>
<p>#include "TM1650.h" //Import the TM1650 library file</p>
<p>//The two ports are GP21 and GP22</p>
<p>#define DIO 21</p>
<p>#define CLK 22</p>
<p>TM1650 DigitalTube(CLK,DIO);</p>
<p>//ds18b20 pin to 13</p>
<p>DS18B20 ds18b20(13);</p>
<p>void setup() </p>
<p>// DigitalTube.displayDot(1,true); //Bit0 display dot. Use before displayBit().</p>
<p>DigitalTube.displayBit(1,0); //DigitalTube.Display(bit,number); bit=0---3 number=0---9</p>
<p>//Motor is connected to 15 4</p>
<p>pinMode(15, OUTPUT);</p>
<p>pinMode(4, OUTPUT);</p>
<p>}</p>
<p>void loop()  else </p>
<p>delay(100);</p>
<p>}</p>
<p>void displayFloatNum(float temp)</p>
<p>if(dat%10000/1000 != 0)</p>
<p>if(dat%1000/100 != 0)</p>
<p>DigitalTube.clearBit(1);</p>
<p>DigitalTube.clearBit(2);</p>
<p>DigitalTube.clearBit(3);</p>
<p>DigitalTube.displayBit(4, dat%100/10);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

5.  **Code Explanation**

The setting of variables and the storage of detection values are the
same as what we learned earlier. We also set a temperature threshold and
control the rotation of the motor when the threshold is exceeded, and
then we use the digital tube to display the temperature value.

6.  **Test Result**

Connect the wires according to the experimental wiring diagram and power
on. Switch the DIP switch on the ESP32 expansion board to the ON end,
compile and upload the code to the ESP32. After uploading successfully,
we can see the temperature of the current environment (unit is Celsius)
on the four-digit segment display, as shown in the figure below. If this
value exceeds the value we set, the fan will rotate to dissipate heat.

### Project 53: Intelligent Entrance Guard System

![](media/6dbae618241cc2dd3060dc4abf94f3a6.jpeg)

1.  **Description**

In this project, we use the RFID522 card swiping module and the servo to
set up an intelligent access control system. The principle is very
simple.We use RFID522 swipe card module, an IC card or key card to
unlock.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/c9020c6015e55923afec197ab9d03fae.png" style="width:1.05278in;height:0.48819in" alt="4" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/decf08b83c5594f7f1e51f6e93051f4b.png" style="width:1.30208in;height:0.69722in" alt="3 (2)" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/2a40c5c68dc7802d29bcf719bb688f64.png" style="width:1.3in;height:0.81806in" alt="门卡2" /></td>
</tr>
<tr class="even">
<td>ESP32 Board*1</td>
<td>ESP32 Expansion Board*1</td>
<td>Key*1</td>
<td>IC Card*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/a96fbaff92e93d2804dac04e0480dc67.png" style="width:1.18194in;height:0.65972in" alt="RFID刷卡" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/b9a96e60ed3aee985db5d4dcaf9bf38b.png" style="width:1.05833in;height:1.05069in" alt="舵机" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/269c154eda332be03643bada56070124.jpeg" style="width:0.91458in;height:0.35625in" alt="4p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.94722in;height:0.41875in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>Keyestudio RFID Module*1</td>
<td>Servo*1</td>
<td>4P Dupont Wire*1</td>
<td>Micro USB*1</td>
</tr>
</tbody>
</table>

**3.Connection Diagram**

![](media/c8af51059d15f075c781609e64efa43a.png)

**4. Test Code**

**Note: Different RFID-MFRC522 IC cards and keys have diverse values.You
can substitute your own IC cards and keys values for the corresponding
values read by the RFID-MFRC522 module in the program, otherwise the
servo can’t be controlled when uploading the test code to the ESP32.**

**For example: You can replace the rfid\_str of the**
![](media/91ad84c2093215062451bfa29efdf1a5.png) **in the program code with your own IC cards
and keys values read by the RFID-MFRC522 module.**

<table>
<tbody>
<tr class="odd">
<td><p>//*************************************************************************************</p>
<p>/*</p>
<p>* Filename : Intelligent_access_control</p>
<p>* Description : RFID controlled steering gear simulated door opening</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Wire.h&gt;</p>
<p>#include "MFRC522_I2C.h"</p>
<p>// IIC pins default to GPIO21 and GPIO22 of ESP32</p>
<p>// 0x28 is the i2c address of SDA, if doesn't match，please check your address with i2c.</p>
<p>MFRC522 mfrc522(0x28); // create MFRC522.</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>Servo myservo; // create servo object to control a servo</p>
<p>int servoPin = 15; // Servo motor pin</p>
<p>String rfid_str = "";</p>
<p>void setup() </p>
<p>void loop() </p>
<p>// select one of door cards. UID and SAK are mfrc522.uid.</p>
<p>// save UID</p>
<p>rfid_str = ""; //String emptying</p>
<p>Serial.print(F("Card UID:"));</p>
<p>for (byte i = 0; i &lt; mfrc522.uid.size; i++) </p>
<p>Serial.println(rfid_str);</p>
<p>if (rfid_str == "edf7945a" || rfid_str == "4c96b6e") </p>
<p>}</p>
<p>void ShowReaderDetails() </p>
<p>}</p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

5.  **Code Explanation**

In the previous experiment, our card swipe module has tested the
information of IC card and key. Then we use this corresponding
information to control the door.

6.  **Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Open the serial monitor and set the baud
rate to 9600.

We need to press the reset button on the ESP32, when we use the IC card
or blue key to swipe the card, the monitor displays the card and the key
information and “open the door”, at the same time, the servo rotates to
the corresponding angle to simulate opening the door.

![](media/dcab433d9b0d267837296f0d3cf7faec.png)

### Project 54：Bluetooth

This chapter mainly introduces how to use the bluetooth of ESP32 for
simple data transmission with mobile phone. Project 60.1 is conventional
bluetooth, and Project 60.2 is bluetooth control LED.

### Project 54.1：Classic Bluetooth

1.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.83611in;height:0.44792in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" alt="IMG_256" /></td>
</tr>
<tr class="even">
<td>Micro USB*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

In this experiment, we need to use a BT dobbed serial terminal to make
an experiment. If you haven’t install it, please click the installation:
<https://www.appsapk.com/serial-bluetooth-terminal/> .

![](media/7b98d6708888b0a6f38f85ffca484857.png)

2.  **Component Knowledge**

Bluetooth is a short-distance communication system that can be divided
into two types, namely low power bluetooth (BLE) and classic bluetooth.
There are two modes for simple data transfer: master mode and slave
mode. 

**Master Mode**: In this mode, work is done on the master device and can
be connected to the slave device. When the device initiates a connection
request in the main mode, information such as the address and pairing
password of other bluetooth devices are required.  Once paired, you can
connect directly to them.  

**Slave Mode**: A bluetooth module in the slave mode can only accept
connection requests from the host, but cannot initiate connection
requests. After being connected to a host device, it can send and
receive data through the host device . Bluetooth devices can interact
with each other, when they interact, the bluetooth device in the main
mode searches for nearby devices. While a connection is established,
they can exchange data. For example, when a mobile phone exchanges data
with ESP32, the mobile phone is usually in master mode and the ESP32 is
in slave mode.  

![](media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

master mode slave mode

**3. Wiring Diagram**

We can use a USB cable to connect ESP32 mainboard to the USB port on the
Raspberry Pi.

![](media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

1.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Classic Bluetooth--SerialToSerialBT</p>
<p>* Description : ESP32 communicates with the phone by bluetooth and print phone's data via a serial port</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "BluetoothSerial.h"</p>
<p>BluetoothSerial SerialBT;</p>
<p>String buffer;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>if (SerialBT.available()) </p>
<p>delay(20);</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**5. Test Result**

Compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set the baud rate to 115200. We need to press the reset
button on the ESP32, when you see the serial prints the character, as
shown below, it means that the ESP32's bluetooth is waiting for
connection with a phone. (If open the serial monitor and set the baud
rate to 115200, the information is not displayed, please press the
button RESET of the ESP32)

![](media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](media/e414dec6ce31d365a37ebca2ee724ac8.png)

Ensure that your mobile phone bluetooth is enabled and the bluetooth
application of "Serial Bluetooth Terminal" is installed.  

![](media/382529edef3989e60264cad217d88e6f.png)

Click“Search”，search for the nearby bluetooth and select to connect
the“ESP32 test”.

![](media/0608c9a78b5f56d4c8f1994c55c9cd46.png)

Open the software APP and click the left side of the terminal, select
"Devices".

![](media/32b8c3abd51fc538ba854b1d72e1165e.png)

If you select ESP32test in classic Bluetooth mode, a successful
connection message will appear as shown below.  

![](media/00f9b335cb512704763e3621e7c598b2.png)

Data can be transferred between your phone and Raspberry Pi via ESP32
now.  

Send “Hello！”, When the Raspberry Pi receives it, which will reply with
"Hi\!".

![](media/9d95fba12c5ba1e8c0bb3da8965e6a68.png)

![](media/4f4e6b4e45996ccbde4da17219f02d00.png)

### Project 54.2：Bluetooth Control LED

**1. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:2.17847in;height:1.0625in" alt="ks0413-3(1)" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/6d96c844b0260ad712130945d692a7a2.jpeg" style="width:1.34444in;height:1.02986in" alt="ks0465-1" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>ESP32 Expansion Board*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/12ecb079cf6481a6f0f04d6b7bb31fd8.png" style="width:0.70417in;height:0.93889in" alt="白色LED模块" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/0d81e07a0f67700c5a396fc7e1e614e1.jpeg" style="width:0.88056in;height:0.32083in" alt="3p线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.83611in;height:0.44792in" alt="USB线" /></td>
</tr>
<tr class="even">
<td>Keyestudio Purple LED Module*1</td>
<td>3P Dupont Wire*1</td>
<td>Micro USB*1</td>
</tr>
</tbody>
</table>

2.  **Connection Diagram**
    
    ![](media/a4c49636627363f7413e03a917c02fac.png)

3.  **Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : Bluetooth Control LED</p>
<p>* Description : The phone controls esp32's led via bluetooth.</p>
<p>When the phone sends "LED_on," ESP32's LED lights turn on.</p>
<p>When the phone sends "LED_off," ESP32's LED lights turn off.</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include "BluetoothSerial.h"</p>
<p>#include "string.h"</p>
<p>#define LED 15</p>
<p>BluetoothSerial SerialBT;</p>
<p>char buffer[20];</p>
<p>static int count = 0;</p>
<p>void setup() </p>
<p>void loop() </p>
<p>if(count&gt;0)</p>
<p>if(strncmp(buffer,"led_off",7)==0)</p>
<p>count=0;</p>
<p>memset(buffer,0,20);</p>
<p>}</p>
<p>}</p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**4. Test Result**

Connect the wires according to the experimental wiring diagram, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. The APP operation is the same as the
project 54.1 We need to press the reset button on the ESP32, if you want
to make the external LED on and off, simply change the sending content
to "LED\_on" and "LED\_OFF". Moving the APP to send data:

![](media/21ec63e3abe43a119ab8a3d4634894f0.png)

The serial monitor will display as follows:

![](media/5f7f8afb264d781931c9afe006cbc539.png)

![](media/334d5037b44c03ebfe7f9b1789f2366e.png)

![](media/fb6c21908efd4fe455cc00ad87ebfbe0.png)

**Note:** If the sent content is not "LED-on 'or" LED-off ", the status
of the LED will not change. If the LED is on, it remains on when
irrelevant content is received;Conversely, if the LED is off, it
continues to be off when irrelevant content is received.   

### Project 55：WiFi Station Mode

1.  **Description**

ESP32 has three different WiFi modes: Station mode, AP mode and
AP+Station mode. All WiFi programming projects must be configured with
WiFi running mode before using, otherwise the WiFi cannot be used. In
this project, we are going to learn the WiFi Station mode of the ESP32.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.83611in;height:0.44792in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" alt="IMG_256" /></td>
</tr>
<tr class="even">
<td>Micro USB*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

Plug the ESP32 to the USB port of your Raspberry Pi.

![](media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**4. Component Knowledge**

**Station mode：**

When setting Station mode, the ESP32 is taken as a WiFi client. It can
connect to the router network and communicate with other devices on the
router via a WiFi connection. As shown in the figure below, the PC and
the router have been connected. If the ESP32 wants to communicate with
the PC, the PC and the router need to be connected.

![](media/f74baff97695aa2ee33a8c19370d2547.png)

**5. Test Code**

Since WiFi names and passwords vary from place to place, thereby users
need to enter the correct WiFi names and passwords in the box shown
below before the program code runs.  

![](media/c3cb845e23d9d718cfc6ac62f4474c4a.png)

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi Station</p>
<p>* Description : Connect to your router using ESP32</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;WiFi.h&gt; //Include the WiFi Library header file of ESP32.</p>
<p>//Enter correct router name and password.</p>
<p>const char *ssid_Router = "ChinaNet-2.4G-0DF0"; //Enter the router name</p>
<p>const char *password_Router = "ChinaNet@233"; //Enter the router password</p>
<p>void setup()</p>
<p>Serial.println("\nConnected, IP address: ");</p>
<p>Serial.println(WiFi.localIP());//Serial monitor prints out the IP address assigned to ESP32.</p>
<p>Serial.println("Setup End");</p>
<p>}</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

After entering the correct WiFi names and passwords, compile and upload
the code to the ESP32. After uploading successfully，we will use a USB
cable to power on. Open the serial monitor and set the baud rate to
115200. When the ESP32 successfully connects to ssid\_WiFi, the serial
monitor prints out the IP address, then monitor will display as follows:
(If open the serial monitor and set the baud rate to 115200, the
information is not displayed, please press the button RESET of the
ESP32)

![](media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](media/41785c9fa9c496b8630ba0971ae7e7c3.png)

### Project 56：WIFI AP Mode

1.  **Description**

ESP32 has three different WiFi modes: Station mode, AP mode and
AP+Station mode. All WiFi programming projects must be configured with
WiFi running mode before using, otherwise the WiFi cannot be used. In
this project, we are going to learn the WiFi AP mode of the ESP32.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:0.83611in;height:0.44792in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" alt="IMG_256" /></td>
</tr>
<tr class="even">
<td>Micro USB*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

Plug the ESP32 mainboard to the USB port of your Raspberry Pi

![](media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**4. Component Knowledge**

**AP Mode:**

When setting AP mode, a hotspot network will be created, waiting for
other WiFi devices to connect. As shown below;

Take the ESP32 as the hotspot, if a phone or PC needs to communicate
with the ESP32, it must be connected to the ESP32's hotspot.
Communication is only possible after a connection is established via the
ESP32.

![](media/35d90f1ce10814ea1897ba63f8bd7ad9.png)

**5.Test Code**

Before the program code runs, you can make any changes to the ESP32 AP
name and password in the box as shown below, but in a default
circumstance, it doesn’t need to modify.

![](media/01dfd7f9005c516dffcb0701f9899a30.png)

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi AP</p>
<p>* Description : Set ESP32 to open an access point</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;WiFi.h&gt; //Include the WiFi Library header file of ESP32.</p>
<p>const char *ssid_AP = "ESP32_WiFi"; //Enter the router name</p>
<p>const char *password_AP = "12345678"; //Enter the router password</p>
<p>IPAddress local_IP(192,168,1,108);//Set the IP address of ESP32 itself</p>
<p>IPAddress gateway(192,168,1,1); //Set the gateway of ESP32 itself</p>
<p>IPAddress subnet(255,255,255,0); //Set the subnet mask for ESP32 itself</p>
<p>void setup()else</p>
<p>Serial.println("Setup End");</p>
<p>}</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

![](media/1fd21fafd84d2b529931a89d21a03d6a.png)

**6. Test Result**

Compile and upload the code to the ESP32. After uploading
successfully，we will use a USB cable to power on. Open the serial
monitor and set the baud rate to 115200, then monitor will display as
follows: (If open the serial monitor and set the baud rate to 115200,
the information is not displayed, please press the button RESET of the
ESP32)

![](media/6facc59811adf709e5471fea1301205f.png)

When observing the printed information of the serial port monitor, turn
on the WiFi scanning function of the mobile phone, you can see the
ssid\_AP on ESP32, which is dubbed "ESP32\_Wifi" in this program code.
You can connect to it either by typing the password "12345678" or by
modifying the program code to change its AP name and password.  

![](media/3e0ad895bea7f5100cc02a415adcace7.png)

### Project 57：WIFI AP+Station Mode

1.  **Description**

In this project, we are going to learn the AP+Station mode of the ESP32.

**2. Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/edbfec59fe015bd9987e4b4d542b466d.png" style="width:1.53889in;height:0.825in" alt="USB线" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" alt="IMG_256" /></td>
</tr>
<tr class="even">
<td>MicroUSB Cable*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

**3. Wiring Diagram**

Plug the ESP32 mainboard to the USB port of your Raspberry Pi

![](media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

**4. Component Knowledge**

**AP+Station mode**

In addition to the AP mode and the Station mode, **AP+Station mode** can
be used at the same time. Turn on the Station mode of the ESP32, connect
it to the router network, and it can communicate with the Internet
through the router. Then turn on the AP mode to create a hotspot
network. Other WiFi devices can be connected to the router network or
the hotspot network to communicate with the ESP32.

**5. Test Code：**

Before the program code runs, you need to modify the ssid\_Router,
password\_Router, ssid\_AP and password\_AP, as shown in the box below:

![](media/481fc26b5f53389ff501a1bfd1d7921e.png)

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi AP+Station</p>
<p>* Description : ESP32 connects to the user's router, turning on an access point</p>
<p>* Auther : http//www.keyestudio.com</p>
<p>*/</p>
<p>#include &lt;WiFi.h&gt;</p>
<p>const char *ssid_Router = "ChinaNet-2.4G-0DF0"; //Enter the router name</p>
<p>const char *password_Router = "ChinaNet@233"; //Enter the router password</p>
<p>const char *ssid_AP = "ESP32_WiFi"; //Enter the router name</p>
<p>const char *password_AP = "12345678"; //Enter the router password</p>
<p>void setup()else</p>
<p>Serial.println("\nSetting Station configuration ... ");</p>
<p>WiFi.begin(ssid_Router, password_Router);</p>
<p>Serial.println(String("Connecting to ")+ ssid_Router);</p>
<p>while (WiFi.status() != WL_CONNECTED)</p>
<p>Serial.println("\nConnected, IP address: ");</p>
<p>Serial.println(WiFi.localIP());</p>
<p>Serial.println("Setup End");</p>
<p>}</p>
<p>void loop() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

**6. Test Result**

Ensure that the code in the program has been modified correctly, compile
and upload the code to the ESP32. After uploading successfully，we will
use a USB cable to power on. Open the serial monitor and set the baud
rate to 115200, then monitor will display as follows: (If open the
serial monitor and set the baud rate to 115200, the information is not
displayed, please press the button RESET of the ESP32)

![](media/1fd21fafd84d2b529931a89d21a03d6a.png)

![](media/67a927c029230fd16203e2903d2b6a0b.png)

Open the WiFi scanning function of the mobile phone, you can see the
ssid\_AP.

![](media/3e0ad895bea7f5100cc02a415adcace7.png)

### Project 58: Comprehensive Experiment

![](media/c92bfcbd1ecd7fe91198066d0c9a4df6.jpeg)

1.  **Introduction**

We did a lot of experiments, and for each one we needed to re-upload the
code, so can we achieve different functions through an experiment? In
this experiment, we will use an external button module to achieve
different functions.



**3.Wiring Diagram：**

![](media/9a02c45a8c8689060b102bdc742432f2.png)

**4.Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************</p>
<p>/*</p>
<p>* Filename : Comprehensive experiment</p>
<p>* Description : Multiple sensors/modules work together</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include "xht11.h"</p>
<p>//xht11 to gpio15</p>
<p>xht11 xht(15);</p>
<p>//rgb is connected to 4,0,2</p>
<p>int ledPins[] = ; //define red, green, blue led pins</p>
<p>const byte chns[] = ; //define the pwm channels</p>
<p>int red, green, blue;</p>
<p>//Rocker module port</p>
<p>int X = 35;</p>
<p>int Y = 34;</p>
<p>int KEY = 32;</p>
<p>//Potentiometer pin is connected to analog port 33</p>
<p>int resPin = 33;</p>
<p>//Trace sensor pin connected to IO port 14</p>
<p>int TrackingPin = 14;</p>
<p>//LED is Connected to GP5</p>
<p>#define PIN_LED 5 // the pin of the LED</p>
<p>#define CHAN 3</p>
<p>//Obstacle avoidance sensor is connected to GP27</p>
<p>int Avoid = 27;</p>
<p>//Ultrasonic sensor port</p>
<p>int Trig = 13;</p>
<p>int Echo = 12;</p>
<p>//Key module port</p>
<p>int button = 23;</p>
<p>int PushCounter = 0;//Store the number of times a key is pressed</p>
<p>int yushu = 0;</p>
<p>unsigned char dht[4] = ;//Only the first 32 bits of data are received, not the parity bits</p>
<p>bool ir_flag = 1;</p>
<p>float out_X, out_Y, out_Z;</p>
<p>void counter() </p>
<p>}</p>
<p>void setup() </p>
<p>}</p>
<p>void loop()  else if (yushu == 1)  else if (yushu == 2)  else if (yushu == 3) else if (yushu == 4)  else if (yushu == 5)  else if (yushu == 6) </p>
<p>}</p>
<p>//RGB</p>
<p>void yushu_0() </p>
<p>void setColor(byte r, byte g, byte b) </p>
<p>void yushu_1() </p>
<p>else </p>
<p>}</p>
<p>void yushu_2()  else </p>
<p>delay(1200);</p>
<p>}</p>
<p>void yushu_3() </p>
<p>void yushu_4() </p>
<p>void yushu_5() </p>
<p>else </p>
<p>delay(100);</p>
<p>}</p>
<p>void yushu_6() </p>
<p>float checkdistance() </p>
<p>//*************************************************************************************</p></td>
</tr>
</tbody>
</table>

**Code Explanation**

Calculate how many times the button is pressed, divide it by 7, and get
the remainder which is 0, 1 2, 3, 4, 5 , 6. According to different
remainders, construct seven unique functions to realize different
functions.

We can add or reduce sensors or modules.

**Test Result：**

Wire up, upload the code, power on, open the monitor and set baud rate
to 9600. At the beginning, the time of pressing buttons is 0 and
remainder is 0. Then RGB will flash.

Press the button, the RGB stops flashing, press once, the remainder is
1. If the tracking sensor doesn’t detect objects or only detect black
ones, val is 1 and monitor shows **1 Black**; if white objects are
detected, val is 0 and **0 White** is shown. As shown below;

![](media/c7e972b4fe36dca8ae346e8bfd1cb4ae.png)

Note: if a key is pressed, the time of pressing turns out to be 1. Open
the monitor, the program will reset, the time of pressing becomes into
0. You need to press keys to reset times of pressing keys.

Press a key twice, the time of pressing buttons is 2 and the remainder
is 2. Read temperature and humidity values. As shown below;

![](media/316547aa98106ac3a4d6678aefe4088c.png)

Press this key again, the time of pressing buttons is 3 and the
remainder is 3. Read digital values at x, y and z axis of the joystick
module. As shown below;

![](media/b7cf43d8aa18d17d424d6d45e2c0c84d.png)

Press the key for the fourth time, the remainder is 4. Then the
potentiometer can adjust the PWM value at the GPI05 port to control LED
brightness of the purple LED.

![](media/5cef554e481f1792a16fcff4858de6d5.png)

Press the key for the fifth time, the remainder is 5. Then the
ultrasonic sensor can detect obstacles, as shown below;

![](media/cdf416c04c3dd73993c36c06b4659a3a.png)

Press the key for the sixth time, the remainder is 6. Then the distance
away from obstacles will be shown, as shown below;

![](media/0efa68d63700482f58fb1b459b8bce15.png)

Press the key for seventh time and the remainder is 0. The RGB will
flash. If pressing keys continuously, remainders also change.

### Project 59: WiFi
**[Smart](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;) [Home](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)**

1.  **Description**

In the previous experiment, we have learned the WiFi Station mode, WiFi
AP mode and WiFi AP+Station mode of the ESP32. In this project, We will
use ESP32's WiFi Station mode to control the work of multiple
sensors/modules through APP connection with WiFi to achieve the effect
of WiFi smart home.


**3. Wiring Diagram：**

![](media/dc2a48d68547d18a47f6aeb898330956.png)

2.  **Install APP**

Android device (mobile phone/PC) APP:

We provide the Android APP
[installation](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)
[package](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)

![](media/8cdb2bdff2a0023a5023974e35b35185.png)

Now transfer the keyes wifi.apk file in the Android APP installation
package to the Android phone or PC, click the keyes wifi.apk file to
enter the installation page, click "ALLOW" key, and then click "INSTALL"
button. After installation, click "OPEN" button to enter the APP
interface.  

![](media/c2b3e3edeede8cc9ab3a253cc5dcab4e.png)

![](media/d620452a9d6188cb3946269510df5ae0.png)

![](media/b311329042f5bbd2880841127b91ebf8.png)

![](media/7c5cfc935371c8e2ab30e999775d5f8f.png)

![](media/d48c065ebaf1c5ca652eb72b15d3e596.png)

![](media/78c89b91c0af2268f6267813e7923a9b.png)

IOS (mobile phone /iPad)

1.  Open App Store

> ![](media/27924fdb3d67692df7c63d8d0fb72287.png)

B. Enter keyes link in the search box and click search, the download
interface appears. Click "![](media/962a57f92b78eea1f0e3e81463497a9c.png)" to download and
install the APP of the keyes link. The following operations are similar
to those of Android system. You can refer to the steps of Android
system.

**5. Test Code ：**

<table>
<tbody>
<tr class="odd">
<td><p>//**********************************************************************************</p>
<p>/*</p>
<p>* Filename : WiFi Smart Home.</p>
<p>* Description : WiFi APP controls Multiple sensors/modules work to achieve the effect of WiFi smart home.</p>
<p>* Auther : http//www.Keyestudio.com</p>
<p>*/</p>
<p>#include &lt;Arduino.h&gt;</p>
<p>#include &lt;WiFi.h&gt;</p>
<p>#include &lt;ESPmDNS.h&gt;</p>
<p>#include &lt;WiFiClient.h&gt;</p>
<p>#include "xht11.h"</p>
<p>//gpio27</p>
<p>xht11 xht(27);</p>
<p>unsigned char dht[4] = ;</p>
<p>#include &lt;ESP32Servo.h&gt;</p>
<p>Servo myservo;</p>
<p>int servoPin = 21;</p>
<p>#define Relay 4</p>
<p>#define IN1 2 //IN1 corresponds to IN+</p>
<p>#define IN2 15 //IN2 corresponds to IN-</p>
<p>#define trigPin 12</p>
<p>#define echoPin 13</p>
<p>int distance1;</p>
<p>String dis_str;</p>
<p>int ip_flag = 1;</p>
<p>int ultra_state = 1;</p>
<p>int temp_state = 1;</p>
<p>int humidity_state = 1;</p>
<p>String item = "0";</p>
<p>const char* ssid = "ChinaNet-2.4G-0DF0"; //the name of user's wifi</p>
<p>const char* password = "ChinaNet@233"; //the password of user's wifi</p>
<p>WiFiServer server(80);</p>
<p>String unoData = "";</p>
<p>void setup() </p>
<p>Serial.println("");</p>
<p>Serial.print("Connected to ");</p>
<p>Serial.println(ssid);</p>
<p>Serial.print("IP address: ");</p>
<p>Serial.println(WiFi.localIP());</p>
<p>server.begin();</p>
<p>Serial.println("TCP server started");</p>
<p>MDNS.addService("http", "tcp", 80);</p>
<p>digitalWrite(IN1, LOW);</p>
<p>digitalWrite(IN2, LOW);</p>
<p>digitalWrite(Relay, LOW);</p>
<p>pinMode(trigPin, OUTPUT);</p>
<p>pinMode(echoPin, INPUT);</p>
<p>}</p>
<p>void loop() </p>
<p>while(client.connected() &amp;&amp; !client.available())</p>
<p>String req = client.readStringUntil('\r');</p>
<p>int addr_start = req.indexOf(' ');</p>
<p>int addr_end = req.indexOf(' ', addr_start + 1);</p>
<p>if (addr_start == -1 || addr_end == -1) </p>
<p>req = req.substring(addr_start + 1, addr_end);</p>
<p>item=req;</p>
<p>Serial.println(item);</p>
<p>String s;</p>
<p>if (req == "/")</p>
<p></p>
<p>else if(req == "/btn/0")</p>
<p></p>
<p>else if(req == "/btn/1")</p>
<p></p>
<p>else if(req == "/btn/2")</p>
<p></p>
<p>else if(req == "/btn/3")</p>
<p></p>
<p>else if(req == "/btn/4")</p>
<p></p>
<p>else if(req == "/btn/5")</p>
<p></p>
<p>else if(req == "/btn/6")</p>
<p></p>
<p>while(ultra_state&gt;0)</p>
<p></p>
<p>}</p>
<p>else if(req == "/btn/7")</p>
<p></p>
<p>else if(req == "/btn/8")</p>
<p></p>
<p>while(temp_state&gt;0)</p>
<p></p>
<p>temp_state = 0;</p>
<p>}</p>
<p>}</p>
<p>else if(req == "/btn/9")</p>
<p></p>
<p>else if(req == "/btn/10")</p>
<p></p>
<p>while(humidity_state &gt; 0)</p>
<p></p>
<p>humidity_state = 0;</p>
<p>}</p>
<p>}</p>
<p>else if(req == "/btn/11")</p>
<p></p>
<p>//client.print(s);</p>
<p>client.stop();</p>
<p>}</p>
<p>int checkdistance() </p>
<p>//**********************************************************************************</p></td>
</tr>
</tbody>
</table>

Note: You need to ![](media/9ddee42d7e41abd8a6db60d447cd9f68.png)change the Wifi name and
default Wifi password of the experimental code to your own Wifi name and
Wifi password. 

**Test Result**

After the code has been modified correctly, connect the external power
supply and power on. Turn the DIP switch ON the ESP32 expansion board to
the ON end, compile and upload the code to the ESP32 mainboard.（If
uploading the code is not successful，hold down the Boot
button![](media/d09c4a31563f04a42d451e7bc1a5fb8a.png),
release it when the upload progress percentage appears.)

Open the monitor and set baud rate to 115200. Then the monitor can print
the WiFi IP address.

If no information is displayed, you can press the RESET button

![](media/9c314fc6b06d9f06e9ed203d5bb8dd98.jpeg)

Open WiFi APP, enter the detected WIFI IP address in the text box in
front of the WIFI button (for example, the IP address detected by the
serial monitor above is 192.168.0.156). Next, click the WIFI button to
connect to WIFI, at the same time, the corresponding WiFi IP address
will be displayed in the text box :“Hello from ESP32 at 192.168.0.156”,
then the APP has connected to WiFi.(WiFi IP address sometimes changes,
if the original IP address can not use, you need to re-check it.)  

![](media/ac1bd20a153c3abc5c0c62a416446f52.jpeg)

After the APP is connected to WiFi, the following operations are
performed:

1)  Click![](media/5b9754cb6ec4f995c9eada1da89a8969.png)button, the relay will be opened, the
    APP will display![](media/505b00b0e23f6498c5d51d5d775c8fcb.png)，and the indicator lights up
    on the module. Click![](media/5b9754cb6ec4f995c9eada1da89a8969.png)again, the relay will be
    closed , the APP will display ![](media/deb54a77cdcc87d7569e8b8e46de129f.png)，and the
    indicator on the module is off.

2)  Click![](media/c54f78d819d4e6a8310eaeb79ff66910.png)button，the servo rotates 180°，the APP
    will display
    ![](media/c54f78d819d4e6a8310eaeb79ff66910.png)again，the
    APP will display ![](media/dee12bee3866542bfe5d70a539f79f0b.png)，the servo rotates 0°.

3)  Click![](media/5490abf5b2f8a1d9cea3055da07c251c.png)button，the motor（with small fan
    blades）rotates，the APP will display
    ![](media/5490abf5b2f8a1d9cea3055da07c251c.png)again，close
    the motor，the APP will display ![](media/de6da02ede6d63344546173d36bf5371.png)；

4)  Click![](media/95bfbe879d2391e4e48dcae085abe5a6.png)button，the ultrasonic sensor detects
    the distance, put an object in front of the ultrasonic sensor, the
    APP will display

5)  ![](media/e431e1b9c95bed37b053ae9617f93676.png), the distance between the object and the
    ultrasonic sensor is 14cm；click ![](media/95bfbe879d2391e4e48dcae085abe5a6.png) again, turn
    off the sensor, the APP will display
    ![](media/08c8a35841b31fa4b5327fb7b23a7af5.png)button，the
    temperature and humidity sensor measures the temperature in the
    environment, the APP will display ![](media/0aafd0af43f80b692eca3d6732b551b2.png)，the
    ambient temperature is 28 ° C., click![](media/08c8a35841b31fa4b5327fb7b23a7af5.png) again,
    turn off the sensor，the APP will display ![](media/82887a1385bc7411ecbdc41f60ebd450.png).

6)  Click ![](media/d8e3463ab2f644b3300cdeaa2a68e4c2.png) button，the temperature and humidity
    sensor measures the humidity in the environment,，the APP will
    display ![](media/320b86323631e095db330a22ca97bad7.png), the ambient humidity is
    52%；click![](media/d8e3463ab2f644b3300cdeaa2a68e4c2.png)again，turn off the sensor, the
    APP will display ![](media/adc18d06e626af067286da9040c20252.png).


## 6. Resources
https://fs.Keyestudio.com/KS5005-5006



