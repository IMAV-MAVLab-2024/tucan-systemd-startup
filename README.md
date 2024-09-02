# tucan-systemd-startup
Very simple systemd service to run the Micro-xrce-dds agent needed for interfacing PX4 with ROS2 via a serial connection.

## Installation

0. Ensure that this Repository was cloned in the home directory of the orangepi user.

1. Ensure the script is executable:
```sh
chmod u+x ~/tucan-systemd-startup/mavlink_router.sh
chmod u+x ~/tucan-systemd-startup/micro_xrce.sh
chmod u+x ~/tucan-systemd-startup/zenoh_bridge.sh
```

2. Copy the service file to the coorect directory:
```sh
sudo cp micro-xrce-dds-agent.service /etc/systemd/system/micro-xrce-dds-agent.service
sudo cp mavlink-router.service /etc/systemd/system/mavlink-router.service
sudo cp zenoh-bridge.service /etc/systemd/system/zenoh-bridge.service
```

3. Reload the systemd manager configuration:
```sh
sudo systemctl daemon-reload
```


4. Enable the services to start on boot:
```sh
sudo systemctl enable micro-xrce-dds-agent.service
sudo systemctl enable mavlink-router.service
sudo systemctl enable zenoh-bridge.service
```


5. Start the services manually (optional, avoid restarting):
```sh
sudo systemctl start micro-xrce-dds-agent.service
sudo systemctl start mavlink-router.service
sudo systemctl start zenoh-bridge.service
```


## Set system wide ROS_DOMAIN_ID to prevent clashes

1. Edit the following file:
```sh
sudo nano /etc/environment
```

2. Add this line to the file:
```sh
ROS_DOMAIN_ID=74
```

## Some comments
For some reason the serial port may change, to fix this check which serial ports are available
```
ls /dev/ttyS*
```
You can try the different options if it does not work with the default set in the <micro_xrce.sh> file. In this file you can also set the baud rate, which should correspond to the FCU's baud rate on TELEM2/TEL2 (921600 by default).

Similarly, the baud rate of the mavlink router should be set in the GPS1 parameter.
