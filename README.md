# N20 Motor High-Speed Rotation — Moiré Fringe Artifact Analysis

> **Demonstrating periodic Moiré fringe patterns caused by rolling shutter + high RPM mismatch in N20 DC motors**

---

## 📹 Demo

https://github.com/YOUR_USERNAME/YOUR_REPO/assets/YOUR_ID/n20_moire_fringe_720p.mp4

*(Replace with your actual GitHub asset URL after uploading)*

---

## 📌 Overview

This repository documents a visual artifact phenomenon observed when filming an **N20 micro DC motor** running at high speed using a digital camera sensor.

When the motor RPM aligns (or partially aliases) with the camera's frame rate and rolling shutter scan rate, **periodic bright/dark banding patterns — known as Moiré fringes — appear on the rotating shaft or motor body**.

---

## 🔍 What is a Moiré Fringe?

A **Moiré fringe** is an interference pattern that emerges when two periodic structures (or frequencies) interact. In the context of motor video capture:

| Factor | Description |
|---|---|
| Motor RPM | High rotation speed of N20 gear/shaft |
| Camera frame rate | e.g., 30fps / 60fps / 240fps |
| Rolling shutter | Line-by-line sensor scan creates temporal skew |
| Aliasing | When RPM ÷ fps produces near-integer ratio → fringes appear |

The fringes appear **periodically** because the aliasing condition is met and broken cyclically as motor speed fluctuates slightly.

---

## 🎥 Capture Conditions

| Parameter | Value |
|---|---|
| Motor | N20 DC Micro Motor |
| Resolution | 1280 × 720 |
| Observed artifact | Periodic Moiré banding on rotating parts |
| Fringe occurrence | Periodic / intermittent |

---

## 🛠️ How to Reproduce

1. Mount an N20 motor vertically or horizontally
2. Power at rated voltage (e.g., 3–6V) to achieve high RPM
3. Record video at standard frame rates (30fps or 60fps)
4. Observe banding patterns on the rotating shaft — fringes will appear and disappear periodically

---

## 💡 Mitigation Strategies

- **Increase frame rate** (120fps / 240fps) to shift the aliasing condition
- **Use global shutter camera** to eliminate rolling shutter contribution
- **Vary motor voltage** slightly to shift RPM away from alias frequency
- **Apply optical low-pass filter** in post-processing to reduce fringe visibility

---

## 📂 Repository Structure

```
.
├── README.md
└── n20_moire_fringe_720p.mp4   # Compressed demo video (GitHub-friendly)
```

---

## 📄 License

MIT License — free to use for research and educational purposes.
