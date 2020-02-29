# piRL-backpack
An IRL backpack that uses a Raspberry Pi 4 as the encoder.


## Parts list
#### Required:
* Sony AS300 camera (or a similar one with an HDMI port)
* Raspberry Pi 4 (4GB RAM) & some kind of cooling solution
* Camlink 4K
* Phone(s)/router with 4G that supports Tethering
* Portable battery for power
* Micro-HDMI cable
* Backpack 
#### Optional:
* Cocoon GRID-IT! Accessory Organizer
## Instructions
#### Required:
1. Download the latest version of a light linux distribution (i.e. Raspbian)
2. Flash the .iso to the SD card in the Pi. 
3. Connect the Pi to the Internet via the Ethernet port
4. Run `apt-get update && apt-get upgarde`
5. [Install ffmpeg with omx support.](https://github.com/legotheboss/YouTube-files/wiki/(RPi)-Compile-FFmpeg-with-the-OpenMAX-H.264-GPU-acceleration)
6. Set up an RTMP server and OBS on an old PC or on a cloud service. 
7. Install the OBS websocket plugin
8. Port forward the server
9. Assemble the backpack. Connect the powerbank to the raspberry pi via the USB C port.
10. Connect the Micro-HDMI cable to the camera and to the Camlink. 
11. Connect the phone/router to the Raspberry Pi via USB and enable tethering.
12. Run this command on the Pi (this will start streaming to the RTMP server): `screen ffmpeg -re -f video4linux2 -thread_queue_size 2048 -input_format yuyv422 -s 1280x720 -r 60 -i /dev/video0 -f alsa -thread_queue_size 2048 -ac 2 -i plughw:CARD=1,DEV=0 -c:a aac -c:v h264_omx -threads 4 -f flv -b:v 1500k rtmp://<IP OF RTMP SERVER>/live/rJrwXAhRB`
#### Optional:
* Overclock the Raspberry Pi 4 to increase performance 
