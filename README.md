# tucan-systemd-startup
Very simple systemd service to run the Micro-xrce-dds agent needed for interfacing PX4 with ROS2 via a serial connection.

## Installation

0. Ensure that this Repository was cloned in the home directory of the imav2024 user.

1. Ensure the script is executable:
```sh
chmod u+x /path/to/spark/sbin/start-all.sh
```

2. Copy the service file to the coorect directory:


```sh
sudo cp /etc/systemd/system/micro-xrce-dds-agent.service
```

3. Reload the systemd manager configuration:
```sh
sudo systemctl daemon-reload
```

4. Start the service manually (optional):
```sh
sudo systemctl start micro-xrce-dds-agent.service.
```
