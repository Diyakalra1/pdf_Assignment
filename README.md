# Probability Density Function Learning using Roll-Number-Parameterized Non-Linear Transformation

## Project Overview
This project focuses on learning a probability density function (PDF) from real-world environmental data using a roll-number-dependent non-linear transformation. The objective is to understand how probability distributions can be modeled from transformed data using statistical estimation techniques.

Nitrogen Dioxide (NO₂) concentration values from an Indian air quality dataset are transformed using a custom sinusoidal function. After transformation, a Gaussian-like probability density function is learned from the resulting values.

---

## Dataset Description

- **Dataset Name:** India Air Quality Dataset  
- **Source:** Kaggle  
- **Feature Used:** NO₂ (Nitrogen Dioxide concentration)  
- **Data Type:** Continuous numerical values  

### Preprocessing Steps
- Removed non-numeric entries  
- Dropped missing values  
- Cleaned column names for consistency  

---

## Step 1: Non-Linear Transformation

Each NO₂ value \( x \) is transformed into a new variable \( z \) using the equation:

\[
z = x + a_r \sin(b_r x)
\]

Where the coefficients depend on the university roll number \( r \):

\[
a_r = 0.05 \times (r \bmod 7)
\]

\[
b_r = 0.3 \times ((r \bmod 5) + 1)
\]

### Purpose of the Transformation
- Introduces controlled non-linearity into the data  
- Ensures unique transformation for each roll number  
- Simulates realistic distortions in environmental measurements  

---

## Step 2: Probability Density Function Learning

The probability density function of the transformed variable \( z \) is modeled as:

\[
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
\]

This represents a Gaussian-like distribution defined by parameters \( \mu \), \( \lambda \), and \( c \).

---

## Parameter Estimation Methodology

### Parameter Definitions

| Parameter | Description |
|---------|------------|
| \( \mu \) | Mean of transformed data |
| \( \sigma^2 \) | Variance of transformed data |
| \( \lambda \) | Spread parameter |
| \( c \) | Normalization constant |

### Estimation Formulas

\[
\mu = \frac{1}{n}\sum_{i=1}^{n} z_i
\]

\[
\sigma^2 = \frac{1}{n}\sum_{i=1}^{n}(z_i - \mu)^2
\]

\[
\lambda = \frac{1}{2\sigma^2}
\]

\[
c = \frac{1}{\sigma \sqrt{2\pi}}
\]

---

## Results

The parameters \( \mu \), \( \lambda \), and \( c \) are computed directly from the transformed dataset. These values vary based on the roll number and the dataset used.

---

## Result Visualization

The notebook includes:
- Histogram of transformed variable \( z \)
- Learned probability density function curve
- Comparison between empirical distribution and learned PDF

---

## Experimental Workflow

1. Load the air quality dataset  
2. Extract NO₂ values  
3. Apply roll-number-based non-linear transformation  
4. Estimate PDF parameters  
5. Learn the probability density function  
6. Analyze results through visualization  

---

## How to Run the Project

1. Download the dataset from Kaggle  
2. Place the dataset in the working directory or update the file path  
3. Update the roll number in the notebook  
4. Run all cells sequentially  
5. Observe parameter values and plots  

---

## Conclusion

This project demonstrates how probability density functions can be learned from real-world data using non-linear transformations and statistical estimation methods. The roll-number-based transformation ensures uniqueness, while the Gaussian-like PDF provides mathematical clarity and interpretability.

---

## References

- Probability Theory and Statistics  
- Gaussian Distribution  
- Maximum Likelihood Estimation  
- India Air Quality Dataset (Kaggle)  
