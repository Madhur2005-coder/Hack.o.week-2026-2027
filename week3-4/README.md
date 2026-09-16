# 🚀 ML Learning Playground — Interactive Web Application

An interactive, visual-first machine learning education platform covering core foundations, mathematics, supervised algorithms, pipelines, and clustering across **Weeks 3 through 10** of the ML curriculum. Built with HTML5 Canvas, modern Vanilla CSS (glassmorphism & dark aesthetic), Chart.js, and clean Vanilla JavaScript.

---

## 📚 Curriculum Breakdown

### 🐍 Week 3 & 4: Python & Data Science Essentials
- **Python Essentials**: Interactive code demos showing Functions, Object-Oriented Programming (Classes & Inheritance), List and Dictionary Comprehensions.
- **NumPy**: Vector and matrix operations, multidimensional array manipulation, broadcasting rules visualized with dynamic grid dimensions.
- **Pandas**: Interactive DataFrame viewer with live column sorting, department filtering, statistics aggregation (`groupby`), and table merging.
- **Data Visualization**: Chart.js-powered visualizations with customizable data sizes and plot types (Bar charts, Scatter plots, Line charts).

### 📐 Week 5 & 6: Math for Machine Learning
#### Linear Algebra
- **2D Vectors**: Draggable vector handles showing components $(x, y)$, magnitude $\|v\|$, and orientation angle $\theta$.
- **Dot Product & Projections**: Real-time vector projection scalar calculation:
  $$\mathbf{a} \cdot \mathbf{b} = \|\mathbf{a}\| \|\mathbf{b}\| \cos(\theta)$$
- **Matrix Transformations**: Interactive $2 \times 2$ matrix controls ($a_{11}, a_{12}, a_{21}, a_{22}$) transforming a 2D coordinate grid in real time with determinant display.
- **Eigenvalues & Eigenvectors**: Visual demonstration of invariant directions where $A\mathbf{v} = \lambda\mathbf{v}$.

#### Calculus for ML
- **Derivatives & Tangent Lines**: Dynamic tangent line moving along curves ($f(x) = x^2, \sin(x), x^3 - 3x$) showing the derivative slope $f'(x)$.
- **Gradient Descent**: 2D contour map of a bivariate loss surface with step-by-step or animated descent trajectory, tunable learning rate ($\alpha$), and momentum.
- **Chain Rule & Backpropagation**: Interactive computational graph displaying node values, forward evaluations, and backward gradient passes:
  $$\frac{\partial L}{\partial x} = \frac{\partial L}{\partial y} \cdot \frac{\partial y}{\partial x}$$

### 📈 Week 7 & 8: Supervised Learning Models
#### Regression
- **Linear Regression**: Interactive canvas allowing users to click and place points or generate noisy datasets, computing closed-form Ordinary Least Squares (OLS) line ($y = mx + b$) with MSE readout.
- **Polynomial Regression**: Degree slider ($1$ through $10$) displaying polynomial feature transformations and illustrating underfitting vs. overfitting.
- **Ridge ($L_2$) & Lasso ($L_1$) Regularization**: Side-by-side canvas visualization showing coefficient shrinkage and sparsity as penalty parameter $\lambda$ / $\alpha$ increases.
- **Cost Surface**: 3D-perspective contour bowl of Mean Squared Error with real-time parameter tracking ($w, b$).

#### Classification
- **Logistic Regression**: Interactive 2D point placement for Class 0 vs. Class 1, computing decision boundaries and plotting the Sigmoid activation curve:
  $$\sigma(z) = \frac{1}{1 + e^{-z}}$$
- **K-Nearest Neighbors (KNN)**: Multi-point 2D decision boundary rendering with live $K$ slider ($1$ to $15$), real-time accuracy, precision, recall metrics, and confusion matrix.
- **Model Comparison**: Side-by-side comparison of Logistic Regression vs. KNN across various dataset topologies (Linearly separable, Concentric circles, Moons, XOR).

### ⚙️ Week 9 & 10: Scikit-Learn Workflow & Clustering
#### Scikit-Learn Workflow & Pipelines
- **Interactive Pipeline Architect**: Live stage configurator:
  - *Imputation*: `SimpleImputer` (mean, median, constant, passthrough)
  - *Scaling*: `StandardScaler`, `MinMaxScaler`, `RobustScaler`, none
  - *Feature Engineering*: `PCA(n_components=2)`, `PolynomialFeatures(deg=2)`, `SelectKBest(k=2)`
  - *Estimators*: `LogisticRegression`, `RandomForestClassifier`, `SVC(rbf)`, `GradientBoostingClassifier`
- **Visual Transformation Flow**: Real-time vector inspection demonstrating how raw data ($[28, \text{NaN}, 45000]$) transforms stage-by-stage into scaled, dimensionally-reduced features and class probabilities.
- **Auto-Generated Python Code**: Production-grade Scikit-Learn code snippet updated dynamically with one-click copy.
- **Data Leakage & Cross-Validation**: Interactive 5-Fold visualizer illustrating why global pre-processing causes severe optimistic bias and how `Pipeline.fit()` encapsulates transformations strictly within training folds.

#### Clustering (Unsupervised Learning)
- **K-Means Clustering**:
  - Step-by-step Lloyd's algorithm controls: Assign Points $\leftrightarrow$ Update Centroids.
  - Centroid trajectory animation and K-Means++ initialization.
  - Interactive **Elbow Method Curve**: Real-time Within-Cluster Sum of Squares (WCSS / Inertia) plotted for $K=1 \dots 7$.
- **Hierarchical (Agglomerative) Clustering**:
  - Distance metrics with Single, Complete, and Average linkage criteria.
  - Paired **Interactive Dendrogram Canvas**: Slices the hierarchical merge tree with a dynamic horizontal threshold cutoff slider, immediately recoloring 2D clusters.
- **DBSCAN (Density-Based Clustering)**:
  - Density exploration with tunable Radius ($\varepsilon$) and $MinPts$ parameters.
  - Precise categorization into **Core Points**, **Border Points**, and **Noise / Outliers** ('×' markers).
  - Hover inspection revealing $\varepsilon$-neighborhood circles and neighbor counts.
- **Algorithm Comparison Suite**:
  - Side-by-side evaluation of K-Means vs. Hierarchical vs. DBSCAN on tricky geometries (Two Interlocking Moons, Concentric Circles, Convex Blobs).

### 🚀 Week 9 & 10 Capstone Project: Customer Segmentation & ML Pipeline Studio
A complete practical project tying together both topics:
- **Real-World E-Commerce Customer Dataset**: $N=188$ records with missing values ($NaN$) across Income, Spending Score, Age, Visits/Mo, and Acquisition Channels.
- **Leak-Free Scikit-Learn Preprocessing Pipeline**: `SimpleImputer(strategy='median')` $\to$ `StandardScaler()` $\to$ `PCA(n_components=2)`.
- **Tri-Clustering Behavioral Persona Segmentation**:
  - **K-Means**: Generates 4 marketing personas (*💎 VIP High Rollers*, *⚡ Impulsive Trendsetters*, *🛡️ Conservative Savers*, *🏷️ Budget Seekers*) with Silhouette score and automated marketing playbooks.
  - **Hierarchical**: Slices customer hierarchical dendrogram into clusters.
  - **DBSCAN**: Detects coherent high-density behavioral groups while isolating anomalous shopper accounts ('×' markers).
- **Interactive 2D Scatter Canvas**: Live canvas displaying customer coordinates with detailed hover tooltip cards.
- **Downstream Supervised ML Pipeline**: Fits a `Pipeline([('preprocessor', ...), ('classifier', RandomForestClassifier())])` predicting VIP conversion with Feature Importance percentages and a holdout confusion matrix.
- **Python Project & Jupyter Notebook Export**: 1-click clipboard copy and `.py` file download.

---

## 🛠️ Project Structure

```
d:\hackoweek\
├── index.html              # Main application shell with sidebar and responsive tabs
├── css/
│   └── styles.css          # Design system (Dark mode, glassmorphism, glowing accents)
├── js/
│   ├── app.js              # Application controller, routing, particle hero animation
│   ├── python-basics.js    # Week 3-4: Python code runner, NumPy & Pandas simulations
│   ├── linear-algebra.js   # Week 5-6: Canvas vector, matrix, and eigenvalue tools
│   ├── calculus.js          # Week 5-6: Tangent lines, gradient descent, computational graph
│   ├── regression.js        # Week 7-8: Linear, Polynomial, Ridge/Lasso fitting engines
│   ├── classification.js   # Week 7-8: Logistic regression, KNN, confusion matrix
│   ├── pipelines.js        # Week 9-10: Scikit-learn Pipeline builder & CV leakage visualizer
│   ├── clustering.js       # Week 9-10: K-Means (Elbow), Hierarchical (Dendrogram), DBSCAN
│   └── project-week9-10.js # Week 9-10 Capstone: Customer Segmentation & Pipeline Studio
└── README.md               # Documentation & setup guide
```

---

## 🚀 Running Locally

No build step or node package installations required. Pure standard web technologies.

### Option 1: Python Built-in Server (Recommended)
```bash
cd d:\hackoweek
python -m http.server 8080
```
Then open [http://localhost:8080](http://localhost:8080) in your browser.

### Option 2: Node.js / npx
```bash
npx serve d:\hackoweek
```

### Option 3: Direct File
Open `index.html` directly in any modern browser.
