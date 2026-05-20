Arabic AI-Generated Text Detection Using Big Data Analytics


Key Results
Metric	Value
Best Accuracy	95.62% (Logistic Regression)
Best AUC	96.72% (Logistic Regression)
Best F1-Score	95.29% (Logistic Regression)
Streaming Accuracy	100% on test samples
 Overview
This project develops a complete big data pipeline for detecting AI-generated Arabic academic abstracts. Using Apache Spark for distributed processing, the system:

Processes 41,940 Arabic abstracts (human-written + AI-generated from 4 LLMs)

Implements Arabic-specific text preprocessing (diacritic removal, normalization, stop-word filtering, ISRI stemming)

Engineers hybrid features combining TF-IDF vectors with stylometric features

Trains and evaluates 4 classification models

Demonstrates real-time inference via file-based streaming

Analyzes scalability on distributed infrastructure

 Dataset
Source: KFUPM-JRCAI/arabic-generated-abstracts (Hugging Face)

Distribution
Label	Count	Percentage
Human (1)	33,552	80%
AI (0)	8,388	20%
AI Models Used
Allam

Jais (bilingual Arabic-English LLM)

LLaMA

OpenAI/GPT

Source Splits
Split	Count
by_polishing	14,255
from_title_and_content	12,870
from_title	14,815
🏗️ System Architecture
text
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Data Loading   │───▶│  Preprocessing   │───▶│ Feature Engine  │
│  (Hugging Face) │    │  (Spark UDFs)    │    │  (TF-IDF +      │
└─────────────────┘    └──────────────────┘    │  Stylometric)   │
                                                └────────┬────────┘
                                                         │
┌─────────────────┐    ┌──────────────────┐    ┌─────────▼────────┐
│  Streaming      │◀───│  Model Training  │◀───│  Model Training  │
│  Inference      │    │  (4 Classifiers) │    │  Pipeline        │
└─────────────────┘    └──────────────────┘    └──────────────────┘
 Technical Stack
Component	Technology
Big Data Framework	Apache Spark 4.0.2
Language	Python 3.9+
Data Format	Parquet
Stream Processing	Spark Structured Streaming
Arabic NLP	PyArabic, NLTK (ISRIStemmer)
Machine Learning	Spark MLlib
