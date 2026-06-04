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

---# N20 Motor — Moiré Fringe Analysis (Multi-Take Study)

> **Systematic investigation of periodic Moiré fringe artifacts in high-speed N20 DC motor video capture**  
> 4 repeated takes recorded to characterize fringe occurrence frequency and temporal behavior.

---

## 📹 Videos

| File | Take | Duration | Description |
|---|---|---|---|
| `n20_moire_take1.mp4` | Take 1 | 44s | Longest run — 14 fringe events detected |
| `n20_moire_take2.mp4` | Take 2 | 26s | 11 fringe events, ~2.26s mean interval |
| `n20_moire_take3.mp4` | Take 3 | 28s | Highest fringe rate (~1.0 Hz) |
| `n20_moire_take4.mp4` | Take 4 | 34s | 12 fringe events, ~2.56s mean interval |

---

## 📊 Analysis Results

### FFT — Dominant Fringe Frequencies

| Take | Top Frequency | Period | Notes |
|---|---|---|---|
| Take 1 | 0.091 Hz | 11.0 s | Very slow oscillation |
| Take 2 | 0.349 Hz | 2.87 s | Mid-range |
| Take 3 | 0.389 Hz | 2.57 s | Multiple harmonics visible |
| Take 4 | 0.145 Hz | 6.89 s | Low-frequency dominant |

### Fringe Event Statistics

| Take | Events | Mean Interval | Std Dev | Est. Freq |
|---|---|---|---|---|
| Take 1 | 14 | 3.23 s | ±7.07 s | 0.310 Hz |
| Take 2 | 11 | 2.26 s | ±4.03 s | 0.442 Hz |
| Take 3 | 9  | 0.98 s | ±0.40 s | 1.018 Hz |
| Take 4 | 12 | 2.56 s | ±5.48 s | 0.390 Hz |

> **Key finding:** The large standard deviation (std >> mean in Takes 1, 2, 4) confirms that fringe occurrence is **quasi-periodic and irregular**, not strictly periodic — consistent with motor RPM micro-fluctuations causing the aliasing condition to be met intermittently.

---

## 🔍 Analysis Plots

| Plot | Description |
|---|---|
| `plot1_timeseries.png` | Per-frame brightness with Hilbert envelope + fringe event markers |
| `plot2_fft.png` | FFT power spectrum — dominant fringe frequency per take |
| `plot3_spectrogram.png` | STFT spectrogram — time-frequency evolution |
| `plot4_histogram.png` | Inter-arrival time distribution of fringe events |
| `plot5_summary.png` | Overlaid FFT comparison + event count bar chart |

---

## 🧠 Physical Interpretation

```
Moiré fringe appearance condition:
  f_fringe ≈ |f_motor_rotation × N_blades - f_camera × k|

Where:
  f_motor    = motor shaft rotation frequency (Hz)
  N_blades   = number of periodic features on shaft (slots, marks, etc.)
  f_camera   = 29.91 fps (measured)
  k          = integer (aliasing order)
```

The fringes appear **intermittently** because:
1. Motor RPM fluctuates slightly due to load variations and brush contact
2. When the aliasing condition is met → fringe appears
3. As RPM drifts away → fringe disappears
4. Repeat → quasi-periodic fringe rhythm (~0.1–1.0 Hz)

---

## 📂 Repository Structure

```
.
├── README.md
├── n20_moire_take1.mp4          # 44s compressed video
├── n20_moire_take2.mp4          # 26s compressed video
├── n20_moire_take3.mp4          # 28s compressed video
├── n20_moire_take4.mp4          # 34s compressed video
├── plot1_timeseries.png         # Brightness time series
├── plot2_fft.png                # FFT power spectrum
├── plot3_spectrogram.png        # STFT spectrogram
├── plot4_histogram.png          # Fringe inter-arrival histogram
└── plot5_summary.png            # Summary comparison
```

---

## 🛠️ Analysis Method

- **Tool:** Python 3, OpenCV, NumPy, SciPy, Matplotlib
- **Signal:** Per-frame mean brightness of center ROI (50% crop)
- **Fringe detection:** Negative peak detection on detrended brightness signal
- **Frequency analysis:** Hanning-windowed FFT + STFT spectrogram
- **Camera:** 1280×720 @ ~29.91 fps, rolling shutter (H.264)

---

## 📄 License

MIT — free for research and educational use.

## 📄 License

MIT License — free to use for research and educational purposes.
