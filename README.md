# Intelligent Log Classification System

A Hybrid NLP-powered log classification framework that combines **Regex Rules**, **Sentence Transformers**, **Machine Learning**, and **Large Language Models (LLMs)** to automatically categorize system logs with high accuracy and scalability.

---

## Project Overview

Modern applications generate massive amounts of logs from servers, databases, authentication systems, cloud services, and network devices. Manually analyzing these logs is time-consuming and error-prone.

This project implements an intelligent multi-stage classification pipeline that automatically assigns categories to log messages using:

* Rule-Based Classification (Regex)
* Semantic Classification (Sentence Transformers + Logistic Regression)
* LLM-Based Classification for unseen logs

The hybrid architecture ensures both speed and accuracy by selecting the most suitable classification strategy for each log message.

---

## Problem Statement

Organizations rely on logs to monitor application health and diagnose issues. Traditional log monitoring systems struggle when:

* New log patterns appear
* Error messages vary significantly
* Rules become difficult to maintain
* Large volumes of logs need processing

This project addresses these challenges by combining traditional NLP techniques with modern Large Language Models.

---

## Solution Architecture

```text
Incoming Log Message
        │
        ▼
 ┌─────────────────┐
 │ Regex Matching  │
 └─────────────────┘
        │
   Match Found?
      /      \
    Yes       No
    │          │
    ▼          ▼

 Return    Sentence Transformer
 Category          │
                   ▼
         Logistic Regression
                   │
          High Confidence?
             /       \
           Yes        No
           │           │
           ▼           ▼

       Return         LLM
      Category   Classification
                       │
                       ▼
                Return Category
```

---

## Classification Approaches

### 1. Regex-Based Classification

Used for structured and predictable log patterns.

Example:

```text
User login successful
```

Advantages:

* Fast execution
* Easy interpretation
* No training required

---

### 2. Sentence Transformer + Logistic Regression

For categories with sufficient training examples.

Workflow:

```text
Log Message
      │
      ▼
Sentence Transformer
      │
      ▼
Embedding Vector
      │
      ▼
Logistic Regression
      │
      ▼
Predicted Category
```

Advantages:

* Captures semantic meaning
* Lightweight inference
* High classification accuracy

---

### 3. LLM-Based Classification

Used when confidence from previous stages is low or when logs contain unseen patterns.

Example:

```text
Unexpected timeout while synchronizing distributed cache cluster
```

Advantages:

* Understands context
* Handles previously unseen logs
* Strong generalization ability

---

## Features

* Hybrid AI Architecture
* Multi-Stage Classification Pipeline
* Semantic Text Understanding
* LLM Fallback Mechanism
* FastAPI Deployment
* Scalable Design
* Production-Oriented Workflow

---

## Technology Stack

### Programming Language

* Python

### Natural Language Processing

* Sentence Transformers
* Hugging Face Transformers

### Machine Learning

* Logistic Regression
* Scikit-Learn

### Backend

* FastAPI
* Uvicorn

### Data Processing

* Pandas
* NumPy

### Large Language Models

* OpenAI Compatible Models
* DeepSeek Models
* Llama Models

---

## Project Structure

```text
Intelligent-Log-Classification-System/
│
├── classify.py
├── server.py
├── requirements.txt
├── README.md
│
├── models/
├── resources/
├── training/
├── notebooks/
│
└── screenshots/
    ├── architecture.png
    └── demo.png
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/Desilva93/Intelligent-Log-Classification-System.git

cd Intelligent-Log-Classification-System
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Application

Start the FastAPI server:

```bash
uvicorn server:app --reload
```

Open:

```text
http://127.0.0.1:8000/docs
```

to access the interactive API documentation.

---

## API Example

### Request

```json
{
  "log": "Database connection timeout"
}
```

### Response

```json
{
  "category": "Database Error"
}
```

---

## Sample Predictions

| Log Message                         | Predicted Category |
| ----------------------------------- | ------------------ |
| User login successful               | Authentication     |
| Password validation failed          | Authentication     |
| Database connection timeout         | Database Error     |
| Packet loss detected                | Network Issue      |
| Service unavailable due to overload | System Failure     |

---

## Skills Demonstrated

* Natural Language Processing (NLP)
* Sentence Embeddings
* Text Classification
* Machine Learning
* Large Language Models (LLMs)
* Prompt Engineering
* FastAPI Development
* Model Deployment
* Hybrid AI Systems

