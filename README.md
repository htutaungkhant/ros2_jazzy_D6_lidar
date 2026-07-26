# CSPC LiDAR Setup (Temporary Fix)

If you get the following error:

```bash
version M1CT_TOF
***/dev/sc_mini
lidar_set_port wrong
node_lidar init error
```

It usually means the driver is trying to open `/dev/sc_mini`, but your LiDAR is detected as `/dev/ttyUSB0`.

## 1. Source the ROS 2 Workspace

```bash
cd ~/ros2_ws
source install/setup.bash
```

## 2. Create a Symbolic Link

Create a temporary symbolic link from `/dev/sc_mini` to `/dev/ttyUSB0`.

```bash
sudo ln -s /dev/ttyUSB0 /dev/sc_mini
```

> **Note**
> This is a temporary solution. The symbolic link will disappear after reboot.

## 3. Verify the Link

```bash
ls -l /dev/sc_mini
```

Expected output:

```bash
lrwxrwxrwx 1 root root ... /dev/sc_mini -> /dev/ttyUSB0
```

## 4. Run the LiDAR Node

```bash
ros2 run cspc_lidar cspc_lidar
```

---

## Complete Commands

```bash
cd ~/ros2_ws
source install/setup.bash

sudo ln -s /dev/ttyUSB0 /dev/sc_mini

ls -l /dev/sc_mini

ros2 run cspc_lidar cspc_lidar
```

---

## Troubleshooting

Check whether the LiDAR is detected:

```bash
ls /dev/ttyUSB*
```

Expected:

```bash
/dev/ttyUSB0
```

If `/dev/ttyUSB0` is not found:

- Check the USB cable.
- Reconnect the LiDAR.
- Verify the USB serial driver is loaded.
- Run:

```bash
dmesg | tail -20
```

to inspect USB connection messages.

---

## Permanent Solution

Instead of creating the symbolic link manually after every reboot, create a **udev rule** that automatically maps the LiDAR device to `/dev/sc_mini`.
