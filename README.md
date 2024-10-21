# Kohonen Self-Organizing Map (SOM) for Color Mapping

## Overview

This project implements a **Kohonen Self-Organizing Map (SOM)** that organizes **24 colors** over a **100x100 grid** of neurons. The goal is to map RGB color shades (red, green, blue, yellow, teal, and pink) onto a 2D grid using an unsupervised learning approach, with the SOM adjusting its weights over time to create a meaningful color representation on the grid.

## Problem Statement

Designing a Kohonen SOM with the following characteristics:

- **Input**: 24 RGB color shades selected from [RGB Color Table: Basic Colors](http://www.rapidtables.com/web/color/RGB_Color.htm).
- **Grid Size**: 100x100 neurons.
- **Learning Rate**: A time-varying learning rate \( \alpha(k) = \alpha_0 \exp \left(-\frac{k}{T} \right) \), where:
  - \( k \) is the current training epoch (starting from 0),
  - \( \alpha_0 = 0.8 \),
  - \( T = 1000 \) is the total number of epochs.
  
- **Neighborhood Function**: The topological neighborhood function \( N_{i,j}(k) \) of a node \( j \) around the winning unit \( i \) is given by:
  \[
  N_{i,j}(k) = \exp \left( -\frac{d_{i,j}^2}{2\sigma^2(k)} \right)
  \]
  Where:
  - \( d_{i,j} \) is the distance between the winning node \( i \) and the surrounding node \( j \),
  - \( \sigma(k) = \sigma_0 \exp \left( -\frac{k}{T} \right) \),
  - \( \sigma_0 \) is varied with values of 1, 10, 30, 50, 70.

## Methodology

### Input Colors

The input to the SOM consists of **24 RGB colors** (shades of red, green, blue, yellow, teal, and pink). The RGB values are normalized between 0 and 1 for the SOM training (as opposed to the usual 0 to 255 scale).

### Learning Rate

The learning rate \( \alpha(k) \) decreases exponentially over the training process, starting with \( \alpha_0 = 0.8 \) and decreasing to ensure gradual adjustment of weights.

### Neighborhood Function

The neighborhood function \( N_{i,j}(k) \) defines how the weights of neighboring nodes are updated relative to the winning neuron. The size of the neighborhood decreases with increasing epochs, allowing the network to fine-tune weights.

### Training Process

- The SOM is initialized with random weights.
- Over **1000 epochs**, the SOM is trained using the **24 input colors**, adjusting weights based on the current learning rate and neighborhood size.
- The SOM output is visualized at epochs **20, 40, 100, and 1000** to track its progress.

## Visualization

The SOM output is visualized at several stages:
1. **Initial grid** (random weights).
2. After **20 epochs**.
3. After **40 epochs**.
4. After **100 epochs**.
5. After **1000 epochs**.

I experimented with different values of \( \sigma_0 = 1, 10, 30, 50, 70 \) to observe how the topological neighborhood size influences the SOM's performance and output.

