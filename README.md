**Disease Diagnosis Support System**

This project is a machine learning tool designed to support clinicians by predicting the likelihood of specific diseases based on patient medical data. It currently supports predictions for Diabetes and Parkinson's disease.

The core of this project is a FastAPI microservice that provides fast, reliable, and—most importantly—explainable predictions, making it suitable for integration into clinical dashboards and other healthcare applications.

**Key Features**
1. **Dual-Disease Prediction**: Models trained to predict both Diabetes and Parkinson's disease.

2. **High-Performance Models**: Utilizes XGBoost and Scikit-learn for accurate and efficient predictions.

3. **Explainable AI (XAI)**: Integrated with SHAP (SHapley Additive exPlanations) to provide human-understandable reasons for each prediction, building trust and transparency.

4. **Microservice Architecture**: Deployed as a lightweight and scalable FastAPI service, allowing for easy integration via API calls.

5. **Ready for Deployment**: The application is container-ready and can be easily deployed in cloud environments.

**Tech Stack**

Backend: FastAPI

Machine Learning: PyTorch, Scikit-learn, XGBoost

Explainability: SHAP

Data Handling: Pandas, NumPy

**Installation and Setup**
To run this project locally, follow these steps:

**Clone the repository**:

git clone https://github.com/Sahasranshu-Shastri/insight-care.git
cd disease-diagnosis-support

**Create and activate a virtual environment**:

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

Install the required dependencies:

pip install -r requirements.txt

Run the FastAPI server:

uvicorn main:app --reload

The application will be available at http://127.0.0.1:8000.

API Endpoints
The service exposes the following endpoints for making predictions.

1. Predict Diabetes
Endpoint: /predict/diabetes

Method: POST

Body: A JSON object containing the patient's medical data.

{
  "Pregnancies": 6,
  "Glucose": 148,
  "BloodPressure": 72,
  "SkinThickness": 35,
  "Insulin": 0,
  "BMI": 33.6,
  "DiabetesPedigreeFunction": 0.627,
  "Age": 50
}

Response:

{
  "prediction": "Positive",
  "probability": 0.88,
  "explanation": {
    "feature_1": "contribution_value_1",
    "feature_2": "contribution_value_2"
  }
}

2. Predict Parkinson's
Endpoint: /predict/parkinsons

Method: POST

Body: A JSON object containing the patient's voice measurement data.

{
  "MDVP:Fo(Hz)": 119.992,
  "MDVP:Fhi(Hz)": 157.302,
  "MDVP:Flo(Hz)": 74.997,
  "...": "..."
}

Response:

{
  "prediction": "Positive",
  "probability": 0.92,
  "explanation": {
    "feature_x": "contribution_value_x",
    "feature_y": "contribution_value_y"
  }
}
