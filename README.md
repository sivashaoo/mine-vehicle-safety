# MineGuard — Mine Vehicle Safety System

AI-assisted safety and efficiency system for mine vehicles operating in fog and low-visibility conditions in open-cast iron ore mines.

## Project Goal

MineGuard is designed to improve mine-vehicle safety when visibility is poor by combining thermal imaging, LiDAR, GPS, AI object detection, vehicle information, communication with a control room, and local fail-safe protection.

## Main Features

- Thermal-camera-based object detection
- AI object classification and confidence monitoring
- LiDAR distance measurement
- GPS position and heading information
- Dynamic safe-distance and collision-risk calculation
- Visibility-adaptive speed recommendations
- Driver cabin warning/display
- Control-room monitoring
- Communication-failure fail-safe operation
- Automatic vehicle stop for critical conditions
- Traffic-conflict handling for mine haul roads
- Efficiency estimation based on vehicle operation and safety events
- Simulation scenarios for fog, sensor faults, communication failure and traffic hazards

## MineGuard Simulation

The project includes an interactive browser-based simulation named **MineGuard — Safe & Efficient Operation of Mine Vehicles in Fog | SIH Prototype**. The simulation provides controls for visibility/fog, vehicle speed and load state, sensors, communication, AI confidence and multiple safety scenarios.

### Simulation scenarios

1. Normal Visibility
2. Light Fog
3. Dense Fog
4. Stationary Truck Ahead
5. Blind Corner
6. Communication Failure
7. Thermal Camera Failure
8. LiDAR Degradation

The simulation also contains driver-cabin information, sensor-fusion/risk-engine data, a control-room dashboard, fail-safe status, event timeline and a physics-based efficiency module.

## Repository Structure

```text
mine-vehicle-safety/
├── README.md
├── docs/
│   ├── system-architecture.md
│   ├── safety-logic.md
│   ├── prototype-roadmap.md
│   └── test-plan.md
├── hardware/
│   ├── bill-of-materials.md
│   └── pinout.md
├── ai/
│   └── README.md
├── firmware/
│   └── README.md
└── simulation/
    ├── README.md
    └── mineguard.html
```

## Prototype Note

This is an engineering prototype for demonstration, simulation and validation. Sensor specifications, calibration values, stopping distances, speed limits and protection thresholds must be validated against the actual mine vehicle, road geometry, operating procedures and applicable safety standards before any real-world deployment.

## Technology Direction

**Sensing → AI detection → Sensor fusion → Risk assessment → Driver warning → Local fail-safe → Control-room communication**

## Status

🚧 Prototype / SIH development
