# tucan-systemd-startup
Very simple systemd service to run the Micro-xrce-dds agent needed for interfacing PX4 with ROS2 via a serial connection.

## Installation

0. Ensure that this Repository was cloned in the home directory of the imav2024 user.

1. Ensure the script is executable:
```sh
chmod u+x /home/imav2024/tucan-systemd-startup/mavlink_router.sh
chmod u+x /home/imav2024/tucan-systemd-startup/micro_xrce.sh
```

2. Copy the service file to the coorect directory:
```sh
sudo cp micro-xrce-dds-agent.service /etc/systemd/system/micro-xrce-dds-agent.service
sudo cp mavlink-router.service /etc/systemd/system/mavlink-router.service
```

3. Reload the systemd manager configuration:
```sh
sudo systemctl daemon-reload
```


4. Enable the services to start on boot:
```sh
sudo systemctl enable micro-xrce-dds-agent.service
sudo systemctl enable mavlink-router.service
```


5. Start the services manually (optional):
```sh
sudo systemctl start micro-xrce-dds-agent.service
sudo systemctl start mavlink-router.service
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

