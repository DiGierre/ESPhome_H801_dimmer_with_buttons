# ESPhome_H801_dimmer_with_buttons
ESPhome yaml for a 2 channel DC monochromatic dimmer with control buttons and some extras.

What is ESPhome? See [here](https://esphome.io). <BR><BR>
The H801 is a cheap esp8266 based 5 channel (RGBWW) dimmer. I am going to use this in my kitchen for the ceiling and cabinet LED lights. They need to be locally controlled through push buttons. These are already integrated into the wall as part of the existing installation. I use the Gira brand and in my case, the kitchen is already prepared for this (separate DC low voltage cables inside the wall). In addition I also want it controllable through the home automation of course. At present I am using Domoticz.

More info on the H801 can be found on the [ESPhome](https://esphome.io/cookbook/h801.html) site, on [Revspace](https://revspace.nl/H801) (Dutch only) and by [Tinkerman](https://tinkerman.cat/post/closer-look-h801-led-wifi-controller) (who btw also has great ESP8266 firmware, ESPURNA).

<B>Hardware setup</B>:

- 2 x PWM outputs to control two strings of LED lights
- 1 x Switch output to switch 12V (I have a 12V Internet radio / smart speaker that has no power off button so I want to control the power)
- 2 x push buttons for the dimmer (one per light)
- 1 x push button to control the switch
- 1 x active buzzer (defined as a light output) to get audible feedback for events. The buzzer is connected to 12V through a resistor

<B>Dimmer button behaviour</B>:

- Single click: Toggle power of the light
- Double Click: Toggle between Max brightness and min brightness
- Hold: Toggle between dimming up and dimming down. While dimming, when max or min brightness is exceeded beep the buzzer once

In the YAML file you of course have to make the changes for SSID, passwords etc. and comment/uncomment what you do/don't need.

<B>ToDo</B>:
- Define light effects so you can e.g. blink the lights when the doorbell rings
- Define more buzzer effects so you can e.g. easily use the buzzer also for alarming
- Domoticz MQTT (potential candidate - I haven't made up my mind as I don't like how Domoticz deals with MQTT)
- ~~Dimming currently only works well with GAMMA correction = 1.0 set for the light due to the way brightness is read in the lambda (i have to figure this out)~~ Done in v0.4
- ~~In some use case the dimmer tries to dim up even when brightness = max, makes little sense so needs to be corrected~~ Done in v0.4

Here's how it looks on a breadboard for testing:

![alt text](H801_dimmer.jpg "ESPhome H801 based dimmer - breadboard test setup")

Note: the NodeMCU on the left is not part of the H801 test setup - it's just there by default....
