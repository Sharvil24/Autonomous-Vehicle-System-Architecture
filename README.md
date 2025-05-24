# Autonomous-Vehicle-System-Architecture

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Autonomous Vehicle System Architecture</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            font-family: 'Arial', sans-serif;
            background: #1a1a2e;
            color: #fff;
            overflow-x: auto;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            min-width: 1200px;
        }
        
        h1 {
            text-align: center;
            color: #00d4ff;
            margin-bottom: 30px;
            font-size: 2.5em;
            text-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
        }
        
        .architecture {
            display: flex;
            flex-direction: column;
            gap: 20px;
            position: relative;
        }
        
        .layer {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(0, 212, 255, 0.3);
            border-radius: 15px;
            padding: 20px;
            position: relative;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        
        .layer:hover {
            border-color: rgba(0, 212, 255, 0.7);
            box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
            transform: translateY(-2px);
        }
        
        .layer-title {
            font-size: 1.4em;
            font-weight: bold;
            color: #00d4ff;
            margin-bottom: 15px;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        .components {
            display: grid;
            gap: 10px;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        }
        
        .component {
            background: rgba(0, 212, 255, 0.1);
            border: 1px solid rgba(0, 212, 255, 0.3);
            border-radius: 8px;
            padding: 12px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            font-size: 0.9em;
        }
        
        .component:hover {
            background: rgba(0, 212, 255, 0.2);
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0, 212, 255, 0.3);
        }
        
        .sensor-layer .component { border-color: #ff6b6b; background: rgba(255, 107, 107, 0.1); }
        .perception-layer .component { border-color: #ffd93d; background: rgba(255, 217, 61, 0.1); }
        .localization-layer .component { border-color: #6bcf7f; background: rgba(107, 207, 127, 0.1); }
        .prediction-layer .component { border-color: #e056fd; background: rgba(224, 86, 253, 0.1); }
        .planning-layer .component { border-color: #00b894; background: rgba(0, 184, 148, 0.1); }
        .control-layer .component { border-color: #74b9ff; background: rgba(116, 185, 255, 0.1); }
        .system-layer .component { border-color: #a29bfe; background: rgba(162, 155, 254, 0.1); }
        .safety-layer .component { border-color: #ff4757; background: rgba(255, 71, 87, 0.1); }
        
        .arrow {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 40px;
            height: 40px;
            z-index: 10;
        }
        
        .arrow svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 10px rgba(0, 212, 255, 0.5));
        }
        
        .side-components {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            width: 250px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(0, 212, 255, 0.3);
            border-radius: 10px;
        }
        
        .left-side {
            left: -280px;
        }
        
        .right-side {
            right: -280px;
        }
        
        .side-title {
            font-size: 1.1em;
            color: #00d4ff;
            margin-bottom: 10px;
            font-weight: bold;
            text-align: center;
        }
        
        .side-item {
            background: rgba(0, 212, 255, 0.1);
            border: 1px solid rgba(0, 212, 255, 0.3);
            border-radius: 5px;
            padding: 8px;
            margin: 5px 0;
            font-size: 0.85em;
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .side-item:hover {
            background: rgba(0, 212, 255, 0.2);
            transform: translateX(5px);
        }
        
        .data-flow {
            position: absolute;
            width: 2px;
            background: linear-gradient(to bottom, transparent, #00d4ff, transparent);
            left: 50%;
            top: 0;
            bottom: 0;
            transform: translateX(-50%);
            z-index: 1;
            opacity: 0.3;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }
        
        .data-flow::before {
            content: '';
            position: absolute;
            width: 10px;
            height: 10px;
            background: #00d4ff;
            border-radius: 50%;
            left: 50%;
            transform: translateX(-50%);
            animation: pulse 2s infinite;
        }
        
        .hmi-section {
            position: absolute;
            bottom: -80px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(0, 212, 255, 0.3);
            border-radius: 10px;
            padding: 15px;
            width: 600px;
            text-align: center;
        }
        
        .hmi-components {
            display: flex;
            justify-content: space-around;
            margin-top: 10px;
        }
        
        .tooltip {
            position: absolute;
            background: rgba(0, 0, 0, 0.9);
            border: 1px solid #00d4ff;
            border-radius: 5px;
            padding: 10px;
            font-size: 0.85em;
            display: none;
            z-index: 100;
            max-width: 250px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Autonomous Vehicle System Architecture</h1>
        
        <div class="architecture">
            <div class="data-flow"></div>
            
            <!-- Sensor Layer -->
            <div class="layer sensor-layer">
                <div class="layer-title">Sensor Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="360° 3D point cloud data">LiDAR</div>
                    <div class="component" data-tooltip="Visual perception & recognition">Cameras (8-12)</div>
                    <div class="component" data-tooltip="Object detection in all weather">Radar</div>
                    <div class="component" data-tooltip="Close proximity detection">Ultrasonic</div>
                    <div class="component" data-tooltip="High-precision positioning">GPS/GNSS</div>
                    <div class="component" data-tooltip="Motion & orientation tracking">IMU</div>
                    <div class="component" data-tooltip="Wheel rotation measurement">Encoders</div>
                </div>
                <div class="arrow" style="bottom: -30px;">
                    <svg viewBox="0 0 40 40">
                        <path d="M20 5 L20 30 L15 25 M20 30 L25 25" stroke="#00d4ff" stroke-width="2" fill="none"/>
                    </svg>
                </div>
            </div>
            
            <!-- Perception Layer -->
            <div class="layer perception-layer">
                <div class="layer-title">Perception Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Combines all sensor data">Sensor Fusion</div>
                    <div class="component" data-tooltip="Identifies vehicles, pedestrians, etc">Object Detection</div>
                    <div class="component" data-tooltip="Real-time environment mapping">3D Reconstruction</div>
                    <div class="component" data-tooltip="Road marking detection">Lane Detection</div>
                    <div class="component" data-tooltip="Scene understanding">Segmentation</div>
                    <div class="component" data-tooltip="Temporal object tracking">Object Tracking</div>
                </div>
                <div class="arrow" style="bottom: -30px;">
                    <svg viewBox="0 0 40 40">
                        <path d="M20 5 L20 30 L15 25 M20 30 L25 25" stroke="#00d4ff" stroke-width="2" fill="none"/>
                    </svg>
                </div>
            </div>
            
            <!-- Localization Layer -->
            <div class="layer localization-layer">
                <div class="layer-title">Localization & Mapping Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Simultaneous Localization and Mapping">SLAM</div>
                    <div class="component" data-tooltip="Lane-level map data">HD Map Integration</div>
                    <div class="component" data-tooltip="Aligns perception with maps">Map Matching</div>
                    <div class="component" data-tooltip="Coordinate system management">Transformations</div>
                </div>
                <div class="arrow" style="bottom: -30px;">
                    <svg viewBox="0 0 40 40">
                        <path d="M20 5 L20 30 L15 25 M20 30 L25 25" stroke="#00d4ff" stroke-width="2" fill="none"/>
                    </svg>
                </div>
            </div>
            
            <!-- Prediction Layer -->
            <div class="layer prediction-layer">
                <div class="layer-title">Prediction Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Predicts other vehicles' paths">Behavior Prediction</div>
                    <div class="component" data-tooltip="Multiple scenario evaluation">Scenario Analysis</div>
                    <div class="component" data-tooltip="Collision probability calculation">Risk Assessment</div>
                    <div class="component" data-tooltip="Understands other drivers' plans">Intent Recognition</div>
                </div>
                <div class="arrow" style="bottom: -30px;">
                    <svg viewBox="0 0 40 40">
                        <path d="M20 5 L20 30 L15 25 M20 30 L25 25" stroke="#00d4ff" stroke-width="2" fill="none"/>
                    </svg>
                </div>
            </div>
            
            <!-- Planning Layer -->
            <div class="layer planning-layer">
                <div class="layer-title">Planning Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Overall route selection">Route Planning</div>
                    <div class="component" data-tooltip="High-level driving decisions">Behavior Planning</div>
                    <div class="component" data-tooltip="Trajectory generation">Motion Planning</div>
                    <div class="component" data-tooltip="Multi-objective optimization">Optimization</div>
                    <div class="component" data-tooltip="Backup plan generation">Contingency Planning</div>
                </div>
                <div class="arrow" style="bottom: -30px;">
                    <svg viewBox="0 0 40 40">
                        <path d="M20 5 L20 30 L15 25 M20 30 L25 25" stroke="#00d4ff" stroke-width="2" fill="none"/>
                    </svg>
                </div>
            </div>
            
            <!-- Control Layer -->
            <div class="layer control-layer">
                <div class="layer-title">Control Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Steering control">Path Following</div>
                    <div class="component" data-tooltip="Throttle & brake control">Speed Control</div>
                    <div class="component" data-tooltip="Vehicle dynamics management">Stability Control</div>
                    <div class="component" data-tooltip="Hardware command translation">Actuator Interface</div>
                </div>
            </div>
            
            <!-- System Management -->
            <div class="layer system-layer" style="margin-top: 40px;">
                <div class="layer-title">System Management Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="Overall system coordination">System Supervisor</div>
                    <div class="component" data-tooltip="Error detection & handling">Fault Diagnosis</div>
                    <div class="component" data-tooltip="Backup system management">Redundancy Mgmt</div>
                    <div class="component" data-tooltip="Autonomous/Manual switching">Mode Management</div>
                </div>
            </div>
            
            <!-- Safety & Security -->
            <div class="layer safety-layer">
                <div class="layer-title">Safety & Security Layer</div>
                <div class="components">
                    <div class="component" data-tooltip="ISO 26262 compliance">Functional Safety</div>
                    <div class="component" data-tooltip="Emergency brake system">Emergency Stop</div>
                    <div class="component" data-tooltip="Last-resort intervention">Collision Avoidance</div>
                    <div class="component" data-tooltip="Secure system boot">Secure Boot</div>
                    <div class="component" data-tooltip="Data protection">Encryption</div>
                    <div class="component" data-tooltip="Cyber threat detection">Intrusion Detection</div>
                </div>
            </div>
            
            <!-- Left Side Components -->
            <div class="side-components left-side">
                <div class="side-title">Computing Platform</div>
                <div class="side-item">Central GPU/TPU</div>
                <div class="side-item">Distributed ECUs</div>
                <div class="side-item">Redundant Systems</div>
                <div class="side-item">Real-time OS</div>
                <div class="side-item">ROS 2 Middleware</div>
            </div>
            
            <!-- Right Side Components -->
            <div class="side-components right-side">
                <div class="side-title">Communication</div>
                <div class="side-item">V2X Communication</div>
                <div class="side-item">5G/LTE Cellular</div>
                <div class="side-item">Automotive Ethernet</div>
                <div class="side-item">CAN-FD Bus</div>
                <div class="side-item">Cloud Services</div>
            </div>
            
            <!-- HMI Section -->
            <div class="hmi-section">
                <div class="side-title">Human-Machine Interface</div>
                <div class="hmi-components">
                    <div class="side-item">Visual Display</div>
                    <div class="side-item">Audio Alerts</div>
                    <div class="side-item">Haptic Feedback</div>
                    <div class="side-item">Voice Interface</div>
                    <div class="side-item">Remote Monitoring</div>
                </div>
            </div>
        </div>
        
        <div class="tooltip" id="tooltip"></div>
    </div>
    
    <script>
        // Add hover effects for components
        const components = document.querySelectorAll('.component');
        const tooltip = document.getElementById('tooltip');
        
        components.forEach(component => {
            component.addEventListener('mouseenter', (e) => {
                const tooltipText = e.target.getAttribute('data-tooltip');
                if (tooltipText) {
                    tooltip.textContent = tooltipText;
                    tooltip.style.display = 'block';
                }
            });
            
            component.addEventListener('mousemove', (e) => {
                tooltip.style.left = e.pageX + 10 + 'px';
                tooltip.style.top = e.pageY + 10 + 'px';
            });
            
            component.addEventListener('mouseleave', () => {
                tooltip.style.display = 'none';
            });
        });
        
        // Add pulsing effect to data flow
        const dataFlow = document.querySelector('.data-flow');
        let pulsePosition = 0;
        
        setInterval(() => {
            pulsePosition += 2;
            if (pulsePosition > 100) pulsePosition = 0;
            
            const beforeElement = dataFlow.querySelector('::before') || dataFlow;
            if (beforeElement.style) {
                beforeElement.style.top = pulsePosition + '%';
            }
        }, 50);
    </script>
</body>
</html>
