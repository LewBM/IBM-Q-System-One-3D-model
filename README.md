# Quantum
3D-printed model of IBM Q System One

OpenSCAD model of a 1cm to 1foot scale model of the IBM Q System One Quantum Computer.


## Print list...
Set one of the control variables to *true* and all the others to *false* at the top of the model file to render each component in turn.

*black filament*
+ base
+ base_lid
+ back_box  * print with raft *  
+ top_box  
+ top_box_lid (inverted)   
+ lid (inverted)  
+ lid_lower (inverted)  
+ lid plinth (inverted for smoothness)   

*white filament*
+ reflector in white (inverted)  
+ reflector_strip in white

*translucent filament*
+ diffuser in clear filament (inverted)

Cryostat needs to be a 25mm x 44mm silver tube (I used chrome-plated wardrobe rail)

Glass walls in 1mm acrylic (2 of each size)  
front and back: 92 x 81 mm  
left and right: 85 x 81 mm

## Exploded view of the printed components

![exploded view](https://github.com/andysc/Quantum/blob/master/images/System%20Q%20v4.5.png)

## The finished model

![IBM Q System One model](https://github.com/andysc/Quantum/blob/master/images/IMG_2301.jpeg)

## Electronics

The top box has a row of 8 neopixels (144 leds/metre) inside, with a Wemos ESP-8266 Arduino (in the back box) controlling it via MQTT over WiFi. There's a cut-out for a micro-USB cable to come out through the back of the base.  

For information about how to connect a Wemos with Neopixels using MQTT, see @DrLucyRogers' excellent article here:
[Connect your IoT "Thing" to the Cloud](https://www.rs-online.com/designspark/content-types/project/13257?lang=en)

![top box detail](https://github.com/andysc/Quantum/blob/master/images/IMG_2057.jpeg)

This is controlled by a node-red flow which controls the colours.

First it goes into a cool blue mode  

Then we run a Qiskit python script which connects to the real quantum computer (though the simulator takes much less time in the batch queue!), does a quantum coin flip, then returns an answer.

When we get the answer, we display a "superposed" state on the lights (red on one side and green on the other side, with a nice merge in the middle), pause for dramatic effect, then turn all red or all green, depending on whether it was heads or tails.
