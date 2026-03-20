# Predictive-Modeling-for-Police-Stop-Fairness-Analysis
A machine learning audit of racial bias in San Diego Police Department traffic stop outcomes, using 383,027 stop records from the Stanford Open Policing Project (2014–2017).

**Overview**
This project investigates whether race independently predicts search, arrest, and contraband outcomes in SDPD traffic stops after controlling for stop reason, service area, time of day, and other contextual factors. It is intended as a civil-rights audit tool, not a predictive policing system.

**Research Questions**
What factors predict whether a traffic stop results in an arrest?
What factors predict whether an officer conducts a search?
Conditional on a search occurring, what predicts whether contraband is found?

**Methods**
Models: Logistic Regression (interpretable, odds-ratio output) and Random Forest (predictive benchmark)
Evaluation: AUC-ROC, F1, precision/recall, logistic odds ratios by race, grouped Gini feature importance, and contraband hit-rate benchmarking
Train/test split: Temporal (pre–October 2016 training; October 2016–March 2017 holdout) to prevent data leakage across policy-change boundaries
Class imbalance: Addressed via balanced class weights (arrest rate 1.3%, search rate 4.3%)

**Key Findings**
Black individuals face 2.25× higher odds of being searched than otherwise-identical white individuals; Hispanic individuals face 1.53× higher odds
Despite higher search rates, Black and Hispanic individuals yield contraband at 2.2–3.4 percentage points lower rates than white individuals — indicating a lower evidentiary threshold is applied at the point of search
Subject race is the second-most-important predictor of search decisions in the Random Forest model (18.3% grouped importance), trailing only stop reason (39.5%)

**Data**
Stanford Open Policing Project — San Diego extract
383,027 stops · January 2014 – March 2017
https://openpolicing.stanford.edu

**Ethical Note**
The models in this repository are diagnostic audit tools only. Subject race must never be used as input to any real-time stop or search decision. See the limitations section of the report for a full discussion of causal inference constraints and misuse risks.
