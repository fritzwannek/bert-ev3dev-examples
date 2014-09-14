---
---

## bert-ev3dev-examples

### Examples of bits and pieces running at Jessie level 

Scripts are available also as zip/tgz on the  [releases page](https://github.com/BertLindeman/bert-ev3dev-examples/releases).

Issues can be found [here](https://github.com/BertLindeman/bert-ev3dev-examples/issues).

These shell-scripts are located on my EV3-brick at `/usr/local/bin`
but with some simple edits you can place them where **you** want them.
They are are meant to be run on a terminal session, like in an ssl-session.

1. Supporting scripts used by other scripts
    * [asciicolor](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/asciicolors) Creates some variables to ease using ANSI colors in shell script. E.G. red blue etc.
    * [bert_ev3dev_functions](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/bert_ev3dev_functions) Replaces asciicolor and adds some common functions.
2. Scripts related to managing the EV3-brick
    * [checkpower](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/checkpower) Add this script to a crontab to check for the battery voltage. On lower power the EV3-led on the left will blink green on lower voltage, then amber and eventually red (with a beep). 
    Uses [blinkvoltage](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/blinkvoltage)
    * [showactivity](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showactivity) Makes the right green led blink on I/O activity.
    * [stopmotors](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/stopmotors) Well, stops all motors.
3. Scripts discovering sensors and / or motors
    * [blinkleds](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/blinkleds) Simply blink the EV3 leds a few times.
    * [setled](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/setled) Script to set an EV3-led **red**, **green** or **amber** to **ON** or **OFF** and set a trigger for it. Do not confuse with **setleds** program to set keyboard leds.
    * [showleds](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showleds) Provides a small display of the status of the EV3-leds.
    * [showmotor](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showmotor) Finds the tacho-motor number for attached motors. Displays many fields related to the motor(s). Tested with EV3 (large and servo) and NXT motor.
    * [showpower](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showpower) Shows various fields related to the EV3-power.
    * [showsensors](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showsensors) Show data about connected sensors. Only *regular* sensors that are recognized are reported, I assume I2C sensors are not yet supported by the script.
    * [showsound](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/showsound) Shows a little info from the snd-legoev3 driver. (Not to be confused with the sound-sensor!)
    * [testmotor](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/testmotor) Test one motor. Too simple script, only uses a fixed suffix on ```/sys/class/tacho-motor/tacho-motor``` The kernel takes the *next* number if a motor is plugged in. Algorithm in **showmotor** is connecting motor port to tacho-motor suffix. You can call testmotor with one parameter: the number of the motor. E.g. ```testmotor 3```
    

### Have your EV3 report the IP-addresses by speach after boot
For this an update is needed to `/media/mmc_p1/ev3dev.rc.local`

Add the next lines to the bottom of `/media/mmc_p1/ev3dev.rc.local`

```
if [ -e /media/mmc_p1/tellIP ]; then
echo "Executing /media/mmc_p1/tellIP"
. /media/mmc_p1/tellIP
fi
```

and place the script [`tellIP`](https://github.com/BertLindeman/bert-ev3dev-examples/blob/master/tellIP)
in the same directory: `/media/mmc_p1/`

