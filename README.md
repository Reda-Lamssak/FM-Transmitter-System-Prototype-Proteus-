# FM Transmitter System Prototype (Proteus)

This repository documents the design and simulation of a low‑power **FM transmitter** implemented and analysed using Proteus as part of the **BEJ30103 Electronic Communication Systems – Problem‑Based Learning (Task 2)** coursework.

## Project Overview

- Designed a single‑channel FM transmitter using discrete components (BC547 NPN transistors, RC biasing network, and LC tank).  
- Implemented and tested the circuit in Proteus to study the behaviour of the power‑supply filter, audio pre‑amplifier, RF oscillator, and output coupling stages.  
- Analysed the simulated time‑domain waveforms and frequency spectrum to verify the carrier frequency and the effect of the audio modulating signal.

## Circuit Architecture

The transmitter is divided into several functional blocks:

<img width="699" height="390" alt="image" src="https://github.com/user-attachments/assets/e673bcae-2297-4133-9816-ab8e4d5c4e5f" />


1. **Power Supply & Filtering**  
   - 3 V DC supply with a decoupling capacitor to reduce noise and provide a stable DC rail.  
   - Ensures that variations in the battery voltage do not significantly disturb the RF oscillator.

2. **Audio Input & Coupling**  
   - Sine‑wave audio source representing the **modulating signal**.  
   - Coupling capacitor allows the AC audio signal to pass into the circuit while blocking DC, preventing bias point shifts at the next stage.

3. **Pre‑Amplifier Stage (Q1)**  
   - First BC547 NPN transistor configured as a small‑signal amplifier.  
   - Bias resistors set the operating point; an emitter bypass/coupling capacitor passes the amplified audio to the RF stage.  
   - Increases the amplitude of the audio so that it can effectively modulate the carrier oscillator.

4. **RF Oscillator Stage (Q2 + LC Tank)**  
   - Second BC547 NPN transistor with an LC tank (inductor L1 and capacitors C5, C6) forming the **carrier oscillator**.  
   - Feedback capacitor and bias network maintain sustained oscillation.  
   - The instantaneous oscillator frequency varies with the audio‑induced change at the transistor base, producing **frequency modulation (FM)**.

5. **Output Coupling**  
   - Small coupling capacitor at the output passes the high‑frequency RF signal to either a measurement probe or a notional antenna while isolating the oscillator from load effects.

## Mathematical Model

The transmitter behaviour can be described by the following signal equations:

- **Carrier signal**  
  \( v_c(t) = V_c \sin(2 \pi f_c t) \)

- **Modulating signal**  
  \( v_m(t) = V_m \sin(2 \pi f_m t) \)

- **Frequency‑modulated signal**  
  \( v_{FM}(t) = V_c \cos\big( 2 \pi f_c t + \beta \sin(2 \pi f_m t) \big) \)

where \( f_c \) is the carrier frequency set by the LC tank, \( f_m \) is the audio frequency, and \( \beta \) is the modulation index determined by the frequency deviation.

## Simulation Results

<img width="756" height="374" alt="image" src="https://github.com/user-attachments/assets/6752a870-bdbd-452f-9f6a-87c06bebbe40" />


- The LC tank and chosen component values yield a carrier in the VHF band (around the broadcast FM range).  
- Frequency‑spectrum plots show a strong carrier component with sidebands spaced at integer multiples of the modulating frequency, characteristic of FM.

<img width="753" height="378" alt="image" src="https://github.com/user-attachments/assets/f26c2494-caba-4532-9191-d0623151c524" />


- Time‑domain waveforms demonstrate a sinusoidal RF signal whose instantaneous frequency varies with the audio input amplitude.  
- Measured carrier and modulating frequencies match the theoretical design values within simulation tolerance.

## Tools and Workflow

- **Design & Simulation:** Proteus (schematic capture and transient / frequency‑domain analysis).  
- **Tasks performed:**  
  - Selecting practical resistor, capacitor, and inductor values based on FM design equations.  
  - Building and wiring the schematic in Proteus, including probes for waveform observation.  
  - Running transient and frequency‑spectrum simulations and recording key measurements.  
  - Relating simulation results to theoretical FM signal equations.

## Possible Extensions

- Add an RF buffer/amplifier stage to drive a real antenna while isolating the oscillator.  
- Explore different audio amplitudes and frequencies to study how the modulation index affects the spectrum.  
- Compare narrowband and wideband FM operation by adjusting component values and deviation.  
- Implement a matching FM **receiver** simulation and demonstrate end‑to‑end communication in Proteus.
