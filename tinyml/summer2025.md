---
layout: single
title: "Summer 2025 Project: Optimization, Neural Networks, and TinyML"
permalink: /tinyml/summer2025/
---

**Advisor:** Dr. Erfan Yazdandoost Hamedani  
---

## What is Arduino?  

The **Arduino Nano 33 BLE Sense** is a low-power microcontroller that integrates a tiny camera and multiple sensors (motion, acceleration, sound, rotation).  
It can be programmed directly via the **Arduino IDE** and supports deploying small-scale machine learning models.  

<figure style="text-align: center;">
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino kit" style="width:40%;">
  <figcaption><em>Arduino Nano 33 BLE Sense used in our experiments.</em></figcaption>
</figure>

---

## What is TinyML?  

**TinyML** refers to deploying machine learning models on resource-constrained hardware like microcontrollers.  
- Models must be **compressed** (small number of layers and neurons).  
- They run **on-device**, without needing a cloud connection.  
- Applications include embedded vision, speech recognition, and sensor data processing.  

In this project, TinyML enabled **real-time classification** of shapes and handwritten digits directly on the Arduino board.  

---

## Task 1: Binary Shape Classification  

### Goal  
Train a classifier to distinguish between **stars** and **circles** using images captured by the Arduino’s camera.  

### Building the Dataset  
- Students drew **stars and circles** on sticker cards.  
- Each card was placed in front of the Arduino camera.  
- Images were collected using a Python script (`reading_image.py`) and labeled (1 = star, 0 = circle).  

<figure style="text-align: center;">
  <img src="/assets/tinyml/summer2025/star.jpg" alt="Star card" style="width:40%;">
  <figcaption><em>Example of card used for Task 1.</em></figcaption>
</figure>

### Training the Model  
- The script `training_binary.py` was used to learn from the labeled images.  
- We implemented **gradient descent** as the optimization method.  
- Students experimented with **different learning rates** (`lr = 0.1, 1, 10`) to observe convergence speed and stability.  

### Testing and Results  
- The trained model was tested on new cards.  
- Performance was evaluated by prediction accuracy and error patterns.  

![Arduino camera setup](/assets/tinyml/summer2025/kitsetup1.jpeg)  
*Data collection and testing pipeline with Arduino camera.*  

---

## Task 2: Handwritten Digit Classification (MNIST Deployment)  

### Goal  
Deploy a neural network on Arduino to classify handwritten digits (0–9).  

### Model Design and Constraints  
- Base training done in Python (`training_MNIST.py`).  
- Model exported and uploaded to Arduino (`handwritten_digit_recognition.ino`).  
- To fit TinyML constraints:  
  - **Maximum:** 4 hidden layers  
  - **Maximum neurons:** 900 total  
  - Tested optimizers: Adam, SGD, RMSprop  
  - Activation functions: ReLU, tanh, sigmoid  

### Building the Dataset  
- Digits (0–9) drawn on cards and placed under Arduino’s camera.  
- Data captured using reset + onboard buttons.  

![Digit cards](/assets/tinyml/summer2025/numbers.jpg)  
*Example of handwritten digit card used for Task 2.*  

### Testing and Results  
- The model classified digits in real-time, showing predictions in the Arduino IDE serial monitor.  
- Accuracy depended on architecture and optimizer choices.  
- Students observed trade-offs between **model complexity** and **hardware constraints**.  

---

## Outcomes  

This project demonstrated how optimization and neural networks can be taught and deployed in **embedded machine learning** settings.  
- **Task 1** (binary classification) introduced gradient descent and loss minimization in a simple, visual way.  
- **Task 2** (digit classification) extended to deeper models and highlighted constraints of TinyML.  

Overall, this hands-on project connected **optimization theory** with **practical deployment** on embedded devices.  
