---
layout: single
title: "Summer 2025 Project: Optimization, Neural Networks, and TinyML"
permalink: /tinyml/summer2025/
---

**Advisor:** Dr. Erfan Yazdandoost Hamedani  
**Student Lead:** Cody Melcher  

---

## Context

This project was part of a **one-day summer camp for high school students in Tucson**.  
The camp introduced participants to engineering concepts through hands-on activities that combined **optimization, neural networks, and TinyML**.  
Students worked directly with Arduino kits to explore how mathematical ideas (like gradients and optimization) power real-world machine learning applications.  

---

## What is Arduino?  

The **Arduino Nano 33 BLE Sense** is a low-power microcontroller designed for embedded applications.  
Key features:  
- Built-in camera and multiple sensors (motion, acceleration, rotation, sound).  
- Programs can be written in the **Arduino IDE**.  
- Supports **TinyML** deployment, enabling on-device inference.  

<p align="center">
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino Nano 33 BLE Sense kit" style="width:30%;"><br>
  <em>Arduino Nano 33 BLE Sense used in our experiments.</em>
</p>

---

## What is TinyML?  

**TinyML** = *Tiny Machine Learning* → deploying ML models on microcontrollers.  
- Models must be **small** (few layers, limited neurons).  
- Run entirely **on-device** without cloud or internet.  
- Applications include **embedded vision**, **speech recognition**, and **sensor data processing**.  

In this camp, TinyML enabled **real-time classification** of shapes and handwritten digits directly on the Arduino board:contentReference[oaicite:2]{index=2}.  

---

## Task 1: Binary Shape Classification  

### Goal  
Train a simple classifier to distinguish between **stars** and **circles** using the Arduino camera.  

### Building the Dataset  
- Students created **sticker cards** with stars and circles.  
- Each card was placed in front of the Arduino camera.  
- Images were captured using a Python script (`reading_image.py`).  
- Labels were assigned (`1 = star`, `0 = circle`):contentReference[oaicite:3]{index=3}.  

<p align="center">
  <img src="/assets/tinyml/summer2025/star.jpg" 
       alt="Card with star used for Task 1 classification" 
       style="width:30%;"><br>
  <em>Example of card used for Task 1.</em>
</p>

### Training the Model  
- Training was done with `training_binary.py`.  
- The algorithm used **gradient descent** to minimize a loss function.  
- Students experimented with different learning rates (`lr = 0.1, 1, 10`).  
- This showed how **step size** impacts convergence:  
  - Too small → slow learning.  
  - Too large → unstable or diverging:contentReference[oaicite:4]{index=4}.  

### Testing and Results  
- Models were tested on new cards and even borrowed cards from peers.  
- Accuracy was measured by correct predictions vs. errors.  
- Students reflected on: Which shapes were harder to classify? Why?:contentReference[oaicite:5]{index=5}  

<p align="center">
  <img src="/assets/tinyml/summer2025/kitsetup1.jpeg" 
       alt="Arduino camera setup for data collection and testing" 
       style="width:30%;"><br>
  <em>Data collection and testing pipeline with Arduino camera.</em>
</p>

---

## Task 2: Handwritten Digit Classification (MNIST on Arduino)  

### Goal  
Deploy a **neural network** on Arduino to classify handwritten digits (0–9).  

### Model Design and Constraints  
- Base model trained in Python (`training_MNIST.py`).  
- Exported and uploaded to Arduino (`handwritten_digit_recognition.ino`).  
- TinyML limits:  
  - ≤ **4 hidden layers**  
  - ≤ **900 neurons total**  
- Students tried different optimizers (Adam, SGD, RMSprop) and activations (ReLU, tanh, sigmoid):contentReference[oaicite:6]{index=6}.  

### Building the Dataset  
- Students drew digits (0–9) on cards.  
- Each card was placed under the Arduino camera.  
- Image capture required pressing **reset + onboard buttons**:contentReference[oaicite:7]{index=7}.  

<p align="center">
  <img src="/assets/tinyml/summer2025/numbers.jpg" 
       alt="Handwritten digit cards used for Task 2 classification" 
       style="width:30%;"><br>
  <em>Example of handwritten digit card used for Task 2.</em>
</p>

### Testing and Results  
- Models classified digits in real-time, with predictions displayed in the Arduino Serial Monitor.  
- Students tested on a **set of 8–10 digit cards**.  
- Observations:  
  - Some digits were consistently harder to classify.  
  - Increasing model complexity could improve accuracy, but risked overfitting.  
  - Trade-offs highlighted the challenge of deploying ML under **hardware constraints**:contentReference[oaicite:8]{index=8}:contentReference[oaicite:9]{index=9}.  

---

## Outcomes  

The camp provided students with a **hands-on introduction** to optimization, neural networks, and TinyML.  

- **Task 1** (binary shapes): demonstrated how gradient descent and learning rate choices affect optimization.  
- **Task 2** (digits): extended to deeper models and showed the limits of on-device ML.  

Overall, the project bridged **optimization theory** with **practical embedded ML deployment**, offering students both intuition and experience in how AI systems are built and tested in real-world settings.  
