# Acoustic Ear — Public Results Notes

Last updated: September 24, 2026.

This file is a public, sanitized summary of measured project evidence. Raw recordings, private development paths, restricted data, credentials, and internal machine artifacts are intentionally omitted.

## Evaluation rule

The frozen scorer uses one-to-one exact-MIDI matching with a 0.10-second onset tolerance. Reference offsets are not scored. These settings are preserved across the results below.

**Important limitation:** attack onsets were human-reviewed, but performed pitches were not independently verified. Metrics are therefore conditional on the intended pitch labels used by the controlled recording protocol.

## Experiment 001 — first real-microphone baseline

Reference setup: Martin D-18, Samson Meteor USB microphone, stock Basic Pitch 0.4.0.

- 6 reviewed reference attacks
- 26 predicted events
- 3 matches
- 3 misses
- 23 unmatched predictions
- precision: 0.115385
- recall: 0.500000
- F1: 0.187500
- mean absolute matched onset error: 12.07 ms

This is a deliberately preserved baseline. No thresholds or labels were changed to improve the result.

## Experiment 002 — five-take repeatability

Five complete takes were scored; one partial take was preserved and excluded rather than silently replaced.

Across the five scored takes:

- 31 reviewed reference attacks
- 117 predictions
- 31 matches
- 0 misses
- 86 unmatched predictions
- precision: 0.265
- recall: 1.000
- F1: 0.419
- mean absolute onset error: 5.4 ms

This prompted open-string test is not evidence of accuracy on natural music.

## Repeated unmatched-prediction pattern

Across the five repeatability takes:

- MIDI 32 / G♯1 appeared unmatched 37 times
- it appeared in all five takes
- 24 of those G♯1 events occurred completely before the first reviewed guitar attack
- 27 unmatched events of any pitch occurred before the first reviewed attack
- extra E4 and G4 predictions also recurred

This localizes a repeatable mismatch but does **not** establish its acoustic or model cause.

The next controlled experiment separates room-only sound, instrument handling with damped strings, damped/free E2 and G3 conditions, and isolated high E4 before any model threshold or architecture is changed.

## Single-WAV transcription workflow

A real 25-second repeatability WAV completed the normal Acoustic Ear transcription path and produced:

- JSON report
- note-event CSV
- MIDI transcription

For that WAV, the normal Basic Pitch CLI produced the same 22 MIDI/onset/offset event records as the archived CUDA inference result. The ordinary CLI selected ONNX Runtime's CPU provider, so this observation is not a CPU/GPU speed comparison.

Scored against that take's reviewed reference:

- 6 matches
- 0 misses
- 16 unmatched predictions
- F1: 0.428571

This establishes a working single-file transcription workflow, not general transcription accuracy.

## Engineering support

The project also includes:

- dataset provenance and integrity checks
- immutable experiment outputs and hashes
- a guided local research recorder
- a local chromatic/browser tuner
- frozen scoring rules
- planned controlled experiments for tempo, dynamics, sustain/muting, monophonic music, flatpicking, polyphony, techniques, recording robustness, model comparison, controlled adaptation, and held-out acceptance

## What is not claimed

Acoustic Ear does not currently claim:

- state-of-the-art transcription
- reliable transcription of natural songs
- verified pitch-label accuracy for the current open-string experiments
- a known cause for the recurring G♯1/E4/G4 unmatched predictions
- model superiority
- a CPU/GPU speedup
- completed training or fine-tuning

The project is still in controlled characterization. The purpose of publishing these early results is to make later improvements auditable rather than impressive-looking.
