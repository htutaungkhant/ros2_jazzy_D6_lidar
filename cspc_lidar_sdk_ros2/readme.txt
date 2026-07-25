# CSPC LiDAR Setup

## English

### 1. Copy the udev Rule

```bash
sudo cp sc_mini.rules /etc/udev/rules.d
```

This allows Linux to recognize the LiDAR device correctly.

### 2. Launch the LiDAR Node

```bash
ros2 launch cspc_lidar lidar_launch.py
```

This starts the LiDAR driver and publishes scan data.

### 3. Open RViz2

```bash
ros2 launch cspc_lidar lidar_rviz.py
```

RViz2 will display the LiDAR scan data.

---

# やさしい日本語

## 1. udev ルールをコピーします。

```bash
sudo cp sc_mini.rules /etc/udev/rules.d
```

Linux が LiDAR を正（ただ）しく認識（にんしき）できるようにします。

## 2. LiDAR ノードを起動（きどう）します。

```bash
ros2 launch cspc_lidar lidar_launch.py
```

LiDAR ドライバーを起動して、スキャンデータを送（おく）ります。

## 3. RViz2 を起動（きどう）します。

```bash
ros2 launch cspc_lidar lidar_rviz.py
```

RViz2 に LiDAR のスキャンデータが表示（ひょうじ）されます。
