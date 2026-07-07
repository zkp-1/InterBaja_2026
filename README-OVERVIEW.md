# InterBaja_2026
Repo of Electrical Team for the pre-existing vehicle electrical system design from scratch.

# Electrical System Retrofit for Existing BAJA Vehicle

## System Overview
This repository contains the electrical system design and schematics for retrofitting a legacy BAJA competition car from the Interamerican University of Puerto Rico (Bayamon Campus). The vehicle originally featured no onboard electrical system. The new designed architecture provides reliable power distribution, relay-driven load switching, and essential safety measures.

Due to current hardware availability and specific application requirements, the system is split into two schematic variants:
1. **[Final System Design.pdf] (Current Implementation):** Operates entirely on pre-charged onboard batteries[cite: 2].
2. **[Final System Design (with Alternator).pdf] (Alternate Implementation):** Includes an integrated charging circuit (Alternator -> Filtered Rectifier -> Voltage Regulator -> Battery Terminals) which can be implemented, given that an alternator can be .

## Power Delivery & Management

* **Dual-Battery Configuration:** The system utilizes two 12V 12Ah (or bigger Amp-hour capacity) batteries wired in parallel. This upgrade from a single battery was necessary to increase the total Amp-hour (Ah) capacity of the system, ensuring sustained operation without an active charging source.
* **Magneto Isolation:** During initial testing, tapping the engine's built-in magneto as an AC source overloaded the circuit. Completing the circuit by attaching the ground to the AC pin of the bridge rectifier caused severe voltage sag, resulting in a loss of engine spark and subsequent stalling. Therefore, the magneto is strictly isolated and dedicated solely to the car's ignition system. 
* **Charging State:** In the current "Main Design" configuration, there is no self-charging capability. The batteries must be fully charged prior to operational use. The only exception, is when using the "Main Design with Alternator" Variant which provides self-charging and should also run without batteries.

## Switching, Logic, & Loads

* **Safety Cut-offs:** A main kill switch is integrated to shut down the main bus immediately in the event of an emergency or to disable the +12V bus during testing. 
* **Relay Logic:** Standard SPST-NO relays are used to reliably control the load distribution for the brake lights and other auxiliary systems.
* **Load Provisions (DNP):** The system design includes the necessary wiring and relay logic for a Reverse Light and a designated "Third Load". These are currently marked as DNP (Do Not Populate) with an 'X' as they are unused in the present application, but the infrastructure remains for future plug-and-play capability.
* **Relay Flyback protection:** Flyback and protection diodes across the system are standard diodes or typical power diodes to safely handle inductive loads. These should at least be rated for 1A.

## Roadmap & Future Improvements

The current electrical framework provides a solid, modular foundation for the following expansions:
* **Active Charging System:** Installing a belt-driven alternator to utilize the **[Final System Design (with Alternator).pdf]** schematic, enabling self-charging.
* **Microcontroller Integration:** Adding an onboard MCU (e.g., Arduino, Teensy, or ESP32) to process and transmit vehicle telemetry.
* **Instrumentation:** 
  * RPM Gauge utilizing a Hall Effect sensor on the drivetrain/engine.
  * Fuel level sensor and dedicated dashboard gauge.
  * System Voltage monitor to track battery depletion or system voltage during operation.
