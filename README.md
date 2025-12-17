# Javascript-FacadeRNN

This repository provides a facaded, browser-based Recurrent Neural Network (RNN) system in JavaScript. It supports Simple RNN, LSTM, and GRU architectures, with full introspection and manipulation through a user-accessible facade API. The application allows step-by-step exploration of all internal RNN states and sequence behavior.

---

## Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Basic Example](#basic-example)
- [Facade API](#facade-api)
- [Usage Notes](#usage-notes)
- [License](#license)

---

## About

Javascript-FacadeRNN is an interactive web application for building, training, and analyzing sequence models using modern recurrent neural network cells.  
A facade API is provided, exposing every neuron, gate, gradient, optimizer statistic, and sequence state in the model.  
This design enables technical transparency, controlled experimentation, and educational demonstration of RNNs, LSTMs, and GRUs for time-series or sequential data.

---

## Features

- Configurable RNN models:
  - Select Simple RNN, LSTM, or GRU cell type
  - Adjustable input, output, and multi-layer hidden network sizes
  - Choice of activation functions (`tanh`, `sigmoid`, `relu`, or `linear`)
  - Output activation options (`sigmoid`, `tanh`, `softmax`, `linear`)
  - Loss options (`MSE` or `Cross-Entropy`)
  - Training hyperparameters: learning rate, dropout, gradient clipping, and BPTT step size
- Data management:
  - Upload sequence data from CSV files
  - Paste CSV directly or synthesize classed sequence data in-browser
  - Train/validation splitting and batch size selection
- Training and evaluation:
  - Progress and loss tracking over training epochs
  - Live chart of training and validation loss
- Facade-based introspection and manipulation:
  - Inspect/set all neuron states and outputs at any timestep/layer
  - Access or modify hidden and cell states (LSTM), or gate values (LSTM/GRU)
  - Step through and visualize gradients, optimizer states, dropout masks, and LayerNorm stats
  - Sequence-wide access to all hidden/cell states, output sequences, and gate values
  - Tools for histogramming, gradient flow, and checking for vanishing/exploding gradients
  - Reset or inject arbitrary states (useful for experiments or ablation)
- Prediction and evaluation:
  - Enter custom input sequences for inference and view outputs

---

## Getting Started

### Requirements

- A modern web browser (Chrome, Firefox, Edge, Safari, etc.)

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/matthewJamesAbbott/Javascript-FacadeRNN.git
    ```
2. Open `index.html` with your browser.

_No installation or server needed._

---

## Basic Example

To build and train an LSTM on synthetic sequence data:

1. Open `index.html`
2. Under **Network Configuration**:
    - Input Size: `4`
    - Hidden Sizes (comma sep): `8,8`
    - Output Size: `3`
    - Cell Type: `LSTM`
    - Activation: `Tanh`
    - Output Activation: `Linear`
    - Loss Function: `MSE`
    - Learning Rate: `0.01`
3. Click **Create Network**
4. Click **Generate Test Data** with default or preferred sample count and class count
5. Under **Train Network**:
    - Epochs: `100`
    - Batch Size: `1`
    - Validation Split: `0.2`
    - Log Interval: `10`
6. Click **Train RNN** or **Train with Progress**
7. Use **RNN Facade API Explorer** to inspect and manipulate internal network states.

---

## Facade API

This application exposes all internal model details through the **RNN Facade API Explorer** section. Actions include:

- Step-by-step access to hidden, cell, output, gate, pre-activation, and input vector values (per layer/timestep/neuron)
- Visualization and access to gradients, optimizer statistics, and dropout masks
- Extraction of entire hidden state, cell state, gate, or output sequences
- Diagnostics: histogram visualizations, vanishing/exploding gradient detection
- State mutation: reset/inject hidden/cell/output state at arbitrary positions

API operations are available via web UI controls. Results display in the output panel or as visualizations/histograms.

---

## Usage Notes

- Model/head sizes are limited primarily by browser performance and memory
- Single or small batch training is default; for larger data, use appropriate batch sizes and validation splits
- All data remains within your browser; no cloud storage or external data transmission
- CSV format should be row-wise: `[input values..., target values...]`, one sequence per row

---

## License

MIT License.  
Use, modify, and share freely for any purpose.

---

## Vercel Link

https://javascript-facade-rnn.vercel.app/
