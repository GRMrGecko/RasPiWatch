#Parts Needed
A Raspberry Pi

A TFT LCD display. I bought one of these https://www.adafruit.com/products/1601 complete at http://raspberrypilcd.com/collections/frontpage/products/pitft-assembled-320x240-2-8-tft-touchscreen-for-raspberry-pi. Simply follow these instructions to configure Debian for the screen https://learn.adafruit.com/adafruit-pitft-28-inch-resistive-touchscreen-display-raspberry-pi/software-installation (Don't ask me why they are using a fake ssh on a windows machine which you should never use).

Any battery with USB output to provide power.
#Additional software installation
```
sudo apt-get install unclutter x11-xserver-utils
```
#Setting up
1. You need to copy over this folder to the Desktop (/home/pi/Desktop/) named clock (you can rename, but make sure you correct any differences with the instructions).
2. Create a file in the home directory (/home/pi/) and name it .xinitrc putting the contents of below:
```
xset s off #Don’t activate screensaver
xset -dpms #Disable DPMS (Energy Star) features.
xset s noblank #Don’t blank the video device
exec /etc/alternatives/x-session-manager #Start lxde
```
3. Edit /etc/xdg/lxsession/LXDE/autostart to add at the end the following:
```
@midori -e Fullscreen -a /home/pi/Desktop/RasPiWatch/index.html
```
4. Reboot the Pi or plug it in and wait for it to boot. Once booted, you will have a nice watch face!

#Adding Backgrounds
Simply make a new folder with the name ```bg``` in the RasPiWatch folder and add photos that are 320x240. Once you have all the photos you want, if you're using a mac, you can use a hack of mine to make the list for the Array called backgrounds. My hack is to copy all of the files and paste into TextMate which will create the list of files, one per line, then you need to replace everything but the file name with find and replace and replace new lines with ```","``` (with quotes). Once you got every replaced, cap the list out with quotes so it looks like ```"1.jpg","2.jpg"``` and then paste into the array.

#Operation
The time does not retain on the clock, so in-order to keep the time correct you need to plug into ethernet or have Wifi setup so that Debian can call the time server to get the current time.

Once started, you may exit by hooking up a mouse and right clicking to choose exit full screen or you can use a keyboard to hit F11 to exit full screen or even enter full screen.

#Other ideas
You can possibly add music and setup the HTML so you can load and control the music.

You can possibly have video and setup the HTML so you can load and control the video.

You can install Nginx and php and make the clock a PHP clock which will allow you to do advanced things via the system command.

You can configure the buttons on the TFT to do things.

You can hook up a bluetooth dongle, write an android app, and get notifications.