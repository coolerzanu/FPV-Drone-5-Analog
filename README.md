# FPV Drone

A 5 inch analog freestyle FPV quadcopter, built from individually sourced parts on a student budget.

![Class](https://img.shields.io/badge/class-5%22%20freestyle-6f42c1)
![Video](https://img.shields.io/badge/video-5.8GHz%20analog-informational)
![Link](https://img.shields.io/badge/control-ExpressLRS%202.4GHz-success)
![Firmware](https://img.shields.io/badge/firmware-Betaflight-blue)

<img src="Media/Final.jpg" alt="Completed FPV drone" height="600">

[First flight and music video](https://drive.google.com/file/d/1u81eMg4rBYhqM3jJ49E8gZRlQipSc7sH/view?usp=sharing)

Video transmission quality in the recorded footage is degraded, because the propellers clipped the VTX antenna mid-session. See [Lessons Learned](#lessons-learned).

## Contents

- [Overview](#overview)
- [Specifications](#specifications)
- [Components](#components)
- [Build Log](#build-log)
- [Firmware Configuration](#firmware-configuration)
- [Lessons Learned](#lessons-learned)
- [Gallery](#gallery)

## Overview

In the summer of 2025 I received a $250 engineering innovation grant. My prior work was in embedded systems, specifically a modular node network for early forest fire detection, and while developing it I kept reaching the same conclusion: the platform would be far more useful airborne. Mounting the sensor nodes on a UAV turns a fixed grid into a mobile survey tool.

Instead of buying a ready-made airframe, I used the grant to build one, so that every subsystem on it would be one I had specified, soldered, and configured myself. The finished aircraft is a 5 inch analog freestyle quad assembled from individually sourced components and tuned in Betaflight.

I also spent over 30 hours learning to fly it properly, which turned out to be the harder half of the project.

<img src="Media/Setup.jpg" alt="Workbench setup" height="600">

## Specifications

| | |
|---|---|
| Class | 5 inch freestyle quadcopter |
| Propellers | 5.1 inch, 3 blade |
| Motors | 2207 or 2306 brushless |
| Stack | F405 flight controller with 40-50 A 4-in-1 ESC |
| Video | 5.8 GHz analog VTX, 1200 TVL micro camera |
| Control link | ExpressLRS 2.4 GHz nano receiver (CRSF) |
| Firmware | Betaflight |
| Tested range | approx. 200 m |
| Top speed | approx. 60 mph |
| Build cost | approx. $120 in components |

## Components

Parts were sourced individually to stay inside budget without giving up freestyle performance.

| Subsystem | Part | Notes |
|---|---|---|
| Frame | 5 inch carbon fiber freestyle frame | |
| Stack | F405 FC with 40-50 A 4-in-1 ESC | |
| Motors | 2207 or 2306 brushless, x4 | |
| VTX | 5.8 GHz analog | SmartAudio control over UART |
| Camera | 1200 TVL analog micro | |
| Receiver | ExpressLRS 2.4 GHz nano | CRSF protocol |
| Propellers | 5.1 inch, 3 blade | |

## Build Log

### 1. Frame and motors

Assembled the carbon fiber frame and mounted the four motors, routing the phase wires through the arms.

<img src="Media/FRAMEO.jpg" alt="Frame and motors assembled" height="600">

### 2. Power delivery

Worked through the ESC datasheet, then soldered the low-ESR capacitor across the power pads and attached the battery lead. The capacitor is not optional on an analog build, since it suppresses the voltage ripple that otherwise shows up as noise in the video feed.

<img src="Media/ESC.JPG" alt="ESC with capacitor and power lead soldered" height="600">

### 3. Stack assembly

Soldered the motor phase wires to the ESC and mated the flight controller to form the stack. The flight controller was an off-brand board, so the pinouts for the VTX, camera, and receiver had to be traced from its datasheet rather than assumed from a standard F405 layout.

<img src="Media/Diagram.PNG" alt="Wiring diagram" height="600">

### 4. Final assembly and flashing

Closed up the airframe, mounted the camera and antennas, and flashed Betaflight.

<img src="Media/Built.jpg" alt="Completed build" height="600">

## Firmware Configuration

Betaflight handles flight dynamics and hardware communication. The setup sequence was:

1. Flashing and ports. Flashed the current firmware target to the flight controller, then mapped the UART ports for the ELRS receiver and VTX SmartAudio.
2. Receiver. Set the protocol to CRSF for the ExpressLRS link.
3. Modes. Bound transmitter switches to arming, flight modes (Acro and Angle), and Turtle Mode for flip-over-after-crash recovery.
4. OSD. Configured the analog overlay to display battery voltage, link quality, and flight timer in the goggles.

## Lessons Learned

Antenna placement needs to be treated as a structural decision. The VTX antenna sat inside the propeller disc and was cut in half during flight, which is why the recorded footage degrades. Mounting it behind the rear arms, above the prop plane, would have avoided the problem.

Off-brand flight controllers cost time rather than money. The savings on the stack were real, but the undocumented pinout added hours of datasheet tracing that a mainstream board would not have required.

Learning to fly took far longer than building. The build itself was a fraction of the 30+ hours that acro practice took, which is worth planning for on a fixed timeline.

## Gallery

FPV goggles

<img src="Media/Goggles.jpg" alt="FPV goggles" height="600">

Field setup before the first flight

<img src="Media/Outside.jpg" alt="Outdoor setup before first flight" height="600">
