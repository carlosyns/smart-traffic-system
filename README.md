# 🚦 AI-Based Smart Traffic Management & Emergency Vehicle Priority System

> An intelligent, dual-node IoT and computer-vision traffic control system designed to optimize urban intersection timing through historical pattern analysis and instantaneous emergency vehicle preemption.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Repository Structure](#-repository-structure)
- [Hardware & Software Stack](#-hardware--software-stack)
- [Git Workflow & Branching Strategy](#-git-workflow--branching-strategy)
- [Getting Started](#-getting-started)
- [Team & Roles](#-team--roles)

---

## 🎯 Overview
Traditional traffic control relies on rigid, pre-programmed fixed-time cycles that fail to adapt to fluctuating urban traffic densities, resulting in unnecessary delays and gridlock. 

Designed with a specific focus on urban bottlenecks in Lebanon (such as the Greater Beirut area), this project implements a smart intersection model for two roads (**Road A** and **Road B**). The system separates normal traffic management—which analyzes historical weekly patterns to optimize recurring signal timings—from real-time emergency response, ensuring ambulances receive immediate priority without disrupting overall network safety.

---

## ✨ Key Features

- 👁️ **Computer Vision Monitoring:** A dedicated camera node captures traffic flow across both intersection approaches.
- 📈 **Historical Pattern Analysis:** Stores and evaluates vehicle counts week-over-week to inform routine, data-driven green-light durations.
- 🚑 **Real-Time Emergency Preemption:** Instantly detects ambulances in real time, overriding historical routines to grant immediate green-wave priority.
- 🌐 **Web-Based Management Interface:** Provides a centralized dashboard for Municipality Administrators and Municipal Police Officers to monitor traffic conditions, review ambulance events, and perform manual overrides.
- ⚙️ **Dual-Node Architecture:** Distributes processing cleanly between a dedicated vision/camera node and a separate traffic-control node.

---

## 🏗 System Architecture

```text
  ┌──────────────────────────────────────────────┐
  │              Camera & Vision Node            │
  │               (ESP32-S3 Board)               │
  │  - Monitors Road A & Road B                  │
  │  - Performs Vehicle Counting & Detection     │
  │  - Detects Real-Time Ambulances              │
  └──────────────────────┬───────────────────────┘
                         │ Transmits Data / Status
                         ▼
  ┌──────────────────────────────────────────────┐
  │             Traffic-Control Node             │
  │               (ESP32-S3 Board)               │
  │  - Manages Traffic Light LEDs                │
  │  - Executes Routine & Emergency Transitions  │
  └──────────────────────┬───────────────────────┘
                         │
                         ▼
  ┌──────────────────────────────────────────────┐
  │             Web Dashboard & DB               │
  │  - Municipality & Police Admin Interface     │
  │  - Historical Traffic Logs & Event Tracking  │
  └──────────────────────────────────────────────┘
