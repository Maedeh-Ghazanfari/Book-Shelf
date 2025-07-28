📘 Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow (2nd Edition) by Aurélien Géron

This is a personal study repo where I take notes as I work through the book. My goal is to understand ML concepts better and build a review-friendly reference for myself and others. Feel free to follow along, fork, or suggest ideas!

* Not all the topics here in the book, but there was something in the book that made me search and study new issues!

🧠 What I’ve learned so far:

## Some Types of Noise in Data

Stochastic Noise: Random variations in data that cannot be explained by input features — also known as irreducible error. It’s unpredictable, not caused by the model, and inherent in real-world data.


Rounding Error: A rounding error is a deterministic type of noise that arises due to limitations in how numbers are stored or represented, especially when working with floating-point numbers. Rounding error occurs when a number cannot be represented exactly in the computer's memory, so it gets rounded to the nearest representable value. It’s systematic, meaning it's introduced in a predictable, repeatable way.

## Plots along with the correlation coefficient between their horizontal and vertical axes:

<img width="858" height="381" alt="image" src="https://github.com/user-attachments/assets/30aa8760-443d-44bb-b165-6a0a8b7f3785" />

## Feature Scaling:

<img width="838" height="293" alt="image" src="https://github.com/user-attachments/assets/74dbb2cb-594c-4c6e-9be7-2a4935615050" />

Always split before normalizing.  Normalize test data using training data stats. If you normalize before splitting, the min and max (or mean and std) used for scaling will be influenced by the test set. That means your test data is "leaking" into your training process — this is called data leakage, and it can lead to unrealistically good performance.

Which algorithms need scaling?

Some algorithms are sensitive to the scale or units of the features because they rely on distances or gradients; therefore, they require scaling:

k-NN uses Euclidean distance to compare samples
Logistic Regression	uses gradient descent for optimization
Linear Regression (if GD used)	Same as above
SVM (Support Vector Machine)	Distance to the hyperplane matters
K-Means Clustering	Uses distances to cluster centers
PCA	Based on variance/covariance, sensitive to scale
Neural Networks	Gradient-based; scales improve convergence

*Remember, tree-based models don't need scaling.

## Parametric VS non-parametric algorithms:

Parametric (e.g., Linear Regression):
 
You decide the form of the model ahead of time.

Only learn a fixed number of parameters (weights).

May underperform if data doesn't fit the assumed shape (e.g., non-linear trends).

Non-Parametric (e.g., Decision Tree):

No equation assumed.

It learns structure from the data itself (e.g., where to split based on feature values).

Model complexity grows as data grows.

More flexible and can fit complex patterns, but can overfit if not controlled.

Pros for non-parametric:

Non-parametric models are more powerful for:

Capturing non-linear relationships

Working with messy real-world data

Avoiding incorrect assumptions (like “data must be normally distributed”)

Cons:

May need more data to work well

Tend to be slower or more memory-intensive

They are often harder to interpret

## Hard classification VS Soft classification:


| Aspect               | Hard Classification                     | Soft Classification                                        |
| -------------------- | --------------------------------------- | ---------------------------------------------------------- |
| **What it predicts** | A single class label (e.g., “cat”)      | Probabilities for all classes (e.g., “cat: 0.7, dog: 0.3”) |
| **Output type**      | Discrete, e.g., class 0 or class 1      | Continuous probabilities between 0 and 1                   |
| **Decision rule**    | Pick the class with highest probability | Use probabilities directly or threshold them               |
| **Use case**         | When you just want a class prediction   | When you need confidence levels, thresholds, or rankings   |
| **Example**          | Predict “spam” or “not spam”            | Predict “spam with 85% confidence”                         |


You can usually turn a classification into a soft classification if the model or method can provide class probabilities or scores instead of just hard labels.

## Regularization:

When a model learns too well from training data, it may start fitting noise rather than the actual pattern. This causes poor performance on new, unseen data.

Regularization helps by penalizing large weights in the model, encouraging simpler models that generalize better.

Regularization helps by adding a penalty to discourage the model from becoming too complex.


| Regularization | Model                  | scikit-learn Class   | Key Parameters           |
| -------------- | ---------------------- | -------------------- | ------------------------ |
| L2             | Ridge Regression       | `Ridge`              | `alpha`                  |
| L1             | Lasso Regression       | `Lasso`              | `alpha`                  |
| L1 + L2        | Elastic Net            | `ElasticNet`         | `alpha`, `l1_ratio`      |
| L2 (default)   | Logistic Regression    | `LogisticRegression` | `penalty`, `C`, `solver` |
| L2             | Support Vector Machine | `SVC`                | `C`, `kernel`            |


