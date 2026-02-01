# Sentinex | State Estimation & Sensor Simulation Lab

Sentinex is a C++20 framework designed for the development and validation of multi-sensor state estimation algorithms. It integrates a modular Extended Kalman Filter (EKF) with a high-fidelity sensor simulation engine, enabling deterministic benchmarking of estimation accuracy against absolute "Ground Truth."

The project serves as a laboratory for analyzing how various sensor noise profiles—including GPS-denied environments and IMU bias instability—impact the reliability of vehicle localization.

## Key Features

- Deterministic Physics Simulation: A 2D vehicle kinematics engine that provides Ground Truth telemetry (Position, Heading, Velocity) as a baseline for accuracy assessment.

- Stochastic Sensor Modeling:

  - GPS: Models urban canyon effects through GPS-denied zones and configurable measurement error probabilities.

  - Gyroscope: Implements bias instability and Gaussian white noise models to simulate real-world MEMS sensor drift.

  - LiDAR: Generates range/bearing data from beacon maps, supporting configurable Data Association (DA).

  - Performance Benchmarking: Real-time tracking of RMSE (Root Mean Square Error) to quantify the divergence between the filter's estimate and the simulated vehicle state.

## Project Structure
The repository is organized to separate the simulation environment from the estimation logic, following professional software-in-the-loop (SiL) patterns:
- sentinex-core: The estimation engine. Contains the EKF implementation, state-space transition logic, and matrix abstractions.

- sentinex-sim: The simulation environment. Contains the GPSSensor, GyroSensor, and LidarSensor classes responsible for "corrupting" truth data into realistic inputs.

- sentinex-test: Unit testing and experimentation harness.

- sentinex-cli: Reference executable for running simulation scenarios and inspecting telemetry output.

---

## Prerequisites

### macOS

```bash
sudo port install clang-20 cmake doxygen
```
## Building

    mkdir .bld
    cd .bld
    cmake ..
    make -j

Also:

    make help

to see a list of possible of build targets.

## Running

Run the test and experimentation harness:

    ./sentinex-test

Run the reference CLI executable:

    ./sentinex-cli


# Contributors

- jishnuperiya@gmail.com
- jonathon.bell@gmail.com
