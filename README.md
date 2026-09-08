# MineGuard — Safe & Efficient Mine Vehicle Safety System

> **SIH Prototype | Open-Cast Iron Ore Mines | Fog & Low-Visibility Operations**

MineGuard is a cost-conscious safety and efficiency concept for mine haul vehicles operating in fog, dust, rain and other low-visibility conditions. It combines thermal imaging, LiDAR, AI-based object detection, ultrasonic fallback sensing, GPS, vehicle/load information and communication with a control room.

## Problem

Dense fog and poor visibility can reduce the driver's ability to detect trucks, people, rocks and other hazards early enough. MineGuard aims to provide an additional sensing and fail-safe layer without depending on a single sensor.

## Core Objectives

- Detect vehicles and hazards in low visibility.
- Give the driver early warnings and visibility-adaptive speed advice.
- Calculate collision risk using distance, relative motion and vehicle state.
- Use thermal imaging as the major sensing source when visible-light conditions are poor.
- Use LiDAR for distance/geometry information and sensor fusion.
- Use ultrasonic sensing as a local fallback/threshold detector.
- Detect sensor/communication failures and move to a safe state.
- Send important events to a control room.
- Support traffic decisions such as lane change, waiting and clearance-bay behavior.
- Monitor vehicle load state, GPS position and mine entry/exit.
- Estimate operational efficiency while maintaining safety.

## System Flow

```text
Thermal Camera ─┐
LiDAR ──────────┤
Ultrasonic ─────┤
GPS ────────────┤
Vehicle/Load ───┤ → Sensor Fusion → AI/Object Detection → Risk Engine
Weather/Fog ────┘                                      ↓
                                      Speed Advisory / Driver Warning
                                                        ↓
                                           Local Fail-Safe Protection
                                                        ↓
                                             V2X / Control Room
```

## Sensors and Functions

| Module | Main purpose |
|---|---|
| Thermal camera | Detect heat signatures of trucks, people and other objects in poor visibility |
| LiDAR | Distance and spatial information; supports sensor fusion |
| Ultrasonic | Short-range fallback/threshold detection |
| GPS | Vehicle position, heading and mine entry/exit information |
| Weather/visibility input | Fog, dust and rain condition assessment |
| Load sensor/state | Distinguish loaded and empty haul vehicles |
| Communication/V2X | Exchange warnings/events with control room or other vehicles |

### Important design decision

LiDAR performance can be affected by dense fog because of scattering. Therefore the concept does **not** treat LiDAR as the only safety sensor. Thermal sensing is prioritized for object detection, while LiDAR and ultrasonic sensing provide complementary/fallback information.

## Safety Logic

### Normal visibility

- Empty truck approaches a loaded truck.
- System checks whether the opposite/second lane is clear.
- If clear, the empty truck changes lane and passes safely.
- After the loaded truck has moved sufficiently ahead, the empty truck returns to the main lane.
- Prototype normal operating speed target: **25 km/h**.

### Dirt/rain condition

- Same traffic-conflict logic is maintained.
- Speed is reduced to approximately **15 km/h** in the prototype.
- Wet/dust conditions increase the required safety margin.

### Fog conditions

- Visibility is continuously represented in the simulation.
- Speed recommendations reduce as visibility worsens.
- Dense fog uses the most conservative speed policy.
- Thermal sensing remains the primary object-detection path.

### Blocked lane

If the passing lane is blocked, the empty truck does not repeatedly attempt lane changes. It reverses toward a designated clearance/waiting bay and waits until the route is safe.

### Communication failure

- Local safety logic continues operating.
- If communication remains unavailable, the prototype applies a fail-safe after approximately **10 seconds**.
- A loaded vehicle is commanded to stop in the fail-safe condition.
- If the alternate lane is safe, an empty vehicle may still use the local traffic maneuver logic; if it is blocked, vehicles stop/wait.

### Thermal camera failure

The prototype represents camera contamination/failure, including a cleaning/wiper concept. If the camera remains unavailable after the cleaning attempt, the system enters a degraded/fail-safe state rather than silently trusting an unavailable sensor.

## Prototype Hardware Direction

- Raspberry Pi Pico / suitable embedded controller for prototype control.
- Thermal camera module.
- LiDAR module.
- Ultrasonic sensor.
- GPS module.
- Load/weight sensing interface.
- Wireless communication interface.
- Driver display/buzzer/indicator.
- Camera cleaning/wiper mechanism.

The early prototype cost direction discussed for the project was approximately ₹15,000, with example component estimates of about ₹4,000 for the thermal camera, ₹3,000 for LiDAR and ₹3,000 for the controller. Actual prices depend on selected parts and supplier.

## AI Approach

The AI layer is intended to identify thermal signatures and classify relevant objects such as:

- Truck
- Person
- Rock
- Unknown object

The prototype uses an AI confidence value and object classification as inputs to the safety decision layer. Edge Impulse is suitable for the initial model-training workflow.

## MineGuard Browser Simulation

The repository is designed to include the supplied single-file HTML simulation:

`simulation/mineguard.html`

The simulation contains:

1. Normal Visibility
2. Light Fog
3. Dense Fog
4. Stationary Truck Ahead
5. Blind Corner
6. Communication Failure
7. Thermal Camera Failure
8. LiDAR Degradation

It also demonstrates driver-cabin information, sensor fusion, collision-risk assessment, physics-based efficiency, control-room status, fail-safe state and an event timeline.

## Suggested Repository Structure

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

## Validation and Safety Note

MineGuard is an engineering prototype and simulation, not a certified vehicle safety system. Stopping distances, sensor ranges, speed limits, fail-safe behavior, mine-road rules, radio links and thresholds must be validated on the target vehicle and site before any real-world deployment. A production system must follow the applicable mine-safety, machinery, functional-safety and wireless requirements.

## Development Status

🚧 **Prototype / SIH development**

## Team Pitch

**MineGuard does not depend on one sensor. It combines thermal vision, ranging, local fallback sensing, AI and fail-safe control so that mine vehicles can make safer decisions when normal visibility is poor.**