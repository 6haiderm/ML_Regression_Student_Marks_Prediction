                             # **Student Performance Indicator - End-to-End Machine Learning Project**

This project demonstrates a comprehensive, **end-to-end machine learning implementation**, focusing on a **generic project structure** that can be adapted for various data science tasks. The primary goal is to predict student test scores based on several demographic and educational factors.

---

## **Project Overview**
The **problem statement** explores how student performance (specifically test scores) is influenced by variables such as gender, ethnicity, parental level of education, lunch types, and test preparation courses. The project follows a modular programming approach, ensuring industry-standard clean code.

### **Key Features**
*   **Modular Coding**: Segmented into components such as data ingestion, transformation, and model training.
*   **Custom Logging & Exception Handling**: Robust tracking of execution and error details, including file names and line numbers.
*   **Automated Pipelines**: Includes both training and prediction pipelines for seamless deployment.
*   **Hyperparameter Tuning**: Implementation of automated model selection using `GridSearchCV`.

---

## **Project Structure**
The project is organised into a clear directory structure to facilitate collaboration and scalability:

*   **`src/components/`**: Handles the core ML lifecycle modules.
    *   `data_ingestion.py`: Reads data from sources and performs train-test splits.
    *   `data_transformation.py`: Performs feature engineering, handles missing values, and applies categorical encoding.
    *   `model_trainer.py`: Trains multiple models and selects the best performer based on R2 score.
*   **`src/pipeline/`**: Contains `train_pipeline.py` and `predict_pipeline.py`.
*   **`src/logger.py` & `src/exception.py`**: Custom scripts for tracking execution and handling errors.
*   **`src/utils.py`**: Houses common functionalities like saving/loading pickle files and model evaluation.
*   **`notebook/`**: Contains Jupyter notebooks used for initial **Exploratory Data Analysis (EDA)** and model prototyping.

---

## **Installation and Setup**

1.  **Environment Creation**:
    It is recommended to create a dedicated environment using Python 3.8.
    ```bash
    conda create -p venv python=3.8 -y
    conda activate venv/
    ```

2.  **Install Dependencies**:
    The project uses `setup.py` to build the application as a package, triggered by the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```

---

## **Workflow**

### **1. Data Ingestion**
The ingestion component reads the raw dataset (e.g., from a CSV or database) and creates an **artifact folder** to store the train, test, and raw data files.

### **2. Data Transformation**
Using `ColumnTransformer` and `Pipeline`, the project applies different strategies for numerical and categorical data:
*   **Numerical Features**: Handled via `SimpleImputer` (median strategy) and `StandardScaler`.
*   **Categorical Features**: Handled via `OneHotEncoder` and `StandardScaler`.
*   The final preprocessor object is saved as a **pickle file** for future use.

### **3. Model Training & Tuning**
The project evaluates several algorithms, including **Linear Regression, Random Forest, Gradient Boosting, and XGBoost**. Hyperparameter tuning is integrated via `GridSearchCV` to ensure optimal performance.

---

## **Deployment**
The application is designed for deployment on **AWS Elastic Beanstalk** using a **Continuous Delivery (CD)** pipeline via **AWS CodePipeline**. 

*   **Entry Point**: The application uses `application.py` as the entry point for AWS deployment.
*   **Configuration**: Includes `.ebextensions/python.config` to define the WSGI path for the environment.
*   **Automation**: Any code push to the GitHub repository automatically triggers a redeployment if the pipeline is active.

---

## **Source Information**
This project was developed following the tutorials by **Krish Naik**, focusing on industry-level end-to-end ML implementation.
