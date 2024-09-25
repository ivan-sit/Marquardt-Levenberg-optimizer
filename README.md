# Marquardt-Levenberg Optimizer

This project implements a custom Marquardt-Levenberg optimizer in PyTorch/TensorFlow, designed for non-linear least squares problems. The optimizer is designed to efficiently handle matrix inversion and multiplication, and includes profiling to analyze the computation time spent on various operations.

## Features

- **Custom Optimizer**: Implements the Marquardt-Levenberg optimization algorithm, a popular method for non-linear least squares problems.
- **Performance Profiling**: Profiles the percentage of time spent on matrix multiplications, matrix inversions, and other operations during optimization.
- **Flexible and Extendable**: Built on top of PyTorch/TensorFlow, making it easy to integrate into existing projects.

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/your-repository-name.git
Navigate to the project directory:

bash
Copy code
cd your-repository-name
Install the necessary dependencies:

bash
Copy code
pip install -r requirements.txt
(Note: Make sure to include a requirements.txt if your project has specific dependencies.)

Usage
Basic Example
Here is an example of how to use the Marquardt-Levenberg optimizer:

python
Copy code
import torch
from marquardt_levenberg import MarquardtLevenberg

model = torch.nn.Linear(10, 2)
optimizer = MarquardtLevenberg(model.parameters(), lr=1e-3, lambd=1e-2)

input = torch.randn(5, 10)
target = torch.randn(5, 2)
criterion = torch.nn.MSELoss()

for epoch in range(10):
    def closure():
        optimizer.zero_grad()
        output = model(input)
        loss = criterion(output, target)
        loss.backward()
        return loss

    optimizer.step(closure)

optimizer.profile()
Profiling
The optimizer includes a profiling method to analyze the time spent on different operations:

python
Copy code
optimizer.profile()
This will output the percentage of time spent on matrix inversion, matrix multiplication, and other operations.
