# On-Device Speech Translation Pipeline on ARM (Termux)

## Overview

This project presents a **fully offline, on-device speech translation pipeline** implemented on an **ARM-based Android smartphone** using **Termux**.  
The system captures live speech through the device microphone, performs on-device speech recognition and translation, and generates spoken audio output — **without relying on any cloud services**.

The project demonstrates the feasibility of **edge AI deployment on mobile devices**, focusing on **low-latency execution**, **privacy preservation**, and **ARM CPU–optimized inference** under real-world mobile constraints.

---

## Problem Statement

Most existing speech translation systems depend on cloud-based processing, which introduces:
- Privacy and data security concerns  
- Higher end-to-end latency  
- Reduced reliability in low or no network conditions  

The objective of this project is to design a solution that performs **speech recognition, language translation, and audio output entirely on-device**, leveraging the capabilities of **ARM-based mobile CPUs**.

---

## Key Features

- Fully offline execution (no internet or cloud dependency)
- Live microphone input on Android
- On-device speech recognition and translation
- On-device audio synthesis and playback
- Optimized for ARM-based CPUs using lightweight, quantized models
- Suitable for edge AI and mobile inference scenarios

---

## System Architecture
Microphone Input
→ Audio Recording (Termux API)
→ Audio Preprocessing (FFmpeg)
→ Speech Recognition & Translation (Whisper.cpp)
→ Text Output
→ Audio Synthesis (eSpeak)
→ Speaker Output


All processing stages are executed **locally on the smartphone**.

---

## Technology Stack

| Component | Technology Used |
|--------|----------------|
| Device | ARM-based Android smartphone |
| Linux Environment | Termux |
| Speech Recognition & Translation | Whisper.cpp |
| Model Format | Quantized GGML |
| Audio Processing | FFmpeg |
| Audio Output | eSpeak |
| Microphone Access | termux-api |
| Programming | C++, Bash |

---

## Implementation Summary

The pipeline follows a **chunk-based processing approach**, where short audio segments are recorded and processed sequentially.  
This method enables **near real-time performance** while respecting mobile power, thermal, and latency constraints.

All inference is executed using **CPU-only computation**, making the solution practical for devices without dedicated AI accelerators.

---

## Execution Commands

The exact commands used to run the complete pipeline on the device are documented in:
commands/pipeline_commands.md


These commands include:
- Live audio recording
- Audio preprocessing
- On-device speech recognition
- On-device translation
- Audio synthesis and playback

---

## ARM & Edge AI Relevance

- Native C/C++ execution with Whisper.cpp
- Quantized models for reduced memory footprint
- CPU-optimized inference suitable for ARM architectures
- Designed for energy-efficient mobile deployment

This aligns with core principles of **edge AI on ARM platforms**.

---

## Experimental Note

Google Colab was used **only for early experimentation and understanding model behavior**.  
The **final implementation and all demonstrated results** are from the **on-device ARM smartphone setup** using Termux.

---

## Limitations

- Continuous infinite audio streaming is limited by Android microphone APIs
- Chunk-based processing is used instead of continuous streaming
- Translation relies on Whisper’s internal translation capability

These constraints are inherent to mobile environments and do not affect the validity of the approach.

---

## Conclusion

This project successfully demonstrates a fully offline, on-device speech translation pipeline running on an ARM-based smartphone.  
It highlights the practicality of deploying speech and language processing workloads directly on mobile edge devices while maintaining acceptable latency, privacy, and efficiency.

---

## License

This project is released under the **MIT License**.
