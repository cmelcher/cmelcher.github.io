---
layout: single
title: "Summer 2025 Project: Optimization, Neural Networks, and TinyML"
permalink: /tinyml/summer2025/
---

**Advisor:** Dr. Erfan Yazdandoost Hamedani  

---

## Context

This project session was part of a one-day science and engineering summer camp for high school students in Tucson. Our goal was to introduce students, without assuming prior math or computing background, to some core ideas from calculus, optimization, and scientific computing. Through two guided activities, they explored how concepts like gradients and optimization drive modern machine learning. Students built and tested small classification models directly on Arduino Nano 33 BLE Sense kits, gaining experience with how math and computing ideas translate directly into real world applications.

---

## What is Arduino?  

The **Arduino Nano 33 BLE Sense** is a small, low-power microcontroller designed for embedded applications. The device comes with a variety of sensors that make it ideal for machine learning projects:
- Built-in camera and multiple sensors (motion, acceleration, rotation, sound).  
- Programs can be written in a dedicated IDE.   
- Main use is TinyML deployment, enabling on-device inference with low energy and resource requirements.  

<p align="center">
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino Nano 33 BLE Sense kit" style="width:30%;"><br>
  <em>Arduino Nano 33 BLE Sense used in our experiments.</em>
</p>

---

## What is TinyML?  

TinyMl (Tiny Machine Learning) is an environment for deploying ML models on microcontrollers. TinyML takes the learning methods that usually run on powerful GPUs and CPUs and compresses them to work on small, low-power devices. 
- Models must be compact (few layers, limited total number of neurons).  
- Models run directly on the device, without needing cloud interaction. This makes computation more efficient and helps with privacy considerations.   
- Applications include embedded computer vision and speech recognition.

In this session, students used TinyML to classify shapes and handwritten digits in real time directly on the Arduino board. 
---

## Task 1: Binary Shape Classification  

### Goal  
Train a simple classifier to distinguish between **stars** and **circles** using the Arduino camera.  

### Building the Dataset  
- Students created **sticker cards** with stars and circles.  
- Each card was placed in front of the Arduino camera.  
- Images were captured using a Python script (`reading_image.py`) pre-written by Dr. Yazdandoost Hamedani and myself.  
- Labels were assigned (`1 = star`, `0 = circle`)

<p align="center">
  <img src="/assets/tinyml/summer2025/star.jpg" 
       alt="Card with star used for Task 1 classification" 
       style="width:30%;"><br>
  <em>Example of card used for Task 1.</em>
</p>

### Training the Model  
- Training was done with `training_binary.py`.  
- The algorithm used **gradient descent** to minimize a loss function.  
- We had the students experimented with different learning rates (`lr = 0.1, 1, 10`) to test how the classification changed.  
- This demonstrated how step size choice impacts convergence to a solution:  
  - Too small → slow learning.  
  - Too large → unstable or diverging.

### Testing and Results  
- Models were tested on new cards and even borrowed cards from peers.  
- Accuracy was measured by correct predictions vs. errors.  
- Students reflected on: Which shapes were harder to classify? Why?:
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
- Students tried different optimizers (Adam, SGD, RMSprop) and activations (ReLU, tanh, sigmoid).

### Building the Dataset  
- Students drew digits (0–9) on cards.  
- Each card was placed under the Arduino camera.  
- Image capture required pressing **reset + onboard buttons**.  

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
  - Trade-offs highlighted the challenge of deploying ML under **hardware constraints**.

---

## Outcomes  

The camp provided students with a **hands-on introduction** to optimization, neural networks, and TinyML.  

- **Task 1** (binary shapes): demonstrated how gradient descent and learning rate choices affect optimization.  
- **Task 2** (digits): extended to deeper models and showed the limits of on-device ML.  

Overall, the project bridged **optimization theory** with **practical embedded ML deployment**, offering students both intuition and experience in how AI systems are built and tested in real-world settings.  
