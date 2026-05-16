# README.md

# Wild Pebble

A generative rhythm and melody organism for the
Music Thing Modular Workshop Computer.

Inspired by the spirit of Jonah Senzel's Pet Rock.

Wild Pebble creates evolving rhythmic structures, quantised melodic patterns, modulation voltages, and clocked sample-and-hold noise textures using lightweight integer-only sequencing logic.

The goal is not precise repeatability, but constrained musical evolution.

---

# Features

* Dual probabilistic trigger streams
* Quantised melodic CV generation
* Clocked sample-and-hold noise voice
* Self-mutating sequence behaviour
* Phrase replication and variation
* Slowly rotating scale system
* Internal tension modulation
* External or internal clocking
* Swing timing modes
* Integer-only DSP and sequencing
* Low CPU usage

---

# Outputs

## Pulse Output 1

Primary rhythm stream.

Used internally to drive:

* melodic progression
* click percussion output

---

## Pulse Output 2

Derived companion rhythm stream.

Used internally to:

* trigger sample-and-hold noise updates
* create correlated rhythmic modulation

---

## CV Output 1

Quantised melodic pitch output.

Generated from evolving scale-constrained note sequences.

---

## CV Output 2

Energy/tension modulation output.

A smoothed evolving modulation source derived from:

* step energy
* accent
* internal tension state

---

## Audio Output 1

Minimal transient percussion/click voice.

Generated from:

* trigger pulses
* accent values
* simple bipolar transient shaping

---

## Audio Output 2

Clocked sample-and-hold noise voice.

Unlike white noise, the random value is only updated when Pulse 2 fires.

This creates:

* rhythmic stepped noise
* pseudo-analog sample-and-hold textures
* correlated percussion bursts
* evolving modulation-like audio

---

# Controls

## Main Knob

Controls internal clock speed.

Ignored when external clock is present.

---

## X Knob

Controls rhythmic density.

Higher values increase trigger probability.

CV Input 1 modulates density.

---

## Y Knob

Controls mutation intensity.

Higher values increase:

* sequence mutation
* melodic movement
* structural instability

CV Input 2 modulates mutation amount.

---

## Switch Modes

### Up

* stable melodic motion
* minimal swing
* conservative mutation

### Middle

* balanced mutation
* moderate swing
* wider melodic motion

### Down

* aggressive mutation
* strongest swing
* larger melodic jumps
* denser companion triggers

---

# External Inputs

## Pulse Input 1

External clock input.

Automatically overrides the internal clock while active.

---

## Pulse Input 2

Freeze input.

While held high:

* mutation is disabled
* current structure is preserved

Clocking and playback continue normally.

---

# Sequencing Behaviour

Wild Pebble continuously evolves using:

* probabilistic trigger generation
* constrained mutation resistance
* phrase copying
* harmonic rotation
* tension cycling

The system is designed to preserve recognisable musical structure while gradually transforming over long time scales.

---

# Technical Notes

## Integer-Only Design

All sequencing and DSP logic uses integer arithmetic.

This reduces:

* CPU load
* timing instability
* floating point overhead

---

## Clocked Sample-and-Hold

Noise generation uses a held random value:

```cpp
if(pulse2)
{
    heldNoise =
        ((int32_t)(Random() & 255) - 128);
}
```

The value remains stable between trigger events.

This produces more musical behaviour than continuous white noise.

---

## RNG

Wild Pebble uses a lightweight xorshift pseudo-random generator seeded from:

* RP2040 unique board ID
* live control states

Each hardware unit therefore develops slightly different long-term behaviour.

---

# Building

Requires:

* Raspberry Pi Pico SDK
* Workshop Computer framework

Typical build flow:

```bash
mkdir build
cd build
cmake ..
make
```

---

# CPU Design Goals

Wild Pebble is intentionally lightweight.

Optimisations include:

* no floating point DSP
* no dynamic memory allocation
* event-rate random generation
* low-rate LED updates
* compact integer sequencing

Designed for stable performance on Workshop Computer hardware at 144 MHz.

---

# Philosophy

Wild Pebble is intended to feel less like a fixed sequencer and more like a small autonomous musical system.

The interaction between:

* mutation
* repetition
* probability
* tension
* harmonic drift
* sample-and-hold noise

creates continuously evolving patterns that remain musically coherent.
