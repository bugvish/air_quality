air-quality
===========

This tutorial will cover the fundamentals of deploying a solar powered air quality monitor using the cellular network.  Though we will be using a dust particle sensor to measure air quality, the same setup could easily be modified for other sensors such ____.  This setup also uses the Xively platform which allows for real-time data streams to be displayed on the web.  To begin, you will need:

- Arduino Uno
- Arduino GSM Shield
- Active SIM Card (AT&T or T-Mobile)
- Dust Particle Sensor
- Voltaic Solar Kit 

The Arduino GSM shield is a powerful module that enables connection to the cellular network.  Using this shield, we can make phone calls, send text messages and even access  web pages.  All of this functionality relies on an active SIM card from any GSM carrier.  We will be using T-Mobile for our example.  

Image 
http://arduino.cc/en/uploads/Guide/SlideSIMIn.jpg


The Dust Particle Sensor from Groove uses a small LED to detect the number of particles passing through the housing.  To incorporate the sensor into the Arduino GSM shield simple connect the black wire to ground, the red wire to 5v and the yellow wire to pin 8.  The sensor ships with a connector which we simple cut off and soldered header pins onto the wires individually.

Following the hardware setup, we will need to choose a unique identifier for the unit.  This identifier will be the "thingname" used with Dweet.io - the messaging service we use to send/display our data on the web.  Supply the chosen Thingname in the credentials.h source code.

The next stage is implementing the Arduino code to connect to your cellular network. Modify the 'air_quality.ino' file to change the GPRS_APN to match you carrier.  For T-Mobile the GPRS_APN is "epc.tmobile.com" and for AT&T the GPRS_APN is "wap.cingular".

The final piece to modify is the frequency that data is sent to Dweet.io.   This can be change by modifying the postingInterval variable which is set in milliseconds.  Setting this will dramatically affect the battery life.

The unit will send the following three datapoints per the above interval: concentration(con) of particles, the ratio(ratio) of the particles to air and the low pulse occupancy(lpo). Navigate to [https://dweet.io/follow] and type in the unit's thingname to see the live data stream.
