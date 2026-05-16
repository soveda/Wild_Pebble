# Wild Pebble

A playable generative rhythm and melody organism
for the Music Thing Modular Workshop Computer.

Wild Pebble is inspired by the spirit of generative
modular systems like Pet Rock, but adapted for the
Workshop Computer's constraints and strengths.

It is designed to feel:
- alive
- musical
- patchable
- slightly unpredictable
- but never completely chaotic

The card continuously evolves rhythms, melodies,
and modulation signals while preserving recurring
motifs and groove identity.

---

# Main Features

- Two evolving trigger outputs
- Quantised melodic CV output
- Expressive modulation/energy CV
- Phrase memory and motif reuse
- Constrained mutation engine
- Behaviour personalities
- Internal tension/release cycles
- Swing and syncopation
- Internal or external clocking
- Lightweight integer-only DSP

---

# Controls

| Control | Function |
|---|---|
| Main knob | Tempo |
| X knob | Rhythm density |
| Y knob | Mutation amount |

---

# Switch Modes

| Position | Personality |
|---|---|
| Up | Hypnotic and repetitive |
| Middle | Curious and evolving |
| Down | Nervous and glitchy |

These modes affect:
- rhythmic mutation
- melodic movement
- swing behaviour
- syncopation
- phrase stability
- tension behaviour

---

# Inputs

| Input | Function |
|---|---|
| Pulse In 1 | External clock |
| Pulse In 2 | Freeze sequence evolution |
| CV In 1 | Density modulation |
| CV In 2 | Mutation modulation |

---

# Outputs

| Output | Function |
|---|---|
| Pulse Out 1 | Main groove |
| Pulse Out 2 | Companion rhythm |
| CV Out 1 | Quantised melody |
| CV Out 2 | Energy/modulation contour |
| Audio Out 1 | Percussive click monitor |
| Audio Out 2 | Noise/percussion texture |

---

# Musical Behaviour

Wild Pebble is intentionally designed to avoid
pure randomness.

Instead, it uses:
- rhythmic memory
- weighted melodic movement
- phrase copying
- tension/release cycles
- groove preservation
- constrained mutation

This creates sequences that gradually evolve
without losing their musical identity.

---

# Energy CV

CV Out 2 is not a second melody.

Instead, it outputs a continuously evolving
"energy" signal derived from:
- accent behaviour
- mutation activity
- rhythmic density
- tension state
- phrase transitions

Useful patch targets:
- filter cutoff
- wavefolder amount
- VCA level
- reverb depth
- FM amount
- LPG dynamics

---

# Freeze Behaviour

Holding Pulse Input 2 high freezes sequence mutation.

The pattern continues playing, but evolution pauses.

This allows performers to temporarily capture
interesting grooves before letting the system evolve again.

---

# Clock Behaviour

If an external clock is detected on Pulse In 1,
Wild Pebble synchronises automatically.

Otherwise it uses its internal clock.

Internal clock modes also introduce subtle swing
and timing personality.

---

# Technical Notes

Wild Pebble is designed specifically for the
Workshop Computer hardware.

Implementation details:

- integer-only sequencing logic
- no floating-point DSP in ProcessSample()
- fixed-size memory structures
- lightweight control-rate scheduling
- calibrated pitch output using CVOut1MIDINote()
- safe CPU usage for Workshop timing constraints

Recommended:
- 144MHz system clock
- copy_to_ram build target

---

# Patch Ideas

## Self-Playing Voice

- CV Out 1 -> oscillator pitch
- Pulse Out 1 -> envelope trigger
- CV Out 2 -> filter cutoff

Creates a complete evolving synth voice.

---

## Generative Drum Brain

- Pulse Out 1 -> kick
- Pulse Out 2 -> hats/snare
- CV Out 2 -> decay modulation

Useful for evolving percussion systems.

---

## Living Modulation Source

- CV Out 2 -> wavefolder amount
- Pulse Out 2 -> clock reset
- Audio Out 2 -> percussion texture

Turns Wild Pebble into an animated modulation organism.

---

# Design Philosophy

Wild Pebble embraces the Workshop Computer philosophy:

- constraints as creative tools
- clarity over complexity
- musical usefulness over technical purity
- behaviour over precision

Small imperfections are intentional.

The goal is not laboratory-perfect sequencing.

The goal is a tiny musical organism that feels alive.
