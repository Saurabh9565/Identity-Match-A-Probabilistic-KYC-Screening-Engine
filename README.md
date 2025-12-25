# Identity-Match-A-Probabilistic-KYC-Screening-Engine(Anti-Money Laundering)

📌 Project Overview

In the financial and insurance sectors, organizations must constantly screen their customers against "Blacklists" (Sanctions, PEPs, or Defaulters) to remain compliant with Anti-Money Laundering (AML) and KYC (Know Your Customer) regulations.

This project is a Proof of Concept (POC) developed to automate the identification of high-risk policyholders. Since real-world data is often "noisy" (typos, variations in names, different date formats), this engine uses probabilistic fuzzy matching rather than exact matching to ensure no potential threat is missed.

🛠 Tech Stack

Platform: Databricks
Language: PySpark (Python)
Algorithms: Jaro-Winkler Similarity
Data Handling: Spark DataFrames


🧠 The Logic & Scoring Model

The engine compares a Policyholder Dataset against a Blacklist Dataset across two key dimensions. Each dimension is assigned a weight based on its reliability in identifying an individual:

Attribute      Logic / Algorithm	    Weight	                Description
  Name	          Jaro-Winkler	       80%	       Handles typos and name transpositions
  DOB            Near-Date Logic       20%             Matches exact/almost dates 


The Threshold
Confidence Score > 80%: High-probability match. These records are flagged for an high risk
Confidence Score < 80%: No match / Low risk.

🚀 Key Features
Fuzzy Matching: Uses the Jaro-Winkler distance, which is superior for names as it gives more weight to the prefix of the string.
Weighted Aggregation: A custom formula calculates a final "Confidence Score" across multiple data points.
Scalability: Built on PySpark to ensure the logic can handle millions of policyholder records in a production environment.
Data Normalization: Includes steps to clean names and format dates before comparison.

📁 Repository Structure
Identity_Match_Engine.ipynb: The complete Databricks notebook containing the code and rendered outputs.
requirements.txt: Necessary libraries (e.g., jellyfish).
data: Sample synthetic datasets used for the POC.

👨‍💻 Author
Saurabh Kumar Gupt
LinkedIn: https://www.linkedin.com/in/saurabh-kumar-gupt/
