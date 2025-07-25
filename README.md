# Salary Prediction Machine Learning Model

A comprehensive machine learning project that predicts salaries based on demographic and professional factors. This project implements multiple ML algorithms and provides a user-friendly web interface for salary predictions.

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Features](#features)
- [Models Implemented](#models-implemented)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Model Performance](#model-performance)
- [Web Application](#web-application)
- [Data Preprocessing](#data-preprocessing)
- [Contributing](#contributing)
- [Academic Paper](#academic-paper)

## 🎯 Overview

This project analyzes salary data across different demographics and job categories to build predictive models. The system uses various machine learning algorithms to predict salaries based on factors such as age, gender, education level, job title, years of experience, country, race, and seniority level.

## 📊 Dataset

The project uses two main datasets:
- **Salary.csv**: Primary dataset with 6,684 salary records
- **Salary_Data_Based_country_and_race.csv**: Extended dataset with additional demographic information

### Dataset Features:
- **Age**: Employee age (21-62 years)
- **Gender**: Male/Female
- **Education Level**: 0-3 scale (Higher education levels)
- **Job Title**: Various job categories including Technology, Business, HR, IT, etc.
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
- **Web Interface**: Interactive Flask web application for real-time predictions
- **Model Persistence**: Trained models saved as pickle files for quick deployment
- **Visualization**: Data analysis and model performance visualizations
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
- Max features: √(number of features)
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
├── Salary_Data_Based_country_and_race.csv  # Extended dataset
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
   - Save trained models

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
- **Real-time Predictions**: Instant salary predictions
- **Clean UI**: Professional styling with CSS

### API Endpoints:
- `GET /`: Main prediction form
- `POST /predict`: Process prediction request and return results

## 🔧 Data Preprocessing

The preprocessing pipeline includes:

1. **One-Hot Encoding**: Categorical variables (Gender, Job Title, Country, Race)
2. **Feature Scaling**: StandardScaler for numerical features
3. **Principal Component Analysis (PCA)**: Dimensionality reduction
4. **Target Scaling**: Salary normalization for improved model performance

### Preprocessing Steps:
```python
# One-hot encoding for categorical features
encoder = OneHotEncoder(sparse_output=False)
encoded_features = encoder.fit_transform(categorical_data)

# PCA for dimensionality reduction
pca = PCA()
X_transformed = pca.fit_transform(X)

# Target variable scaling
scaler_y = StandardScaler()
y_scaled = scaler_y.fit_transform(y)
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
- Conclusions and future work

## 🎓 Course Information

This project was developed for **ECS 171** (Machine Learning) course, demonstrating practical application of machine learning concepts in salary prediction.

## 📄 License

This project is available for educational and research purposes.

## 🔮 Future Enhancements

- [ ] Add more advanced models (XGBoost, LightGBM)
- [ ] Implement cross-validation
- [ ] Add feature importance analysis
- [ ] Extend to more countries and job categories
- [ ] Add API endpoints for programmatic access
- [ ] Implement model retraining capabilities
- [ ] Add data visualization dashboard

---

**Note**: This model is for educational and research purposes. Actual salary predictions may vary based on numerous factors not captured in the dataset.
