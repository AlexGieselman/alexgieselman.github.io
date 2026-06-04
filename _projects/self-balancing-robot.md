---
layout: page
title: Self-Balancing Robot
description: Two-wheeled inverted pendulum robot built for EE2850
importance: 1
category: work
---

A two-wheeled self-balancing robot designed and built for EE2850. The robot uses sensor feedback and a control loop to stay upright on two wheels, implementing the classic inverted pendulum control problem in hardware.

## Overview

The robot balances on two wheels by continuously reading its tilt angle and driving the motors to counteract any deviation from vertical. This is the same fundamental challenge as balancing a broom on your palm — the system is inherently unstable and requires constant correction.

## Hardware

- **Microcontroller:** (add your MCU here)
- **IMU:** (add your sensor, e.g. MPU-6050) for pitch angle measurement
- **Motors:** DC gear motors with encoders
- **Motor driver:** (add your driver, e.g. L298N)
- **Power:** (add your battery setup)

## Control System

The balancing is handled by a PID controller:

$$
u(t) = K_p e(t) + K_i \int_0^t e(\tau)\, d\tau + K_d \frac{de(t)}{dt}
$$

where $$ e(t) $$ is the error between the measured tilt angle and the upright setpoint. The gains $$ K_p $$, $$ K_i $$, and $$ K_d $$ were tuned experimentally.

The IMU provides raw accelerometer and gyroscope data, which are fused using a complementary filter to get a stable angle estimate:

$$
\theta = \alpha \cdot (\theta_{\text{prev}} + \omega \cdot \Delta t) + (1 - \alpha) \cdot \theta_{\text{accel}}
$$

## Results

(Add a short description of how well it worked, demo video link, or what you'd improve.)
