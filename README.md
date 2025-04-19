# EXPERIMENT-06-INTERFACING-CAMERA-MODULE-FOR-REAL-TIME-FEED-ON-RASPI

  
## AIM
To interface a camera module with Raspberry Pi and display real-time video feed using the camera module.

## APPARATUS REQUIRED
1.	Raspberry Pi (any model with CSI/USB port; Pi 3/4 recommended)
2.	Raspberry Pi Camera Module (CSI-based) or USB webcam
3.	MicroSD card with Raspberry Pi OS
4.	Monitor, HDMI cable, Keyboard, Mouse (for GUI)
5.	Power supply for Raspberry Pi
6.	Internet connectivity (optional for updates)

## THEORY
Raspberry Pi supports both CSI-based camera modules and USB webcams. The camera module communicates via the Camera Serial Interface (CSI) for high data throughput. When interfaced correctly and enabled via the configuration settings, the camera module can capture and stream video using libraries like picamera, OpenCV, or through command-line tools like libcamera. These tools allow developers and hobbyists to build applications ranging from surveillance systems to computer vision solutions.
HARDWARE INSTALLATION AND PROCEDURE 
Installing a camera on Raspberry Pi is straightforward once you find the location of the port:
Take the Raspberry Pi board in hand. Unplug all cables, the Raspberry Pi must be turned off and disconnected from the power supply.
Find the camera port on the Raspberry Pi (between the HDMI and audio ports).
You’ll find it easily because it’s the only one that fits the cable width, and it should be written “CAMERA” on the main board.
 

![image](https://github.com/user-attachments/assets/7fcce32e-cb17-456a-a1ed-310e5c239862)
Figure-01 Hardware setup of camera port

Before plugging in the cable, you may need to remove the plastic film and lightly pull the black plastic.
Plug the cable and push the black plastic to hold the cable inside.
Make sure to align both connectors on the same side (cable connectors on the HDMI port side, blue side of the ribbon towards the USB ports):
Connect to the Raspberry Pi via SSH (you can find useful tips here to connect via SSH from your computer).
If you prefer, you can use a terminal on the Raspberry Pi OS desktop, or even use the Lite version.
Start the raspi-config tool:
sudo raspi-config
Go to “Interface options” > “Camera”:
 
![image](https://github.com/user-attachments/assets/b9d9d5ad-7fe9-459a-a2ce-f8b405a7fd96)


	“Would you like the camera interface to be enabled?”.
Yes!
Exit raspi-config and accept to reboot the device.
![image](https://github.com/user-attachments/assets/a5e3eca1-2cde-4247-9278-7527450e94f1)

That’s all you need to do.
After the reboot, the camera is ready to use.
 
	
The first thing you can try is to simply take a picture of the image seen by the camera.
“rpicam-still” is the new command on Raspberry Pi OS Bookworm (replacing “raspistill” and “libcamera-still”).
It’s already installed on your system.
To use it, the basic command line is:
rpicam-still -o image.jpg
With -o you define the target file name (where the pictures will be saved). It’s possible to use a file name including the path, for example:
rpicam-still -o ~/Pictures/mypicture.jpg
Use the -h parameter to display all the possible options for this command:
rpicam-still -h
 
--width arg (=0) Set the output image width (0 = use default value)
--height arg (=0) Set the output image height (0 = use default value)
-t [ --timeout ] arg (=5000) Time (in ms) for which program runs
-o [ --output ] arg Set the output file name
-n [ --nopreview ] =arg(=1) Do not show a preview window-p [ --preview ] arg (=0,0,0,0) Set the preview window dimensions, given as x,y,width,height e.g. 0,0,640,480
-f [ --fullscreen ] =arg(=1) Use a fullscreen preview window
--qt-preview =arg(=1) Use Qt-based preview window (WARNING: causes heavy CPU load, fullscreen not
supported)
--rotation arg (=0) Request an image rotation, 0 or 180
--brightness arg (=0) Adjust the brightness of the output images, in the range -1.0 to 1.0
--contrast arg (=1) Adjust the contrast of the output image, where 1.0 = normal contrast
--saturation arg (=1) Adjust the colour saturation of the output, where 1.0 = normal and 0.0 =
greyscale
-q [ --quality ] arg (=93) Set the JPEG quality parameter
For your information, on the Legacy edition of Raspberry Pi OS, it will be:
raspistill -o image.jpg
rpicam-vid -o video.h264
Use the CTRL+C shortcut to stop the recording, or add the -t option to specify the recording duration.
H264 files are compatible with VLC.
If needed, you can install it on Raspberry Pi OS Desktop with:
sudo apt install vlc
•	It’s the same to see all the parameters available, use rpicam-vid -h to get all options with a short description. Useful options are:
•	–t: to choose the video duration in ms (ex: 6000 for a 6s video). This way you don’t need to use CTRL+C and can schedule the video capture with a script or cron.
•	-w and -h: video size (width and height).
OUTPUT 
![image](https://github.com/user-attachments/assets/dc7c7faf-cc86-461b-8196-9e2de4c946d3)

 
RESULT
The camera module was successfully interfaced with the Raspberry Pi, and a real-time video feed was displayed

