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

## Task 1: Classifying Stars and Circles  

In our first activity, students built a simple image classifier using the Arduino Nano 33 BLE Sense.  
The goal was to train a model that could recognize whether a drawing was a **star** or a **circle**.  

### Step 1: Create a Dataset  
Students drew their own stars and circles on sticker cards. These cards were then placed over the Arduino’s built-in camera to capture training images.  

<p align="center">  
  <img src="/assets/tinyml/star_card.jpg" alt="Star card example" width="250"/>  
  <br><em>Example student star drawing used for training.</em>  
</p>  

### Step 2: Capture Images  
A Python script (`reading_image.py`) was used to capture images from the Arduino and save them with labels.  
Students updated the label parameter to distinguish between stars and circles.  

<p align="center">  
  <img src="/assets/tinyml/reading_image.png" alt="Python script for image capture" width="500"/>  
  <br><em>Script for capturing and labeling images.</em>  
</p>  

### Step 3: Train the Model  
Once the dataset was ready, students ran a second script (`training_binary.py`) to train a binary classifier.  
They also experimented with the **learning rate** to see how step size affects optimization and convergence.  

<p align="center">  
  <img src="/assets/tinyml/training_binary.png" alt="Training script" width="500"/>  
  <br><em>Training script for binary classification.</em>  
</p>  

### Step 4: Test the Model  
Finally, students tested their models using new drawings, including some borrowed from classmates.  
A testing script (`testing_binary.py`) displayed predictions in real time, showing whether the model classified the card as a star or a circle.  

<p align="center">  
  <img src="/assets/tinyml/testing_binary.png" alt="Testing script" width="500"/>  
  <br><em>Testing script used to evaluate classification results.</em>  
</p>  

This activity introduced students to the **full machine learning workflow**—from data collection and labeling to training, optimization, and evaluation—all on a tiny device.  


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
