MNIST Multi-Layer Perceptron Optimization
Project Overview
This project systematically explores the hyperparameter space for Multi-Layer Perceptrons (MLPs) on the MNIST handwritten digit classification task. The goal was to identify the optimal combination of network architecture, activation functions, learning rates, and optimizers to maximize validation accuracy while staying within a 200,000 parameter constraint.
Objective
Train and evaluate MLP models on MNIST to:

Achieve the highest possible validation accuracy under 200,000 parameters
Understand the relative impact of different hyperparameters on model performance
Document experimental methodology and results for reproducibility

Constraints

No convolutional layers - MLPs only (fully connected/dense layers)
Maximum 200,000 parameters per model
No meta-learning techniques
Standard MNIST dataset (60,000 training images, 10,000 test images)

Experimental Design
Initial Comprehensive Search (135 Experiments)
I designed a systematic grid search across four key dimensions:
1. Architectures (5 variations):

Small [128, 64] - Baseline funnel architecture (~109k params)
Medium [200, 100] - Wider layers for increased capacity (~178k params)
Deep [128, 128, 64] - Three-layer depth test (~126k params)
Narrow_Deep [64, 64, 64, 64] - Four layers testing efficiency through depth (~63k params)
Very_Deep [150, 100, 75, 50, 25] - Five-layer hierarchical learning (~146k params)

2. Activation Functions (3 types):

ReLU (Rectified Linear Unit)
Tanh (Hyperbolic Tangent)
Sigmoid

3. Learning Rates (3 values):

0.001 (conservative)
0.01 (moderate)
0.1 (aggressive)

4. Optimizers (3 algorithms):

SGD (Stochastic Gradient Descent)
SGD with Momentum (0.9)
Adam (Adaptive Moment Estimation)

Total: 5 architectures × 3 activations × 3 learning rates × 3 optimizers = 135 unique configurations
Methodology
Each experiment:

Built the specified MLP architecture
Trained for 10 epochs with batch size 128
Tracked training accuracy, validation accuracy, training loss, and validation loss
Logged all metrics to a structured spreadsheet for analysis

Refinement Phase
After identifying the best-performing configuration from the initial 135 experiments, I conducted targeted refinement:

Architecture variations - Testing slight modifications around the winning architecture
Learning rate fine-tuning - Narrower search around optimal learning rate
Dropout regularization - Attempting to reduce overfitting and improve generalization

Tools & Libraries

Python 3.x
TensorFlow/Keras - Model building and training
NumPy - Data manipulation
Pandas - Results tracking and analysis
Matplotlib/Seaborn - Visualization (optional)
Google Colab - GPU-accelerated training environment

Key Findings
(You can fill this in with your actual results)
The optimal configuration achieved 98.04% validation accuracy:

Architecture: Small [128, 64]
Activation: ReLU
Learning Rate: 0.001
Optimizer: Adam
Training Accuracy: 99.34%
Validation Loss: 0.0741

Additional insights:

ReLU activation consistently outperformed tanh and sigmoid
Adam optimizer showed superior performance across most configurations
The relatively simple [128, 64] architecture proved optimal - deeper/wider networks showed diminishing returns
Dropout regularization reduced overfitting but decreased overall validation accuracy

Repository Structure
├── mnist_mlp_optimization.ipynb    # Main Jupyter notebook with all experiments
├── mnist_mlp_experiments.xlsx      # Comprehensive results spreadsheet
├── README.md                       # This file
└── visualizations/                 # (Optional) Charts and graphs
How to Run

Open the notebook in Google Colab or Jupyter
Ensure GPU runtime is enabled (Runtime → Change runtime type → GPU)
Run cells sequentially
Results will be exported to an Excel file for analysis

Lessons Learned

Systematic hyperparameter search is essential for finding optimal configurations
More parameters doesn't always mean better performance - architecture efficiency matters
The train-validation gap can indicate overfitting, but small gaps may represent normal model behavior
For MNIST with simple MLPs, well-tuned smaller architectures can achieve excellent results without complex regularization
