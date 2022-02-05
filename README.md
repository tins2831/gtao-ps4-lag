# GTAO-PS4-Lag
Lag switch for Grand Theft Auto: Online on PS4. It blocks all outbound (by default) traffic whose destination port is either 6672 or 61456. Untested on other platforms.

### Requirements
* A Linux (preferably Debian based) system. WSL might work, but I don't have a windows system to test that on.
* `tc` (Traffic Control):
  * Check if it's installed by running the following command: `sudo tc -V`.
  * If not installed, run `sudo apt install iproute2`.
* [Python 3.9](https://www.python.org/downloads/release/python-3910/)

### Setup
To begin, you should create a hotspot on your linux system. [linux-router](https://github.com/garywill/linux-router) allows you to easily create one.

Press q at the prompt or Ctrl + C to exit.
```
$ git clone https://github.com/tins2831/gtao-ps4-lag.git
$ cd gtao-ps4-lag
$ # get the list of network interfaces to compare later
$ ls /sys/class/net
$ sudo lnxrouter --ap SSID -p PASSWORD &
$ # there should now be a new entry
$ ls /sys/class/net
$ sudo ./gtao-ps4-lag INTERFACE
v>> Press any key to begin or Ctrl + C to exit.
```

### Options
```
$ sudo ./gtao-ps4-lag --help
usage: sudo ./gtao-ps4-lag [-h] [--amount VALUE] [-i] INTERFACE

Lag switch for Grand Theft Auto: Online on PS4.

positional arguments:
  INTERFACE       Network interface to target.

optional arguments:
  -h, --help      show this help message and exit
  --amount VALUE  Amount of packet loss to induce. Defaults to 90.
  -i, --inbound   Drop inbound packets instead. Outbound packets are dropped by
                  default.

https://github.com/tins2831/gtao-ps4-lag
```

### Notice
This software uses [netimpair](https://github.com/urbenlegend/netimpair) which uses the MIT license:
```
The MIT License (MIT)

Copyright (c) 2015 Benjamin Xiao

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
