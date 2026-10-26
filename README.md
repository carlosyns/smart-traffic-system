# 🚦 AI-Based Smart Traffic Control & Monitoring System

> An intelligent, computer-vision-driven traffic signal management system designed to eliminate static delays, prioritize emergency response, and dynamically manage urban intersection queues.

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
Traditional traffic control relies heavily on rigid **fixed-time cycles** or **inductive-loop sensors**, which degrade road infrastructure and fail during peak dynamic congestion. 

This project implements an **edge-deployed Computer Vision and AI pipeline** that captures live multi-lane visual data, calculates real-time vehicle density and queue lengths, and dynamically adjusts signal timing to minimize idle wait times and clear intersection gridlock.

---

## ✨ Key Features

- 📹 **Real-Time Vehicle Detection:** Utilizes lightweight YOLO object detection to track vehicles frame-by-frame.
- ⚡ **Dynamic Green-Light Allocation:** Replaces fixed timers with adaptive signal cycles based on live lane density.
- 🚨 **Emergency Vehicle Preemption (EVP):** Instantly detects approaching ambulances/fire engines to grant immediate green-wave priority.
- 🚗 **Multi-Class Vehicle Identification:** Differentiates between passenger cars, heavy trucks, buses, and two-wheelers.
- 📊 **Traffic Analytics Dashboard:** Logs vehicle counts, flow rates, and queue metrics for offline traffic planning.

---

## 🏗 System Architecture

```text
  ┌─────────────────┐       ┌──────────────────────┐       ┌──────────────────────┐
  │   Video Feed    │ ───►  │  Edge AI Processing  │ ───►  │ Traffic Logic Engine │
  │ (CCTV / Camera) │       │ (OpenCV / YOLO Model)│       │  (Density & Queues)  │
  └─────────────────┘       └──────────────────────┘       └──────────┬───────────┘
                                                                      │
                                                                      ▼
  ┌─────────────────┐       ┌──────────────────────┐       ┌──────────────────────┐
  │ Physical LEDs / │ ◄───  │ Microcontroller Hub  │ ◄───  │ Control Signal Rules │
  │  Traffic Light  │       │   (ESP32 / AVR C)    │       │ (Preemption / Delay) │
  └─────────────────┘       └──────────────────────┘       └──────────────────────┘
