# MineGuard Interactive Simulation

The MineGuard browser simulation demonstrates the proposed mine-vehicle safety logic under normal and low-visibility conditions.

## Open the simulation

Open `mineguard.html` in a modern desktop browser.

## Available controls

- Visibility / fog distance
- Normal, light-fog and dense-fog modes
- Dust and rain conditions
- Ego and other vehicle speed
- Forward/reverse direction
- Loaded/empty vehicle state
- Opposite-lane blockage
- Thermal camera, LiDAR, GPS and communication status
- AI detection and confidence
- Detected object type

## Demonstration scenarios

- Normal Visibility
- Light Fog
- Dense Fog
- Stationary Truck Ahead
- Blind Corner
- Communication Failure
- Thermal Camera Failure
- LiDAR Degradation

## Safety logic demonstrated

The simulation combines object classification, distance, vehicle speed, relative speed, visibility, sensor health and communication status to calculate a risk state. It also demonstrates visibility-adaptive speed recommendations, driver warnings, control-room reporting and local fail-safe behavior.

A communication failure scenario includes a 10-second local fail-safe auto-stop sequence. Sensor faults cause conservative operation and are reported to the control room.

## Important

This simulation is a prototype and should not be treated as a certified vehicle-control or mine-safety system. Real deployment requires hardware validation, calibration, safety analysis, mine-specific operating rules and appropriate certification.
