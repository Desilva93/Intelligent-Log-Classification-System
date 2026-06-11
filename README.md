# Intelligent Log Classification System

## Overview

The Intelligent Log Classification System is a hybrid NLP-powered framework designed to automatically categorize enterprise and application logs. The system combines rule-based methods, machine learning models, and Large Language Models (LLMs) to efficiently handle logs with varying levels of complexity.

By integrating multiple classification strategies, the framework provides accurate and scalable log categorization for monitoring, debugging, and operational analysis.

---
## System Architecture

![System Architecture](resources/architecture.png)

---

## Hybrid Classification Framework

The system uses a three-stage classification pipeline:

### 1. Regex-Based Classification

The first stage handles predictable and structured log patterns using predefined regular expression rules.

Examples:

* HTTP status logs
* Authentication events
* IP blocking messages
* System activity logs

### 2. Sentence Transformer + Logistic Regression

For logs that cannot be classified through regex, semantic embeddings are generated using Sentence Transformers.

These embeddings are passed to a Logistic Regression classifier trained on labeled log data.

Advantages:

* Captures contextual meaning
* Works well with sufficient training examples
* Fast inference

### 3. LLM-Based Classification

When logs are ambiguous or insufficient labeled examples exist, the system uses Large Language Models (LLMs) to determine the appropriate category.

This stage is particularly useful for:

* Legacy systems
* Rare events
* Complex workflow failures
* Deprecation notices

---

## System Architecture

```text
Input Log Messages
        │
        ▼
 Regex Classifier
        │
        ▼
Sentence Transformer
        │
        ▼
Logistic Regression
        │
        ▼
    LLM Layer
        │
        ▼
 Classified Output
```

---

## Project Structure

```text
Intelligent-Log-Classification-System/
│
├── models/
│   └── Saved Logistic Regression model
│
├── resources/
│   ├── test.csv
│   ├── output.csv
│
├── training/
│   ├── Model training scripts
│   ├── Dataset files
│   └── Experiment notebooks
│
├── classify.py
├── processor_regex.py
├── processor_bert.py
├── processor_llm.py
├── server.py
├── requirements.txt
└── .env
```

---

## Technologies Used

### Backend

* FastAPI
* Uvicorn

### Machine Learning

* Scikit-Learn
* Logistic Regression
* DBSCAN

### NLP

* Sentence Transformers
* Regular Expressions
* BERT

### LLM

* Groq API
* Llama Models

### Data Processing

* Pandas
* NumPy

---

## Installation

### Clone Repository

```bash
git clone https://github.com/Desilva93/Intelligent-Log-Classification-System.git
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Configure Environment Variables

Create a `.env` file and add:

```text
GROQ_API_KEY=your_api_key_here
```

---

## Running the Application

Start the FastAPI server:

```bash
uvicorn server:app --reload
```

Server URLs:

```text
http://127.0.0.1:8000
```

---

## Input Format

Upload a CSV file containing:

| Column      | Description               |
| ----------- | ------------------------- |
| source      | System generating the log |
| log_message | Log text to classify      |

Example:

```csv
source,log_message
ModernCRM,User login successful
LegacyCRM,Workflow execution failed due to missing dependency
```

---

## Output Format

The system generates a classified CSV file containing:

| Column       | Description          |
| ------------ | -------------------- |
| source       | Log source           |
| log_message  | Original log message |
| target_label | Predicted category   |

Example:

```csv
source,log_message,target_label
ModernCRM,User login successful,User Activity
LegacyCRM,Workflow execution failed,Workflow Error
```

---
