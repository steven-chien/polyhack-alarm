# Smart Alarm

An alarm clock that uses PIR sensor to make sure that you have got out of your room before stopping. Intended to run on Raspberry Pi.

### Getting Started

1. Install the dependencies

	```
	# apt-get install vorbis-tools
	# pip install cherrypy
	# pip install python-deamon
	```
	On Mac install vorbis-tools with
	```
	brew install vorbis-tools
	```
2. Configure crontab

	Add the following to the root crontab
	```
	* * * * * /bin/sed -e :a -e '$q;N;301,$D;ba' -i /tmp/raw_state.dat
	```
	Add the following to the user(pi) crontab
	```
	* * * * * /usr/bin/python (abs path to your location)/wakeup.py (abs path to your location) >> /tmp/wakeup.log 2>&1 &
	```
3. Run the sensor daemon
	```
	sudo python sensor/movement_sensor.py
	```
4. Run the server
	```
	python server.py
	```
5. Launch your browser, go to 
	```
	localhost:8080
	```

### Libraries
Smart alarm uses the following libraires and hardware:

* [Bootstrap] - CSS library
* [CherryPy] - A Minimalist Python Web Framework
* [python-daemon] - Library help daemonize script
* [Python GPIO] - The library used for reading GPIO pins on the Pi
* [ogg123] - A Linux Ogg Vorbis audio player
* [jQuery] - A cross-platform JavaScript library


### Version
v0.1

### License
Copyright (C) 2016 Anson Kwan, Carson Yan, Star Poon and Steven Chien

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>
