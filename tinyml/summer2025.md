---
layout: single
title: "Summer 2025 Project: Optimization, Neural Networks, and TinyML"
permalink: /tinyml/summer2025/
---

Advisor: Dr. Erfan Yazdandoost Hamedani  

---

## Context

The goal of this project is to spark interest in math, computing, and engineering for undergraduate and high school students by showing how optimization and machine learning power technologies encountered every day. No background in calculus or coding is assumed.

This project introduces key concepts such as derivatives, gradients, microcontrollers, classification (binary and multi-class), and neural networks. Participants adjust and test small classification models directly on **Arduino Nano 33 BLE Sense** kits to see how mathematical ideas translate into real-world applications.

This project has been implemented in outreach activities at the University of Arizona (e.g., a one-day science and engineering summer camp), and the materials here are organized as a stand-alone tutorial so anyone can follow along.

Code for both projects as well as the slides and handout we gave students can be found here:
<p align="center">
  <a href="https://github.com/cmelcher/summer2025code" target="_blank">
    <img src="https://img.shields.io/badge/View%20Code-GitHub-blue?style=for-the-badge&logo=github" alt="View Materials">
  </a>
</p>


## What is Arduino?  

The **Arduino Nano 33 BLE Sense** is a small, low-power microcontroller designed for embedded applications. It includes multiple onboard sensors and supports on-device ML (TinyML).

- Built-in sensors (motion, acceleration, rotation, sound) and camera modules can be integrated.
- Programs can be written in the Arduino IDE (or CLI).
- Ideal for TinyML deployment—running inference with low energy and memory.

<p align="center">
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino Nano 33 BLE Sense kit" style="width:40%;"><br>
  <em>Arduino Nano 33 BLE Sense board.</em>
</p>

---

## What is TinyML?  

**TinyML (Tiny Machine Learning)** compresses ML models so they can run on microcontrollers and other extremely resource-constrained devices.

- Models must be compact (few layers, limited total neurons), reflecting real engineering constraints.
- Inference runs directly on the device—no cloud required—improving efficiency and privacy.
- Common applications include embedded vision and simple speech recognition.

In this tutorial, you’ll classify **shapes** (binary) and **handwritten digits** (multi-class) in real time on the Arduino board.

<p align="center">
  <img src="/assets/tinyml/summer2025/kitsetup0.jpeg" alt="kitsetup" style="width:55%;"><br>
  <em>Setup for the two activities.</em>
</p>

---

## Task 1: Binary Classification (Stars vs. Circles)

In this activity, you’ll build a simple **binary** image classifier on the Arduino Nano 33 BLE Sense.

### Step 1: Create a Dataset
- Draw **5–10 stars** and **5–10 circles** on sticker/index cards.
- Place each card over the Arduino’s camera to capture images.

<p align="center">
  <img src="/assets/tinyml/summer2025/star.jpg" alt="Star card example" style="width:40%;"><br>
  <em>Example star drawing used for training.</em>
</p>

### Step 2: Capture Images
- Use the provided Python script `reading_image.py` to capture images and save labels.
- Set the label parameter appropriately (e.g., `star` vs `circle`).

<p align="center">
  <img src="/assets/tinyml/summer2025/reading_binary.png" alt="Python script for image capture" style="width:55%;"><br>
  <em>Image capture and labeling.</em>
</p>

### Step 3: Train the Model
- Run `training_binary.py` to train a binary classifier.
- Experiment with different **learning rates** to observe effects on optimization and convergence.

<p align="center">
  <img src="/assets/tinyml/summer2025/training_binary.png" alt="Training script" style="width:55%;"><br>
  <em>Training for binary classification.</em>
</p>

### Step 4: Test the Model
- Use `testing_binary.py` to test on new drawings (including peers’ drawings if available).
- View predictions in real time.

<p align="center">
  <img src="/assets/tinyml/summer2025/testing_binary.png" alt="Testing script" style="width:55%;"><br>
  <em>Evaluation and live predictions.</em>
</p>

**Reflection**
- Which step size yielded faster but stable convergence?
- How many images did the model correctly classify?
- Which drawings were harder for the model?

---

## Task 2: Handwritten Digit Classification (MNIST on Arduino)

Extend to a **multi-class** problem: recognizing handwritten digits (0–9). You’ll train a small network and deploy it to the Arduino.

### Step 1: Train the Model
- Run `training_MNIST.py` to train a compact network on MNIST.
- Export a quantized model header (e.g., `mnist_model_quant.h`) for deployment.

<p align="center">
  <img src="/assets/tinyml/summer2025/multiclass_training.png" alt="Training MNIST script" style="width:55%;"><br>
  <em>Training for the MNIST model.</em>
</p>

### Step 2: Deploy to Arduino
- Load the exported model into the Arduino sketch `handwritten_digit_recognition.ino`.
- Upload the sketch to the board and confirm it runs inference locally.

<p align="center">
  <img src="/assets/tinyml/summer2025/handwritten_image.png" alt="Arduino digit recognition sketch" style="width:55%;"><br>
  <em>Arduino sketch for digit recognition.</em>
</p>

### Step 3: Create a Test Set
- Draw digits **0–9** (one per card), centered on a white background.
- Place each card over the camera to form a small test set.

<p align="center">
  <img src="/assets/tinyml/summer2025/numbers.jpg" 
       alt="Handwritten digit cards used for Task 2 classification" 
       style="width:30%;"><br>
  <em>Example handwritten digit card.</em>
</p>

### Step 4: Test the Model
- Use the reset/onboard buttons to capture each image.
- View predictions in the Arduino Serial Monitor.

**Try / Reflect**
- Which digits were most/least accurate?
- How do architecture changes (e.g., up to **4 layers** and **≤900 total neurons**) affect accuracy and overfitting?

---

## Outcomes  

This tutorial connects **optimization** (e.g., gradient descent, step size choice) with **neural networks** and **TinyML** on real hardware.

- **Task 1 (shapes):** observe how learning rate affects convergence and performance.
- **Task 2 (digits):** deploy a compact model and explore architecture-accuracy tradeoffs under embedded constraints.

---

