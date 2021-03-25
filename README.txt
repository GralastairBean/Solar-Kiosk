# Solar-Disk-Kiosk

################### Scientific Data ################### 

0. OVERVIEW

The Solar Dynamics Observatory (SDO) is a NASA mission launched into a geosynchronous orbit on 11 February 2010, the observatory is part of the Living With a Star (LWS) program.

We are now in solar cycle 25. The north pole on the sun has had a negative charge for the last 14 years. The polarity of the sun's north pole has just recently changed to positive. Now the south pole of the sun is in the process of changing polarity from positive to negative.

Sunspots generally group together in pairs to form the poles of solar magnets. One sunspot of each bipolar pair has positive ("north", or outward -directed) magnetic polarity. Its partner has the opposite negative ("south", or inward-directed) polarity. Magnetograms show "line-of-sight" magnetic fields (that is, those either coming directly towards us or going away from us). White color corresponds to positive and black is negative polarity field.
Look at the groups of bipolar sunpots in the active sun image above. Notice that each spot group seems to contain black and white members. Notice too that the groups are usually oriented roughly parallel to the Sun's equator. Leading sunspot matches hemisphere polarity.

1. SDO AIA 171 Å = 17.1 nm = EUV
Emitted by iron-9 (Fe IX) at around 600,000 Kelvin. This wavelength shows the quiet corona and coronal loops, and is typically colorized in gold. This channel is especially good at showing coronal loops - the arcs extending off of the Sun where plasma moves along magnetic field lines. The brightest spots seen here are locations where the magnetic field near the surface is exceptionally strong.

2. SDO HMI Continuum = visible light 
Continuums provide photographs of the solar surface, incorporating a broad range of visible light appearing yellow and orange. 

3. SOHO HMI visible light Black and White
Highlights sunpots and shows scale.

4. SDO HMI Magnetogram
White is positive
Black is negative
Magnetograms show "line-of-sight" magnetic fields (that is, those either coming directly towards us or going away from us). White color corresponds to positive and black is negative polarity field.

5. SDO AIA 304 Å = 30.4 nm = EUV
Emitted by helium-2 (He II) at around 50,000 Kelvin. This light is emitted from the chromosphere and transition region. SDO images of this wavelength are typically colorized in red. 

################### Setup ################### 

[guide: https://pimylifeup.com/raspberry-pi-kiosk/]

1. We create a file in the home directory called "kiosk.sh"
2. This file stops various functions like screen saver and mouse diaply, opens the chromium tabs and then changes tab using xdotool to simulate ctl+tab keydown strokes.
3. We tell the pi to autorun the kiosk.sh file on boot by editing the kiosk.service system file then running:
   sudo systemctl enable kiosk.service
   in the terminal
4. kiosk auto starts on boot, to stop it use: sudo systemctl stop kiosk.service
5. to start it again either reboot or use: sudo systemctl start kiosk.service
6. to check status and see any errors in the kiosk mode use: sudo systemctl status kiosk.service
7. to stop the kiosk mode from running at boot use: sudo systemctl disable kiosk.service
8. to re-enable kiosk mode at start use: sudo systemctl enable kiosk.service


################### BUTTON ################### 

1. autostart file is in /etc/xdg/lxsession/LXDE-pi/autostart
2. It runs at startup and starts a python script that detects a button input to change tab

3. in terminal type: sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
4. this brings up the autostart file so you can edit it
5. we add as last line: python /home/pi/myscript.py
6. press ctrl+x, then y, then enter to save 
7. to stop this script from auto running just delete these lines and save as per line 6






############## CRONTAB ##############
REMOVED ALL CRONTAB AS IT WASN'T WORKING, USING A MODIFIED AUTOSTART FILE INSTEAD SEE "BUTTON" ABOVE
https://www.raspberrypi-spy.co.uk/2013/07/running-a-python-script-at-boot-using-cron/


