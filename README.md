# 🚗 Directional Collision Anticipation AI

<p align="center">
  <strong>AI-powered system that detects, tracks, and anticipates potential road collisions from video.</strong>
</p>

<p align="center">
  Detect → Track → Understand → Predict → Assess Risk → Alert
</p>

<p align="center">

<a href="https://github.com/AlthafShaik15/directional-collision-anticipation-ai">
<img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github" alt="GitHub">
</a>

<img src="https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">

<img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">

<img src="https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React">

<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript">

<img src="https://img.shields.io/badge/YOLOv11-Object%20Detection-111111?style=for-the-badge" alt="YOLOv11">

<img src="https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV">

<img src="https://img.shields.io/badge/ByteTrack-Object%20Tracking-orange?style=for-the-badge" alt="ByteTrack">

<img src="https://img.shields.io/badge/PyTest-Testing-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white" alt="PyTest">

<img src="https://img.shields.io/badge/SIH-2026-FF6B00?style=for-the-badge" alt="SIH">

</p>

---

## 📌 About the Project

**Directional Collision Anticipation AI** is a computer-vision-based system that analyzes road and dashcam videos to identify objects, understand their movement, predict their future paths, and estimate potential collision risks.

Instead of only asking:

> **"What objects are visible?"**

the system tries to answer:

> **"Which object could become a threat, from which direction, and how serious is the situation?"**

The project is designed as a **software-only simulation prototype for Smart India Hackathon (SIH)** and focuses on Indian mixed-traffic scenarios.

---

## 🎯 Problem

Road traffic in India can involve many different road users moving in unpredictable ways:

- 🚗 Cars
- 🏍️ Motorcycles
- 🚌 Buses
- 🚚 Trucks
- 🚶 Pedestrians
- 🚲 Bicycles

Common challenges include:

- Unpredictable vehicle movements
- Lane violations
- Sudden lane changes
- Dense mixed traffic
- Pedestrians and motorcycles sharing road space
- Vehicles approaching from different directions

A simple object detector can identify a pedestrian or vehicle, but detection alone does not tell us whether that object is becoming a collision threat.

This project adds **tracking, motion analysis, direction reasoning, trajectory prediction, and risk assessment** to move from simple detection toward collision anticipation.

---

# 🧠 How It Works

The system follows this pipeline:

```text
                 ROAD / DASHCAM VIDEO
                         │
                         ▼
                ┌─────────────────┐
                │ Object Detection│
                │     YOLOv11     │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Object Tracking │
                │   ByteTrack     │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Motion Analysis │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │    Direction    │
                │    Reasoning    │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │    Trajectory   │
                │    Prediction   │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │    Collision    │
                │    Analysis     │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │   Risk Scoring  │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Threat Ranking  │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Driver Warning  │
                │ / Voice Alert   │
                └─────────────────┘
