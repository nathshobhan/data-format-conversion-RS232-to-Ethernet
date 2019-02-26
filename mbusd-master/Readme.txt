Installation instructions:

$ git clone https://github.com/3cky/mbusd.git mbusd.git
$ cd mbusd.git
$ mkdir -p build && cd build
$ cmake -DCMAKE_INSTALL_PREFIX=/usr ..
$ make
$ sudo make install



The mbusd service can be started via:

# systemctl start mbusd@<serial port>.service

where <serial port> is serial port device name (like ttyUSB0).

mbusd started by systemd will read its configuration from file named /etc/mbusd/mbusd-<serial port>.conf. This way it's possible to run multiple mbusd instances with different configurations.

To see the mbusd service status:

# systemctl status mbusd@<serial port>.service

To monitor the mbusd service:

# journalctl -u mbusd@<serial port>.service -f -n 10

To start the mbusd service on system boot:

# systemctl enable mbusd@<serial port>.service




Data transfer at TCP port

# mbusd -L/tmp/mbusd.log -p /dev/ttyUSB0 -s 9600 -P 502 -d -v9