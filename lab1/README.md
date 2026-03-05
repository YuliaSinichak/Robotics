# 🤖 Robotics Lab 1 – Gazebo Robot Control

This project demonstrates how to launch a simulation environment and control a robot using command-line commands in **Gazebo**.

The workflow uses **two terminals**:
- **Terminal 1** – starts the container and the Gazebo simulation
- **Terminal 2** – sends movement commands to the robot

---

# 📋 Requirements

Before running the project, make sure you have:

- Docker installed
- Gazebo installed
- Access to the project repository
- Linux environment (tested on Ubuntu)


# 🚀 Running the Simulation

## Terminal 1: Starting the Container and Gazebo

This terminal initializes the container, loads the simulation world, and starts the physics engine.

```bash
cd ~/Labs/Lab1/robotics_lpnu
sudo ./scripts/cmd run
```

Inside the container shell:

```bash
cd src/code/lab1
gz sim worlds/building_robot.sdf
```

After running these commands, **Gazebo will launch with the robot simulation**.

---

## Terminal 2: Sending Movement Commands

Use this terminal to manually control the robot by publishing velocity commands.

```bash
cd ~/Labs/Lab1/robotics_lpnu
sudo ./scripts/cmd bash
```

Send a movement command:

```bash
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.5}, angular: {z: 0.0}"
```

##
# 🎮 Example Commands

Move forward:

```bash
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.5}, angular: {z: 0.0}"
```

Rotate left:

```bash
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.0}, angular: {z: 0.5}"
```

Rotate right:

```bash
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.0}, angular: {z: -0.5}"
```

Stop the robot:

```bash
gz topic -t "/cmd_vel" -m gz.msgs.Twist -p "linear: {x: 0.0}, angular: {z: 0.0}"
```