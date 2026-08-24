# Tank Level Control Simulation (CODESYS — FBD + ST)

A simulated tank level control system built in CODESYS, combining Function
Block Diagram (FBD) and Structured Text (ST), with automatic/manual pump
control, HMI visualization, and a latched high-level safety interlock.

## Video Demonstration
The video demonstration showcasing the system logic and HMI features can be accessed here https://youtu.be/_G4MfmdS9TY

## Overview

This project simulates a real industrial level-control application: a tank
is filled/drained via a simulated process variable, with a PLC controlling a
pump automatically based on high/low level setpoints, or manually via
operator control. It was also used as a first hands-on project for learning
Structured Text alongside existing FBD/Ladder knowledge.

## Features

- **Auto/Manual pump control** — SR-latch-based mode switching in FBD
- **High/Low level sensors** driving automatic pump start/stop
- **ST-based level simulation** (`SimulateLevel` action) modeling tank
  fill/drain behavior via an INT-scaled level variable
- **HMI visualization** with a live tank-level progress bar
- **HighHigh level alarm** — latched, interlocks the pump off while active,
  and requires a manual fault reset from the HMI (built independently)

## System Architecture

- **Language mix:** FBD (main control logic) + ST (level simulation action)
- **Platform:** CODESYS
- **I/O:** [Start, Stop, Auto/Manual
  switch, High level sensor, Low level sensor, HighHigh alarm sensor, Pump
  output]

## How It Works

1. `SimulateLevel` (ST) increments/decrements a tank level variable to model
   filling and draining.
2. The main FBD program reads the level against High/Low setpoints.
3. In **Auto mode**, an SR latch starts the pump on Low level and stops it
   on High level.
4. In **Manual mode**, the operator directly controls the pump from the HMI.
5. If level reaches **HighHigh**, a latched alarm engages: the pump is
   interlocked off regardless of mode, and an alarm indication is triggered
   until cleared via a dedicated fault reset on the HMI.

   
