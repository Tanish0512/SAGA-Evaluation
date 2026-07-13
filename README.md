# SAGA: Script-to-Audio-Generation-Agent

*Tanish Sahu, Gautham Das, Shubham Sharma, Nishant Singh, Mudit Batra, Shrikant Venkataramani, Vasu Sharma*

**Pocket FM** · [`shubham.s@pocketfm.com`](mailto:shubham.s@pocketfm.com)

> This repository accompanies the paper **"SAGA: Script-to-Audio-Generation-Agent"** and hosts the audio demos and evaluation material referenced therein.

---

## 🎧 Audio Demos

**Listen to the SAGA-mastered vs. human-mastered samples here:**

👉 **[SAGA Audio Demos](#)** *(replace this link with your hosted demo page)*

The evaluated audios range in duration from **3 to 17 minutes** (average ~8 min) and span multiple aesthetic and production dimensions.

---

## Abstract

Producing high-quality audio dramas requires herculean efforts and hours of intensive labor across analysis, generation, alignment, and mixing. This makes the process tedious for professional sound engineers and prohibitively difficult for novice creators. While a few recent automated approaches address high-level planning and speech generation, the low-level layering, placement, and mixing of background music (BGM) and sound effects (SFX) remain largely unaddressed within such end-to-end pipelines.

To bridge this gap, we present **SAGA (Script-to-Audio-Generation-Agent)**, a novel three-stage agentic framework that automates an expert sound engineer's workflow end to end — from script understanding to a final mastered episode. SAGA matches the quality of a human-in-the-loop workflow in objective evaluation scores while reducing production time from several hours to a few minutes, making it an effective tool for both expert and novice creators.

---

## Overview

SAGA transforms a raw script into a professionally mastered audio-drama episode through **three sequential lanes**:

| Lane | Stage | What it does |
|------|-------|--------------|
| **Lane A** | Multi-Agent Script Analysis | Agentic creative director: character casting, sequence segmentation, narrative extraction, SFX/BGM design, and a word-anchored intensity curve (0–10). |
| **Lane B** | Generating & Placing Audio Layers | Renders dialogue (TTS), BGM & SFX (text-to-audio), and aligns everything to a global **episode clock** using word-level anchors. |
| **Lane C** | Layering, Mixing & Mastering | Per-layer processing, scene-intensity-driven levels, loudness normalization to −16 LUFS / −1.5 dBTP (EBU R128), delivered as a 48 kHz, 24-bit stereo master. |

```
          ┌─────────── LANE A ───────────┐   ┌────────── LANE B ──────────┐   ┌──── LANE C ────┐
 Script → │ Casting · Segmentation ·     │ → │ TTS · SFX/BGM generation · │ → │ Mix & Master → │ → Mastered Audio
          │ Narrative · SFX/BGM ·        │   │ Episode Clock & Mapping    │   │ (−16 LUFS)     │
          │ Intensity extraction         │   │                            │   │                │
          └──────────────────────────────┘   └────────────────────────────┘   └────────────────┘
```

---

## Key Contributions

- **A Holistic, Automated End-to-End Production Pipeline** — a novel agentic three-lane structure that replicates the comprehensive workflow of a professional sound engineer, from script to complete mastered file.
- **Empirical Validation Against Professional Human Mixing** — SAGA delivers compelling audio dramas more *consistently* than the traditional human-in-the-loop approach, at the same quality across multiple aesthetic evaluation metrics.
- **Democratization & Turnaround Optimization** — reduces end-to-end production from hours to minutes and removes the need for deep domain expertise, making it viable for both experts and novices.

---

## Evaluation

### Objective (Meta Audiobox-Aesthetics, 1–10)

SAGA is competitive with human mastering on every axis and **significantly leads on Production Complexity**, while being **more consistent** across episodes (std. dev. ~2× smaller than human on every axis).

- **Content Enjoyment (CE)**, **Content Usefulness (CU)**: SAGA matches or exceeds human on 3 of 4 axes.
- **Production Complexity (PC)**: largest gap, **+0.99** in SAGA's favor.
- Evaluated over **35 episodes**.

### Production Time per Episode (Human vs. SAGA)

| Pipeline lane | Human | SAGA | Speedup |
|---|---|---|---|
| Script analysis | 2 h | 5 min | 25× |
| Audio layer creation | 8 h | 12 min | 40× |
| Layering, mix & master | 1 h | 1 min | 60× |
| **Total / episode** | **~11 h** | **~18 min** | **~40×** |

### Subjective Ratings by Professional Sound Engineers

| Dimension | Human Mastered (mean ± 95% CI) | SAGA (mean ± 95% CI) |
|---|---|---|
| Overall Audio Quality | 7.48 ± 0.21 | 5.56 ± 0.24 |
| Music Quality | 6.90 ± 0.27 | 5.38 ± 0.29 |
| Music Mood Mapping | 6.66 ± 0.36 | 5.22 ± 0.32 |
| SFX Quality | 6.86 ± 0.32 | 4.58 ± 0.23 |
| SFX Sync / Timing | 7.28 ± 0.24 | 5.78 ± 0.36 |
| Mix Balance | 6.92 ± 0.25 | 5.40 ± 0.25 |
| Audio Levels | 7.24 ± 0.26 | 6.12 ± 0.26 |

Human mastering still holds the edge in subjective ratings (widest gap on SFX quality), but SAGA attains a **consistent, broadcast-ready level** at a fraction of the time and human effort. Closing this residual gap is a clear direction for future work.

---

## Models & Tools Used

- **LLM script analysis** — Gemini 3.5 Flash, Claude Opus 4.8
- **Text-to-Speech** — ElevenLabs (Eleven v3)
- **Text-to-Audio (SFX & BGM)** — Stable Audio 3
- **Loudness / metering** — pyloudnorm, EBU R128
- **Aesthetic evaluation** — Meta Audiobox-Aesthetics

---

## Citation

If you use SAGA or refer to this work, please cite:

```bibtex
@inproceedings{sahu2026saga,
  title     = {SAGA: Script-to-Audio-Generation-Agent},
  author    = {Sahu, Tanish and Das, Gautham and Sharma, Shubham and
               Singh, Nishant and Batra, Mudit and Venkataramani, Shrikant and
               Sharma, Vasu},
  booktitle = {IEEE Spoken Language Technology Workshop (SLT)},
  year      = {2026},
  organization = {Pocket FM}
}
```

---

## Contact

For questions about the paper or demos, reach out to **[shubham.s@pocketfm.com](mailto:shubham.s@pocketfm.com)**.
