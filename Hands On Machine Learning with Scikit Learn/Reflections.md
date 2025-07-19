📘 Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow (2nd Edition) by Aurélien Géron
This is a personal study repo where I take notes as I work through the book. My goal is to better understand ML concepts and build a review-friendly reference for myself and others. Feel free to follow along, fork, or suggest ideas!

🧠 What I’ve learned so far:

🎯Types of Noise in Data

+Stochastic Noise: Random variations in data that cannot be explained by input features — also known as irreducible error. It’s unpredictable, not caused by the model, and inherent in real-world data.
+Rounding Error: A rounding error is a deterministic type of noise that arises due to limitations in how numbers are stored or represented, especially when working with floating-point numbers. Rounding error occurs when a number cannot be represented exactly in the computer's memory, so it gets rounded to the nearest representable value. It’s systematic, meaning it's introduced in a predictable, repeatable way.

Summary of noises:
1. Stochastic Noise (Irreducible Noise)
Definition: Random, unpredictable variations in data.
Cause: Natural randomness or variables not captured in the features.
Example: Human behavior data; even with the same inputs, people might react differently.
Handling: Can't be removed, but models like ensemble methods or probabilistic models can minimize its impact.

2. Deterministic Noise
Definition: Comes from model limitations — the model is too simple to capture patterns.
Example: Fitting a linear model to a nonlinear relationship.
Handling: Use a more expressive model (e.g., move from linear regression to a decision tree or neural net).

3. Label Noise (Mislabeled Data)
Definition: Incorrect target labels.
Example: An image of a cat labeled as "dog".
Handling: Clean the labels manually or with heuristics.
Use robust models (like noise-tolerant loss functions).
Semi-supervised learning can help when only some labels are noisy.

4. Feature Noise
Definition: Errors or variability in the input features.
Example: A height sensor that slightly mismeasures every reading.
Handling: Smoothing (like moving averages),
Feature scaling or transformation,
Dimensionality reduction (e.g., PCA),
Outlier detection.

5. Rounding/Quantization Noise
Definition: Data gets rounded due to limited precision.
Example: Rounding weights to 2 decimal points.
Handling: Use higher precision if possible.
Apply denoising techniques if it affects performance (e.g., Gaussian noise injection during training to generalize better).

