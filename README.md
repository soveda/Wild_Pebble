# README.md

# Wild Pebble

Still very much in Beta testing

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

Bass Drum according to Pulse 1

---

## Audio Output 2

Snare sound according to Pulse 2

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
# LED Behaviour

Wild Pebble uses the Workshop Computer’s 6 LEDs as a live visualisation of rhythm, density, mutation, and system state.

| LED   | Function     | Behaviour                                           |
| ----- | ------------ | --------------------------------------------------- |
| LED 1 | Main Trigger | Flashes when `PulseOut1` fires                      |
| LED 2 | Density      | Brightness follows Density control (`Knob X + CV1`) |
| LED 3 | Mutation     | Brightness follows Mutation amount (`Knob Y + CV2`) |
| LED 4 | Energy       | Displays smoothed internal energy/modulation level  |
| LED 5 | Clock Source | Fully lit when external clock is active             |
| LED 6 | Tension      | Displays evolving internal tension state            |

## Details

### LED 1 — Main Trigger Pulse

This LED mirrors the primary rhythm stream.

* Bright flash on every `pulse1`
* Shows groove density and rhythmic activity
* Useful for monitoring sparse probabilistic patterns

### LED 2 — Density

Represents rhythmic density.

Higher brightness means:

* more trigger probability
* denser rhythmic behaviour
* more active secondary trigger generation

Driven by:

* `Knob X`
* `CV Input 1`

### LED 3 — Mutation

Represents mutation intensity.

Higher brightness means:

* more frequent sequence mutation
* larger melodic movement
* greater rhythmic instability

Driven by:

* `Knob Y`
* `CV Input 2`

### LED 4 — Energy

Displays the smoothed internal energy system.

Energy is derived from:

* per-step energy
* accent values
* evolving tension

This LED moves slowly and organically rather than flickering rapidly.

### LED 5 — External Clock Detect

Indicates clock source.

| State | Meaning                 |
| ----- | ----------------------- |
| OFF   | Internal clock running  |
| ON    | External clock detected |

Wild Pebble automatically switches to external sync when clock pulses are received at `PulseIn1`.

### LED 6 — Tension

Displays the internal evolving tension value.



# Sequencing Behaviour

Wild Pebble continuously evolves using:

* probabilistic trigger generation
* constrained mutation resistance
* phrase copying
* harmonic rotation
* tension cycling

T

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
