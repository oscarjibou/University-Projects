# Microprocessor-Based Systems

Lab assignments and exercises written in **Motorola 68000 assembly language**, designed to run on the **EASy68K** emulator. The project covers fundamental topics in microprocessor-based systems programming — from register handling and basic I/O to interrupts, subroutines and a final project implementing a Casio-style digital watch with alarm and stopwatch.

> **Course:** Microprocessor-Based Systems
> **Authors:** Oscar Jiménez Bou and Carlos E. Domínguez Martínez
> **Target platform:** Motorola 68000 (EASy68K emulator)

## 📋 Project description

All source files use the `.X68` extension, the standard format used by **EASy68K**. Each file is a standalone assembly program that can be assembled and run independently in the emulator.

## 📁 Project structure

```
microprocessor_systems/
├── Prac1.X68            # Lab 1 — introduction to 68k assembly
├── Prac2.X68            # Lab 2 — Several concatenated exercises
├── Prac3.X68            # Lab 3 — first version
├── Prac3.2.X68          # Lab 3 — second/revised version
├── ej3.6.X68            # Extra exercise 3.6
├── ej3.7.X68            # Extra exercise 3.7
├── ASCII.X68            # ASCII string converter utility
│
└── Casio/               # Final project: Casio watch
    ├── CasioWatch.X68   # Digital watch with alarm and stopwatch
    ├── Alarma.wav       # Alarm sound effect
    └── Beep.wav         # Button beep sound effect
```

## 🛠️ Contents

### `Prac1.X68` — Introduction

First contact with 68k assembly: program origin (`ORG`), entry point (`START`), basic register manipulation and program termination via `TRAP #15`.

### `Prac2.X68` — Concatenated exercises

A series of exercises chained together so that running the program continuously executes all of them in order. Authored by Carlos E. Domínguez.

### `Prac3.X68` and `Prac3.2.X68`

Two versions of Lab 3 showing the progression of the implementation and the improvements introduced in the second iteration.

### `ej3.6.X68`, `ej3.7.X68` — Extra exercises

Complementary exercises for Lab 3, typically dealing with more involved arithmetic or string handling.

### `ASCII.X68` — ASCII string converter

A small utility that converts input strings to/from ASCII, with extra handling for corner cases such as negative numbers and non-numeric input.

### `Casio/CasioWatch.X68` — Final project

A **digital Casio-style watch** implemented in 68k assembly, featuring:

- **Real-time clock** — hours, minutes and seconds driven by a periodic interrupt (`INT_CLK`).
- **Alarm** — user-configurable alarm that triggers the `Alarma.wav` sound.
- **Stopwatch** — independent chronometer for measuring elapsed time.
- **Display buffer** — digit-by-digit rendering using the `PS1/PS2/PM1/PM2/PH1/PH2` memory positions.
- **Sound effects** — button press beeps (`Beep.wav`) and alarm tone (`Alarma.wav`) played via EASy68K's sound TRAPs.

> **Important:** to run `CasioWatch.X68`, make sure that `Alarma.wav` and `Beep.wav` are placed **in the same folder** as the `.X68` file when loading it into EASy68K. Otherwise the sound effects will not play.

## 🚀 How to run

### 1. Install EASy68K

Download the emulator from [easy68k.com](http://www.easy68k.com/). Native builds are available for Windows; macOS and Linux can run it under Wine, or you can use the web-based port if you prefer.

### 2. Open a `.X68` file

Launch EASy68K, open the assembler (`Edit68K`) and load any of the `.X68` files from this folder. The `ORG $1000` directive at the top places the program at memory address `0x1000`.

### 3. Assemble

Click **Project → Assemble Source** (or press `F9`). If the assembly succeeds, a `.L68` and `.S68` listing will be generated.

### 4. Run in the simulator

Click **Execute → Run** (or press `F10`). The simulator (`Sim68K`) will open and load the program. Press **Run** to start execution. You'll interact with the program via EASy68K's built-in console window (keyboard input, text output, etc.).

### 5. Running the Casio watch

```text
1. Copy CasioWatch.X68, Alarma.wav and Beep.wav into the same folder.
2. Open CasioWatch.X68 in Edit68K.
3. Assemble (F9) and run (F10).
4. Use the on-screen keys (mapped in the source) to switch between
   clock / alarm / stopwatch modes and to change the time.
```

## 📝 Key concepts

- **`ORG` directive** — sets the origin address in memory (`$1000` for code, `$1000 * 4` for interrupt vectors).
- **Registers** — data registers `D0–D7` and address registers `A0–A7` (with `A7` used as the stack pointer).
- **Addressing modes** — immediate, direct, register indirect, indexed, etc.
- **`TRAP #15`** — EASy68K system calls for I/O (print string, read number, play WAV, terminate…).
- **Interrupts** — the `CasioWatch` uses a periodic timer interrupt vectored at offset `25 * 4` to update the clock every second.
- **Subroutines** — `BSR` / `RTS` for modular code.
- **Memory-mapped data** — word/long allocations via `DS.W` / `DS.L` / `DC.L`.

## 🧰 Tools used

- **EASy68K** — Motorola 68000 assembler and simulator.
- **`Edit68K`** — integrated editor / assembler.
- **`Sim68K`** — 68000 simulator with built-in I/O console and sound support.

## 🎯 Learning objectives

1. Understand the 68000 programmer's model (registers, stack, addressing modes).
2. Write clean, modular assembly programs with subroutines.
3. Perform basic I/O using `TRAP #15` system calls.
4. Handle periodic interrupts and build a real-time event loop.
5. Combine multiple subsystems (clock + alarm + stopwatch) into a single coherent application.

## 📄 License

Academic project for educational purposes.

## 👤 Authors

Developed as part of the Microprocessor-Based Systems course.

- **Oscar Jiménez Bou**
- **Carlos E. Domínguez Martínez** (co-author on Labs 2, 3 and the final Casio project)

---

> **Note:** the `.X68` files are plain text. They can be opened and read in any text editor, but you need EASy68K (or a compatible 68000 assembler/simulator) to actually assemble and run them.
