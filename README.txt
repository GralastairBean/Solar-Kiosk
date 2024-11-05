## Overview
- The Solar Kiosk is a project that shows a near real-time image of the Sun at different wavelengths taken by two spacecraft; the *Solar Dynamics Observatory* (SDO) spacecraft, a NASA mission launched into a geosynchronous orbit in 2020 and the *Solar and Heliospheric Observatory* (SOHO) launched into a [halo orbit](https://en.wikipedia.org/wiki/Halo_orbit "Halo orbit") around the [[Sun|Sun's]] L1 point by ESA in 1995.
- The [[Raspberry Pi]] boots in kiosk mode, opens 5 browser tabs with the latest images and cycles through them periodically. A push button allows manually switching to different images.  
## Bill of Materials
- [[Raspberry Pi]], any type from zero to 4B is ok, older/more basic versions will just run slower.
- Display Screen
- SD card
- Power supply for Pi and screen
- A few wires
- Momentary push button
## How to build
- Setup the Pi with Raspbian OS.
- **Note, to exit kiosk mode at anytime to access the desktop and make changes etc. press Ctl + space**
- Here is a more complete guide to [kiosk mode](https://pimylifeup.com/raspberry-pi-kiosk/) but the steps are as below...
- We create a file in the home directory (/home/pi/.config/lxsession/LXDE-pi/autostart) called "kiosk.sh"
- This file stops various functions like screen saver and mouse display, opens the chromium tabs and then changes tab using xdotool to simulate ctl+tab keydown strokes.
- We tell the pi to autorun the kiosk.sh file on boot by editing the kiosk.service system file then in the terminal running...
```python
   sudo systemctl enable kiosk.service
```
- kiosk auto starts on boot, to stop it use...
```python
   sudo systemctl stop kiosk.service
```
- to start it again either **reboot** or use..
```python
   sudo systemctl start kiosk.service
```
- to check status and see any errors in the kiosk mode use...
```python
   sudo systemctl status kiosk.service
```
- to stop/re-enable the kiosk mode from running at boot use...
```python
   sudo systemctl disable kiosk.service
   sudo systemctl enable kiosk.service
```
## Pushbutton
- Pushbutton is momentary press type and has one leg connected to ground and one to io pin 10 on the Pi. This pin has built in resistirs so we can set the button to Pull up to avoid floating. 
1. autostart file is in /etc/xdg/lxsession/LXDE-pi/autostart
2. It runs at startup and starts a python script that detects a button input to change tab
3. in terminal type: sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
4. this brings up the autostart file so you can edit it
5. we add as last line: python /home/pi/myscript.py
6. press ctrl+x, then y, then enter to save 
7. to stop this script from auto running just delete these lines and save as per line 6
## Scientific Information
- We are now in solar cycle 25. The north pole on the sun has had a negative charge for the last 14 years. The polarity of the sun's north pole has just recently changed to positive. Now the south pole of the sun is in the process of changing polarity from positive to negative.
- Sunspots generally group together in pairs to form the poles of solar magnets. One sunspot of each bipolar pair has positive ("north", or outward -directed) magnetic polarity. Its partner has the opposite negative ("south", or inward-directed) polarity. Magnetograms show "line-of-sight" magnetic fields (that is, those either coming directly towards us or going away from us). White color corresponds to positive and black is negative polarity field.
- Look at the groups of bipolar sunspots in the active sun image above. Notice that each spot group seems to contain black and white members. Notice too that the groups are usually oriented roughly parallel to the Sun's equator. Leading sunspot matches hemisphere polarity.
- The Solar Kiosk shows a series of 5 images at different wavelengths 
### SDO AIA 171 Å = 17.1 nm = [[ultraviolet|EUV]]
- https://sdo.gsfc.nasa.gov/assets/img/latest/latest_1024_0171.jpg
- Emitted by [[ionisation|iron-9 (Fe IX)]] at around 600,000 Kelvin. This extreme [[ultraviolet]] [[wavelength]] shows the quiet corona and coronal loops, and is typically colorized in gold. This channel is especially good at showing coronal loops - the arcs extending off of the [[Sun]] where [[plasma]] moves along [[electromagnetism|magnetic field lines.]] The brightest spots seen here are locations where the magnetic field near the surface is exceptionally strong. 
### SDO HMI Continuum = visible light 
- https://sdo.gsfc.nasa.gov/assets/img/latest/latest_1024_HMIIC.jpg
- Continuums provide photographs of the solar surface, incorporating a broad range of visible light appearing yellow and orange. 
### SOHO HMI visible light Black and White
- https://soho.nascom.nasa.gov/data/synoptic/sunspots_earth/mdi_sunspots_1024.jpg
- Highlights sunpots and shows scale.
### SDO HMI Magnetogram
- https://sdo.gsfc.nasa.gov/assets/img/latest/latest_1024_HMIB.jpg
- Magnetograms show "line-of-sight" [[electromagnetism|magnetic fields]] (that is, those either coming directly towards us or going away from us). White color corresponds to positive and black is negative polarity field.
- White is positive, black is negative.
### SDO AIA 304 Å = 30.4 nm = EUV
- https://sdo.gsfc.nasa.gov/assets/img/latest/latest_1024_0304.jpg
- Emitted by [[ionisation|helium-2 (He II)]] at around 50,000 Kelvin. This light is emitted from the chromosphere and transition region. SDO images of this wavelength are typically colorized in red. 
