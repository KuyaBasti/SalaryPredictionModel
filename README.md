# Salary Prediction Machine Learning Model

<p align="center"><img src="docs/system-overview.svg" alt="Salary Prediction Model system overview. Offline, the Project.ipynb notebook (Jupyter, scikit-learn) reads Salary.csv (6,684 rows, 9 columns), groups 129 job titles into 8 categories, one-hot encodes, then scales and reduces 29 features to 18 PCA components, and trains and compares linear, polynomial (degrees 1–3), 64×64 MLP and random forest regressors. It pickles encoder.pkl (one-hot of 4 columns), pca.pkl (18 components), model.pkl (8-tree random forest, best test R² 0.85) and scaler_y.pkl (salary StandardScaler). The Flask app.py on port 5000 loads the four pickles at startup. GET / serves index.html, an 8-field form styled by style.css. The browser POSTs the 8 fields to /predict, which applies one-hot, PCA, the random forest and inverse salary scaling, then returns results.html with the predicted salary." width="100%"></p>

A comprehensive machine learning project that predicts salaries based on demographic and professional factors. This project implements multiple ML algorithms and provides a user-friendly web interface for salary predictions.

## 🎯 Overview

This project analyzes salary data across different demographics and job categories to build predictive models. The system uses various machine learning algorithms to predict salaries based on factors such as age, gender, education level, job title, years of experience, country, race, and seniority level.

## 📊 Dataset

The project includes two datasets; the notebook trains on Salary.csv only:
- **Salary.csv**: Primary dataset with 6,684 salary records
- **Salary_Data_Based_country_and_race.csv**: Raw variant with 6,704 records, text education levels and no Senior column; kept for reference and not loaded by the code

### Dataset Features:
- **Age**: Employee age (21-62 years)
- **Gender**: Male/Female
- **Education Level**: 0-3 scale (Higher education levels)
- **Job Title**: 129 raw titles, which the notebook groups into 8 categories (Technology, Business, Human Resources, Information Technology, Social Media, Design, Research and Science, Miscellaneous)
- **Years of Experience**: 0-34 years
- **Salary**: Target variable ($350 - $250,000)
- **Country**: USA, China, Australia, UK, Canada
- **Race**: White, Hispanic, Asian, Korean, Chinese, Australian, Welsh, African American, Mixed, Black
- **Senior**: Binary indicator for senior positions (0/1)

### Dataset Statistics:
- **Total Records**: 6,684
- **Average Salary**: $115,307
- **Age Range**: 21-62 years
- **Experience Range**: 0-34 years
- **Senior Positions**: 14.3% of dataset

## ✨ Features

- **Multiple ML Models**: Implementation of Linear Regression, Polynomial Regression, Neural Networks, and Random Forest
- **Data Preprocessing**: Comprehensive preprocessing pipeline including encoding, scaling, and dimensionality reduction
- **Web Interface**: Interactive Flask web application for form-based salary predictions
- **Model Persistence**: The best model (Random Forest) is saved as a pickle file, together with the one-hot encoder, the 18-component PCA and the salary scaler that the Flask app loads
- **Visualization**: Feature histograms, a salary boxplot, PCA variance-ratio charts and a correlation heatmap; model scores (MSE, R²) are printed
- **Academic Documentation**: Complete research paper included

## 🤖 Models Implemented

### 1. Linear Regression
- Basic linear model for baseline predictions
- Includes feature scaling using StandardScaler

### 2. Polynomial Regression
- Tests multiple polynomial degrees for non-linear relationships
- Feature scaling applied to polynomial features

### 3. Multi-Layer Perceptron (MLP) Neural Network
- Architecture: Two hidden layers with 64 neurons each
- Max iterations: 1000
- Includes both input and output scaling

### 4. Random Forest Regressor
- Number of estimators: 8
- Max features: ⌈√(number of features)⌉ = 5 for the 18 PCA components
- Random state: 42 for reproducibility

## 🛠 Technology Stack

- **Python 3.x**
- **Machine Learning**: scikit-learn, numpy, pandas
- **Data Visualization**: matplotlib, seaborn
- **Web Framework**: Flask
- **Frontend**: HTML5, CSS3
- **Data Processing**: Pickle for model serialization
- **Development Environment**: Jupyter Notebook

## 📁 Project Structure

```
SalaryPredictionModel/
├── Project.ipynb              # Main Jupyter notebook with ML pipeline
├── app.py                     # Flask web application
├── Salary.csv                 # Primary dataset
├── Salary_Data_Based_country_and_race.csv  # Raw variant (not loaded by the code)
├── SalaryPredictionMLPaper.pdf # Academic research paper
├── model.pkl                  # Trained ML model
├── encoder.pkl                # One-hot encoder for categorical features
├── pca.pkl                    # PCA transformer
├── scaler_y.pkl              # Target variable scaler
├── templates/
│   ├── index.html            # Main web interface
│   └── results.html          # Prediction results page
├── static/
│   └── css/
│       └── style.css         # Web application styling
├── docs/
│   └── system-overview.svg   # System overview diagram
└── README.md                 # Project documentation
```

## 🚀 Installation

### Prerequisites
- Python 3.x
- Anaconda (recommended)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd SalaryPredictionModel
   ```

2. **Install dependencies**
   
   If using Anaconda (recommended):
   ```bash
   conda activate base
   ```
   
   All required libraries are available in the base Anaconda environment:
   - numpy
   - pandas
   - scikit-learn
   - matplotlib
   - seaborn
   - flask

3. **Alternative installation with pip**
   ```bash
   pip install numpy pandas scikit-learn matplotlib seaborn flask
   ```

## 💻 Usage

### Running the Jupyter Notebook

1. **Start Jupyter Notebook**
   ```bash
   jupyter notebook Project.ipynb
   ```

2. **Execute cells sequentially** to:
   - Load and explore the dataset
   - Perform data preprocessing
   - Train multiple ML models
   - Evaluate model performance
   - Save the trained model and preprocessing objects

### Running the Web Application

1. **Start the Flask app**
   ```bash
   python app.py
   ```

2. **Access the web interface**
   - Open your browser and navigate to `http://localhost:5000`
   - Fill in the prediction form with employee details
   - Click "Predict Salary" to get results

### Making Predictions

The web interface accepts the following inputs:
- **Job Category**: Technology, Business, HR, IT, Social Media, Design, Research and Science, Miscellaneous
- **Years of Experience**: Numeric input
- **Age**: Numeric input
- **Country**: USA, China, Australia, UK, Canada
- **Race**: White, Hispanic, Asian, Korean, Chinese, Australian, Welsh, African American, Mixed, Black
- **Gender**: Male/Female
- **Education Level**: 0-3 scale
- **Senior Position**: Yes/No

## 📈 Model Performance

The project evaluates models using:
- **Mean Squared Error (MSE)**
- **R² Score (Coefficient of Determination)**

Performance metrics are calculated for each model to determine the best predictor for salary estimation.

## 🌐 Web Application

### Features:
- **Responsive Design**: Mobile-friendly interface
- **Form Validation**: Ensures all required fields are completed
- **Predictions**: Submitting the form POSTs to `/predict` and renders `results.html` with the predicted salary
- **Styling**: The input form uses `static/css/style.css`

### API Endpoints:
- `GET /`: Main prediction form
- `POST /predict`: Process prediction request and return results

## 🔧 Data Preprocessing

The preprocessing pipeline includes:

1. **Job Title Grouping**: 129 raw job titles mapped to 8 categories
2. **One-Hot Encoding**: Categorical variables (Gender, Job Title, Country, Race)
3. **Outlier Clipping**: IQR-based clipping of Age and Years of Experience outliers
4. **Feature Scaling**: StandardScaler on all 29 encoded features, including the one-hot columns
5. **Principal Component Analysis (PCA)**: Dimensionality reduction from 29 to 18 components
6. **Target Scaling**: Salary normalization for improved model performance

Note: `app.py` applies only the saved encoder, the 18-component PCA, the model and the inverse salary scaling. The feature scalers and the first PCA pass are not saved, so web inputs are not transformed exactly as in training.

### Preprocessing Steps:
```python
# One-hot encoding for categorical features
encoder = OneHotEncoder(sparse_output=False)
encoded_features = encoder.fit_transform(categorical_data)

# PCA for dimensionality reduction (on the standardized features)
X = PCA().fit_transform(X)    # first pass keeps all 29 components
pca = PCA(n_components=18)    # second pass keeps about 91% of the variance; saved as pca.pkl
X_transformed = pca.fit_transform(X)

# Target variable scaling
scaler_y = StandardScaler()
y_train = scaler_y.fit_transform(y_train.to_numpy().reshape(-1, 1)).ravel()  # fit on the 75% training split only; saved as scaler_y.pkl
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📚 Academic Paper

This project includes a comprehensive research paper (`SalaryPredictionMLPaper.pdf`) that covers:
- Literature review
- Methodology
- Experimental design
- Results and analysis
- Conclusion and discussion

## 🎓 Course Information

This project was developed for **ECS 171** (Machine Learning) course, demonstrating practical application of machine learning concepts in salary prediction.

## 📄 License

This project is available for educational and research purposes.

## 🔮 Future Enhancements

- [ ] Implement cross-validation

---

**Note**: This model is for educational and research purposes. Actual salary predictions may vary based on numerous factors not captured in the dataset.
