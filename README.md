
# Artificial Neural Network — Forward Propagation From Scratch

This project implements a simple Artificial Neural Network (ANN) **from scratch in Python** and demonstrates how predictions are produced using **forward propagation**.  
The notebook builds the network structure, initializes weights and biases, and computes node activations layer by layer until producing the final output.

The purpose of the project is educational: to clearly illustrate how neural networks compute predictions internally.

---

## Table of Contents

- Overview
- Neural Network Computation
- Project Workflow
- Code Structure
- Forward Propagation Algorithm
- Results and Analysis
- Running the Notebook

---

## Overview

Here, I build a neural network from scratch and see how it predicts using forward propagation.

Artificial Neural Networks consist of layers of nodes where each node computes:

1. A **weighted sum** of its inputs  
2. A **nonlinear activation function**

This process repeats layer by layer until the **output layer** produces the final prediction.

---

## Neural Network Computation

Each node performs two main computations.

### Weighted Sum

For inputs \(x_1, x_2, ..., x_n\), weights \(w_1, w_2, ..., w_n\), and bias \(b\):

```

z = w_1 x_1 + w_2 x_2 + ... + w_n x_n + b

```

or equivalently

```

z = w · x + b

```

### Sigmoid Activation Function

The activation function used in this notebook is the **sigmoid**:

```

σ(z) = 1 / (1 + e^{-z})

```

This converts the weighted sum into a value between **0 and 1**, which allows the network to model nonlinear relationships.

---

## computing output for given inputs

The notebook first demonstrates how a neural network computes an output for specific input values by manually calculating the weighted sums and applying the sigmoid function.

This step illustrates how hidden layer activations are produced before computing the final output.

---

## Build a Neural Network

The project then constructs a full neural network programmatically.  
The network structure contains:

- Input layer
- One or more hidden layers
- Output layer

Each node contains:

- A vector of weights
- A bias value

---

## initialize weights

Weights and biases are randomly initialized when creating the network.

Random initialization is important because it prevents symmetric learning and allows different nodes to learn different patterns.

---

Previous code initializes weights and biases for any network with any number of nodes and layers. Now I put it in a function.

---

## Initializing a network

The notebook defines a function that generates the network structure with randomly initialized parameters.

Each layer contains nodes stored in a dictionary structure such as:

```

network[layer][node] = {
weights,
bias
}

```

This makes the architecture flexible and easy to scale to different network sizes.

---

Using the function above, I calculate the weighted sum at the first node in the first hidden layer.  
The functions used random weight and random bias.

---

## Computing node activation (sigmoid)

After computing the weighted sum, the sigmoid activation function is applied to produce the node output.

The notebook defines a reusable function:

```

node_activation(weighted_sum)

```

which applies the sigmoid transformation.

---

Now I create a function that puts together the calculations of weighted sum and sigmoid for each layer and sends them to output layer.

---

## Forward Propagation Algorithm

The central function implemented in this project is:

```

forward_propagate(network, inputs)

```

The procedure works as follows:

1. Start with the input vector.
2. For each layer in the network:
   - Compute the weighted sum for every node
   - Apply the sigmoid activation
3. Store node outputs as the inputs for the next layer.
4. Continue until reaching the output layer.

Mathematically, each layer computes:

```

z^{(l)} = W^{(l)} x^{(l-1)} + b^{(l)}

```

followed by

```

a^{(l)} = σ(z^{(l)})

```

where

- \(W^{(l)}\) is the weight matrix
- \(b^{(l)}\) is the bias vector
- \(σ\) is the sigmoid activation

---

Using above function to calculate predictions of my network.

---

## Initializing another network

The notebook also demonstrates generating another randomly initialized network and running forward propagation again to produce predictions with different parameters.

This highlights how network outputs depend on the initialized weights.

---

So basically, here is what I did:<br>
1- initialize_network: randomly assigns weights to edges<br>
2- forward_propagate: calculates prediction by computing each weighted sum in the middle<br>

---

## Results and Analysis

During forward propagation the notebook prints:

- Weighted sums at nodes
- Hidden layer activations
- Final output prediction

These intermediate outputs help illustrate how information flows through the network.

The step-by-step outputs allow easy debugging and provide insight into how neural networks transform inputs into predictions.

---

## Running the Notebook

1. Clone the repository

```

git clone [https://github.com/yourusername/your-repository.git](https://github.com/yourusername/your-repository.git)

```

2. Install required packages

```

pip install numpy

```

3. Launch the notebook

```

jupyter notebook

```

4. Run the notebook cells sequentially to observe how the neural network computes predictions.

---

## Summary

This project demonstrates the fundamental mechanics of neural networks by implementing forward propagation from scratch.

Key components implemented:

- Random network initialization
- Weighted sum computation
- Sigmoid activation
- Layer-by-layer forward propagation

The notebook provides a transparent and educational view of how neural networks transform inputs into outputs.
```
