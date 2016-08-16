NGIMU-Teensy-IO-Expansion-Example
=================================

This is an example project demonstrating how a Teensy can be used with the NGIMU auxiliary serial in *OSC passthrough* mode to send/receive custom OSC messages to provide access to the Teensy I/O and peripherals through the NGIMU.  OSC messages generated by the Teensy are forwarded by the NGIMU to the host alongside it's own OSC messages; and OSC messages sent by the host to the NGIMU that are not recognised are forwarded to the Teensy.  The example setup uses a [Teensy 3.2](https://www.pjrc.com/store/teensy32.html), an [analogue joystick](https://www.sparkfun.com/products/9032), 3 [push buttons](http://www.mouser.co.uk/search/ProductDetail.aspx?R=0virtualkey0virtualkeyFSM4JAH), and [piezo transducer](https://www.sparkfun.com/products/10293).

This example is intended to serve as a template for user projects.  In most cases, only the `Receive.cpp` and `Send.cpp` files need to be modified.  The auxiliary serial baud rate can be increased in the NGIMU settings and `setup()` function in the `NGIMU-Teensy-IO-Expansion-Example.ino` to achieve higher throughput and lower latency.

OSC messages send by the Teensy
-------------------------------
* `/teensy/joystick/xy` - Contains the analogue joystick x and y values.  Sent continuously at 10 Hz.
* `/teensy/joystick/button` - Contains no arguments.  Sent each time the joystick button is pressed.
* `/teensy/counter` - Contains a counter value that increments each time the message is sent.  Sent continuously at 1 Hz.
* `/teensy/button/a` - Contains no arguments.  Sent each time button A is pressed.
* `/teensy/button/b` - Contains no arguments.  Sent each time button B is pressed.
* `/teensy/button/b` - Contains no arguments.  Sent each time button C is pressed.
* `/error` - Contains an error message string argument.  Sent if invalid OSC packet is received by the Teensy.

OSC messages received by the Teensy
-----------------------------------
* `/led` - Contains one value to turn the Teensy on-board LED on/off.
* `/tone` - Contains one value to set the frequency the piezo transducer

Teensy board connections
------------------------
* 3V3 - NGIMU auxiliary serial interface 3.3 V output
* GND - NGIMU auxiliary serial interface ground
* RX1 - NGIMU auxiliary serial interface TX
* TX1 - NGIMU auxiliary serial interface RX
* 9 - Piezo transducer
* 10 - Button A
* 11 - Button B
* 12 - Button C
* A0 - Joystick HORZ
* A1 - Joystick VERT
* 16 - Joystick SEL
