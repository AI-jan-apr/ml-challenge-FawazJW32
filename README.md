### Overview

This project contains two machine learning tasks focused on:

- Multi-Label Classification

- Noise Introduction and Removal using Machine Learning

Both tasks are implemented using the MNIST dataset (mnist_784) from OpenML.

- The goal is to understand how machine learning models behave when:

- Predicting multiple labels per sample

- Learning to reconstruct clean data from noisy inputs

### ✅ Task 1 — Multi-Label Classification
🎯 Objective

Convert the original MNIST digit labels into a multi-label format, then train a model to predict both labels simultaneously.

Instead of predicting:
```text
Digit = 7
```
We predict two properties:
```text
Odd or Not

Greater Than 5
```
Example:
```text
Digit	Odd	Greater Than 5
3	True	False
8	False	True
```
### 🛠 Methodology
1️⃣ Load Dataset
```text
MNIST (70,000 images)

28x28 grayscale images (784 features)
```
2️⃣ Convert Labels

Two binary labels were created:
```text
Odd = (digit % 2 == 1)

GreaterThan5 = (digit > 5)
```
3️⃣ Model

Used:
```text
StandardScaler

OneVsRestClassifier

LogisticRegression
```
- Implemented inside a Pipeline to prevent data leakage.

4️⃣ Evaluation Metrics

Since this is multi-label classification, I used:

- Precision

- Recall

- F1-Score

- Subset Accuracy (strict metric)

Subset Accuracy counts a sample as correct only if both labels are correct.

### 📊 Results

The model successfully learned both binary tasks simultaneously.

Multi-label classification allows a single input to have multiple outputs, which is useful in:

- Image tagging

- NLP tagging systems

- Recommendation systems

### ✅ Task 2 — Noise Removal Using Machine Learning
🎯 Objective

- Simulate noise in image data and train a model to reconstruct the original clean image.

This is a denoising regression problem.

### 🛠 Methodology
1️⃣ Normalize Images

Pixel values scaled from:
```text
[0, 255] → [0, 1]
```
2️⃣ Add Gaussian Noise

Noise was introduced using:
```text
X_noisy = X_clean + Gaussian noise
```
Noise standard deviation controlled corruption strength.

3️⃣ Model

Used:

- StandardScaler

- Ridge Regression

- Pipeline ensures:

Scaling learned from training data only

- No data leakage

The model learns:
```text
Noisy Image → Clean Image
```text
4️⃣ Evaluation Metrics
```
Used regression metrics:

- Mean Squared Error (MSE)

- Root Mean Squared Error (RMSE)

Lower RMSE indicates better reconstruction.

### 📈 Visualization

For evaluation, we plotted:

- Noisy image

- Reconstructed image

- Ground truth clean image

This visually demonstrates the model’s ability to remove noise.

### 🧠 Key Concepts Learned
🔹 Multi-Label Classification
```text
One sample → Multiple outputs
```
Different from multi-class classification.

🔹 Data Leakage Prevention

- Split before scaling

- Fit scaler only on training data

- Use Pipeline for safety

🔹 Noise Robustness

- Real-world datasets are often noisy.
- Machine learning models must handle corrupted or imperfect data.

🔹 Denoising via Regression

- Mapping corrupted input back to clean output.

### 📦 Requirements
```text
numpy
pandas
scikit-learn
matplotlib
seaborn
jupyter
```
Install using:
```text
pip install -r requirements.txt
```
