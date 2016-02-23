# RaspberryPi2016
Contains the necessary files, and setup information for Grip on Pi

1. Obtain RaspberryPi 2 B+ with 4GB MicroSD (Class 4 or above).
2. Format MicroSD (Fat32)
3. Download https://downloads.raspberrypi.org/NOOBS_latest and follow the installation instructions.
4. In an SSH or Terminal do: 

```bash

pi@raspberry: sudo apt-get update && sudo apt-get install emacs

```
5. Follow the steps from "GRIP CORE" through "Using mjpg-streamer with a Raspberry Pi Camera" found here. Note use this link for the latest versions (which are needed): https://www.dropbox.com/sh/ixbcshu9astnfzj/AACRaa60bwZnwrTPhXUzjss3a?dl=0
   Also note that the steps around getting the deployment are incorrect, there should be a /home/pi/code where the grip folder goes.
6. Download start_grip.sh and start_mjpeg_streamer.sh and place them in /home/pi/vision
7. Download LEDgtg.py and place it in /home/pi/vision
8. Open up putty, SSH to the raspberry pi (Login with pi and raspberry).
9. In the terminal run this:
```bash
pi@raspberry: sudo emacs /etc/rc.local
```
And add the following lines between the existing uncommented lines and where it says "exit 0"
```bash
sleep 10
/home/pi/vision/start_mjpeg_streamer.sh &
sleep 5
/home/pi/vision/start_grip.sh &
sleep 15
python /home/pi/LEDgtg.py
```
10. Plug in the LED to pins 37 and 39, Camera and Ethernet Cable. 
11. Plug in power, and verify that approximately 30 seconds later the LED turns on. 

---

Now you can set the static IP address.
