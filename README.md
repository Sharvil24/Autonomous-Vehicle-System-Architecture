<h1 align="center"> Autonomous Vehicle System Architecture</h1>

<p align="center">
  <img width="1504" alt="AV_SA_image" src="https://github.com/user-attachments/assets/7e8855cc-c185-4128-ac0b-79b7f507eb11" />

</p>

<h2>📋 Overview</h2>

<p>This repository presents a comprehensive autonomous vehicle system architecture designed with a modular, layered approach. The architecture enables safe, reliable self-driving capabilities through the integration of advanced sensors, AI algorithms, and robust control systems.</p>

<h2>🏗️ Architecture Components</h2>

<h3>🔴 Sensor Layer</h3>
<p>The foundation of environmental perception, collecting raw data about the vehicle's surroundings.</p>

<ul>
  <li><strong>LiDAR</strong>: Provides 360° 3D point cloud data for precise distance measurements</li>
  <li><strong>Cameras (8-12)</strong>: High-resolution visual sensors for object recognition and lane detection</li>
  <li><strong>Radar</strong>: Millimeter-wave sensors for all-weather object detection and velocity measurement</li>
  <li><strong>Ultrasonic</strong>: Short-range sensors for parking assistance and close-proximity detection</li>
  <li><strong>GPS/GNSS</strong>: High-precision satellite positioning with RTK correction</li>
  <li><strong>IMU</strong>: Inertial measurement unit for vehicle motion and orientation tracking</li>
  <li><strong>Encoders</strong>: Wheel rotation sensors for accurate odometry calculations</li>
</ul>

<h3>🟡 Perception Layer</h3>
<p>Processes sensor data to create comprehensive environmental understanding.</p>

<ul>
  <li><strong>Sensor Fusion</strong>: Combines multiple sensor inputs into unified environmental model</li>
  <li><strong>Object Detection</strong>: Identifies vehicles, pedestrians, cyclists, and obstacles using deep learning</li>
  <li><strong>3D Reconstruction</strong>: Builds real-time 3D representation of surroundings</li>
  <li><strong>Lane Detection</strong>: Recognizes road markings and drivable surfaces</li>
  <li><strong>Segmentation</strong>: Pixel-level scene understanding and classification</li>
  <li><strong>Object Tracking</strong>: Maintains temporal consistency of detected objects</li>
</ul>

<h3>🟢 Localization & Mapping Layer</h3>
<p>Determines precise vehicle position and maintains environmental maps.</p>

<ul>
  <li><strong>SLAM</strong>: Simultaneous Localization and Mapping for real-time positioning</li>
  <li><strong>HD Map Integration</strong>: Interfaces with centimeter-accurate road maps</li>
  <li><strong>Map Matching</strong>: Aligns sensor observations with map data</li>
  <li><strong>Transformations</strong>: Manages coordinate system conversions</li>
</ul>

<h3>🟣 Prediction Layer</h3>
<p>Anticipates future behaviors of detected objects and environmental changes.</p>

<ul>
  <li><strong>Behavior Prediction</strong>: ML-based trajectory forecasting for road users</li>
  <li><strong>Scenario Analysis</strong>: Evaluates multiple possible future scenarios</li>
  <li><strong>Risk Assessment</strong>: Calculates collision probabilities and safety margins</li>
  <li><strong>Intent Recognition</strong>: Infers intentions of pedestrians and drivers</li>
</ul>

<h3>🟦 Planning Layer</h3>
<p>Makes high-level decisions about vehicle path and behavior.</p>

<ul>
  <li><strong>Route Planning</strong>: Determines optimal path from origin to destination</li>
  <li><strong>Behavior Planning</strong>: Manages driving states (lane changes, intersections, parking)</li>
  <li><strong>Motion Planning</strong>: Generates smooth, feasible trajectories</li>
  <li><strong>Optimization</strong>: Balances safety, comfort, and efficiency objectives</li>
  <li><strong>Contingency Planning</strong>: Prepares alternative paths for unexpected situations</li>
</ul>

<h3>🔵 Control Layer</h3>
<p>Executes planned trajectories through vehicle actuators.</p>

<ul>
  <li><strong>Path Following</strong>: Steering control to track planned trajectory</li>
  <li><strong>Speed Control</strong>: Manages acceleration and braking profiles</li>
  <li><strong>Stability Control</strong>: Maintains vehicle stability in all conditions</li>
  <li><strong>Actuator Interface</strong>: Translates commands to vehicle hardware</li>
</ul>

<h3>🟪 System Management Layer</h3>
<p>Oversees entire autonomous system operation.</p>

<ul>
  <li><strong>System Supervisor</strong>: Coordinates all subsystems and state transitions</li>
  <li><strong>Fault Diagnosis</strong>: Detects and handles system failures gracefully</li>
  <li><strong>Redundancy Management</strong>: Switches between primary and backup systems</li>
  <li><strong>Mode Management</strong>: Handles autonomous/manual mode transitions</li>
</ul>

<h3>🔴 Safety & Security Layer</h3>
<p>Ensures safe operation and protects against threats.</p>

<ul>
  <li><strong>Functional Safety</strong>: ISO 26262 compliant safety monitoring</li>
  <li><strong>Emergency Stop</strong>: Fail-safe mechanisms for critical situations</li>
  <li><strong>Collision Avoidance</strong>: Last-resort intervention systems</li>
  <li><strong>Secure Boot</strong>: Authenticated software verification</li>
  <li><strong>Encryption</strong>: Protects data transmission and storage</li>
  <li><strong>Intrusion Detection</strong>: Monitors for cybersecurity threats</li>
</ul>

<h2>💻 Supporting Infrastructure</h2>

<h3>Computing Platform</h3>
<ul>
  <li><strong>Central GPU/TPU</strong>: High-performance AI processing units</li>
  <li><strong>Distributed ECUs</strong>: Specialized processors for specific functions</li>
  <li><strong>Redundant Systems</strong>: Backup computing for critical operations</li>
  <li><strong>Real-time OS</strong>: QNX or RT Linux for deterministic performance</li>
  <li><strong>ROS 2 Middleware</strong>: Inter-process communication framework</li>
</ul>

<h3>📡 Communication Systems</h3>
<ul>
  <li><strong>V2X Communication</strong>: Vehicle-to-Everything connectivity</li>
  <li><strong>5G/LTE Cellular</strong>: Cloud services and remote monitoring</li>
  <li><strong>Automotive Ethernet</strong>: High-speed internal data transfer</li>
  <li><strong>CAN-FD Bus</strong>: Traditional vehicle network communication</li>
  <li><strong>Cloud Services</strong>: OTA updates and fleet management</li>
</ul>

<h3>🖥️ Human-Machine Interface</h3>
<ul>
  <li><strong>Visual Display</strong>: System status and planned actions</li>
  <li><strong>Audio Alerts</strong>: Warnings and notifications</li>
  <li><strong>Haptic Feedback</strong>: Tactile alerts through steering/seats</li>
  <li><strong>Voice Interface</strong>: Natural language interaction</li>
  <li><strong>Remote Monitoring</strong>: Fleet management capabilities</li>
</ul>
