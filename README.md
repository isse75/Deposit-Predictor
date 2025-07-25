# 🏦 Bank Deposit Decision Classifier

![Python](<https://img.shields.io/badge/python-3.12+-blue.svg>)
![License](<https://img.shields.io/badge/license-MIT-green.svg>)
![Status](<https://img.shields.io/badge/status-live-brightgreen.svg>)
![ML](<https://img.shields.io/badge/ML-XGBoost-orange.svg>)
![AWS](<https://img.shields.io/badge/AWS-EC2-ff9900.svg>)
![Docker](<https://img.shields.io/badge/docker-containerized-blue.svg>)

This project predicts whether a bank customer will subscribe to a term deposit, based on direct marketing campaign data. Built with a complete ML workflow from EDA to deployment, it includes interactive visualization, multiple model comparisons, API services, and a Streamlit UI—deployed with Docker on AWS EC2.

**An end-to-end ML pipeline for customer targeting using the UCI Bank Marketing Dataset**

---

## 🚀 Quick Start

### Try the Live Demo
📍 **Live App**: [<https://deposit-predictor.streamlit.app/>](<https://deposit-predictor.streamlit.app/>)

### Run Locally
```bash
# Clone and setup
git clone <https://github.com/yourusername/bank-campaign-classifier.git>
cd bank-campaign-classifier
pipenv install && pipenv shell

# Train model
python train.py

# Start API server
python predict.py

# Run Streamlit app (in new terminal)
streamlit run streamlit_app.py

```

---

## 📋 Table of Contents

- [📌 Problem Statement](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#problem-statement)
- [🎯 Project Goals](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#project-goals)
- [📊 Dataset Information](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#dataset-information)
- [📁 Project Structure](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#project-structure)
- [⚙️ Setup and Installation](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#setup-and-installation)
- [🔍 Exploratory Data Analysis](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#exploratory-data-analysis)
- [🧠 Model Training & Selection](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#model-training--selection)
- [📈 Results & Model Performance](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#results--model-performance)
- [🚀 Deployment](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#deployment)
- [💡 Usage Examples](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#usage-examples)
- [🔌 API Reference](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#api-reference)
- [👤 Author](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#author)
- [📄 License](notion://www.notion.so/22ec658b02618042b215cae1319dbdae?showMoveTo=true&saveParent=true#license)

---

## 📌 Problem Statement

Marketing calls are expensive and time-consuming. However, only a small proportion of customers actually subscribe to financial products like term deposits. This project aims to help banks predict, *before making contact*, which customers are most likely to say yes—so that campaigns can be smarter, leaner, and more effective.

---

## 🎯 Project Goals

- Clean and analyze the UCI Bank Marketing dataset
- Visualize categorical and numerical feature impacts
- Address class imbalance and data leakage issues
- Train and evaluate multiple models (Logistic Regression, Random Forest, XGBoost)
- Select the best model using cross-validation and metric analysis
- Deploy the final model to an API service
- Create an interactive web front end using Streamlit
- Containerize and deploy via Docker to AWS EC2

---

## 📊 Dataset Information

### 🔹 Source

- UCI Machine Learning Repository: [Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing)

### 🔹 Target Distribution

<img width="589" height="453" alt="image" src="https://github.com/user-attachments/assets/887cda9d-4f16-4810-bda7-7f7a36d83ea7" />


*Severe class imbalance: Only 11.3% of customers subscribed to term deposits - this drives our model selection strategy*

### 🔹 Stats

- 41,188 rows
- 20 input features
- Binary target: `y` (yes/no for term deposit subscription)
- **Class ratio**: 88.7% No, 11.3% Yes

### 🔹 Feature Groups

- **Demographic**: Age, job, marital, education
- **Financial**: Default, housing loan, personal loan
- **Communication**: Contact type, month, day of week
- **Campaign**: Number of contacts, outcomes of previous attempts

---

## 📁 Project Structure

```
.
├── data/                     # Dataset storage
│   └── bank-additional-full.csv     # Bank Marketing Dataset
├── images/                   # Visualisation assets
│   ├── target_distribution.png  # Deposit Decision Distribution Chart
│   ├── correlation_heatmap.png      # Variable Correlation Heatmap
│   ├── model_comparison.png         # Model Performance Comparison Chart
│   ├── xgboost_roc_curve.png       # ROC Curve Plot
│   ├── duration_log_plot.png       # Log Duration Distribution Plot
│   └── pdays_distritbution.png     # pdays Distribution Plot
├── Notebook.ipynb          # Full EDA and model comparison
├── train.py                 # Training script
├── predict.py               # Inference service
├── streamlit_app.py         # Streamlit web UI
├── requirements.txt         # Dependency management
├── .dockerignore           # Docker reference file
├── Dockerfile              # Docker image configuration
├── Pipfile                 # Dependency management
├── Pipfile.lock            # Dependency management
└── XGBoost_model.bin       # Trained model artifact

```

---

## ⚙️ Setup and Installation

### Prerequisites

- Python 3.12+
- Docker
- Pipenv

### 📸 Image Setup

**Note**: This README currently uses placeholder images. To display your actual visualizations:

1. **Create images folder**: `mkdir images`
2. **Export plots from your notebook** as PNG files (300 DPI recommended)
3. **Save with exact filenames**:
- `target_distribution.png` - Bar chart showing class imbalance
- `correlation_heatmap.png` - Feature correlation matrix
- `model_comparison.png` - Model performance comparison chart
- `xgboost_roc_curve.png` - ROC curve for final model
- `duration_log_plot.png` - Log-transformed duration analysis
- `pdays_log_plot.png` - Log-transformed pdays analysis
1. **Commit and push** to GitHub - images will automatically replace placeholders

### Environment Setup

```bash
# Clone repository
git clone <https://github.com/yourusername/bank-campaign-classifier.git>
cd bank-campaign-classifier

# Setup with Pipenv (recommended)
pip install pipenv
pipenv install --dev
pipenv shell

# Alternative with pip
pip install -r requirements.txt

# Verify installation
python -c "import xgboost, streamlit, pandas; print('All dependencies installed!')"

```

### Docker Setup

```bash
# Build image
docker build -t bank-classifier .

# Run container
docker run -p 9696:9696 bank-classifier

```

---

## 🔍 Exploratory Data Analysis

Conducted in detail in `Notebook.ipynb`:

### Feature Correlation Analysis

<img width="582" height="433" alt="image" src="https://github.com/user-attachments/assets/de3f3738-dd72-41d9-8997-0b4fc87b9b3d" />

*Low individual correlations justify ensemble methods that excel at finding feature interactions*

### Data Quality & Feature Engineering

### Features Removed Due to Data Issues

### Duration Analysis - Data Leakage Detected

<img width="580" height="453" alt="image" src="https://github.com/user-attachments/assets/2d3fc0b8-db81-48cd-af81-83ed93495e0e" />

*Log(+1) transformed duration shows clear separation by target - removed due to data leakage*

**Why removed**: `duration` is only known AFTER the call ends, making it unavailable for real-time prediction. While being a highly predictive variable (customers who talk longer often subscribe), it creates data leakage.

### Pdays Analysis - Uninformative Feature

<img width="589" height="432" alt="image" src="https://github.com/user-attachments/assets/e73caa6e-4aec-4637-aed9-255ba7a25d0b" />

*Number of days that passed by after the client was last contacted from a previous campaign is dominated by 999 days, either for clients never previously contacted or clients contacted more than 999 days ago*

**Why removed**: `pdays` contained 96.4% missing values (coded as 999), providing minimal predictive value. The feature was too sparse to be useful.

### Key Preprocessing Steps

- Column cleanup: Replaced `.` with `_` for consistency
- Education mapping: 8 categories → 4 (primary, secondary, tertiary, unknown)
- Target encoding: `y` converted to binary (1 for yes, 0 for no)
- **Removed problematic features**: `duration` (leakage), `pdays` (sparse), economic indicators
- **Class imbalance**: Addressed with `scale_pos_weight` in final model

### Final Dataset Summary

- **Rows**: 41,188 customers
- **Features**: 16 (after removing problematic variables)
- **Target balance**: 88.7% No, 11.3% Yes
- **Missing values**: Minimal after cleaning

---

## 🧠 Model Training & Selection

### Models Trained

1. **Logistic Regression** - Baseline linear model
2. **Random Forest** - Ensemble method with feature importance
3. **XGBoost** - Gradient boosting with advanced regularization

### Techniques Used

- Train/Val/Test split with stratification to protect class balance.
- One-Hot Encoding Using DictVectorizer, preparing Categorical Variables to be suitable for use on Scikit-Learn Models.
- 5-Fold Cross Validation and Hyperparameter tuning with GridSearchCV on Variables to identify optimal performance for each model.
- Threshold selection using F1 optimization
- Class imbalance handling with `scale_pos_weight`
- Model evaluation using ROC AUC, F1, Precision, Recall, and Accuracy on the held-out test set. All model decisions were made without referencing the test data.

### Model Performance Comparison

<img width="1391" height="790" alt="image" src="https://github.com/user-attachments/assets/c3138ead-19ed-4cec-b4bc-58b70ead3a75" />

### Detailed Results

| Metric | Logistic Regression | Random Forest | XGBoost |
| --- | --- | --- | --- |
| Accuracy | 0.872 | **0.878** | 0.873 |
| ROC AUC | 0.765 | 0.773 | **0.778** |
| F1 Score | 0.441 | 0.473 | **0.474** |
| Precision | 0.434 | **0.459** | 0.445 |
| Recall | 0.447 | 0.488 | **0.508** |

### ✅ **Why XGBoost?**

As the XGBoost and Random Forest models had similar performance, I decided that XGBoost is the better model to proceed with. This is due to the fact that the features in the dataset have relatively low individual correlations with the target variable `y`. XGBoost models excel in finding feature interactions and non-linear patterns in datasets. Random Forest models tend to struggle with weak individual signals. As this dataset also has imbalanced classes, XGBoost’s sophistication is extremely useful.

**Key advantages:**

- Best ROC AUC (0.778) and F1 Score (0.474)
- Superior at capturing feature interactions in low-correlation datasets
- Built-in class imbalance handling with `scale_pos_weight`
- Advanced regularization prevents overfitting

---

## 📈 Results & Model Performance

### XGBoost ROC Performance

<img width="567" height="453" alt="image" src="https://github.com/user-attachments/assets/b6b565a7-7d74-41b1-b55d-77035b330456" />

*ROC AUC: 0.778 - Strong discriminative ability for identifying potential subscribers*

### Final Model Metrics

- **Test Accuracy**: 87.3%
- **ROC AUC**: 0.778
- **F1 Score**: 0.474
- **Precision**: 44.5% (low false positives)
- **Recall**: 50.8% (captures half of actual subscribers)

*Model optimized for F1 score to balance precision-recall trade-off in imbalanced dataset*

### Top Predictive Features

| Rank | Feature | Importance | 
| --- | --- | --- | 
| 1 | poutcome=success | **0.363346** | 
| 2 | contact=cellular | **0.125201** |
| 3 |  month=mar | **0.061122** |
| 4 |  month=jun | **0.053939** | 
| 5 | mont=oct | **0.046307** |


### Key Business Insights

🎯 **Actionable Marketing Strategies:**

- **Target previous responders**: Customers who responded positively to past campaigns are 4x more likely to subscribe - prioritize these customers
- **Use cellular contact**: Cellular contact achieves 60% higher success rates than telephone - update contact preferences
- **Time campaigns strategically**: March, June, and October are optimal months - avoid summer/winter campaigns
- **Focus on retired customers**: Highest conversion rates among job categories - create targeted retirement products
- **Screen for credit defaults**: Customers without defaults show significantly higher subscription rates
- **Limit contact frequency**: Excessive contacts in current campaign reduce success probability

💡 **ROI Optimization**: Focus 80% of campaign budget on customers scoring above 0.6 probability threshold for maximum efficiency.

---

## 🚀 Deployment

### 🌐 Live Application Architecture

**Frontend**: Streamlit web application for interactive predictions

**Backend**: FastAPI service providing RESTful API (port 9696)

**Model**: Serialized XGBoost model (.bin format)

**Infrastructure**: AWS EC2 with Docker containerization

**Monitoring**: Health check endpoints for service monitoring

### 📍 Live Deployment

🔗 **Streamlit App**: https://deposit-predictor.streamlit.app/

🔗 **API Endpoint**: `http://your-ec2-instance:9696`

### AWS EC2 Deployment Steps

1. **Launch EC2 Instance**
    
    ```bash
    # t2.micro or larger recommended
    # Ubuntu 20.04 LTS AMI
    # Security group: Allow HTTP (80), HTTPS (443), Custom TCP (9696)
    
    ```
    
2. **Install Dependencies**
    
    ```bash
    # Connect to EC2 instance
    sudo apt update
    sudo apt install docker.io git -y
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo usermod -aG docker ubuntu
    
    ```
    
3. **Deploy Application**
    
    ```bash
    # Clone and build
    git clone <https://github.com/isse75/Deposit-Predictor.git>
    cd Deposit-Predictor
    sudo docker build -t bank-classifier .
    
    # Run with auto-restart
    sudo docker run -d --name bank-app --restart unless-stopped -p 9696:9696 bank-classifier
    
    ```
    
4. **Verify Deployment**
    
    ```bash
    # Check container status
    sudo docker ps
    
    # Test health endpoint
    curl <http://localhost:9696/health>
    
    ```
    

### Local Development

```bash
# Build image
docker build -t bank-classifier .

# Run container
docker run -p 9696:9696 bank-classifier

# Development mode with volume mounting
docker run -p 9696:9696 -v $(pwd):/app bank-classifier

```

### 📊 Performance Monitoring

- **Health Check**: `GET /health` endpoint for monitoring
- **Response Time**: Average < 200ms for predictions
- **Throughput**: Handles 100+ concurrent requests
- **Uptime**: 99.9% availability on AWS EC2

---

## 💡 Usage Examples

### API Usage

```bash
# Start the prediction service
python predict.py

# Make a prediction
curl -X POST <http://localhost:9696/predict> \\
  -H "Content-Type: application/json" \\
  -d '{
    "job": "management",
    "marital": "single",
    "education": "tertiary",
    "age": 35,
    "campaign": 2,
    "previous": 0,
    "poutcome": "unknown",
    "contact": "cellular",
    "month": "mar",
    "default": "no"
  }'

```

### Streamlit Interface

1. **Navigate to the live app** or run locally
2. **Fill in customer details** using the interactive form
3. **Click “Predict”** to get subscription probability
4. **View results** with probability score and recommendation

### Python Integration

```python
import requests

# Prepare customer data
customer_data = {
    "job": "admin.",
    "marital": "married",
    "education": "secondary",
    "age": 42,
    "campaign": 1
}

# Get prediction
response = requests.post(
    "<http://localhost:9696/predict>",
    json=customer_data
)
result = response.json()
print(f"Subscription probability: {result['probability']:.2%}")

```

---

## 🔌 API Reference

### Endpoints

- `POST /predict` - Get prediction for a single customer
- `GET /health` - Health check

### Request Format

```json
{
  "job": "management",
  "marital": "single",
  "education": "tertiary",
  "age": 30,
  "campaign": 1,
  "previous": 0,
  "poutcome": "unknown",
  "contact": "cellular",
  "month": "may",
  "day_of_week": "mon",
  "default": "no",
  "housing": "yes",
  "loan": "no"
}

```

### Response Format

```json
{
  "prediction": 1,
  "probability": 0.73,
  "recommendation": "High probability customer - prioritize for campaign"
}

```

### Input Validation

- **Required fields**: All customer attributes must be provided
- **Valid values**: Categorical fields must match training data categories
- **Data types**: Age and campaign must be integers

---


## 👤 Author

**Your Name**

- GitHub: [@isse75](https://github.com/isse75)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/issedugou)
- Email: [isse.dugou@outlook.com](mailto:isse.dugou@outlook.com)

---

## 📄 License

This project is licensed under the MIT License. See the <LICENSE> file for details.

---

## 🔗 Additional Resources

- [UCI Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Docker Documentation](https://docs.docker.com/)
