# University Projects

A collection of projects and lab assignments developed during my engineering studies at the **Universitat Politècnica de València (UPV)**. This repository gathers work from several courses covering **communications**, **digital signal processing**, **telematic services**, **econometrics** and **microprocessor-based systems**.

> **Author:** Oscar Jiménez Bou
> **University:** Universitat Politècnica de València (UPV)

---

## 📚 Table of contents

1. [Overview](#-overview)
2. [Repository structure](#-repository-structure)
3. [Courses and projects](#-courses-and-projects)
   - [Telematic Services Design](#1-telematic-services-design-design_telematic_services)
   - [Digital Signal Processing — Audio](#2-digital-signal-processing--audio-digital_signal_processing)
   - [Digital Signal Processing and Communications](#3-digital-signal-processing-and-communications-digital_signal_processing_comunications)
   - [Econometrics](#4-econometrics-econometrics)
   - [Microprocessor-Based Systems](#5-microprocessor-based-systems-microprocessor_systems)
4. [Technologies used](#-technologies-used)
5. [Getting started](#-getting-started)
6. [License](#-license)
7. [Contact](#-contact)

---

## 🔭 Overview

This monorepo brings together five different courses, each with its own lab assignments, datasets and documentation. The goal is to keep all my academic work in a single place, both as a personal portfolio and as a reference for future projects.

Each top-level subdirectory is an **independent project**: it can have its own dependencies, its own more detailed `README.md` and its own execution flow. This main README acts as a general guide and entry point for the whole repository.

| Course | Main technologies | Focus |
|---|---|---|
| Telematic Services Design | Python, TCP/UDP, MQTT, SMTP, TOTP | Network protocols and authentication |
| Digital Signal Processing (Audio) | Python, NumPy, SciPy, Librosa, PyTorch | Audio signals and neural networks |
| Digital Signal Processing and Communications | Python, NumPy, SciPy | Coding, compression, transforms |
| Econometrics | Python, pandas, statsmodels, SARIMAX | Econometric models and time series |
| Microprocessor-Based Systems | Motorola 68000 assembly (EASy68K) | Low-level programming |

---

## 📁 Repository structure

```
University-Projects/
├── design_telematic_services/              # Telematic Services Design
│   ├── P1/                                 # TCP/UDP + OTP
│   ├── P2/                                 # MQTT
│   ├── P3/                                 # SMTP
│   ├── requirements.txt
│   └── README.md
│
├── digital_signal_processing/              # DSP applied to audio
│   ├── P1/ … P6/                           # Labs 1–6
│   ├── Audios_model/                       # Spoken-digit classifier
│   ├── Grader/                             # MATLAB grading helpers
│   ├── Makefile
│   ├── utils.py
│   └── README.md
│
├── digital_signal_processing_comunications/ # DSP applied to communications
│   ├── P1/ … P5/                           # Labs 1–5
│   ├── data/                               # Test WAVs and images
│   └── README.md
│
├── econometrics/                           # Econometrics
│   ├── Prac4.py … Prac12.py                # Lab assignments
│   ├── Examen.py                           # Final exam
│   ├── Plantilla_A.py / Plantilla_B.py     # Working templates
│   ├── utilities.py                        # Helper functions
│   ├── *.csv / *.gdt                       # Datasets
│   └── Plots EXAMEN.pdf
│
├── microprocessor_systems/                 # Microprocessor-Based Systems
│   ├── Prac1.X68 … Prac3.2.X68             # Assembly lab assignments
│   ├── ej3.6.X68, ej3.7.X68                # Extra exercises
│   ├── ASCII.X68                           # ASCII utility
│   └── Casio/
│       ├── CasioWatch.X68                  # Casio watch with alarm and stopwatch
│       ├── Alarma.wav
│       └── Beep.wav
│
└── .gitignore
```

---

## 🎓 Courses and projects

### 1. Telematic Services Design (`design_telematic_services`)

Python implementation of three fundamental telematic-service protocols plus a two-factor authentication system.

- **Lab 1 — TCP/UDP + OTP:** TCP and UDP servers and clients, plus a TOTP-based (Time-based One-Time Password) authentication system using `pyotp`. The main client connects to a remote server sending name, national ID (DNI) and OTP code.
- **Lab 2 — MQTT:** publisher/subscriber clients built with `paho-mqtt`, wildcard support (`#`, `+`), callbacks and a request/response flow over the `DST/PETICION`, `DST/CODIGO` and `DST/SOLUCION` topics.
- **Lab 3 — SMTP:** sending emails via `smtplib`, address validation, RFC 822 compliant bodies and PDF attachments via `MIMEMultipart`. Uses the `smtp.upv.es` server.

**Main dependencies:** `pyotp`, `paho-mqtt`, `validate-email`.

For full details on scripts, topics and configuration, see [`design_telematic_services/README.md`](design_telematic_services/README.md).

---

### 2. Digital Signal Processing — Audio (`digital_signal_processing`)

A digital signal processing project focused on **audio**, going from basic analysis all the way to spoken-digit classification with neural networks.

- **P1 — Basic signal analysis:** WAV reading, time-domain plots, sampling.
- **P2 — Energy and frames:** per-frame energy, windowing.
- **P3 — Spectral analysis:** FFT and spectrograms.
- **P4 — Feature extraction:** spectral centroid, rolloff, flux, etc.
- **P5 — Feature-based classification:** classification from feature vectors (`train_spanish_2022_python.mat`, `validation_spanish_2022_python.mat`).
- **P6 — Neural network for audio:** **PyTorch** CNN trained on `base_datos_numeros_2023_AB` (~12,800 train samples, ~3,000 test samples) to recognize the digits 0–9 spoken in Spanish.
- **`Audios_model/`** — Spoken-digit classification pipeline: M4A→WAV conversion, 16 kHz resampling, Voice Activity Detection (VAD), segmentation and organization by digit.
- **`Grader/`** — MATLAB helper functions used for course grading.
- **`utils.py`** — Shared functions (`cut_signal_frames`, `detect_voice_activity`, `number_count_detector`, `spectral_centroid_spread`, `spectral_flux`, `spectral_rolloff`, `convert_m4a_to_wav`…).

**Main dependencies:** `numpy`, `scipy`, `matplotlib`, `librosa`, `pydub`, `torch`, `sounddevice`, `simpleaudio`, `tqdm`, `pandas`.

For details on each lab, see [`digital_signal_processing/README.md`](digital_signal_processing/README.md).

---

### 3. Digital Signal Processing and Communications (`digital_signal_processing_comunications`)

A project focused on **coding, compression and transforms** applied to audio and images in the context of digital communications.

- **P1 — Basic audio processing:** WAV reading/playback, normalization and visualization.
- **P2 — Image coding:** binary format conversion (grayscale and RGB), `code`/`decode` functions.
- **P3 — PCM:** pulse-code modulation applied to audio (`codPCM`, `decPCM`).
- **P4 — Lossless compression:** **Rice** coding and prediction on images.
- **P5 — DCT and filtering:** block-based Discrete Cosine Transform and filtering in the transformed domain.
- **`data/`** — Test signals: `clarinete.wav`, several voices (`v1.wav`, `v4.wav`, `vt1.wav`…) and images (`i1.png` … `i4.png`).

**Main dependencies:** `numpy`, `scipy`, `matplotlib`, `sounddevice`, `pillow`.

For details on each lab, see [`digital_signal_processing_comunications/README.md`](digital_signal_processing_comunications/README.md).

---

### 4. Econometrics (`econometrics`)

A set of lab assignments and the final exam for the econometrics course, implemented in Python as an alternative to Gretl. Covers simple and multiple linear regression, residual analysis, ARIMA/SARIMAX and statistical tests.

- **Labs `Prac4.py` – `Prac12.py`:** weekly assignments on different datasets (`MRD*`, `MRL*`, `MST*`, `TASA_PARO.csv`).
- **`Examen.py` + `Plots EXAMEN.pdf`:** final exam with a SARIMAX model applied to a real time series, with residual analysis and diagnostics.
- **`Plantilla_A.py` / `Plantilla_B.py`:** reusable templates to start an analysis.
- **`utilities.py`:** helper functions:
  - Residual computation
  - Time-series and autocorrelation plots (ACF/PACF)
  - White-noise, heteroskedasticity (Breusch-Pagan, White), normality (Jarque-Bera) and autocorrelation (Durbin-Watson) tests
  - Seasonal decomposition
  - VIF (Variance Inflation Factor) for multicollinearity detection

**Included datasets:** `.csv` and `.gdt` files with macroeconomic and financial time series used in the different labs.

**Main dependencies:** `pandas`, `numpy`, `statsmodels`, `pmdarima`, `scipy`, `matplotlib`, `seaborn`.

For details, see [`econometrics/README.md`](econometrics/README.md).

---

### 5. Microprocessor-Based Systems (`microprocessor_systems`)

Lab assignments and exercises written in **Motorola 68000 assembly**, meant to be run on the **EASy68K** emulator.

- **`Prac1.X68` – `Prac3.2.X68`:** course labs covering register handling, memory, interrupts and subroutines.
- **`ej3.6.X68`, `ej3.7.X68`:** extra exercises.
- **`ASCII.X68`:** small utility related to the ASCII table.
- **`Casio/CasioWatch.X68`:** final project — a **Casio-style watch** with alarm and stopwatch implemented in 68k assembly, co-authored with Carlos E. Domínguez Martínez. Requires the sound files `Alarma.wav` and `Beep.wav` to be placed in the same folder as the `.X68` file when running it in EASy68K.

> To run these files, download [EASy68K](http://www.easy68k.com/) (Windows) or use its macOS/Linux build, open the `.X68` file and assemble it from the IDE.

For details, see [`microprocessor_systems/README.md`](microprocessor_systems/README.md).

---

## 🧰 Technologies used

Across the repository, the main tools and libraries are:

- **Python 3** as the common language for DSP, communications, telematics and econometrics.
- **Jupyter Notebooks** (`.ipynb`) for interactive work with signals and models.
- **NumPy, SciPy, pandas, matplotlib, seaborn** as the core numerical stack.
- **Librosa, pydub, sounddevice, simpleaudio** for audio processing and playback.
- **PyTorch** for the spoken-digit recognition neural network.
- **statsmodels, pmdarima** for econometric models and SARIMAX.
- **paho-mqtt, pyotp, smtplib, validate-email** for the telematic-services lab work.
- **Motorola 68000 assembly** (EASy68K) for microprocessor-based systems.
- **MATLAB** (only in `digital_signal_processing/Grader/`) for course grading helpers.

---

## 🚀 Getting started

### 1. Clone the repository

```bash
git clone https://github.com/oscarjibou/University-Projects.git
cd University-Projects
```

### 2. Pick a project

Each course is independent. Move into the folder you're interested in and, if available, read its own `README.md`:

```bash
cd design_telematic_services          # or any of the other subprojects
cat README.md
```

### 3. Create a virtual environment (recommended)

For the Python projects, it's recommended to isolate dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate              # Linux/macOS
# .venv\Scripts\activate               # Windows
```

### 4. Install dependencies

When the subproject ships a `requirements.txt` (e.g. `design_telematic_services`):

```bash
pip install -r requirements.txt
```

Otherwise, install what the internal README or the scripts' imports call for, for example:

```bash
# Signal processing
pip install numpy scipy matplotlib librosa pydub torch sounddevice tqdm pandas

# Econometrics
pip install pandas numpy statsmodels pmdarima scipy matplotlib seaborn
```

### 5. Run

- **Python scripts:** `python script_name.py`
- **Notebooks:** open the `.ipynb` file with Jupyter Lab, Jupyter Notebook or VS Code.
- **68k assembly:** open the `.X68` file in EASy68K and assemble it from the IDE.

---

## ⚠️ Important notes

- Some scripts (especially in `design_telematic_services`) depend on **environment variables** such as `DNI`, `NAME`, `EMAIL_FROM`, `EMAIL_TO`. Set them before running or edit the values directly in the code.
- The remote servers used in the labs (MQTT broker, TCP server, `smtp.upv.es`) **may not be reachable outside the UPV network**.
- The neural network in `digital_signal_processing/P6` requires the `base_datos_numeros_2023_AB` dataset, which is included in the folder.
- This is an **academic repository**: the code is meant for educational purposes and may contain shortcuts or simplifications typical of a classroom context.

---

## 📄 License

Academic project for educational purposes. Feel free to reuse any part of the code as long as you credit the author.

---

## 👤 Contact

**Oscar Jiménez Bou**
Engineering student — Universitat Politècnica de València (UPV)
GitHub: [@oscarjibou](https://github.com/oscarjibou)

---

> If you spot any issues or want to suggest improvements, feel free to open an issue or a pull request.
