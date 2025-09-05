---
layout: single
title: "Summer 2025 Project: Optimization, Neural Networks, and TinyML"
permalink: /tinyml/summer2025/
---

**Advisor:** Dr. Erfan Yazdandoost Hamedani  

---

## Context

During the Summer of 2025, Dr. Yazdandoost Hamedani and I ran an optimization and computing session for high school students from Tucson that aimed to introduce students to optimization basics, machine learning (ML), and coding. Our project session was part of a one-day science and engineering summer camp organized by the University of Arizona. 

The goal was to spark interest in math, computing, and engineering by showing how optimization and machine learning power technologies students encounter every day. Students came in with no assumed background in calculus or coding. 

We introduced key concepts like derivatives, gradients, microcontrollers, classification (both binary and multi-class), and neural networks. During the session we had students adjust and test pre-built small classification models (both binary and multi) directly on Arduino Nano 33 BLE Sense kits, gaining experience with how math and computing ideas translate directly into real world applications.


---

## What is Arduino?  

The **Arduino Nano 33 BLE Sense** is a small, low-power microcontroller designed for embedded applications. The device comes with a variety of sensors that make it ideal for machine learning projects:
- Built-in camera and multiple sensors (motion, acceleration, rotation, sound).  
- Programs can be written in a dedicated IDE.   
- Main use is TinyML deployment, enabling on-device inference with low energy and resource requirements.  

<p align="center">
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino Nano 33 BLE Sense kit" style="width:40%;"><br>
  <em>Arduino Nano 33 BLE Sense board.</em>
</p>


---

## What is TinyML?  

TinyMl (Tiny Machine Learning) is an environment for deploying ML models on microcontrollers. TinyML takes the learning methods that usually run on powerful GPUs and CPUs and compresses them to work on small, low-power devices. 
- Models must be compact (few layers, limited total number of neurons). These restrictions mirror real-world engineering restrictions: with limited hardware, every design choice matters.   
- Models run directly on the device, without needing cloud interaction. This makes computation more efficient and helps with privacy considerations.   
- Applications include embedded computer vision and speech recognition.

In this session, students used TinyML to classify shapes and handwritten digits in real time directly on the Arduino board.  
<p align="center">
  <img src="/assets/tinyml/summer2025/kitsetup0.jpeg" alt="kitsetup" style="width:40%;"><br>
  <em>Setup for the two activities</em>
</p>

---

In the first activity, students worked with a simple binary image classifier using the Arduino Nano 33 BLE Sense.  
The goal was to train a model that could accurately predict whether a drawing was a **star** or a **circle**.  

### Step 1: Create a Dataset  
Students drew 5–10 stars and 5–10 circles on sticker cards. These were placed one at a time over the Arduino’s built-in camera to capture training images.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/star.jpg" alt="Star card example" style="width:40%;"><br>  
  <em>Example student star drawing used for training.</em>  
</p>  

### Step 2: Capture Images  
A pre-written Python script (`reading_image.py`) captured images from the Arduino and saved them with labels. Students updated the label parameter to distinguish between stars and circles.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/reading_binary.png" alt="Python script for image capture" style="width:40%;"><br><em>Script for capturing and labeling images.</em>  
</p>  

### Step 3: Train the Model  
Students then ran `training_binary.py` to train a binary classifier.  
We had the students experiment with changing the learning rate of the gradient descent method, observing how this choice affects optimization and convergence of the algorithm.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/training_binary.png" alt="Training script" style="width:40%;"><br><em>Training script for binary classification.</em>  
</p>  

### Step 4: Test the Model  
Finally, students tested their models using new drawings, including some borrowed from classmates.  
The `testing_binary.py` script displayed predictions in real time.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/testing_binary.png" alt="Testing script" style="width:40%;"><br><em>Testing script used to evaluate classification results.</em>  
</p>  

**Reflection Questions:**  
- Which step size led to faster or more stable convergence?  
- How many images did your model classify correctly?  
- Were some drawings harder to classify?  

This activity introduced students to the **full machine learning workflow**: data collection, labeling, training, optimization, and evaluation.  

## Task 2: Handwritten Digit Classification (MNIST on Arduino)  

### Goal  
Students built and deployed a neural network on the Arduino Nano 33 BLE Sense to recognize handwritten digits (0–9) in real time.  

### Model Design and Constraints  
- Models were first trained in Python (`training_MNIST.py`) and then exported to Arduino (`handwritten_digit_recognition.ino`).  
- TinyML hardware limitations forced creative design choices:  
  - ≤ **4 hidden layers**  
  - ≤ **900 neurons total**  
- Students experimented with different **optimizers** (Adam, SGD, RMSprop) and **activation functions** (ReLU, tanh, sigmoid).  

### Building the Dataset  
- Instead of a pre-loaded dataset, students created their own:  
  - Digits (0–9) were drawn on index cards.  
  - Each card was placed under the Arduino’s camera.  
  - Image capture was triggered by pressing **reset + onboard buttons**.  

<p align="center">
  <img src="/assets/tinyml/summer2025/numbers.jpg" 
       alt="Handwritten digit cards used for Task 2 classification" 
       style="width:30%;"><br>
  <em>Example of handwritten digit card used for Task 2.</em>
</p>

### Testing and Results  
- Predictions were displayed directly in the Arduino Serial Monitor.  
- Each team tested their models on a **set of 8–10 digit cards**.  

**Key Takeaways:**  
- Certain digits (like 4, 7, 9) were harder to classify consistently.  
- Larger networks improved accuracy but risked **overfitting** on the small dataset.  
- Students saw how changes in neurons, layers, and optimizers impacted performance.  

**Reflection Questions:**  
- Which digits were hardest to classify?  
- What happened when the first layer grew from 100 to 700 neurons?  
- How many digits did your team classify correctly out of 10?  

---


## Outcomes  

The camp provided students with a **hands-on introduction** to optimization, neural networks, and TinyML.  

- **Task 1** (binary shapes): demonstrated how gradient descent and learning rate choices affect optimization.  
- **Task 2** (digits): extended to deeper models and showed the limits of on-device ML.  

Overall, the project bridged **optimization theory** with **practical embedded ML deployment**, offering students both intuition and experience in how AI systems are built and tested in real-world settings.  
