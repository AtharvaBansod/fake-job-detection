
# Fake Job Posting Detection using Machine Learning

[Live Demo 🚀](https://www.worksure.streamlit.app/)

## Overview

This project addresses the critical problem of identifying fraudulent job postings online. It utilizes a machine learning pipeline to classify job listings as either legitimate or fraudulent based on their textual and categorical features.

The core of this project is a user-friendly web application built with **Streamlit**, which allows anyone to input the details of a job posting and receive an instant analysis from three different trained models: **Logistic Regression**, **Random Forest**, and **Naive Bayes**. The application provides a clear, aggregated "consensus verdict" as well as a detailed breakdown of each model's prediction and confidence score.



## 🚀 Key Features

-   **Multi-Model Analysis:** Leverages three distinct ML models to provide a more robust and reliable prediction.
-   **Interactive Web UI:** A clean and intuitive interface built with Streamlit for easy use by anyone.
-   **Detailed Predictions:** Displays not only the final classification (Real vs. Fake) but also the confidence probability for each model.
-   **Consensus Verdict:** Provides a high-level summary based on a majority vote from the models.
-   **Modular Codebase:** The project is structured into separate components for backend logic, UI elements, and the main application, making it easy to maintain and extend.
-   **Feature-Rich Preprocessing:** Handles text data using TF-IDF and encodes categorical data to build a comprehensive feature set for the models.


## 🛠️ Technology Stack

-   **Backend & ML:** Python 3.10+
-   **Machine Learning:** Scikit-learn, Pandas, Joblib
-   **Web Framework:** Streamlit
-   **Data Handling:** NumPy, Pandas



## 📂 Project Structure

The project follows a modular structure for better organization and scalability.

```
fake-job-detection/
├── models/
│   ├── logistic_model.pkl
│   ├── naive_bayes_model.pkl
│   ├── random_forest_model.pkl
│   └── preprocessor.pkl
├── ui/
│   ├── __init__.py
│   ├── input_form.py
│   └── results_display.py
├── utils.py
├── app.py
├── requirements.txt
└── README.md
```


## ⚙️ Local Setup and Installation

Follow these steps to run the application on your local machine.

### 1. Prerequisites

-   Python 3.10 or higher
-   `pip` and `venv`

### 2. Clone the Repository

```bash
git clone https://github.com/your-username/fake-job-detector.git
cd fake-job-detector
```

### 3. Set Up a Virtual Environment

It is highly recommended to use a virtual environment to manage dependencies.

-   **On macOS/Linux:**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```
-   **On Windows:**
    ```bash
    python -m venv venv
    .\venv\Scripts\activate
    ```

### 4. Install Dependencies

Install all the required Python packages using the `requirements.txt` file.

```bash
pip install -r requirements.txt
```

### 5. Ensure Models are Present

Make sure the pre-trained model files (`.pkl`) and the preprocessor are located in the `/models` directory as shown in the project structure.



## How to Run the App

Once the setup is complete, you can start the Streamlit application with a single command:

```bash
streamlit run app.py
```

Your default web browser will automatically open a new tab with the running application.


## 🤖 The Machine Learning Pipeline

### 1. Data Source

The models were trained on the "Fake Job Postings" dataset, which contains 17,000+ real and fraudulent job listings.

### 2. Preprocessing & Feature Engineering

The raw data undergoes a rigorous preprocessing pipeline before being fed into the models:
-   **Missing Value Imputation:** Missing text fields are filled with empty strings, and categorical fields are filled with an 'Unknown' tag.
-   **Feature Creation:** A new numerical feature, `description_word_count`, is engineered to capture the length of the job description.
-   **Text Vectorization:** Textual columns (`title`, `description`, `requirements`, etc.) are converted into numerical vectors using `TfidfVectorizer` to capture word importance.
-   **Categorical Encoding:** Categorical columns (`employment_type`, `required_experience`, etc.) are converted to a numerical format using `OneHotEncoder`.

This entire pipeline is encapsulated in a `ColumnTransformer` and saved as `preprocessor.pkl`.

### 3. Model Training

Three different classification models were trained and evaluated:
-   **Logistic Regression:** A robust linear model with L2 regularization.
-   **Random Forest Classifier:** A powerful ensemble model capable of capturing non-linear relationships.
-   **Multinomial Naive Bayes:** A probabilistic model that performs exceptionally well on text classification tasks.

Hyperparameter tuning was performed using `GridSearchCV` with F1-score as the primary evaluation metric to handle class imbalance effectively.


<!-- ## 🔮 Future Improvements

-   **Local Explanations:** Integrate `SHAP` or `LIME` to show users *why* a specific prediction was made by highlighting key words in the description.
-   **Advanced NLP Models:** Experiment with transformer-based models like BERT or DistilBERT for feature extraction to potentially improve accuracy.
-   **Deployment:** Deploy the application to a cloud service like Streamlit Community Cloud, Heroku, or AWS for public access.
-   **Database Integration:** Connect the app to a database to log prediction requests and user feedback, which can be used for continuous model improvement. -->

