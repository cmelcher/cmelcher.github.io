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
  <img src="/assets/tinyml/summer2025/arduinopic.jpeg" alt="Arduino Nano 33 BLE Sense kit" style="width:40%;"><br>
  <em>Arduino Nano 33 BLE Sense board.</em>
</p>

---

## What is TinyML?  

TinyMl (Tiny Machine Learning) is an environment for deploying ML models on microcontrollers. TinyML takes the learning methods that usually run on powerful GPUs and CPUs and compresses them to work on small, low-power devices. 
- Models must be compact (few layers, limited total number of neurons).  
- Models run directly on the device, without needing cloud interaction. This makes computation more efficient and helps with privacy considerations.   
- Applications include embedded computer vision and speech recognition.

In this session, students used TinyML to classify shapes and handwritten digits in real time directly on the Arduino board.  
<p align="center">
  <img src="/assets/tinyml/summer2025/kitsetup0.jpeg" alt="kitsetup" style="width:40%;"><br>
  <em>Setup for the two activities</em>
</p>

---

## Task 1: Classifying Stars and Circles  

In the first activity, students worked with a simple binary image classifier using the Arduino Nano 33 BLE Sense.  
The goal was to train a model that could accurately predict whether a drawing was a **star** or a **circle**.  

### Step 1: Create a Dataset  
Students drew their own stars and circles on sticker cards. These cards were then placed over the Arduino’s built-in camera to capture training images.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/star.jpg" alt="Star card example" style="width:40%;"><br>  
  <br><em>Example student star drawing used for training.</em>  
</p>  

### Step 2: Capture Images  
A pre-written Python script (`reading_image.py`) was used to capture images from the Arduino and save them with labels.  
Students updated the label parameter to distinguish between stars and circles.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/reading_binary.png" alt="Python script for image capture" style="width:40%;"><br><em>Script for capturing and labeling images.</em>  
</p>  

### Step 3: Train the Model  
Once the dataset was ready, students ran a second script (`training_binary.py`) to train a binary classifier.  
They also experimented with the **learning rate** to see how step size affects optimization and convergence.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/training_binary.png" alt="Training script" style="width:40%;"><br><em>Training script for binary classification.</em>  
</p>  

### Step 4: Test the Model  
Finally, students tested their models using new drawings, including some borrowed from classmates.  
A testing script (`testing_binary.py`) displayed predictions in real time, showing whether the model classified the card as a star or a circle.  

<p align="center">  
  <img src="/assets/tinyml/summer2025/testing_binary.png" alt="Testing script" style="width:40%;"><br><em>Testing script used to evaluate classification results.</em>  
</p>  

Students repeated the testing step several times, recording their model's overall accuracy. This activity introduced students to the **full machine learning workflow**:data collection and labeling, to training, optimization, and evaluation.  


---

## Task 2: Handwritten Digit Classification (MNIST on Arduino)  

### Goal  
Students built and deployed a neural network on the Arduino Nano 33 BLE Sense to recognize handwritten digits (0–9) in real time.  

### Model Design and Constraints  
- Models were first trained in Python (`training_MNIST.py`) and then exported to Arduino (`handwritten_digit_recognition.ino`).  
- TinyML hardware limitations forced creative design choices:  
  - ≤ **4 hidden layers**  
  - ≤ **900 neurons total**  
- Students experimented with different **optimizers** (Adam, SGD, RMSprop) and **activation functions** (ReLU, tanh, sigmoid) to balance accuracy and efficiency.  

### Building the Dataset  
- Instead of using a pre-loaded dataset, students created their own:  
  - Digits (0–9) were drawn on index cards.  
  - Each card was placed under the Arduino’s camera.  
  - Image capture was triggered by pressing the **reset + onboard buttons**.  

<p align="center">
  <img src="/assets/tinyml/summer2025/numbers.jpg" 
       alt="Handwritten digit cards used for Task 2 classification" 
       style="width:30%;"><br>
  <em>Example of handwritten digit card used for Task 2.</em>
</p>

### Testing and Results  
- Predictions were displayed directly in the Arduino Serial Monitor.  
- Each team tested their models on a **set of 8–10 digit cards**.  
- Key takeaways:  
  - Certain digits (like 4, 7, 9) were harder to classify consistently.  
  - Larger networks improved accuracy but risked **overfitting** on the small dataset.  
  - Students experienced first-hand the **trade-offs** of deploying ML under real-world hardware limits.  

----

## Outcomes  

The camp provided students with a **hands-on introduction** to optimization, neural networks, and TinyML.  

- **Task 1** (binary shapes): demonstrated how gradient descent and learning rate choices affect optimization.  
- **Task 2** (digits): extended to deeper models and showed the limits of on-device ML.  

Overall, the project bridged **optimization theory** with **practical embedded ML deployment**, offering students both intuition and experience in how AI systems are built and tested in real-world settings.  
