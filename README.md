# Autonomous-Vehicle-System-Architecture

graph TB
    subgraph "Sensor Layer"
        A1[LiDAR] 
        A2[Cameras]
        A3[Radar]
        A4[Ultrasonic]
        A5[GPS/GNSS]
        A6[IMU]
    end
    
    subgraph "Perception Layer"
        B1[Sensor Fusion]
        B2[Object Detection]
        B3[3D Reconstruction]
        B4[Lane Detection]
    end
    
    subgraph "Localization & Mapping"
        C1[SLAM]
        C2[HD Map Integration]
        C3[Map Matching]
    end
    
    subgraph "Prediction Layer"
        D1[Behavior Prediction]
        D2[Risk Assessment]
        D3[Intent Recognition]
    end
    
    subgraph "Planning Layer"
        E1[Route Planning]
        E2[Behavior Planning]
        E3[Motion Planning]
    end
    
    subgraph "Control Layer"
        F1[Path Following]
        F2[Speed Control]
        F3[Actuator Interface]
    end
    
    A1 & A2 & A3 & A4 & A5 & A6 --> B1
    B1 --> B2 & B3 & B4
    B2 & B3 & B4 --> C1
    C1 --> C2 --> C3
    C3 --> D1
    D1 --> D2 --> D3
    D3 --> E1
    E1 --> E2 --> E3
    E3 --> F1
    F1 --> F2 --> F3
    
    classDef sensorClass fill:#ff6b6b,stroke:#fff,stroke-width:2px
    classDef perceptionClass fill:#ffd93d,stroke:#fff,stroke-width:2px
    classDef localizationClass fill:#6bcf7f,stroke:#fff,stroke-width:2px
    classDef predictionClass fill:#e056fd,stroke:#fff,stroke-width:2px
    classDef planningClass fill:#00b894,stroke:#fff,stroke-width:2px
    classDef controlClass fill:#74b9ff,stroke:#fff,stroke-width:2px
    
    class A1,A2,A3,A4,A5,A6 sensorClass
    class B1,B2,B3,B4 perceptionClass
    class C1,C2,C3 localizationClass
    class D1,D2,D3 predictionClass
    class E1,E2,E3 planningClass
    class F1,F2,F3 controlClass
