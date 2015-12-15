Here's a few things that may help you build a wake-up light with a Particle.io Photon and a string of WS2811 ("NeoPixel") RGB LEDs.

For my wake-up light, I have connected 21 WS2811 LEDs to pin D6 of a Particle Photon. The Particle and power leads of the LED string feed off a 5V power adapter. The code that runs on the Particle is in `wakeuplight.ino`. It has two functions:

* Start a 30 minute light sequence, simulating dawn and sunrise, with function `wakeup`
* Set the LEDs to a specified color, with function `rgbColor` which accepts values of the format `123,45,56` denoting R, G, B bytes.

You can start the wake-up light from a cronjob, e.g., at 7 each morning

```
0 7 * * 1,2,3,4,5 curl https://api.particle.io/v1/devices/MYDEVICEID/wakeup -d access_token=MYACCESSTOKEN -d "args=blah"
```

You can control the wake-up light's color from a native color picker using the JavaScript in the included `index.html`. Make sure to set your device ID and access token in the HTML file.
