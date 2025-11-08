# Parametric Curve Fitting Assignment

## Assignment Overview
This assignment aims to find the unknown parameters (theta, M, X) of a parametric curve given by:

x(t) = t * cos(theta) - e^(M*|t|) * sin(0.3*t) * sin(theta) + X  
y(t) = 42 + t * sin(theta) + e^(M*|t|) * sin(0.3*t) * cos(theta)

The L1 distance between the predicted curve and the given CSV data points is used as the primary metric for assessment.

---

## Optimized Parameters

- **Theta (deg):** 28.1184  
- **M:** 0.02139  
- **X:** 54.9008  

---

## Parametric Equation (LaTeX)

\[
\left( t \cos(28.1184^\circ) - e^{0.02139 |t|} \sin(0.3 t) \sin(28.1184^\circ) + 54.9008,\ 42 + t \sin(28.1184^\circ) + e^{0.02139 |t|} \sin(0.3 t) \cos(28.1184^\circ) \right)
\]

(t * cos(0.49046) - e^(0.02139 * |t|) * sin(0.3*t) * sin(0.49046) + 54.9008, 42 + t * sin(0.49046) + e^(0.02139 * |t|) * sin(0.3*t) * cos(0.49046))

---

## Average L1 per point

**25.2434**

---

## Process and Steps Followed

1. **Data Loading**
   - The CSV file `xy_data.csv` containing `(x, y)` points was loaded using pandas.
   - Extracted `x_data` and `y_data` as NumPy arrays.

2. **Parametric Model Definition**
   - Defined a function `model(params, t)` to compute `(x, y)` given parameters theta, M, X and array of t-values.

3. **Loss Function (L1 Distance)**
   - Defined `loss(params, t, x_data, y_data)` as the sum of absolute differences between predicted and actual points.
   - L1 distance was chosen as it directly corresponds to the assignment scoring metric.

4. **Parameter Optimization**
   - Set initial guess: theta = 25°, M = 0.0, X = 50.
   - Set bounds according to the assignment:
     - 0° < theta < 50°  
     - -0.05 < M < 0.05  
     - 0 < X < 100
   - Used `scipy.optimize.minimize` to find the parameters that minimize the L1 loss.

5. **Prediction and Visualization**
   - Generated predicted points using the optimized parameters.
   - Plotted the predicted curve alongside the CSV points to verify the fit visually.

6. **Evaluation**
   - Calculated total L1 distance and average L1 per point.
   - The average L1 per point was found to be **25.2434**.

---

## How to Use

1. Open the notebook `parametric_curve_fitting.ipynb` in Google Colab.  
2. Upload `xy_data.csv` to the Colab environment.  
3. Run all cells to reproduce results:
   - Optimized parameters
   - Parametric equation
   - Average L1 per point
   - Plot showing CSV points vs predicted curve
